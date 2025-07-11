Pra trabajar con los lv vg y los pv necesitamos instalar lvm2
```
apt install lvm2
```


Para ver los discos que tenemos disponibles
```
root@lolo:/home/adri# lsblk
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda                         8:0    0   20G  0 disk
├─sda1                      8:1    0    1M  0 part
├─sda2                      8:2    0  1.8G  0 part /boot
└─sda3                      8:3    0 18.2G  0 part
  └─ubuntu--vg-ubuntu--lv 252:0    0   10G  0 lvm  /
sdb                         8:16   0    5G  0 disk
└─vg_first-primer_lv      252:1    0    5G  0 lvm  /mnt/Primer_LV
sdc                         8:32   0    5G  0 disk
sdd                         8:48   0    5G  0 disk
sde                         8:64   0    5G  0 disk
sr0                        11:0    1 1024M  0 rom
```

Tambien podemos utilizar 
```
root@lolo:/home/adri# fdisk -l
Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors
Disk model: VMware Virtual S
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F8120B6D-BE70-49CB-AB97-90BAA755C921

Device       Start      End  Sectors  Size Type
/dev/sda1     2048     4095     2048    1M BIOS boot
/dev/sda2     4096  3719167  3715072  1.8G Linux filesystem
/dev/sda3  3719168 41940991 38221824 18.2G Linux filesystem


Disk /dev/sdc: 5 GiB, 5368709120 bytes, 10485760 sectors
Disk model: VMware Virtual S
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 5 GiB, 5368709120 bytes, 10485760 sectors
Disk model: VMware Virtual S
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdd: 5 GiB, 5368709120 bytes, 10485760 sectors
Disk model: VMware Virtual S
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sde: 5 GiB, 5368709120 bytes, 10485760 sectors
Disk model: VMware Virtual S
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

Pra crea los pv o Phisical Volume
```
pvcreate /dev/sdb
pvcreate /dev/sdc
```

Para verificarlos
```
root@lolo:/home/adri# pvs
  PV         VG        Fmt  Attr PSize  PFree
  /dev/sda3  ubuntu-vg lvm2 a--  18.22g 8.22g
  /dev/sdb   vg_first  lvm2 a--  <5.00g    0
  /dev/sdc             lvm2 ---   5.00g 5.00g

```

Para crea los vg o Volumen Group
```
		 VG_name   PV_location 	
vgcreate vg_first /dev/sdb
```

Psra revisar los vg
```
root@lolo:/home/adri# vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- 18.22g 8.22g
  vg_first    1   1   0 wz--n- <5.00g    0

```

Crear un lv con un tamaño especifico de la capacidad del VG al que pertenecera
```
					LV_name	  VG_name
lvcreate -L 2.5G -n primer_lv vg_first
```

Revisar los lv
```
root@lolo:/home/adri# lvs
  LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 10.00g
  primer_lv vg_first  -wi-ao---- <5.00g
```

Tambien puedes expecificar el LV
```
lvdisplay /dev/vg_first/primer_lv
```

Dar formato al filesystem tene en cuenta que  /dev/vg_first/primer_lv y /dev/mapper/vg_first-primer_lv son lo mismo por lo tanto son validas las dos por preferencias del trabajo siempre utilizaremos  /dev/mapper/vg
```
mkfs.ext4 /dev/mapper/vg_first-primer_lv
mkfs.ext4 /dev/vg_first/primer_lv
```

Crearemos el punto de montaje donde queramos montar
```
mkdir Primer_LV
```

Montaremos el filesystem
```
mount /dev/mapper/vg_first-primer_lv /mnt/Primer_LV/
```

Si nuestro VG tiene aun espacio disponible podemos ampliar el tamaño del LV de las siguientes maneras

```
#Para darle todo el espacio libre que tiene el VG
lvextend -l +100%FREE /dev/mapper/vg_first-primer_lv

#Para darle lo que estimemos conveniente
lvextend -L +5G /dev/mapper/vg_first-primer_lv

```

Para que el filesystem lo detecte debemos hacer un resize2fs
```
resize2fs /dev/mapper/vg_first-primer_lv
```


Extender un VG agregando otro PV primero verificamos los PV disponibles con el pvs

```
root@lolo:/home/adri# pvs
  PV         VG        Fmt  Attr PSize  PFree
  /dev/sda3  ubuntu-vg lvm2 a--  18.22g 8.22g
  /dev/sdb   vg_first  lvm2 a--  <5.00g    0
  /dev/sdc             lvm2 ---   5.00g 5.00g

#Extender el VG
vgextend VG PV 

root@lolo:/home/adri# vgextend vg_first /dev/sdc
  Volume group "vg_first" successfully extended
```

Revisamos
```
root@lolo:/home/adri# pvs
  PV         VG        Fmt  Attr PSize  PFree
  /dev/sda3  ubuntu-vg lvm2 a--  18.22g  8.22g
  /dev/sdb   vg_first  lvm2 a--  <5.00g     0
  /dev/sdc   vg_first  lvm2 a--  <5.00g <5.00g

root@lolo:/home/adri# vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- 18.22g  8.22g
  vg_first    2   1   0 wz--n-  9.99g <5.00g

```

Estos nuevos epacios libres pudieramos asignarlos a un nuevo LV 