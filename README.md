Anschool · by A.N.A.H.I.

Les presento Anschool, una aplicación web progresiva (PWA) dedicada a transformar la enseñanza de las matemáticas, desarrollada por Francisco Almaraz Ocelo, Diego Mendoza Burgos y Irvin Torres Jarquin, el equipo de A.N.A.H.I.

Hoy en día, la mayoría de las herramientas de inteligencia artificial resuelven la tarea por el estudiante, eliminando el proceso de aprendizaje. Anschool nace para resolver ese problema mediante un enfoque pedagógico socrático: nuestra IA nunca entrega la respuesta final; en su lugar, analiza el razonamiento del alumno y lo guía paso a paso para que construya su propia solución. Todo esto bajo una interfaz moderna en tonos rosa y negro, construida con Next.js 14, React 18, TypeScript, Tailwind CSS, Three.js y KaTeX.

Anschool esta diseñada para los estudiantes con rezago en matemáticas, con una forma nueva de aprendizaje donde la IA no te da las respuestas correctas si no te explica y te ayuda a que tu razones y entiendas los temas matemáticos de una forma personalizada y que puedas avanzar en tu aprendizaje a tu ritmo, por eso mismo proponemos el sistema offline-fallback para que el usuario pueda repasar sus apuntes y ejercicios aunque no tengan internet

video demo: https://drive.google.com/drive/folders/1CTLeOVa8ry39KLwV_HTnyforRUh2rq6S

antes de iniciar cabe resaltar que Anschool es un prototipo funcional, mas aun falta  muchas cosas por hacer por ejmeplo:

1. Mejorar la experiencia del usuario.
2. Conectar con una base de datos.
3. Hacer una app para dispositivos moviles.
4. Mejorar la interfaz.
5. Hacerla una plataforma de aprendizaje para múltiples materias. 

 Instalación y Despliegue (Pasos a Seguir)

El proyecto está diseñado para levantarse en minutos y garantizar disponibilidad continua:
(decargar el repositorio)
1. Instalar dependencias:
npm install
2. Configurar variables de entorno:
copy .env.example .env.local
(En este archivo se alojan las llaves gratuitas de IA. Si no se configuran, el sistema entra automáticamente en modo offline-fallback sin interrumpir la experiencia).
3. Ejecutar en entorno local:
npm run dev
Disponible en http://localhost:3000
4. Despliegue en la nube:

* Repositorio: git init && git add . && git commit -m "Anschool MVP" (sin subir .env.local).
* Producción en Vercel: importar el proyecto y agregar las 4 variables de .env.example en Settings → Environment Variables.

Arquitectura de Resiliencia (Router de IA):
Para evitar interrupciones por límites de cuota, implementamos un enrutador en cascada que conecta Google Gemini (gemini-3.6-flash, gemini-3.8-flash, gemini-3.5-flash-lite, gemini-3.1-flash-lite, gemini-2.5-flash y gemini-3.8-flash-tts, configurables con GEMINI_MODELS en .env.local), Groq, NVIDIA NIM y OpenRouter, respaldado por un modo offline. Desde el botón de llaves (🔑) se puede probar la llave y ver qué modelo responde.

 Funcionalidad Principal

Anschool integra visión artificial, procesamiento de voz y memoria adaptativa en los siguientes módulos:


* Tutor socrático multimodal: recibe ejercicios por texto o fotografía. En lugar de dar la respuesta, ofrece pistas del 1 al 3, cuenta con apoyo 3D, voz y Modo Demo.
* Memoria adaptativa ("Anschool recuerda"): registra temas estudiados, ejercicios resueltos, operaciones donde el alumno se equivocó, procedimientos dominados y temas por reforzar, inyectando este contexto al tutor y al saludo de la llamada.
* Cuadernos por tema (/cuaderno): permite llevar apuntes con LaTeX, agregar fotos, retomar ejercicios y generar ejercicios parecidos mediante IA mostrando solo el enunciado y una pista.
* Pizarra interactiva (/pizarra): permite escribir a mano; la IA lee la letra del alumno y le muestra lo que leyó, corrige, guía, activa una "Guía en vivo" al pausar 6 segundos y guarda el trabajo en el cuaderno.
* Videollamada con tutor IA (/llamada): incluye avatar animado que se presenta, micrófono on/off, cámara, voz de mujer o hombre, interrupción natural al hablar (hablas y se calla), teclado, función "Mostrar mi cuaderno" a la cámara y voz HD de Gemini opcional.

Demostración Práctica (Cómo se usa)

Para evaluar el funcionamiento completo de Anschool en menos de dos minutos:

1. Recarga la página para ver la intro animada y activa el Modo Demo para que "Anschool recuerda" se llene con 3 cuadernos.
2. Entra a Cuadernos, selecciona Fracciones, haz clic en "Crear ejercicios parecidos" y comienza a practicar.
3. Abre la Pizarra, escribe a mano 3x - 5 = 10 con un error y presiona Revisar para comprobar cómo lee tu letra y guía sin dar la solución.
4. Entra a Llamada, elige voz, inicia la sesión, habla con el tutor e interrúmpelo para probar la conversación en tiempo real.
