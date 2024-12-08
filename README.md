# Proyecto de Autenticación y Gestión de Usuarios (Versión Mejorada)

Esta versión del proyecto integra Bootstrap 4 mediante el paquete `django-bootstrap4`, y organiza las plantillas extendiendo una plantilla base común (`base.html`). Esto facilita mantener una interfaz coherente, moderna y responsiva en todo el front-end interno (`front_user`).

## Características Principales

- **API REST con DRF**:  
  La API sigue ofreciendo endpoints autenticados para CRUD de usuarios y sus perfiles asociados.
  
- **Autenticación por Sesión en `user_api`**:  
  Permite iniciar sesión vía `/user_api/login/` para acceder a endpoints protegidos como `/user_api/users/`.

- **Front-end Interno con Bootstrap 4**:  
  Ahora el front (`front_user`) utiliza plantillas que extienden `base.html`, incorporando Bootstrap 4 para una mejor experiencia de usuario.  
  Se utilizan las etiquetas y bloques proporcionados por `django-bootstrap4`.

- **Estructura de Plantillas Mejorada**:  
  Las plantillas de creación, edición, detalle y listado de usuarios, así como las de login y registro, heredan de una plantilla base con la barra de navegación y la importación de CSS/JS centralizada.

## Tecnologías Utilizadas

- **Django 5.1.4**
- **Django REST Framework 3.15.2**
- **drf-spectacular 0.28.0** para documentación de la API
- **Pillow 11.0.0** para manipulación de imágenes de perfil
- **Requests 2.32.3** para consumir la API desde `front_user`
- **django-bootstrap4** para integrar fácilmente Bootstrap 4 en las plantillas
- Otras dependencias listadas en `requirements.txt`

## Instalación y Configuración

1. **Clonar el repositorio**:
   ```bash
   git clone https://github.com/tu-usuario/tu-repo.git
   cd tu-repo
   ```

2. **Crear y activar entorno virtual (opcional)**:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Linux/macOS
   venv\Scripts\activate     # Windows
   ```

3. **Instalar dependencias**:
   ```bash
   pip install -r requirements.txt
   ```

   Asegúrate de que `django-bootstrap4` esté presente en `requirements.txt`:
   ```text
   django-bootstrap4>=23.3
   ```

4. **Configurar django-bootstrap4**:
   - Añade `'bootstrap4'` a `INSTALLED_APPS` en `settings.py`.

5. **Migraciones y Servidor**:
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   python manage.py runserver
   ```

## Uso

- **Front-end Interno**:
  - Lista de usuarios: `http://127.0.0.1:8000/users/`
  - Crear usuario (interno): `http://127.0.0.1:8000/users/create/`
  - Login interno: `http://127.0.0.1:8000/login/`
  - Registro interno: `http://127.0.0.1:8000/register/`

- **API (requiere autenticación)**:
  - Login de la API: `http://127.0.0.1:8000/user_api/login/`
  - Usuarios: `http://127.0.0.1:8000/user_api/users/`

- **Documentación**:
  - Swagger UI: `http://127.0.0.1:8000/docs/swagger/`
  - Redoc: `http://127.0.0.1:8000/docs/redoc/`
  - Esquema OpenAPI: `http://127.0.0.1:8000/docs/schema/`

## Estructura del Proyecto

```
Autenticacion/
│
├─ Autenticacion/
│  ├─ settings.py
│  ├─ urls.py
│  └─ ...
│
├─ user_api/
│  ├─ models.py
│  ├─ serializers.py
│  ├─ views.py
│  ├─ urls.py
│  ├─ signals.py
│  └─ apps.py
│
├─ docs/
│  ├─ urls.py
│  └─ ...
│
├─ front_user/
│  ├─ templates/
│  │  ├─ front_user/
│  │  │  ├─ base.html          # Plantilla base con Bootstrap
│  │  │  ├─ login.html
│  │  │  ├─ register.html
│  │  │  ├─ list_users.html
│  │  │  ├─ create_user.html
│  │  │  ├─ detail_user.html
│  │  │  ├─ update_user.html
│  │  │  └─ delete_user.html
│  ├─ views.py
│  ├─ urls.py
│  └─ ...
│
└─ requirements.txt
```
