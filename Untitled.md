# Encotrar Usuarios y Grupos en Linux

---


## Y pa' que 

Ay veses que estamos trabajando con un servidor que tiene mas de un 
usuario o grupo. Por cualquier razon sea en el presente o en el futuro 
se tendra que haser un cambio con un grupo o un usuario. Y la neta puede
ser un problema grande el estar buscando nombres en el systema manual mente. 
Ay varias maneras de poder aser este trabajo un poco mas facil. Pero 
primero vamos a ver los comandos desde su base y agregarle complejisidad.

### Vuscate a los usuarios

El archivo que tiene la lista de usuarios se encuentra en **/etc/passwd**.
Si usamos el commando de **cat**, 

```bash
cat /etc/passwd
```

para producir la lista en la termial vamos a ver que va a producir una lista 
larga de no solo usuarios sino tambien de servicios y sus archivos. Si usamos un 
poco de **regex** y el commando **grep** podemos definir un poco mas la lista y filtrar
el resultado a uno que podamos leer con mas facilidad. Si usamos el mismo comando de **cat** 
y usamos una pipa redirijiendo el resultado a **grep**,

```bash
cat /etc/passwd | grep '/bin/bash'
```

usando el filtro de **'/bin/bash'**, mas o menos diciendole a grep que te de los 
resultados de cada linea que tenga **/bin/bash** presente. En el resultado vamos a ver
que la lista se achico y tenemos un resultado con los nombres de todos los usuarios 
empesando con el usuario **root** y los demas usuarios conforme fueron creados. 

Logico de que si un systema tiene muchos usuarios, tendremos que ser mas 
especificos con el filtro que le damos al commando **grep**. Eso lo dejamos para otra 
ocasion, por el momento tenemos una base por la cual podemos empesar a encontrar 
informacion que podemos usar. 

Cada usuario tendra un identificador llamado **UID** "User ID". Esto es diferente a el identificador que tienen los grupos
que se llama **GUID**. Cuando la terminal nos da los resultados, vemos que la informacion nos es dada en un tipo de formato.
Explicare el formato para que todo tenga sentido.

```bash
drod:x:1000:10:drod:/home/drod:/bin/bash
```

| drod | x | 1000 | 10 | drod | /home/drod | /bin/bash | 
| nombre del usuario | contrasena encripta existe | UID | GID | directorio del usuario | el shell que usa el usuario | 


### Vuscate los grupos 

Cuando nesesitamos que ver a la lista de grupos, si es nesesario vuscarlos,la logica es la misma nomas que tenemos que 
poner atencion a uno pocos detalles. 

Ay servicios y usarios en el systema de linux que pertenses a grupos. Los grupos son 
importantes en linux para separa tales servicios y 
usuarios conforme a los permisos que cada grupo tenga para poder usar los recursos de tu 
computadora. Cada grupo tiene un identificador llamado **GID** "Group ID" en forma de numero.
Siertos numberos son reservados por el systema para siertos grupos usados por el systema. Como por ejemplo, 
el usuario **root** pertenese al grupo con el **GID** de 0. Cuando un administrador agrega
grupos al systema, el systema les dara **GID** a esos grupos empesando con el numero 1000. 
Saviendo esto, sera mas facil encontrar los grupos creados por el administrador.

Usando el comando de **cat** para producir la informacion que se encuentra en **/etc/group**, 

```bash
cat /etc/group
```

vamos a ver la lista completa de los grupos en el systema. Usando la pipa para redirijir nuestro 
comando asia **grep** y usando filtros, podemos aser la lista mas reconosible. 

```bash
cat /etc/group | grep '1[0-9][0-9][0-9]'
```





