1. Obtener el elemento ‘nombre’ del instituto (Ojo! El nombre del ciclo no!)
<nombre>IES Abastos</nombre>

Xpath:
/ies/nombre

2. Obtener el elemento web
<web>http://www.iesabastos.org</web>

Xpath:
/ies/web

3. Del elemento web anterior, extraer sólo el texto
http://www.iesabastos.org

Xpath:
/ies/web/text()

4. Extraer todos los elementos <ciclo>

Xpath:
/ies/ciclos/ciclo

5. Extraer los nombres de los ciclos formativos:

Administración de Sistemas Informáticos en Red
Desarrollo de Aplicaciones Web
Sistemas Microinformáticos y Redes

Xpath:

//ciclos/ciclo/nombre/text()

6. Obtener todas los nodos <horasAnuales> partiendo del elemento <ciclos>:

Xpath:
//ciclos/ciclo/horasAnuales

7. Obtener todos los nodos <ciclo> con la expresión más corta posible (usa //):

Xpath:
//ciclos

8. Obtener los atributos id de los ciclos:

id="ASIR"
id="DAW"
id="SMR”

Xpath:
//ciclos/ciclo/@id

9. Años en los que se publicaron los decretos de los títulos de los Ciclos 
Formativos:

año="2009"
año="2010"
año="2008"

Xpath:
//ciclos/ciclo/decretoTitulo/@año

10. Escribe una expresión que devuelva todos los elementos nombre, tanto los de los ciclos, como el del ies:

<nombre>IES Celia</nombre>
<nombre>Administración de Sistemas Informáticos en
Red</nombre>
<nombre>Desarrollo de Aplicaciones Web</nombre>
<nombre>Sistemas Microinformáticos y Redes</nombre>

Xpath:
/ies//nombre