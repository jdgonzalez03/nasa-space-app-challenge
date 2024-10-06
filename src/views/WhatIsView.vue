<template>
  <section id="about-project" class="about-project-section">
    <h2 class="about-project-title">What is this project?</h2>
    <div class="about-project-content">
      <p class="about-project-description">
        Farmers face a multitude of water-related challenges due to unpredictable weather, pests,
        and diseases. These factors heavily impact crop health, farmers' profits, and food security.
        Depending on the geography, farmers may experience droughts or floods—sometimes both in the
        same season! Our mission is to design a tool that empowers farmers to explore, analyze, and
        utilize NASA data to address these water-related concerns and improve their farming
        practices.
      </p>

      <p class="about-project-description">
        We are electronic and systems engineering students who, through <strong>CapiPlant</strong>,
        seek to provide a solution by leveraging Earth observation data, with a focus on Colombia,
        an agricultural country. We aim to help farmers make better-informed decisions to enhance
        efficiency in their agricultural practices.
      </p>
      <hr />
      <p class="about-project-hackathon">
        This project is part of our participation in the
        <strong>NASA App Space Challenge 2024</strong> in Sogamoso. This hackathon provides us with
        the opportunity to collaborate and find innovative solutions to help farmers tackle their
        daily challenges.
      </p>
    </div>
  </section>
</template>

<style scoped>
.about-project-section {
  padding: 40px;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  gap: 28px;
}

.about-project-title {
  font-size: 2em;
  color: #333;
  text-align: center;
  margin-bottom: 20px;
}

.about-project-content {
  max-width: 800px;
  margin: 0 auto;
  text-align: justify;
}

.about-project-description,
.about-project-hackathon {
  margin-top: 24px;
  font-size: 1.1em;
  color: #555;
  line-height: 1.6;
  margin-bottom: 15px;
}

.about-project-hackathon {
  font-weight: bold;
  color: #444;
  text-align: center;
}
</style>
