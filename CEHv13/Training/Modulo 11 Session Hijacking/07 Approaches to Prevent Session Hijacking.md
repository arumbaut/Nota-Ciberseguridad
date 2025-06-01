**▪ HTTP Strict Transport Security (HSTS)**

HTTP Strict Transport Security (HSTS) is a web security policy that protects HTTPS websites against MITM attacks. The HSTS policy helps web servers force web browsers to interact with them using HTTPS

**▪ Token Binding** **:**El enlace de tokens protege la comunicación cliente-servidor contra los ataques de secuestro de sesión. El cliente crea un par de claves pública-privada para cada conexión a un servidor remoto. Cuando un cliente se conecta al servidor, genera una firma utilizando su clave privada y envía esta firma junto con su clave pública al servidor. El servidor verifica la firma utilizando la clave pública del cliente. Esto asegura que el mensaje fue enviado por un cliente auténtico, ya que solo el cliente posee su clave privada. Incluso si un atacante captura la firma, no es posible que regenere la firma o la reutilice para otra conexión.

**Approaches to Prevent MITM Attacks**

**▪ DNS over HTTPS**

DNS over HTTPS (DoH) is an enhanced version of the DNS protocol that is used to prevent the peeking or snooping of user’s web activities or DNS queries during the DNS lookup process. Implementing DNS over HTTPS makes the traffic undetectable by the attackers or ISPs since it gets hidden within the normal traffic passing through the HTTPS port.

**▪ WPA3 Encryption**

Wireless Protected Access 3 (WPA3) is a wireless protocol intended to protect the traffic sent and received by users over a wireless network.

**▪ VPN**

A VPN creates a safe and encrypted tunnel over a public network to securely send and receive sensitive information. It creates a subnet by using key-based encryption for secure communication between endpoints.

**▪ Two-Factor Authentication, ▪ Password Manager**

**IPsec**

IPsec (Internet Protocol Security) es un conjunto de protocolos desarrollados por la Internet Engineering Task Force (IETF) para soportar el intercambio seguro de paquetes en la capa IP. Asegura una seguridad basada en criptografía interoperable para IPv4 e IPv6, y soporta autenticación de pares a nivel de red, autenticación de origen de los datos, integridad de los datos, confidencialidad de los datos (cifrado) y protección contra repetición.

**Modes of IPsec****:**

**▪ Transport Mode**

In transport mode, IPsec encrypts only the payload of the IP packet and not the IP header. IP headers remain intact, and only the data payload is encrypted or authenticated. This mode is used for end-to-end communications between two hosts.

**▪ Tunnel Mode**

In tunnel mode, IPsec encapsulates the entire IP packet (payload and IP header) and then encrypts the entire packet. This encapsulated packet becomes the payload for a new IP packet with a new IP header.

**Session Hijacking Prevention Tools**
▪ Checkmarx One SAST Source: https://checkmarx.com
▪ Fiddler Source: https://www.telerik.com
▪ Nessus (https://www.tenable.com)
▪ Invicti (https://www.invicti.com)
▪ Wapiti (https://wapiti-scanner.github.io)