<!-- hide -->
# Crear un Generador de Logos de Empresa usando IA
<!-- endhide -->

<how-to-start>

## 🌱 ¿Cómo iniciar este proyecto?

No clones este repositorio porque vamos a utilizar una plantilla diferente.

Recomendamos abrir la `plantilla de React` utilizando una herramienta de aprovisionamiento como [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recomendado) o [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternativamente, puedes [clonar el repositorio de GitHub](https://4geeks.com/how-to/github-clone-repository) en tu computadora local usando el comando `git clone`.

Este es el repositorio que necesitas abrir o clonar:

```
https://github.com/4GeeksAcademy/react-hello
```

> ⚠ Necesitarás tener Node.js instalado si lo haces localmente, pero todo eso ya está instalado en Codespaces o Gitpod.

</how-to-start>

## 📝 Instrucciones

### Paso 1: Configura el Proyecto

- [ ] Configura el proyecto boilerplate desde la plantilla de React proporcionada.
  
- [ ] Sigue las instrucciones en el README del repositorio para configurar tu entorno de desarrollo.

### Paso 2: Obtén acceso a la API de ChatGPT

- [ ] Regístrate para obtener una cuenta en [OpenAI](https://www.openai.com/).
- [ ] Navega a la sección de API y obtén tu clave API para acceder a ChatGPT.

### Paso 3: Crea un Formulario de Entrada

- [ ] En tu aplicación React, crea un formulario donde los usuarios puedan proporcionar detalles sobre la empresa:

   - Nombre de la empresa
   - Industria
   - Estilo de logotipo preferido (por ejemplo, minimalista, vintage, moderno)

### Paso 4: Conecta a la API de ChatGPT

- [ ] Utiliza la entrada del usuario para crear un prompt para la API de ChatGPT.

- [ ] Realiza una solicitud a la API de ChatGPT cuando se envíe el formulario.

Ejemplo:

```js
const handleGenerateLogo = async ({ companyName, industry, style }) => {
  const prompt = `Crea una descripción detallada de un logotipo para una empresa llamada "${companyName}", que opera en la industria de "${industry}". El logotipo debería tener un estilo "${style}".`;

  try {
    const response = await fetch('https://api.openai.com/v1/engines/text-davinci-003/completions', {
      method: 'POST',
      headers: {
        'Authorization': `Bearer TU_CLAVE_API_DE_OPENAI`,
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        prompt: prompt,
        max_tokens: 150,
        n: 1,
        stop: null,
        temperature: 0.7,
      }),
    });

    const data = await response.json();
    const description = data.choices[0].text.trim();
    setLogoDescription(description);
  } catch (error) {
    console.error('Error al generar la descripción del logotipo:', error);
  }
};
```

> **Nota:** Recuerda reemplazar `'TU_CLAVE_API_DE_OPENAI'` con tu clave API real de OpenAI.

### Paso 5: Muestra la Descripción del Logotipo Generado

- [ ] Muestra la descripción del logotipo devuelta por la API al usuario en tu aplicación React.

- [ ] Asegúrate de que la descripción se presente en un formato legible, posiblemente con estilos para mejorar la experiencia del usuario.

### Paso 6: Bonus - Representación Visual

- [ ] Intenta agregar una función donde generes visualmente un logotipo simple basado en la descripción proporcionada por ChatGPT. Puedes usar librerías como [Canvas API](https://developer.mozilla.org/es/docs/Web/API/Canvas_API), [Fabric.js](http://fabricjs.com/), o [Konva.js](https://konvajs.org/) para crear diseños visuales básicos.

- [ ] Alternativamente, puedes integrar una API de generación de imágenes con IA como [DALL·E](https://openai.com/dall-e-2/) para crear una imagen basada en la descripción.

### Sección de Bonus

#### Características Adicionales para Practicar y Mejorar el Proyecto

1. **Variaciones de Logotipo:** Permite a los usuarios generar múltiples descripciones de logotipos con diferentes estilos o temas modificando el prompt.

2. **Estilización:** Mejora la apariencia de tu aplicación usando CSS o librerías de estilos como [Bootstrap](https://getbootstrap.com/) o [Material-UI](https://material-ui.com/).

3. **Guardar Descripciones:** Implementa funcionalidad para guardar o descargar las descripciones de logotipos generadas para referencia futura.

4. **Cuentas de Usuario:** Agrega un sistema de autenticación para que los usuarios puedan guardar sus ideas de logotipos y acceder a ellas más tarde.

5. **Manejo de Errores:** Agrega un manejo de errores robusto para gestionar errores de API, problemas de red o entradas inválidas de manera adecuada.

6. **Diseño Responsivo:** Asegúrate de que tu aplicación se vea bien en varios tamaños de pantalla implementando prácticas de diseño responsivo.

¡Explora diferentes mejoras para hacer tu aplicación generadora de logotipos más interactiva y visualmente atractiva!
