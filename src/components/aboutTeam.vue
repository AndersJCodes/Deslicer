<template>
  <section class="about-section">
    <!-- Vision and Mission Section -->
    <div class="vision-mission">
      <div class="mission">
        <h2>Deslicer at a glance</h2>
        <p>
          We make your SIEM system more human, by letting the computer do the hard work of
          onboarding, maintanance and updates. Now you can spend more time on insights, threat
          defence and company growth.
        </p>
      </div>
      <div class="vision">
        <h2>Our story</h2>
        <p>
          Deslicer was founded by three SIEM industry veterans with a mission to transform SIEM
          implementations into a streamlined, turnkey solution. Their extensive experience in the
          industry has given them deep insight into potential bottlenecks and opportunities for
          innovation.
        </p>
      </div>
    </div>

    <!-- Team Section -->
    <div class="team">
      <h2>Our Team</h2>
      <div class="team-grid">
        <div class="team-member" v-for="member in team" :key="member.name">
          <img :src="member.image" :alt="`Photo of ${member.name}`" />
          <h3>{{ member.name }}</h3>
          <p class="role">{{ member.role }}</p>
          <p class="bio">{{ member.bio }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
interface TeamMember {
  name: string
  role: string
  bio: string
  image: string
}
const team: TeamMember[] = [
  {
    name: 'Roger Lindquist',
    role: 'Founder / CEO',
    bio: 'Roger is an experienced IT professional with over 25 years in various roles, including IT Manager, Architect, and Consultant, now specializing in infrastructure, security, and automation.',
    image: './images/deslicer-roger-2.png', // Replace with actual image paths
  },
  {
    name: 'Saikrishna Gundeti',
    role: 'Founder / CTO',
    bio: 'Saikrishna excels at aligning IT capabilities with business goals, drawing on over 15 years of experience in IT operations, data analytics, and automation. His expertise spans Splunk, AI/ML, and multi-cloud environments.',
    image: './images/deslicer-saikrishna-2.png',
  },
  {
    name: 'Daniel Young',
    role: 'Founder / CSO',
    bio: 'Daniel is a technology leader with a strong background in software engineering, operational intelligence, and strategic leadership. His vision has driven Deslicer’s growth and customer success.',
    image: './images/deslicer-daniel-2.png',
  },
]
</script>

<style scoped>
.about-section {
  padding: 6rem 2rem;
  max-width: 1080px;
  margin: 0 auto;
}

.vision-mission {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2em;
  margin-bottom: 3rem;
}

.vision-mission h2 {
  /*  font-size: 1.5rem; */
  margin-bottom: 0.5rem;
}

.vision-mission p {
  /* font-size: 1rem; */
  /*  line-height: 1.5; */
}

.team {
  padding: 4rem 0;
  text-align: center;
}

.team h2 {
  /* font-size: 2rem; */
  margin-bottom: 2rem;
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}

.team-member {
  border-radius: 8px;
  padding: 1rem;
  text-align: left;
  background-color: var(--color-background-mute);
}

.team-member img {
  border-radius: 8px;
  object-fit: cover;
  width: 100%;
  margin-bottom: 1rem;
}

.team-member h3 {
  color: #f97316; /* Accent color */
}

.team-member .role {
  font-weight: bold;
  margin-bottom: 1rem;
  font-size: 0.8em;
}

.team-member .bio {
  font-size: 0.8em;
}
</style>
