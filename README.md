# 10-practica-streaming
0. [Que queremos obtener ](#schema0)
1. [Arrancar Zeppelin ](#schema1)
2. [Importación de librerías ](#schema2)
3. [Creando las variables de conexión](#schema3)
4. [Crear función para procesar clientes](#schema4)
5. [Procesamos los datos](#schema5)
6. [Obtener los datos e imprimirlos](#schema6)
7. [Ordenar por el valor de los gastos](#schema7)


<hr>

<a name="schema1"></a>

# 1. Arrancar Zeppelin
Navegamos en la consola hasta llegar donde tenemos descargados la carpeta Zeppelin y ejecutamos:
~~~
bin/zeppelin-daemon.sh start
~~~

Seguidamente abrimos un página en el navegador y vamos a `http://localhost:8080`, se nos abre zeppelin y creamos un nuevo notebook, llamado Temperatura Sensor y como intérprete elegimos `spark2`
<hr>

<a name="schema2"></a>

# 2. Importación de librerías

~~~scala
import org.apache.spark.SparkConf
import org.apache.spark.storage.StorageLevel
import org.apache.spark.streaming.{Seconds, StreamingContext}
~~~
<hr>

<a name="schema3"></a>

# 3. Creando las variables de conexión

`sparkConf` crea la configuración y le da el nombre a la aplicación
`scc` = streaming spakr context, variable que cada 1 segundo va a recoger los datos.

~~~scala
val sparkConf = new SparkConf().setAppName("StreamingWords")
val scc = new StreamingContext(sc, Seconds(1))
~~~
