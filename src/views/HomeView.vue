<template>
  <header>
    <Hero
      header="Accelerate SIEM data integration with AI"
      image=".public/images/hero-3.jpg"
      :buttons="heroButtons"
    />
  </header>
  <main>
    <LogoContainer />
    <InlineContent
      image=".public/images/services.png"
      subHeader="The Deslicer Platform"
      header="More growth opportunities, less maintenance"
      text="The Deslicer platform helps you unlock the full potential of your SIEM system by semi-automating administrative tasks. From onboarding apps to maintenance and updates. Focus on what your SIEM does best - protect your company from threats."
      buttonLabel="Ask for a demo"
      :buttonAction="handleLearnMore"
    />
    <section class="background-color">
      <!-- Render Cards Dynamically -->
      <div class="cards-container">
        <CardComponent
          v-for="(card, index) in cards"
          :key="index"
          :icon="card.icon"
          :title="card.title"
          :paragraph="card.paragraph"
          :features="card.features"
        />
      </div>
    </section>
    <InlinecontentTwo
      image=".public/images/siem-expertise.jpg"
      imagePosition="right"
      header="Expertise to help optimize your SIEM system"
      text="While the Deslicer platform is our primary service, our consultants are also available to help optimize your SIEM system. We ensure you unlock the systems's full potential while managing costs effectively, offering strategic guidance at every step to align with your business goals."
      :bulletList="[
        'Long-term strategic planning and roadmap for Splunk implementation and expansion',
        'Architecture and implementation design to maximize efficiency and scalability',
        'Creating dashboards alerts and automated reports for proactive management.',
      ]"
      background-color="var(--vt-c-white-soft)"
    />
    <QuoteComponent
      header="Discover your savings potentials today"
      description="Automation empowers your Splunk platform with superpowers, eliminating tedious administration and management tasks. Reach out to us for a short talk about how much savings you may be able to gain from automating your SIEM system."
      primaryButtonLabel="Call us today"
      :primaryButtonAction="handlePrimaryAction"
      quote="We have hundreds of apps in need of onboarding to our Splunk installation. By investing in the Deslicer platform we can now onboard new software in hours rather than days and for a fraction of the cost!"
      name="Lex Luthor"
      company="Head of IT and AI Automation, Comapny X"
      image=".public/images/siem-automate-ai-deslicer.jpg"
    />
  </main>
</template>

<script setup lang="ts">
import Hero from '../components/HeroImage.vue'
import LogoContainer from '../components/LogoContainer.vue'
import InlineContent from '@/components/InlineContent.vue'
import CardComponent from '@/components/CardComponent.vue'
import InlinecontentTwo from '@/components/InlinecontentTwo.vue'
import QuoteComponent from '@/components/QuoteComponent.vue'

const heroButtons = [
  { label: 'Get in touch', action: () => alert('Get in touch!') },
  { label: 'How it works', action: () => alert('How it works clicked!') },
]

const icon = 'svg/verified.svg'
const cards = [
  {
    icon: 'svg/sync.svg',
    title: 'Onboard apps',
    paragraph:
      'Onboarding apps to a SIEM system demands significant time and resources. For companies managing hundreds or thousands, this process becomes a costly bottleneck that Deslicer can help automate.',
    features: [
      { icon: icon, text: 'Getting data in' },
      { icon: icon, text: 'Agent creation and validation' },
      { icon: icon, text: 'Automated deployment' },
    ],
    buttonLabel: 'Learn More',
    buttonAction: () => alert('Card 1 clicked!'),
  },
  {
    icon: 'svg/monitor.svg',
    title: 'Uncover insights',
    paragraph:
      'Monitor your Splunk installation the same way you monitor your other software and increase the value of you SIEM installation.',
    features: [
      { icon: icon, text: 'SIEM system overview' },
      { icon: icon, text: 'Error handling' },
      { icon: icon, text: 'Process handling' },
    ],
    buttonLabel: 'Learn More',
    buttonAction: () => alert('Card 2 clicked!'),
  },
  {
    icon: 'svg/system.svg',
    title: 'Manage and update',
    paragraph:
      'Automation is not limited to SIEM onboarding. Thanks to the Deslicer platform you can now also reduce the time it takes to manage and continuously update the system.',
    features: [
      { icon: icon, text: 'Automated management' },
      { icon: icon, text: 'Update agents' },
    ],
    buttonLabel: 'Read More',
    buttonAction: () => alert('Card 2 clicked!'),
  },
]

const handlePrimaryAction = () => {
  console.log('Primary action clicked')
}

const handleLearnMore = () => {
  console.log('Learn More button clicked')
}
</script>

<style>
.background-color {
  background-color: #e5e5e5;
}
.cards-container {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
  padding: 0 2rem 6rem 2rem;
  max-width: 1080px;
  margin: 0 auto;
}

@media (min-width: 768px) {
  .cards-container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .cards-container {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>
