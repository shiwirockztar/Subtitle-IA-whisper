# Subtitle-IA-whisper

Este repositorio contiene herramientas y un notebook (`script.ipynb`) pensado para ejecutarse en Google Colab y trabajar con subtítulos (SRT) y modelos de transcripción/traducción.

**Cómo usar el script en Google Colab**

- **Abrir el notebook en Colab (rápido):**
	- Entra en este enlace para abrir directamente el notebook en Colab:
		`https://colab.research.google.com/github/shiwirockztar/Subtitle-IA-whisper/blob/master/script.ipynb`
	- Alternativamente, sube `script.ipynb` en la interfaz de Colab (File → Upload notebook).

- **Pasos recomendados dentro de Colab:**
	1. Montar Google Drive (opcional, para guardar resultados):
		 ```python
		 from google.colab import drive
		 drive.mount('/content/drive')
		 ```
	2. Clonar el repositorio en la máquina de Colab (opcional):
		 ```bash
		 !git clone https://github.com/shiwirockztar/Subtitle-IA-whisper.git
		 %cd Subtitle-IA-whisper
		 ```
	3. Instalar dependencias necesarias (ejecutar en una celda):
		 ```bash
		 # Instala ffmpeg (necesario para procesamiento de audio) y paquetes de Python
		 !apt-get update -y && apt-get install -y ffmpeg
		 !pip install -q -U openai-whisper pysrt pydub transformers sentencepiece
		 ```
		 Nota: la lista puede ajustarse según las celdas de `script.ipynb`.

	4. Subir o situar los archivos de entrada:
		 - Puedes subir archivos desde la barra lateral de Colab (Files → Upload) o copiar los archivos desde Drive hacia `/content`.
		 - Si clonaste el repo, los subtítulos de ejemplo están en `subs/`.

	5. Ejecutar las celdas del notebook en orden. El notebook realiza los pasos de transcripción/traducción/formateo según su implementación.

	6. Guardar o descargar los resultados:
		 - Para guardar en Drive:
			 ```python
			 output_path = '/content/drive/MyDrive/subs/2941456.es.srt'
			 # Ejemplo: escribir contenido a output_path desde el notebook
			 with open(output_path, 'w', encoding='utf-8') as f:
					 f.write(srt_text)
			 ```
		 - Para descargar directamente al equipo local:
			 ```python
			 from google.colab import files
			 files.download('/content/Subtitle-IA-whisper/subs/2941456.es.srt')
			 ```

- **Sugerencias de runtime:**
	- Si el notebook hace uso intensivo de modelo de audio, selecciona un runtime con GPU (Runtime → Change runtime type → GPU).
	- Asegúrate de tener suficiente espacio si subes audios grandes al entorno de Colab.

**Notas de integración**
- El notebook (`script.ipynb`) es el componente principal para ejecutar la pipeline en Colab. Lee los comentarios y las primeras celdas del notebook — suelen contener instrucciones específicas sobre rutas de entrada/salida y parámetros del modelo.
- Si quieres automatizar ejecutar el notebook desde GitHub, puedes usar la URL de Colab (mencionada arriba) o herramientas como `nbconvert`/`papermill` en entornos locales.

Si quieres, actualizo el `script.ipynb` para añadir celdas concretas de instalación/ejemplo de guardado, o creo un `requirements.txt` con las dependencias detectadas. ¿Cuál prefieres?