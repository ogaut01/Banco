# Banco - Sistema de Cajero Automático y Core Bancario Distribuido

Proyecto desarrollado para la cátedra de **Sistemas Distribuidos** (8vo Semestre). Implementa un sistema bancario y cajero automático capaz de operar de manera distribuida, comunicándose con otros nodos bancarios a través de APIs REST para la consulta de saldos, depósitos, retiros e informes de transacciones.

---

## Características Principales

- **Gestión de Cuentas Bancarias**: Apertura de cuentas, asociación a entidades bancarias y cálculo de intereses según el tipo de cuenta.
- **Cajero Multibanco Distribuido**: Capacidad de interactuar con nodos de diferentes bancos a través de servicios web REST, permitiendo operaciones interbancarias en red local o remota.
- **Autenticación con JWT**: Seguridad en transacciones mediante JSON Web Tokens (`djangorestframework-simplejwt`), permitiendo transferir credenciales de autorización entre servicios distribuidos.
- **Módulo de Auditoría**: Trazabilidad completa de eventos (`login`, `transaccion`, `retiro`, `deposito`), registrando dirección IP de origen, servidor, usuario, nivel de severidad y dirección MAC del nodo.
- **Panel Administrativo Moderno**: Integración con `django-jazzmin` para una interfaz de administración ágil y visual.
- **Soporte Multi-Base de Datos**: Configurable para SQLite (desarrollo rápido) o Microsoft SQL Server (vía ODBC Driver 17).

---

## Tecnologías Utilizadas

- **Lenguaje**: Python 3.10+
- **Framework Web**: Django 5.1.1
- **API REST**: Django REST Framework (DRF)
- **Autenticación**: SimpleJWT
- **Tareas Asíncronas**: Celery + Django Celery Beat + Redis
- **Frontend**: Django Templates, Tailwind CSS, jQuery
- **Base de Datos**: SQLite / Microsoft SQL Server

---

## Endpoints de la API

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `POST` | `/api/token/` | Generación de token JWT (Access y Refresh) |
| `POST` | `/api/token/refresh/` | Refresco de token JWT |
| `GET` | `/api/api-list/` | Lista de nodos bancarios distribuidos disponibles |
| `GET` | `/api/user/balance/` | Consulta de saldo de cuenta autenticada |
| `GET` | `/api/celestial/report/` | Listado de transacciones históricas |
| `POST` | `/api/celestial/report/` | Procesamiento distribuido de depósitos y retiros |
| `POST` | `/auditoria/record/<evento>/<nivel>/` | Registro de eventos de auditoría |

---

## ⚙️ Instalación y Puesta en Marcha

### 1. Clonar el repositorio
```bash
git clone https://github.com/ogaut01/Banco.git
cd Banco
```

### 2. Crear y activar entorno virtual
En Windows:
```bash
python -m venv venv
venv\Scripts\activate
```

### 3. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 4. Configurar variables de entorno
Crea un archivo `.env` a partir de la plantilla:
```bash
cp .env.example .env
```
Ajusta `SECRET_KEY`, `DEBUG` y los parámetros de base de datos según tu entorno local.

### 5. Ejecutar migraciones
```bash
python manage.py migrate
```

### 6. Iniciar el servidor
```bash
python manage.py runserver
```
Accede a la aplicación en [http://127.0.0.1:8000](http://127.0.0.1:8000).

---

## 👥 Colaboradores
Proyecto académico desarrollado de forma colaborativa para la carrera de Ingeniería Informática.
