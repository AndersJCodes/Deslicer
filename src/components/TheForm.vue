<template>
  <section class="form-section" :style="{ backgroundImage: `url(${backgroundImage})` }">
    <div class="max-width">
      <div class="form-container">
        <div class="form-info">
          <h2 class="form-title">{{ title }}</h2>
          <p class="form-paragraph" v-if="description">{{ description }}</p>
        </div>
        <form @submit.prevent="handleSubmit" class="form">
          <!-- Name Input -->
          <div class="form-group">
            <label for="name">Name</label>
            <input
              id="name"
              type="text"
              placeholder="Input your name here"
              v-model="formData.name"
              required
            />
          </div>
          <!-- Email Input -->
          <div class="form-group">
            <label for="email">Email (*required)</label>
            <input
              id="email"
              type="email"
              placeholder="example@gmail.com"
              v-model="formData.email"
              required
            />
          </div>
          <!-- Phone Input -->
          <div class="form-group">
            <label for="phone">Phone number</label>
            <input id="phone" type="tel" placeholder="+46701234567" v-model="formData.phone" />
          </div>
          <!-- Message Input -->
          <div class="form-group">
            <label for="message">What can we do for you? (*required)</label>
            <textarea
              id="message"
              placeholder="Describe your challenge"
              v-model="formData.message"
              required
            ></textarea>
          </div>
          <!-- Privacy Checkbox -->
          <div class="checkbox-group">
            <input
              class="checkbox"
              id="privacy"
              type="checkbox"
              v-model="formData.privacy"
              required
            />
            <label for="privacy">
              I agree to the <a href="#" class="privacy-link">privacy policy</a> (*required)
            </label>
          </div>
          <!-- Submit Button -->
          <button type="submit" class="form-button">Send</button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { reactive } from 'vue'

interface FormProps {
  title: string
  description: string
  backgroundImage: string
}

interface FormData {
  name: string
  email: string
  phone: string
  message: string
  privacy: boolean
}

defineProps<FormProps>()

// Reactive form data object
const formData = reactive<FormData>({
  name: '',
  email: '',
  phone: '',
  message: '',
  privacy: false,
})

// Handle form submission
const handleSubmit = async () => {
  if (!formData.privacy) {
    alert('You must agree to the privacy policy.')
    return
  }

  // Create the payload for HubSpot or other APIs
  const payload = {
    name: formData.name,
    email: formData.email,
    phone: formData.phone,
    message: formData.message,
    privacyAccepted: formData.privacy,
  }

  console.log('Form data ready for submission:', payload)

  // Simulate sending the data
  try {
    const response = await fetch('https://api.hubapi.com/form-endpoint', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(payload),
    })

    if (response.ok) {
      alert('Form submitted successfully!')
    } else {
      alert('There was an issue submitting the form.')
    }
  } catch (error) {
    console.error('Error submitting form:', error)
    alert('Error submitting form. Please try again later.')
  }
}
</script>

<style scoped>
.form-section {
  padding: 6rem 0rem;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  min-height: 40vh; /* Ensure it covers the full viewport height */
  margin-top: -62px; /* Adjust this value based on the height of your navbar */
}

.max-width {
  max-width: 1080px;
  margin: 0 auto;
}

.form-container {
  background-color: #e5e5e5d6;
  margin: 0 2rem;
  text-align: left;
  padding: 2rem 2rem;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.form-info {
  flex: 1;
}

.form-title {
  font-size: 1.8rem;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 1rem;
}

.form-paragraph {
  font-size: 1rem;
  color: #2c3e50;
  margin-bottom: 2rem;
}

.form {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  font-size: 1rem;
  margin-bottom: 0.5rem;
  color: #2c3e50;
}

input,
textarea {
  padding: 0.8rem;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 1rem;
}

textarea {
  resize: vertical;
  min-height: 100px;
}

.checkbox-group {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
}

.checkbox {
  margin-bottom: 0.5rem;
}

.privacy-link {
  color: #2c3e50;
  text-decoration: underline;
}

.form-button {
  padding: 0.8rem 1.5rem;
  font-size: 1rem;
  font-weight: bold;
  color: #ffffff;
  background-color: #2c3e50; /* Use your primary color */
  border: none;
  border-radius: 8px;
  cursor: pointer;
}

.form-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.form-button:hover {
  background-color: #1b2937;
}

/* Media query for desktop view */
@media (min-width: 1080px) {
  .form-container {
    flex-direction: row; /* Arrange items in a row */
    align-items: flex-start; /* Align items at the start */
  }

  .form-info {
    flex: 1;
    margin-right: 2rem; /* Add space between info and form */
  }

  .form {
    flex: 1;
  }
}
</style>
