 Manual de Usuario – SIGO BACKEND
Sistema de Gestión de Asistencia – Backend (FastAPI)
 Introducción

Este manual explica de manera sencilla y humana cómo instalar, ejecutar y utilizar el backend del sistema SIGO, un servicio desarrollado con FastAPI que permite registrar y consultar asistencias, gestionar bonos laborales y generar recibos.

El objetivo es que cualquier persona —incluso sin mucha experiencia técnica— pueda levantar el proyecto sin problemas.

 1. Requisitos Previos

Antes de comenzar, asegúrate de tener instalado:

 Python 3.10 o superior

Para verificar tu versión:

python --version

 Git
git --version

 Visual Studio Code (opcional pero recomendado)

Sirve como editor de código.

 2. Clonar el Repositorio

Abre una terminal en tu computadora y ejecuta:

git clone https://github.com/<TU-USUARIO>/sigo-backend.git
cd sigo-backend


Esto descarga el proyecto y se ubica dentro de la carpeta.

 3. Crear el Entorno Virtual

Un entorno virtual evita conflictos con otras aplicaciones.

Crear entorno:
python -m venv venv

Activarlo:
En Windows:
venv\Scripts\activate

En Linux/Mac:
source venv/bin/activate


Cuando esté activo verás algo así:

(venv) PS C:\…\sigo-backend>

 4. Instalar Dependencias

Ejecuta:

pip install -r requirements.txt


Esto instalará FastAPI, Uvicorn y las demás librerías necesarias para el sistema.

 5. Ejecutar el Servidor

Con el entorno virtual activo:

uvicorn main:app --reload


Si todo va bien verás algo como:

INFO:     Uvicorn running on http://127.0.0.1:8000


Este será el servidor del backend.

 6. Endpoints Principales

Una vez el servidor esté levantado, entra aquí en tu navegador:

http://127.0.0.1:8000/docs

Ahí verás la documentación interactiva del sistema (Swagger UI).

Endpoints importantes:

POST /asistencia/registrar → Registrar asistencia

GET /asistencia/listar → Consultar asistencias

POST /bonos/calcular → Calcular bono (alimentación, transporte, etc.)

POST /recibo/generar → Generar recibo

Puedes probar todo desde la misma página.

 7. Archivos Importantes
Archivo	Explicación
main.py	Punto de entrada del backend
models/	Modelos Pydantic (estructuras de datos)
services/	Lógica de negocio (cálculos de bonos, recibos, etc.)
static/	Logo, plantillas u otros recursos
manual.md	Este manual del sistema
README.md	Información principal del repositorio
 8. Flujo Básico de Uso

Abres terminal

Activás el entorno virtual

Ejecutas uvicorn main:app --reload

Entras a http://127.0.0.1:8000/docs

Registras asistencia

Calculas bono

Generas recibo

Todo está automatizado y pensado para ser fácil de usar.

 9. Pruebas Sencillas
 Registrar asistencia

En /asistencia/registrar ejemplo de body:

{
  "cedula": "30555999",
  "nombre": "Frank Mendez",
  "fecha": "2025-11-21",
  "hora": "08:15"
}

 Calcular bono

En /bonos/calcular:

{
  "cedula": "30555999",
  "dias_laborados": 20
}

 10. Errores Comunes y Soluciones
 "‘uvicorn’ no se reconoce como comando"

 Ejecuta:

pip install uvicorn

 "Module not found"

 Instalaste el proyecto sin activar el entorno.
Actívalo y reinstala dependencias.

 Swagger UI no carga

 Revisa que el servidor esté encendido.

11. Contacto / Soporte

Este proyecto puede ser extendido, mejorado y mantenido fácilmente.
Si presentas problemas, puedes abrir un Issue en GitHub o mejorar el proyecto mediante un Pull Request.

 12. Conclusión

Este backend está pensado para ser simple, claro y funcional.
Puedes adaptarlo, conectarlo a un frontend, integrarlo con una base de datos o añadir nuevos módulos según tu necesidad.
