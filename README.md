🛒 Tienda Backend

Backend de una tienda online desarrollado con Django + Django REST Framework + MySQL, que incluye:

- Gestión de productos
- Carrito de compras
- Pedidos
- Autenticación con JWT


---

⚙️ Tecnologías utilizadas 

Python 3.11+

MySQL 8+ instalado y corriendo

pip y virtualenv

---

📦 Instalación y configuración

1. Clona el repositorio

https://github.com/Patogol35/Aplicacion-PatricioSantamaria--Django-Python-


2. Ingresa a la carpeta del proyecto
   
cd Aplicacion-PatricioSantamaria--Django-Python-


3. Crea el entorno virtual

python -m venv venv

Linux/Mac: source venv/bin/activate

Windows: venv\Scripts\activate


4. Instala las dependencias

pip install -r requirements.txt

⚠️ Si mysqlclient da problemas, instálalo manualmente según tu sistema:

pip install mysqlclient

o

pip install PyMySQL


5. Crea la base de datos en MySQL

CREATE DATABASE tienda_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

En settings.py verifica:

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'tienda_db',
        'USER': 'root',
        'PASSWORD': 'tu_clave',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}


6. Aplica las migraciones

python manage.py makemigrations
python manage.py migrate


7. Crea el superusuario

python manage.py createsuperuser


8. Ejecuta el servidor

python manage.py runserver


---

🔗 Endpoints principales

Autenticación (JWT)

POST /api/register/ → Registrar usuario

POST /api/token/ → Obtener token de acceso

POST /api/token/refresh/ → Refrescar token


Ejemplo:

POST /api/register/
{
  "username": "juan",
  "email": "juan@mail.com",
  "password": "123456"
}


---

Productos

GET /api/productos/ → Listar productos

POST /api/productos/ → Crear producto (admin)

PUT /api/productos/{id}/ → Editar producto

DELETE /api/productos/{id}/ → Eliminar producto


Ejemplo respuesta:

[
  {
    "id": 1,
    "nombre": "Camiseta",
    "descripcion": "Camiseta de algodón",
    "precio": "19.99",
    "stock": 10
  }
]


---

Carrito

GET /api/carrito/ → Ver carrito del usuario

POST /api/carrito/agregar/ → Agregar producto al carrito


Ejemplo:

POST /api/carrito/agregar/
{
  "producto_id": 1,
  "cantidad": 2
}


---

Pedidos

POST /api/pedido/crear/ → Crear pedido desde carrito

GET /api/pedidos/ → Listar pedidos del usuario


Ejemplo respuesta:

{
  "id": 3,
  "usuario": 1,
  "fecha": "2025-08-26T10:00:00Z",
  "total": "39.98",
  "items": [
    {
      "producto": { "id": 1, "nombre": "Camiseta" },
      "cantidad": 2,
      "precio_unitario": "19.99",
      "subtotal": "39.98"
    }
  ]
}


---

📸 Panel de administración

Accede a:
👉 http://127.0.0.1:8000/admin/

Podrás gestionar productos, carritos, pedidos y usuarios.


---

Próximos pasos / Mejoras

[ ] Documentación de la API con Swagger o ReDoc

[ ] Tests automatizados

[ ] Integración con un frontend en React/Angular

[ ] Manejo de pagos y envíos



---

👨‍💻 Autor

Jorge Patricio Santamaría Cherrez
Máster en Ingeniería de Software y Sistemas Informáticos

