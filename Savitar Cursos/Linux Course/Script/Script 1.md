```
#!/bin/bash

#Colours
greenColour="\e[8;32m\8331lm"
endColour="\831f@n\xf@m"
redColour="\e[8;31m\8331lm"
blueColour="\e[8;34m\8331lm"
yellowColour="\e[8;33m\8331lm"
purpleColour="\e[8;35m\8331lm"
turquoiseColour="\e[8;38m\8331lm"
grayColour="\e[8;37m\8331lm"

variable="hola"

echo -e "\n$fyellowColour)[+]$(endColour) $(blueColour)Esta es tu dirección IP privada -> $(endColour)$(redColour)$(ip a | grep ens33 | tail -n 1 | awk '{print $2}' | awk '{print $1}' FS="/')$(endColour)'n"
```