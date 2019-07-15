
__BANCALET VIRTUAL API REST DOCUMENTATION__
=================

<!--ts-->
   * [API REST](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)
   * [Main page (MainPageRestApi.class)](#Main-page-(MainPageRestApi.class))
        * [GET /rest](#GET-/rest)
        * [PUT /rest/confirmregister/{id}](#PUT-/rest/confirmregister/{id})
        * [POST /rest/register](#POST-/rest/register)
        * [POST /rest/contact](#POST-/rest/contact)
        * [GET /rest/error/403](#GET-/rest/error/403)
   * [Admin (AdminRestApi.class)](#Admin-(AdminRestApi.class))
        * [GET /rest/admin](#GET-/rest/admin)
        * [GET /rest/admin/totalAyudas](#GET-/rest/admin/totalAyudas)
        * [POST /rest/admin/createUser](#POST-/rest/admin/createUser)
        * [GET /rest/admin/userList](#GET-/rest/admin/userList)
        * [GET /rest/admin/{id}](#GET-/rest/admin/{id})
        * [PUT /rest/admin/{id}/bajaUser](#PUT-/rest/admin/{id}/bajaUser)
        * [PUT /rest/admin/{id}/altaUser](#PUT-/rest/admin/{id}/altaUser)
        * [PUT /rest/admin/{id}/editUser](#PUT-/rest/admin/{id}/editUser)
        * [PUT /rest/admin/{id}/editPass](#PUT-/rest/admin/{id}/editPass)
        * [GET /rest/admin/{id}/ventas](#GET-/rest/admin/{id}/ventas)
        * [GET /rest/admin/{id}/compras](#GET-/rest/admin/{id}/compras)
        * [GET /rest/admin/issues](#GET-/rest/admin/issues)
        * [GET /rest/admin/archivedIssues](#GET-/rest/admin/archivedIssues)
        * [GET /rest/admin/issues/{id}](#GET-/rest/admin/issues/{id})
        * [DELETE /rest/admin/issues/{id}/delete](#DELETE-/rest/admin/issues/{id}/delete)
        * [PUT /rest/admin/issues/{id}/archive](#PUT-/rest/admin/issues/{id}/archive)
   * [Users (UserRestApi.class)](#Users-(UserRestApi.class))
        * [GET /rest/users/sizeMsg/{id}](#GET-/rest/users/sizeMsg/{id})
        * [GET /rest/users/sizeRate/{id}](#GET-/rest/users/sizeRate/{id})
        * [GET /rest/users/listUsers](#GET-/rest/users/listUsers)
        * [GET /rest/users/getMaxVendor/{id}](#GET-/rest/users/getMaxVendor/{id})
        * [GET /rest/users/getMaxBuyer/{id}](#GET-/rest/users/getMaxBuyer/{id})
        * [GET /rest/users/getMaxRated/{id}](#GET-/rest/users/getMaxRated/{id})
        * [GET /rest/users/getUserTotalSales/{id}](#GET-/rest/users/getUserTotalSales/{id})
        * [GET /rest/users/getRate/{id}](#GET-/rest/users/getRate/{id})
        * [GET /rest/users/{id}](#GET-/rest/users/{id})
        * [GET /rest/users/login/{username}](#GET-/rest/users/login/{username})
        * [GET /rest/users/listUsersItems](#GET-/rest/users/listUsersItems)
        * [PUT /rest/users/edit](#PUT-/rest/users/edit)
        * [PUT /rest/users/editPass](#PUT-/rest/users/editPass)
        * [GET /rest/users/misventas](#PUT-/rest/users/editPass)
        * [GET /rest/users/miscompras](#GET-/rest/users/miscompras)
        * [GET /rest/users/miscontactosr](#GET-/rest/users/miscontactosr) BUILDING
        * [GET /rest/users/miscontactose](#GET-/rest/users/miscontactose) BUILDING
        * [POST /rest/users/help](#POST-/rest/users/help)
        * [GET /rest/users/missugerencias](#GET-/rest/users/missugerencias) BUILDING

   * [Items (ItemRestApi.class)](#Items-(ItemRestApi.class))
        * [GET /rest/items/contactosItem/{id}](#GET-/rest/items/contactosItem/{id})
		* [GET /rest/items/contactosMyItem/{id}](#GET-/rest/items/contactosMyItem/{id})
		* [GET /rest/items](#GET-/rest/items)
		* [GET /rest/items/{id}](#GET-/rest/items/{id})
		* [DELETE /rest/items/delete/{id}](#DELETE-/rest/items/delete/{id})
		* [PUT /rest/items/baja/{id}](#PUT-/rest/items/baja/{id})
		* [POST /rest/items/additem](#POST-/rest/items/additem)
		* [PUT /rest/items/update/{id}](#PUT-/rest/items/update/{id})
		* [DELETE /rest/items/delitemimages/{id}](#DELETE-/rest/items/delitemimages/{id})
		* [GET /rest/items/myitems](#GET-/rest/items/myitems)
		* [PUT /rest/items/sendto/{id}](#PUT-/rest/items/sendto/{id})
		* [PUT /rest/items/rate/{id}](#PUT-/rest/items/rate/{id})
<!--te-->

__Main page (MainPageRestApi.class)__
=================

GET /rest 
-----
**Get user loged.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/confirmregister/{id}
-----
**Confirm user email and set user alta.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - Status.ACCEPTED
    - Status.FORBIDDEN
    - Status.NOT_FOUND

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

POST /rest/register
-----
**Create a user with rol USER.**
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
    - JSON("MensajeDTO.class")
        ```json
        {
            "mensaje": "usuar. Mensaje enviado correctamente, te responderemos a traves de: usuar@usuario.com"
        }
        ```
    - Status.FORBIDDEN
    - Status.BAD_REQUEST
    - Status.CONFLICT

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

POST /rest/contact
-----
**Send help form.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/error/403
-----
**Get a forbiden page.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
    - Status.FORBIDDEN

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

__Admin (AdminRestApi.class)__
=================

GET /rest/admin
-----
**Get admin dashboard info.**
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
[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/admin/totalAyudas
-----
**Get the number of help contacts that admin has.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
    - JSON("AdminAyudasDTO.class")
        ```json
        { "totalAyudas": 0 }

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

POST /rest/admin/createUser
-----
**Create user by admin.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/admin/userList
-----
**Get all the users in the aplication filtered.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/admin/{id}
-----
**Get the user corresponding with an id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/admin/{id}/bajaUser
-----
**Suspend the user with the corresponding id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/admin/{id}/altaUser
-----
**Active the user with the corresponding id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/admin/{id}/editUser
-----
**Edit the user with the corresponding id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/admin/{id}/editPass
-----
**Edit the user password with the corresponding id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/admin/{id}/ventas
-----
**Get all sales of the corresponding user with a given id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/admin/{id}/compras
-----
**Get all purchases of the corresponding user with a given id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/admin/issues
-----
**Get all active issues filtered.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/admin/archivedIssues
-----
**Get all archived issues filtered.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/admin/issues/{id}
-----
**Get the issue with the corresponding id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

DELETE /rest/admin/issues/{id}/delete
-----
**Delete the issue with the corresponding id.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - Status.ACCEPTED
    - Status.NOT_FOUND
    - Status.NOT_MODIFIED
    - Status.BAD_REQUEST
    - Status.NOT_FOUND

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/admin/issues/{id}/archive
-----
**Archive the issue with the corresponding id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

__Users (UserRestApi.class)__
=================

GET /rest/users/sizeMsg/{id}
-----
**Get user, with the corresponding id, unread messages.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
    - JSON("LongDTO.class")
        ```json
            {
                "res": 1
            }
        ```
    - Status.FORBIDDEN

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/sizeRate/{id}
-----
**Get user purchases no rated of the given user id.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
    - JSON("LongDTO.class")
        ```json
            {
                "res": 1
            }
        ```

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/listUsers
-----
**Get all users with rol USER.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/getMaxVendor/{id}
-----
**Get if the user with that id is the max seller.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
    - JSON("BooleanDTO.class")
        ```json
        {
            "value": false
        } 
        ```

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/getMaxBuyer/{id}
-----
**Get if the user with that id is the max buyer.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
    - JSON("BooleanDTO.class")
        ```json
        {
            "value": false
        } 
        ```
[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/getMaxRated/{id}
-----
**Get if the user with that id is the most rated.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
    - JSON("BooleanDTO.class")
        ```json
        {
            "value": false
        } 
        ```
[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/getUserTotalSales/{id}
-----
**Get the number of sales of the given user with that id.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
    - JSON("LongDTO.class")
        ```json
        {
            "res": 1
        } 
        ```
[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/getRate/{id}
-----
**Get the rate value of the user.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return: 
    - JSON("LongDTO.class")
        ```json
        {
            "res": 1
        } 
        ```
[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/{id}
-----
**Get the user with the given id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/login/{username}
-----
**Get the user with the given username.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/listUsersItems
-----
**List of near users.**
- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
    - QueryParam("rangeKmSlider") __->__ _The distance in KM._
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - JSON("ListUsersItemsDTO.class")
        ```json
        {
            "nearusers": {
                "entry": [
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
                    }
                ]
            },
            "rangekm": 1287,
            "useritems": {
                "entry": [
                    {
                        "key": 2,
                        "value": "{}"
                    }
                ]
            }
        }
        ```
    - Status.NO_CONTENT

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/users/edit
-----
**Edit the actual user profile.**
- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
    - JSON("UserEditForm.class")
        ```json
        {
            "city": "Oliva",
            "code": 46780,
            "country": "España",
            "direccion": "Calle Ernest Lluch 17",
            "lat": 0.653,
            "lon": 0.89456,
            "tipo": 0,
            "telf": 9623
        }
        ```
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - JSON("UserDTO.class")
        ```json
        {
            "id": 406,
            "user": {
                "city": "Oliva",
                "code": 46780,
                "country": "España",
                "direccion": "Calle Ernest Lluch 17",
                "email": "icatalan@itba.edu.ar",
                "estado": 1,
                "image": "",
                "lat": 0.653,
                "lon": 0.89456,
                "numImg": 0,
                "password": "$2a$10$oNhSkqEUHyJLCnPI43YOzOn5QWOV3NJkvJiBZqN5gJZd72mrwu5jO",
                "rate": 0,
                "role": "USER",
                "telf": "9623",
                "urlImg": "",
                "username": "izan123"
            }
        }
        ```

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/users/editPass
-----
**Edit the actual user password.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/misventas
-----
**Get the actual user sales.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - JSON("UserVentasDTO.class")
        ```json
        {
            "itemsvendidos": {
                "entry": [
                    {
                        "key": 64,
                        "value": {
                            "description": "pescado fresco",
                            "estado": 0,
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
            "listaventas": {
                "entry": [
                    {
                        "key": 20,
                        "value": {
                            "estrellas": 0,
                            "fechaCompra": "2019-07-13",
                            "idComprador": 405,
                            "idVendedor": 406,
                            "itemId": 64,
                            "valoracion": "muy buenaooo"
                        }
                    }
                ]
            },
            "listcompradores": {
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
                    }
                ]
            },
            "user": {
                "city": "Buenos Aires Provincia",
                "code": "44444",
                "country": "Argentina",
                "direccion": "C/Defensa",
                "email": "icatalan@itba.edu.ar",
                "estado": 1,
                "lat": -34.60043279,
                "lon": -58.44685455,
                "numImg": 0,
                "password": "$2a$10$oNhSkqEUHyJLCnPI43YOzOn5QWOV3NJkvJiBZqN5gJZd72mrwu5jO",
                "rate": 0,
                "role": "USER",
                "telf": "3235652323",
                "username": "izan123"
            },
            "userid": 406
        }
        ```
[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/miscompras
-----
**Get the actual user purchases.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - JSON("UserComprasDTO.class")
        ```json
        {
            "compras": {
                "entry": [
                    {
                        "key": 20,
                        "value": {
                            "estrellas": 0,
                            "fechaCompra": "2019-07-13",
                            "idComprador": 405,
                            "idVendedor": 406,
                            "itemId": 64,
                            "valoracion": "muy buenaooo"
                        }
                    }
                ]
            },
            "comprasSize": 1,
            "items": {
                "entry": [
                    {
                        "key": 64,
                        "value": {
                            "description": "pescado fresco",
                            "estado": 0,
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
            "itemsSize": 1,
            "user": {
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
            },
            "userId": 405,
            "vendedores": {
                "entry": [
                    {
                        "key": 406,
                        "value": {
                            "city": "Buenos Aires Provincia",
                            "code": "44444",
                            "country": "Argentina",
                            "direccion": "C/Defensa",
                            "email": "icatalan@itba.edu.ar",
                            "estado": 1,
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
            },
            "vendedoresSize": 1
        }
        ```

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/miscontactosr
-----
**Get the actual user recived messages.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - JSON("UserContactosDTO.class")
        ```json
        {

        }
        ```

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/miscontactose
-----
**Get the actual user sent messages.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - JSON("UserContactosDTO.class")
        ```json
        {
            
        }
        ```

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

POST /rest/users/help
-----
**Sent a help message to the admin.**
- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
    - JSON("ContactAdminForm.class")
        ```json
        {
            "name":"usuario",
            "subject": "subject here",
            "mensaje":"message here",
            "email":"email of the user"
        }
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - JSON("MensajeDTO.class")
        ```json
        {
            "mensaje": "usuario. Mensaje enviado correctamente, te responderemos a traves de: user@user.user"
        }
        ```
[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/users/missugerencias
-----
**Get actual user sugerences.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - JSON("ItemListDTO.class")
        ```json
        {
            
        }
        ```
    - Status.NOT_FOUND

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

__Items (ItemRestApi.class)__
=================

GET /rest/items/contactosItem/{id}
-----
**Get my message sent to an item.**
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
    - Status.FORBIDDEN

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/items/contactosMyItem/{id}
-----
**Get all recived messages for my item with the corresponding id.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - JSON("ContactoDTO.class")
        ```json
        { 
            "size": 1, 
            "contactos": {
                "entry": [
                    {
                        "key": 19,
                        "value": {
                            "estado": 1,
                            "fechaContacto": "2019-07-12",
                            "idComprador": 405,
                            "idVendedor": 406,
                            "itemId": 64,
                            "mensaje": "Lo quiero22222222",
                            "read": 1
                        }
                    }
                ]
            }
        }
        ```
    - Status.NOT_FOUND
    - Status.FORBIDDEN

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/items
-----
**List of filtered items alta.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/items/{id}
-----
**Get the item with the given id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

DELETE /rest/items/delete/{id}
-----
**Delete the item with the given id.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - Status.ACCEPTED
    - Status.FORBIDDEN
    - Status.NOT_FOUND

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/items/baja/{id}
-----
**Set status inactive (sold) of the item with the given id.**
- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Recive:
    - QueryParam("comprador") __->__ _The user purchase id of the item._
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - Status.ACCEPTED
    - Status.FORBIDDEN
    - Status.NOT_FOUND

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

POST /rest/items/additem
-----
**Create a new item.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/items/update/{id}
-----
**Update the item with the given id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

DELETE /rest/items/delitemimages/{id}
-----
**Delete images from the item with the given id.**
- ![#1589F0](https://placehold.it/15/f03c15/000000?text=+) Return:
    - Status.ACCEPTED
    - Status.FORBIDDEN
    - Status.NOT_FOUND

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

GET /rest/items/myitems
-----
**Get items on alta for the actual user.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/items/sendto/{id}
-----
**Send a message to the seller for an item with the given id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)

PUT /rest/items/rate/{id}
-----
**Rate the item with the given id.**
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

[GO BACK](#BANCALET-VIRTUAL-API-REST-DOCUMENTATION)