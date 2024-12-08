# Vue 3 TypeScript Project Documentation

Student: Anders Jacobson

This project demonstrates various Vue 3 and TypeScript features as required for the course. below is how each requirement was implemented.

to start the project simply run `npm install` to install the dependencies and then `npm run dev` to start the development server.

## Project summary

This project is a simple landing page for a business. It is a single page application that uses vue router to navigate between pages. It consists of three pages: Home, About, and Contact.

The Home page has a hero section, a form section, and a footer. The About page has a chatbot section and the Contact page has a form section.

Please read more below for examples of how the code meets the requirements. Please also find a short summary of ai use at the end of the file.

## Core Vue 3 Features

### Text Interpolation

- Used in multiple components, notably in `TheHero.vue` for displaying header text: `{{ header }}`
- Used in `TheForm.vue` for form labels and button text

### Conditional Rendering (v-if)

- Implemented in `TheHero.vue` for optional subheader: `v-if="subHeader"`
- Used in `TheForm.vue` for displaying validation messages

### List Rendering (v-for)

- Used in `LogoContainer.vue` for rendering client logos
- Implemented in `TheHero.vue` for animating text characters

### Event Handling (v-on)

- Form submission handling in `TheForm.vue`: `@submit.prevent="handleSubmit"`
- Button click events in `TheHero.vue`: `@click="button.action"`

### Computed Properties

- Implemented form validation in `TheForm.vue`: Notably to validate email format in real-time with a span element that dispalys the error message below the email input field.

### The site has three pages:

- Home: The landing page with a hero section, a form section, and a footer.
- About: A simple page that introduces the user to the purpose of the site.
- Contact: A simple page that allows the user to contact the site owner.

### The components uses props to pass data from the parent component to the child component.

- The inlineContent component uses props so that we can see at the view page what information we are showing in the component, so that you can do all contnt editing in one place.

### We use the ref() to handle and number of elements

most notably in the form component where it is used to handle the form submission and validation.

### A life cycle hook on mounted is used to animate the header text on the home page.

### The chat component uses a fetch to fetch randomized answers to chatbot questions.

the chatbot can be found on the about page.

### AI has been used to:

- render a draft for this file.
- to create much of the code
- to rewrite the typescript intrfaces, gling from usiing the const props to the interface syntax.
