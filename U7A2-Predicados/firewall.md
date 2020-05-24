1. Expresión Xpath para seleccionar el tercer servicio (FTP)

/services/service[3]

<service>
  <short>FTP</short>
  <description>FTP is a protocol used for remote file transfer. If you plan to make your FTP server publicly available, enable this option. You need the vsftpd package installed for this option to be useful.</description>
  <port protocol="tcp" port="21"/>
  <module name="nf_conntrack_ftp"/>
</service>


2. Expresión Xpath para obtener el elemento port del tercer servicio.

/services/service[3]/port

<port protocol="tcp" port="21"/>


3. Expresión Xpath para seleccionar sólo el elemento descripción del 5º de los servicios.

/services/service[position()<=5]/description

<description>The Domain Name System (DNS) is used to provide and request host and domain names. Enable this option, if you plan to provide a domain name service (e.g. with bind).</description>
<description>This allows a DHCP server to accept messages from DHCP clients and relay agents.</description>
<description>FTP is a protocol used for remote file transfer. If you plan to make your FTP server publicly available, enable this option. You need the vsftpd package installed for this option to be useful.</description>
<description>The Network Time Protocol (NTP) allows to synchronize computers to a time server. Enable this option, if you are providing a NTP server. You need the ntp or chrony package installed for this option to be useful.</description>
<description>MySQL Database Server</description>

4. Expresión Xpath para obtener el último servicio (imagina que a priori no sabes
cuantos hay, por tanto, poner un número concreto NO es una solución viable)

/services/service[last()]

<service>
  <short>squid</short>
  <description>Squid HTTP proxy server</description>
  <port protocol="tcp" port="3128"/>
</service>


5. Expresión Xpath para obtener todos los puertos del primer servicio. Haz uso de la
función position

//service[position()=1]/port

<port protocol="tcp" port="53"/>
<port protocol="udp" port="53"/>


6. Expresión XPATH para obtener el puerto del penúltimo servicio.

//service[last()-1]/port

<port protocol="tcp" port="22"/>


7. Expresión Xpath para obtener el atributo name del elemento module del tercer
servicio.

//service[3]/module[@name]

<module name="nf_conntrack_ftp"/>


8. Expresión Xpath para obtener los elementos port cuyo atributo protocol valga udp.

//service/port[@protocol = 'udp']

<port protocol="udp" port="53"/>
<port protocol="udp" port="67"/>
<port protocol="udp" port="123"/>


9. Expresion Xpath para del 2º al 4º servicio.

//service[position() >=2 and position()<=4]

<service>
  <short>DHCP</short>
  <description>This allows a DHCP server to accept messages from DHCP clients and relay agents.</description>
  <port protocol="udp" port="67"/>
</service>
<service>
  <short>FTP</short>
  <description>FTP is a protocol used for remote file transfer. If you plan to make your FTP server publicly available, enable this option. You need the vsftpd package installed for this option to be useful.</description>
  <port protocol="tcp" port="21"/>
  <module name="nf_conntrack_ftp"/>
</service>
<service>
  <short>Network Time Protocol (NTP) Server</short>
  <description>The Network Time Protocol (NTP) allows to synchronize computers to a time server. Enable this option, if you are providing a NTP server. You need the ntp or chrony package installed for this option to be useful.</description>
  <port protocol="udp" port="123"/>
</service>


10. Expresión para obtener el elemento servicio que tenga como hijo al elemento module
(OJO!! que lo que tienes que obtener debe ser un nodo servicio)

//service[module]

<service>
  <short>FTP</short>
  <description>FTP is a protocol used for remote file transfer. If you plan to make your FTP server publicly available, enable this option. You need the vsftpd package installed for this option to be useful.</description>
  <port protocol="tcp" port="21"/>
  <module name="nf_conntrack_ftp"/>
</service>


11. Selecciona todos los nodos module cuyo atributo port valga 53

-- No se si tienes que mostrar el module o el servicio porque module solo tiene atributo name y es en un unico servicio con el nodo module.
--solo los puertos = 53

//service/port[@port ="53"]

<port protocol="tcp" port="53"/>
<port protocol="udp" port="53"/>


--Servicio completo con puerto = 53

//service[port[@port ="53"]]

<service>
  <short>DNS</short>
  <description>The Domain Name System (DNS) is used to provide and request host and domain names. Enable this option, if you plan to provide a domain name service (e.g. with bind).</description>
  <port protocol="tcp" port="53"/>
  <port protocol="udp" port="53"/>
</service>


12. Selecciona todos los nodos module cuyo atributo port sea mayor de 1000.

--solo los puertos > 1000

//service/port[@port >"1000"]

<port protocol="tcp" port="3306"/>
<port protocol="tcp" port="3128"/>


--Servicio completo con puerto = 53

//service[port[@port >"1000"]]

<service>
  <short>MySQL</short>
  <description>MySQL Database Server</description>
  <port protocol="tcp" port="3306"/>
</service>
<service>
  <short>squid</short>
  <description>Squid HTTP proxy server</description>
  <port protocol="tcp" port="3128"/>
</service>


13. Selecciona todos los nodos module, cuyo atributo port valga entre 40 y 70

--solo los puertos  (40-70)

//service/port[@port >"40" and @port < "70"]

<port protocol="tcp" port="53"/>
<port protocol="udp" port="53"/>
<port protocol="udp" port="67"/>


--Servicio completo con puerto (40-70)

//service[port[@port >"40" and @port < "70"]]

<service>
  <short>DNS</short>
  <description>The Domain Name System (DNS) is used to provide and request host and domain names. Enable this option, if you plan to provide a domain name service (e.g. with bind).</description>
  <port protocol="tcp" port="53"/>
  <port protocol="udp" port="53"/>
</service>
<service>
  <short>DHCP</short>
  <description>This allows a DHCP server to accept messages from DHCP clients and relay agents.</description>
  <port protocol="udp" port="67"/>
</service>


14. Partiendo de la expresión anterior, haz que esta vez seleccione el nodo servicio
completo, de aquellos que tengan un elemento module cuyo atributo port valga entre
40 y 70


--Servicio completo con puerto (40-70)

//service[port[@port >"40" and @port < "70"]]

<service>
  <short>DNS</short>
  <description>The Domain Name System (DNS) is used to provide and request host and domain names. Enable this option, if you plan to provide a domain name service (e.g. with bind).</description>
  <port protocol="tcp" port="53"/>
  <port protocol="udp" port="53"/>
</service>
<service>
  <short>DHCP</short>
  <description>This allows a DHCP server to accept messages from DHCP clients and relay agents.</description>
  <port protocol="udp" port="67"/>
</service>