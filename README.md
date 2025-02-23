<!-- hide -->
# Create a Company Logo Generator using AI
<!-- endhide -->

<how-to-start>

## 🌱 How to start this project

Do not clone this repository because we are going to be using a different template.

We recommend opening the `react template` using a provisioning tool like [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recommended) or [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternatively, you can [clone the GitHub repository](https://4geeks.com/how-to/github-clone-repository) on your local computer using the `git clone` command.

This is the repository you need to open or clone:

```
https://github.com/4GeeksAcademy/react-hello
```

> ⚠ You will need to have Node.js installed if you do it locally, but all of that is already installed on Codespaces or Gitpod.

</how-to-start>

## 📝 Instructions

### Step 1: Set Up the Project

- [ ] Set up the boilerplate project from the provided React template.
  
- [ ] Follow the instructions in the README of the repository to set up your development environment.

### Step 2: Get Access to ChatGPT's API

- [ ] Sign up for an account at [OpenAI](https://www.openai.com/).
- [ ] Navigate to the API section and obtain your API key for accessing ChatGPT.

### Step 3: Create an Input Form

- [ ] In your React app, create a form where users can provide details about the company:

   - Company Name
   - Industry
   - Preferred Logo Style (e.g., minimalist, vintage, modern)

### Step 4: Connect to ChatGPT's API

- [ ] Use the user input to create a prompt for the ChatGPT API.

- [ ] Make a request to the ChatGPT API when the form is submitted.

Example:

```js
const handleGenerateLogo = async ({ companyName, industry, style }) => {
 const prompt = `Create a detailed description of a logo for a company named "${companyName}", operating in the "${industry}" industry. The logo should have a "${style}" style.`;

 try {
   const response = await fetch('https://api.openai.com/v1/engines/text-davinci-003/completions', {
     method: 'POST',
     headers: {
       'Authorization': `Bearer YOUR_OPENAI_API_KEY`,
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
   console.error('Error generating logo description:', error);
 }
};
```

> **Note:** Remember to replace `'YOUR_OPENAI_API_KEY'` with your actual OpenAI API key.

### Step 5: Display the Generated Logo Description

- [ ] Display the logo description returned from the API to the user in your React app.

- [ ] Ensure the description is presented in a readable format, possibly with styling to enhance user experience.

### Step 6: Bonus - Visual Representation

- [ ] Try to add a feature where you visually generate a simple logo based on the description provided by ChatGPT. You can use libraries like [Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API), [Fabric.js](http://fabricjs.com/), or [Konva.js](https://konvajs.org/) to create basic visual designs.

- [ ] Alternatively, you can integrate with an AI image generation API like [DALL·E](https://openai.com/dall-e-2/) to create an image based on the description.

### Bonus Section

#### Additional Features to Practice and Improve the Project

1. **Logo Variations:** Allow users to generate multiple logo descriptions with different styles or themes by modifying the prompt.

2. **Styling:** Enhance your app's appearance using CSS or styling libraries like [Bootstrap](https://getbootstrap.com/) or [Material-UI](https://material-ui.com/).

3. **Save Descriptions:** Implement functionality to save or download the generated logo descriptions for future reference.

4. **User Accounts:** Add a user authentication system so users can save their logo ideas and access them later.

5. **Error Handling:** Add robust error handling to manage API errors, network issues, or invalid inputs gracefully.

6. **Responsive Design:** Ensure your app looks good on various screen sizes by implementing responsive design practices.

Explore different enhancements to make your logo generator app more interactive and visually appealing!
