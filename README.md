
## **API REST**

### **Main page (MainPageRestApi.class)**

 * __GET__ /rest = **Get user loged.**
 	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserDTO.class") 
            ```json 
            {
                "id": 143,
                "user": {
                    "city": "Valencia",
                    "code": "46021",
                    "country": "España",
                    "direccion": "Calle Serpis 17",
                    "email": "usuario1@usuario.com",
                    "estado": 0,
                    "lat": 0.2123,
                    "lon": 0.13456,
                    "numImg": 1,
                    "password": "$2a$10$q5DtZk6jEDS9f.a7M3ekf.Zidm.7BVuqdLIjx1eeoOqSoj0JUIasu",
                    "rate": 0,
                    "role": "ADMIN",
                    "telf": "12345",
                    "urlImg": "",
                    "username": "usuario1"
                }
            }
            ```
		- Status.FORBIDDEN

* __POST__ /rest/register = **Create a user with rol USER.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("UserRegisterForm.class")
            ```json
                {
                    "username": "usuario1",
                    "password": "password1",
                    "repeatPassword": "password1",
                    "telf": 12345,
                    "email": "usuario1@usuario.com",
                    "city": "Valencia",
                    "country": "España",
                    "code": 46021,
                    "direccion": "Calle Serpis 17",
                    "numImg": 1,
                    "lat": 0.2123,
                    "lon": 0.13456 
                }
            ```
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("UserDTO.class")
            ```json
            {
                "id": 143,
                "user": {
                    "city": "Valencia",
                    "code": "46021",
                    "country": "España",
                    "direccion": "Calle Serpis 17",
                    "email": "usuario1@usuario.com",
                    "estado": 0,
                    "lat": 0.2123,
                    "lon": 0.13456,
                    "numImg": 1,
                    "password": "$2a$10$q5DtZk6jEDS9f.a7M3ekf.Zidm.7BVuqdLIjx1eeoOqSoj0JUIasu",
                    "rate": 0,
                    "role": "ADMIN",
                    "telf": "12345",
                    "urlImg": "",
                    "username": "usuario1"
                }
            }
            ```
		- Status.FORBIDDEN
		- Status.BAD_REQUEST
		- Status.CONFLICT

 * __POST__ /rest/contact = **Send help form.**
 	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("ContactAdminForm.class")
            ```json
            {
                "name": "usuar",
                "email": "usuar@usuario.com",
                "subject": "Subject of the message here",
                "mensaje": "Message to admin here" 
            }
            ```
 	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
	 	- JSON("MensajeDTO.class")
            ```json
            {
                "mensaje": "usuar. Mensaje enviado correctamente, te responderemos a traves de: usuar@usuario.com"
            }
            ```
		- Status.BAD_REQUEST
		- Status.FORBIDDEN

 * __GET__ /rest/error/403 = **Get a forbiden page.**
  	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- Status.FORBIDDEN

### **Admin (AdminRestApi.class)**

* __GET__ /rest/admin = **Get admin dashboard info.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("AdminDTO.class")
           ```json
           {   
               "totalAltaItems": 0,
               "totalAyudas": 0,
               "totalItems": 0,
               "totalUsers": 2 
            }
            ```

* __GET__ /rest/admin/totalAyudas = **Get the number of help contacts that admin has.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("AdminAyudasDTO.class")
            ```json
            { "totalAyudas": 0 }

* __POST__ /rest/admin/createUser = **Create user by admin.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("AdminRegisterForm.class")
           ```json
           { 
                "username": "usuario1",
                "password": "password1",
                "repeatPassword": "password1",
                "telf": 12345,
                "email": "usuario1@usuario.com",
                "city": "Valencia",
                "country": "España",
                "code": 46021,
                "direccion": "Calle Serpis 17",
                "numImg": 1,
                "role": "ADMIN",
                "lat": 0.2123,
                "lon": 0.13456 
            }
            ```
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserDTO.class")
			 ```json
             {  
                "user": { 
                    "city": "Valencia",
                    "code": "46021",
                    "country": "España",
                    "direccion": "Calle Serpis 17",
                    "email": "usuario1@usuario.com",
                    "estado": 1,
                    "lat": 0.2123,
                    "lon": 0.13456,
                    "numImg": 1,
                    "password": "$2a$10$q5DtZk6jEDS9f.a7M3ekf.Zidm.7BVuqdLIjx1eeoOqSoj0JUIasu",
                    "rate": 0,
                    "role": "ADMIN",
                    "telf": "12345",
                    "urlImg": "",
                    "username": "usuario1" },
                "userId": 143 
            }
            ```
		- Status.BAD_REQUEST
		- Status.CONFLICT

* __GET__ /rest/admin/userList = **Get all the users in the aplication filtered.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- QueryParam("userRoles") __->__ _Type of user role filter in the search._
		- QueryParam("estado") __->__ _Status of the user filter in the search._
		- QueryParam("userNombre") __->__ _User name filter in the search._
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserListDTO.class")
			```json
            {
                "size": 3,
                "users": {
                    "entry": [
                        {
                            "key": 1,
                            "value": {
                                "city": "Buenos Aires",
                                "code": "CABA123",
                                "country": "Argentina",
                                "direccion": "Calle corrientes numero 1",
                                "email": "administrador@administrador.com",
                                "estado": 1,
                                "image": "",
                                "lat": 0,
                                "lon": 0,
                                "numImg": 0,
                                "password": "$2a$10$s7v6Xsi2JKHxK9BU3RYP9.ZDHfvVmZppoL9m4Sw0Eshst2a4oUB6O",
                                "rate": 0,
                                "role": "ADMIN",
                                "telf": "123456",
                                "urlImg": "",
                                "username": "administrador"
                            }
                        },
                        {
                            "key": 2,
                            "value": {
                                "city": "Buenos Aires",
                                "code": "CABA123",
                                "country": "Argentina",
                                "direccion": "Calle corrientes numero 2",
                                "email": "user@user.user",
                                "estado": 1,
                                "image": "",
                                "lat": 0,
                                "lon": 0,
                                "numImg": 0,
                                "password": "$2a$10$A8plO/WNh8bKc0/Nw/D4wumOSsjX8dON55Oq3tKuk9/7s741bmjSu",
                                "rate": 0,
                                "role": "USER",
                                "telf": "123456",
                                "urlImg": "",
                                "username": "usuario"
                            }
                        },
                        {
                            "key": 143,
                            "value": {
                                "city": "Valencia",
                                "code": "46021",
                                "country": "España",
                                "direccion": "Calle Serpis 17",
                                "email": "usuario1@usuario.com",
                                "estado": 1,
                                "lat": 0.2123,
                                "lon": 0.13456,
                                "numImg": 1,
                                "password": "$2a$10$q5DtZk6jEDS9f.a7M3ekf.Zidm.7BVuqdLIjx1eeoOqSoj0JUIasu",
                                "rate": 0,
                                "role": "ADMIN",
                                "telf": "12345",
                                "urlImg": "",
                                "username": "usuario1"
                            }
                        }
                    ]
                }
            }
            ```
		- Status.NO_CONTENT

* __GET__ /rest/admin/{id} = **Get the user corresponding with an id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserDTO.class")
			```json
            {
                "id": 1,
                "user": {
                    "city": "Buenos Aires",
                    "code": "CABA123",
                    "country": "Argentina",
                    "direccion": "Calle corrientes numero 1",
                    "email": "administrador@administrador.com",
                    "estado": 1,
                    "image": "",
                    "lat": 0,
                    "lon": 0,
                    "numImg": 0,
                    "password": "$2a$10$s7v6Xsi2JKHxK9BU3RYP9.ZDHfvVmZppoL9m4Sw0Eshst2a4oUB6O",
                    "rate": 0,
                    "role": "ADMIN",
                    "telf": "123456",
                    "urlImg": "",
                    "username": "administrador"
                }
            }
            ```
		- Status.NOT_FOUND

* __PUT__ /rest/admin/{id}/bajaUser = **Suspend the user with the corresponding id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserDTO.class")
			```json
            {
                "id": 143,
                "user": {
                    "city": "Valencia",
                    "code": "46021",
                    "country": "España",
                    "direccion": "Calle Serpis 17",
                    "email": "usuario1@usuario.com",
                    "estado": 0,
                    "lat": 0.2123,
                    "lon": 0.13456,
                    "numImg": 1,
                    "password": "$2a$10$q5DtZk6jEDS9f.a7M3ekf.Zidm.7BVuqdLIjx1eeoOqSoj0JUIasu",
                    "rate": 0,
                    "role": "ADMIN",
                    "telf": "12345",
                    "urlImg": "",
                    "username": "usuario1"
                }
            }
            ```
		- Status.NOT_FOUND

* __PUT__ /rest/admin/{id}/altaUser = **Active the user with the corresponding id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserDTO.class")
			```json
            {
                "id": 143,
                "user": {
                    "city": "Valencia",
                    "code": "46021",
                    "country": "España",
                    "direccion": "Calle Serpis 17",
                    "email": "usuario1@usuario.com",
                    "estado": 1,
                    "lat": 0.2123,
                    "lon": 0.13456,
                    "numImg": 1,
                    "password": "$2a$10$q5DtZk6jEDS9f.a7M3ekf.Zidm.7BVuqdLIjx1eeoOqSoj0JUIasu",
                    "rate": 0,
                    "role": "ADMIN",
                    "telf": "12345",
                    "urlImg": "",
                    "username": "usuario1"
                }
            }
            ```
		- Status.NOT_FOUND

* __PUT__ /rest/admin/{id}/editUser = **Edit the user with the corresponding id.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("AdminUserEditForm.class")
			```json
            {
                "city": "Oliva",
                "code": 46780,
                "country": "España",
                "direccion": "Calle Ernest Lluch 17",
                "lat": 0.653,
                "lon": 0.89456,
                "numImg": 0,
                "telf": 9623
            }
            ```
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserDTO.class")
		    ```json
            {
                "id": 143,
                "user": {
                    "city": "Oliva",
                    "code": "46780",
                    "country": "España",
                    "direccion": "Calle Ernest Lluch 17",
                    "email": "usuario1@usuario.com",
                    "estado": 1,
                    "lat": 0.653,
                    "lon": 0.89456,
                    "numImg": 0,
                    "password": "$2a$10$q5DtZk6jEDS9f.a7M3ekf.Zidm.7BVuqdLIjx1eeoOqSoj0JUIasu",
                    "rate": 0,
                    "role": "ADMIN",
                    "telf": "9623",
                    "username": "usuario1"
                }
            }
            ```
		- Status.NOT_FOUND
		- Status.BAD_REQUEST

* __PUT__ /rest/admin/{id}/editPass =  **Edit the user password with the corresponding id.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("UserEditPassForm.class")
			```json
            {
                "password": "pepe123",
                "repeatPassword": "pepe123"
            }
            ```
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- Status.ACCEPTED
		- Status.BAD_REQUEST
		- Status.NOT_FOUND
		- Status.CONFLICT

* __GET__ /rest/admin/{id}/ventas = **Get all sales of the corresponding user with a given id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserVentasDTO.class")
			```json
                {
                    "itemsvendidos": {
                        "entry": []
                    },
                    "listaventas": {
                        "entry": []
                    },
                    "listcompradores": {
                        "entry": []
                    },
                    "user": {
                        "city": "Oliva",
                        "code": "46780",
                        "country": "España",
                        "direccion": "Calle Ernest Lluch 17",
                        "email": "usuario1@usuario.com",
                        "estado": 1,
                        "lat": 0.653,
                        "lon": 0.89456,
                        "numImg": 0,
                        "password": "$2a$10$/tT3co5vlh5q1noGW8H/rutRYGRQLkmx4aX1qZfHqkWtc7RAqNSYO",
                        "rate": 0,
                        "role": "ADMIN",
                        "telf": "9623",
                        "username": "usuario1"
                    },
                    "userid": 143
                }
                ```
		- Status.NO_CONTENT

* __GET__ /rest/admin/{id}/compras = **Get all purchases of the corresponding user with a given id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserComprasDTO.class")
			```json
            {
                "compras": {
                    "entry": []
                },
                "comprasSize": 0,
                "items": {
                    "entry": []
                },
                "itemsSize": 0,
                "user": {
                    "city": "Oliva",
                    "code": "46780",
                    "country": "España",
                    "direccion": "Calle Ernest Lluch 17",
                    "email": "usuario1@usuario.com",
                    "estado": 1,
                    "lat": 0.653,
                    "lon": 0.89456,
                    "numImg": 0,
                    "password": "$2a$10$/tT3co5vlh5q1noGW8H/rutRYGRQLkmx4aX1qZfHqkWtc7RAqNSYO",
                    "rate": 0,
                    "role": "ADMIN",
                    "telf": "9623",
                    "username": "usuario1"
                },
                "userId": 143,
                "vendedores": {
                    "entry": []
                },
                "vendedoresSize": 0
            }
            ```
		- Status.NO_CONTENT

* GET /rest/admin/issues = **Get all active issues filtered.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- QueryParam("tipo") __->__ _Type of issue filter in the search._
		- QueryParam("asunto") __->__ _Asunto filter in the search._
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("AyudaListDTO.class")
			```json
            {
                "ayudas": {
                    "entry": [
                        {
                            "key": 1,
                            "value": {
                                "asunto": "Subject of the message here",
                                "email": "usuar@usuario.com",
                                "estado": 1,
                                "fechaContacto": "2019-07-13",
                                "informe": "",
                                "mensaje": "Message to admin here",
                                "name": "usuar",
                                "userId": -1
                            }
                        }
                    ]
                },
                "sizeAyudas": 1
            }
            ```
		- Status.NO_CONTENT

* __GET__ /rest/admin/archivedIssues = **Get all archived issues filtered.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- QueryParam("tipo") __->__ _Type of issue filter in the search._
		- QueryParam("asunto") __->__ _Asunto filter in the search._
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("AyudaListDTO.class")
			```json
            {
                "ayudas": {
                    "entry": [
                        {
                            "key": 1,
                            "value": {
                                "asunto": "Subject of the message here",
                                "email": "usuar@usuario.com",
                                "estado": 1,
                                "fechaContacto": "2019-07-13",
                                "informe": "",
                                "mensaje": "Message to admin here",
                                "name": "usuar",
                                "userId": -1
                            }
                        }
                    ]
                },
                "sizeAyudas": 1
            }
            ```
		- Status.NO_CONTENT

* __GET__ /rest/admin/issues/{id} = **Get the issue with the corresponding id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("AyudaDTO.class")
            ```json
            { "ayudaId": 1,
                "issue": {
                    "asunto": "Subject of the message here",
                    "email": "usuar@usuario.com",
                    "estado": 1,
                    "fechaContacto": "2019-07-13",
                    "informe": "",
                    "mensaje": "Message to admin here",
                    "name": "usuar",
                    "userId": -1
                }
            }
            ```
		- Status.NOT_FOUND

* __DELETE__ /rest/admin/issues/{id}/delete = **Delete the issue with the corresponding id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- Status.ACCEPTED
		- Status.NOT_FOUND
		- Status.NOT_MODIFIED
		- Status.BAD_REQUEST
		- Status.NOT_FOUND

* __PUT__ /rest/admin/issues/{id}/archive = **Archive the issue with the corresponding id.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("AdminHelpForm.class")
            ```json
            {
                "informe":"This is the input text that admin sends to the users that needs help."
            }
            ```
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("MensajeDTO.class")
            ```json
            {
                "mensaje": "Informe enviado correctamente a usuar@usuario.com."
            }
            ```
		- Status.BAD_REQUEST
		- Status.NOT_FOUND

### **Users (UserRestApi.class)**

* __GET__ /rest/users/sizeMsg/{id} = **Get user, with the corresponding id, unread messages.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("LongDTO.class")
            ```json
                {
                    "res": 1
                }
            ```

* __GET__ /rest/users/sizeRate/{id} = **Get user purchases no rated of the given user id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("LongDTO.class")
            ```json
                {
                    "res": 1
                }
            ```

* __GET__ /rest/users/listUsers = **Get all users with rol USER.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("UserListDTO.class")
             ```json
            { 
                "size": 2, 
                "users": {
                "entry": [
                    {
                        "key": 405,
                        "value": {
                            "city": "Buenos Aires",
                            "code": "CABA123",
                            "country": "Argentina",
                            "direccion": "Calle corrientes numero 2",
                            "email": "user@user.user",
                            "estado": 1,
                            "image": "",
                            "lat": 0,
                            "lon": 0,
                            "numImg": 0,
                            "password": "$2a$10$A8plO/WNh8bKc0/Nw/D4wumOSsjX8dON55Oq3tKuk9/7s741bmjSu",
                            "rate": 0,
                            "role": "USER",
                            "telf": "123456",
                            "urlImg": "",
                            "username": "usuario"
                        }
                    },
                    {
                        "key": 406,
                        "value": {
                            "city": "Buenos Aires",
                            "code": "2222",
                            "country": "Argentina",
                            "direccion": "C/Fitz Roy 1235",
                            "email": "icatalan@itba.edu.ar",
                            "estado": 1,
                            "image": "",
                            "lat": -34.60043279,
                            "lon": -58.44685455,
                            "numImg": 0,
                            "password": "$2a$10$oNhSkqEUHyJLCnPI43YOzOn5QWOV3NJkvJiBZqN5gJZd72mrwu5jO",
                            "rate": 0,
                            "role": "USER",
                            "telf": "3235652323",
                            "urlImg": "",
                            "username": "izan123"
                        }
                    }
                ]
                }
            }
            ```
		- Status.NO_CONTENT

* __GET__ /rest/users/getMaxVendor/{id} = **Get if the user with that id is the max seller.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("BooleanDTO.class")
            ```json
            {
                "value": false
            } 
            ```

* __GET__ /rest/users/getMaxBuyer/{id} = **Get if the user with that id is the max buyer.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("BooleanDTO.class")
             ```json
            {
                "value": false
            } 
            ```

* __GET__ /rest/users/getMaxRated/{id} = **Get if the user with that id is the most rated.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("BooleanDTO.class")
             ```json
            {
                "value": false
            } 
            ```

* __GET__ /rest/users/getUserTotalSales/{id} = **Get the number of sales of the given user with that id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("LongDTO.class")
            ```json
            {
                "res": 1
            } 
            ```

* __GET__ /rest/users/getRate/{id} = **Get the rate value of the user.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
		- JSON("LongDTO.class")
             ```json
            {
                "res": 
            } 
            ```

* __GET__ /rest/users/{id} = **Get the user with the given id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("UserDTO.class")
            ```json
            {
                "id": 406,
                "user": {
                    "city": "Buenos Aires",
                    "code": "2222",
                    "country": "Argentina",
                    "direccion": "C/Fitz Roy 1235",
                    "email": "icatalan@itba.edu.ar",
                    "estado": 1,
                    "image": "",
                    "lat": -34.60043279,
                    "lon": -58.44685455,
                    "numImg": 0,
                    "password": "$2a$10$oNhSkqEUHyJLCnPI43YOzOn5QWOV3NJkvJiBZqN5gJZd72mrwu5jO",
                    "rate": 0,
                    "role": "USER",
                    "telf": "3235652323",
                    "urlImg": "",
                    "username": "izan123"
                }
            }
            ```
		- Status.NOT_FOUND
		- Status.FORBIDDEN

* __GET__ /rest/users/login/{username} = **Get the user with the given username.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("UserDTO.class")
            ```json
            {
                "id": 406,
                "user": {
                    "city": "Buenos Aires",
                    "code": "2222",
                    "country": "Argentina",
                    "direccion": "C/Fitz Roy 1235",
                    "email": "icatalan@itba.edu.ar",
                    "estado": 1,
                    "image": "",
                    "lat": -34.60043279,
                    "lon": -58.44685455,
                    "numImg": 0,
                    "password": "$2a$10$oNhSkqEUHyJLCnPI43YOzOn5QWOV3NJkvJiBZqN5gJZd72mrwu5jO",
                    "rate": 0,
                    "role": "USER",
                    "telf": "3235652323",
                    "urlImg": "",
                    "username": "izan123"
                }
            }
            ```
		- Status.NOT_FOUND
		- Status.FORBIDDEN

*  __GET__ /rest/users/listUsersItems = **List of near users.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- QueryParam("rangeKmSlider") __->__ _The distance in KM._
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("ListUsersItemsDTO.class")
		- Status.NO_CONTENT

*  __PUT__ /rest/users/edit = **Edit the actual user profile.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("UserEditForm.class")
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("UserDTO.class")

*  __PUT__ /rest/users/editPass = **Edit the actual user password.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("UserEditPassForm.class")
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- Status.ACCEPTED

*  __GET__ /rest/users/misventas = **Get the actual user sales.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("UserVentasDTO.class")

*  __GET__ /rest/users/miscompras = **Get the actual user purchases.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("UserComprasDTO.class")

*  __GET__ /rest/users/miscontactosr = **Get the actual user recived messages.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("UserContactosDTO.class")

*  __GET__ /rest/users/miscontactose = **Get the actual user sent messages.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("UserContactosDTO.class")

*  __POST__ /rest/users/help = **Sent a help message to the admin.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("ContactAdminForm.class")
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("MensajeDTO.class")

* __GET__ /rest/users/missugerencias = **Get actual user sugerences.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("ItemListDTO.class")
		- Status.NOT_FOUND

### **Items (ItemRestApi.class)**

* __GET__ /rest/items/contactosItem/{id} = **Get my message sent to an item.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("ContactoDTO.class")
            ```json 
            {
                "contacto":{
                    "estado": 1,
                    "fechaContacto": "2019-07-12",
                    "idComprador": 405,
                    "idVendedor": 406,
                    "itemId": 64,
                    "mensaje": "Lo quiero22222222",
                    "read": 1
                },
                "idContacto": 19
            }
            ```
		- Status.NOT_FOUND

*  __GET__ /rest/items = **List of filtered items alta.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- QueryParam("name") __->__ _The name that will be include in the item filtered name._
		- QueryParam("tipo") __->__ _The type of item filtered._
		- QueryParam("minSlaider") __->__ _The min value of the slider._
		- QueryParam("maxSlaider") __->__ _The max value of the slider._
		- QueryParam("slider") __->__ _The values min and max selected inside the slider._
		- QueryParam("itemTipoCaducidad") __->__ _The type of the date (Before, After, Any)._
		- QueryParam("fecha_caducidad") __->__ _The date selected to be filtered._
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("ItemListFiltroDTO.class")
            ```json
            {
                "date": "2019-07-12",
                "fecha_caducidadCheck": 1,
                "items": {
                    "entry": [
                        {
                            "key": 64,
                            "value": {
                                "description": "frutaaaaa",
                                "estado": 1,
                                "fechaCaducidad": "2019-07-25",
                                "fechaPublicacion": "2019-07-12",
                                "idVendedor": 406,
                                "name": "frutaa",
                                "numeroVisitas": 0,
                                "price": 32,
                                "tipo": 1
                            }
                        }
                    ]
                },
                "max": 32,
                "maximoSeleccionado": 32,
                "min": 0,
                "minimoSeleccionado": 0,
                "name": "f",
                "size": 1,
                "tipoCaducidad": 0,
                "typeFood": 0
            }    
            ```

*  __GET__ /rest/items/{id} = **Get the item with the given id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("ItemDTO.class")
            ```json
            {
                "getImagesItemsEncode": [],
                "item": {
                    "description": "frutaaaaa",
                    "estado": 1,
                    "fechaCaducidad": "2019-07-25",
                    "fechaPublicacion": "2019-07-12",
                    "idVendedor": 406,
                    "name": "frutaa",
                    "numeroVisitas": 1,
                    "price": 32,
                    "tipo": 1
                },
                "itemId": 64,
                "propietario": false,
                "rate": 0,
                "seller": {
                    "city": "Buenos Aires",
                    "code": "2222",
                    "country": "Argentina",
                    "direccion": "C/Fitz Roy 1235",
                    "email": "icatalan@itba.edu.ar",
                    "estado": 1,
                    "image": "",
                    "lat": -34.60043279,
                    "lon": -58.44685455,
                    "numImg": 0,
                    "password": "$2a$10$oNhSkqEUHyJLCnPI43YOzOn5QWOV3NJkvJiBZqN5gJZd72mrwu5jO",
                    "rate": 0,
                    "role": "USER",
                    "telf": "3235652323",
                    "urlImg": "",
                    "username": "izan123"
                },
                "sellerId": 406
            } 
            ```
		- Status.NOT_FOUND

*  __DELETE__ /rest/items/delete/{id} = **Delete the item with the given id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- Status.ACCEPTED
		- Status.FORBIDDEN
		- Status.NOT_FOUND

*  __PUT__ /rest/items/baja/{id} = **Set status inactive (sold) of the item with the given id.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- QueryParam("comprador") __->__ _The user purchase id of the item._
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- Status.ACCEPTED
		- Status.FORBIDDEN
		- Status.NOT_FOUND

*  __POST__ /rest/items/additem = **Create a new item.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("ItemRegisterForm.class")
            ```json
            {
                "description": "pescado fresco",
                "fechaCaducidad": "2019-09-28",
                "name": "pescado",
                "price": 45,
                "tipo": 4,
                "image": ""
            }
            ```
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("ItemCreateDTO.class")
            ```json
            {
                "item": {
                    "description": "pescado fresco",
                    "estado": 1,
                    "fechaCaducidad": "2019-09-28",
                    "fechaPublicacion": "2019-07-12",
                    "idVendedor": 406,
                    "name": "pescado",
                    "numeroVisitas": 0,
                    "price": 45,
                    "tipo": 4,
                    "urlImg": ""
                },
                "itemId": 64
            }
            ```
		- Status.FORBIDDEN

*  __PUT__ /rest/items/update/{id} = **Update the item with the given id.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("ItemRegisterForm.class")
            ```json
            {
                "description": "pescado fresco",
                "fechaCaducidad": "2019-09-28",
                "name": "pescado",
                "price": 45,
                "tipo": 4,
                "image": ""
            }
            ```
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("ItemDTO.class")
            ```json
            {
                "getImagesItemsEncode": [],
                "item": {
                    "description": "pescado fresco",
                    "estado": 1,
                    "fechaCaducidad": "2019-09-28",
                    "fechaPublicacion": "2019-07-12",
                    "idVendedor": 406,
                    "name": "pescado",
                    "numeroVisitas": 0,
                    "price": 45,
                    "tipo": 4,
                    "urlImg": ""
                },
                "itemId": 64,
                "propietario": true,
                "rate": 0,
                "seller": {
                    "city": "Buenos Aires",
                    "code": "2222",
                    "country": "Argentina",
                    "direccion": "C/Fitz Roy 1235",
                    "email": "icatalan@itba.edu.ar",
                    "estado": 1,
                    "image": "",
                    "lat": -34.60043279,
                    "lon": -58.44685455,
                    "numImg": 0,
                    "password": "$2a$10$oNhSkqEUHyJLCnPI43YOzOn5QWOV3NJkvJiBZqN5gJZd72mrwu5jO",
                    "rate": 0,
                    "role": "USER",
                    "telf": "3235652323",
                    "urlImg": "",
                    "username": "izan123"
                },
                "sellerId": 406
            }
            ```
		- Status.FORBIDDEN
		- Status.NOT_FOUND

*  __DELETE__ /rest/items/delitemimages/{id} = **Delete images from the item with the given id.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- Status.ACCEPTED
		- Status.FORBIDDEN
		- Status.NOT_FOUND

*  __GET__ /rest/items/myitems = **Get items on alta for the actual user.**
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("ItemListDTO.class")
            ```json
            {
                "items": {
                    "entry": [
                        {
                            "key": 64,
                            "value": {
                                "description": "pescado fresco",
                                "estado": 1,
                                "fechaCaducidad": "2019-09-28",
                                "fechaPublicacion": "2019-07-12",
                                "idVendedor": 406,
                                "name": "pescado",
                                "numeroVisitas": 0,
                                "price": 45,
                                "tipo": 4,
                                "urlImg": ""
                            }
                        }
                    ]
                },
                "size": 1
            }
            ```
		- Status.NOT_FOUND

*  __PUT__ /rest/items/sendto/{id} = **Send a message to the seller for an item with the given id.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("ContactForm.class")
            ```json
            {
                "mensaje": "Message to send here"
            }
            ```
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- JSON("MensajeDTO.class")
            ```json
            {
                "mensaje": "Message to show on screen here"
            }
            ```
		- Status.NOT_FOUND
		- Status.FORBIDDEN

*  __PUT__ /rest/items/rate/{id} = **Rate the item with the given id.**
	- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
		- JSON("ItemRateForm.class")
            ```json
            {
                "estrellas": 5,
                "valoracion": "valoration text here"
            }
            ```
	- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
		- Status.ACCEPTED
		- Status.NOT_FOUND
		- Status.FORBIDDEN
