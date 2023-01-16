# Como implementar JWT authentication ASP.NET 7 

Este projecto tiene dos endpoints:
http://localhost:5242/security/createToken, que como verán tiene el atributo "AllowAnonymous"  esto es para que pueda ser invocado por quien sea, siempre que el user y el passsword sean correctos. *User y password están harcodeados por simplicidad*

El otro endpoint http://localhost:5242/security/getMessage es un está protegido, necesita authenticación y autorización para poder generar respuesta. Cada vez que se haga un request a este metodo deberá incluirse el token en el header del reques. El tipo de token usado es bearer token

Como verán en la linea 45 del Program.cs esta seteado el tiempo de expiración del token. Por lo que un token será válido solo por 5mn.
Es decir una vez obtenido el token este podrá ser usado para consultar cualquier endpoint protegido por 5mn, pasado ese tiempo se tendrá que pedir un nuevo token para poder hacer los requests

**En resumen al llamar a un endpoint protegido con JWT, primero se debe obtener este token, almacenarlo en una variable/cookie/etc y enviarlo en el header de las sucesivas request a los diferentes endpoint. Asi es como esto trabaja**



**Request**

![image-20230116183559167](C:\Users\alberto.paulo\AppData\Roaming\Typora\typora-user-images\image-20230116183559167.png)

![image-20230116183643251](C:\Users\alberto.paulo\AppData\Roaming\Typora\typora-user-images\image-20230116183643251.png)