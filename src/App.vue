<template>
  <div id="app">
    <hero-banner
    title="Movie night"
    :data="data"></hero-banner>
    <div class="container">
    <accordion :items="data" />
    </div>
  </div>
</template>

<script>
import './assets/css/tailwind/tailwind.css';
import Accordion from './components/Accordion/Accordion.vue';
import HeroBanner from './components/HeroBanner/HeroBanner.vue';

export default {
  name: 'App',
  components: {
    HeroBanner,
    Accordion
  },
  data() {
    return {
      loaded: false,
      data: [
        {
            "name": "Black Widow",
            "description": "At birth the Black Widow (aka Natasha Romanova) is given to the KGB, which grooms her to become its ultimate operative. When the U.S.S.R. breaks up, the government tries to kill her as the action moves to present-day New York, where she is a freelance operative.",
            "image_url": "https://upload.wikimedia.org/wikipedia/en/7/74/Black_Widow_poster.jpg"
        },
        {
            "name": "Dune",
            "description": "Paul Atreides leads nomadic tribes in a battle to control the desert planet Arrakis.",
            "image_url": "https://upload.wikimedia.org/wikipedia/en/6/67/Dune_2020_movie_poster.jpg"
        },
        {
            "name": "James Bond",
            "description": "Recruited to rescue a kidnapped scientist, globe-trotting spy James Bond finds himself hot on the trail of a mysterious villain, who's armed with a dangerous new technology.",
            "image_url": "https://upload.wikimedia.org/wikipedia/en/f/fe/No_Time_to_Die_poster.jpg"
        },
        {
            "name": "Tenet",
            "description": "A secret agent is given a single word as his weapon and sent to prevent the onset of World War III. He must travel through time and bend the laws of nature in order to be successful in his mission.",
            "image_url": "https://upload.wikimedia.org/wikipedia/en/1/14/Tenet_movie_poster.jpg"
        },
        {
            "name": "Star Wars",
            "description": "Jyn's father is forcibly taken by the Galactic Empire to help them complete the Death Star. When she grows up, she joins a group of resistance fighters who aim to steal the Empire's blueprints.",
            "image_url": "https://upload.wikimedia.org/wikipedia/en/d/d4/Rogue_One%2C_A_Star_Wars_Story_poster.png"
        },
        {
            "name": "Harry Potter",
            "description": "Harry Potter, an eleven-year-old orphan, discovers that he is a wizard and is invited to study at Hogwarts. Even as he escapes a dreary life and enters a world of magic, he finds trouble awaiting him.",
            "image_url": "https://upload.wikimedia.org/wikipedia/en/7/7a/Harry_Potter_and_the_Philosopher%27s_Stone_banner.jpg"
        },
        {
            "name": "Die Hard",
            "description": "Hoping to spend Christmas with his estranged wife, detective John McClane arrives in LA. However, he learns about a hostage situation in an office building and his wife is one of the hostages.",
            "image_url": "https://upload.wikimedia.org/wikipedia/en/7/7e/Die_hard.jpg"
        },
        {
            "name": "Spiderman",
            "description": "Peter Parker's life changes when he is bitten by a genetically altered spider and gains superpowers. He uses his powers to help people and finds himself facing the Green Goblin, an evil maniac.",
            "image_url": "https://upload.wikimedia.org/wikipedia/en/f/f3/Spider-Man2002Poster.jpg"
        },
        {
            "name": "Mad Max",
            "description": "In a post-apocalyptic wasteland, Max, a drifter and survivor, unwillingly joins Imperator Furiosa, a rebel warrior, in a quest to overthrow a tyrant who controls the land's water supply.",
            "image_url": "https://upload.wikimedia.org/wikipedia/en/6/6e/Mad_Max_Fury_Road.jpg"
        }
      ]
    }
  }
}
</script>

<style>
html, body {
  height: 100%;
}

#app {
  font-family: Arial, sans-serif;
  background-color: #d8d8d8;
  color: #2c3e50;
}

.Button {
  background: #00458b;
  color: #fff;
  padding: 1rem 2rem;
  font-size: 1.125rem;
}

.container {
  width: 100%;
  max-width: 1024px;
  padding: 4rem 0;
  margin: 0 auto;
}
</style>
