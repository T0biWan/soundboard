<template>
  <div>
    <div class="dropdown" v-bind:class="{'is-active': dropdownIsActive}">
      <div class="dropdown-trigger">
        <button class="button" aria-haspopup="true" aria-controls="dropdown-menu" v-on:click="toggleDropdownIsActive">
          <span>{{activeTopic}}</span>
          <span class="icon is-small"><i class="fas fa-angle-down" aria-hidden="true"></i></span>
        </button>
      </div>
      <div class="dropdown-menu" id="dropdown-menu" role="menu">
        <div class="dropdown-content">
          <a
            v-for="(value, topic, index)  in sounds.topics"
            v-bind:key="index"
            class="dropdown-item"
            v-bind:class="{'is-active':(activeTopic === topic)}"
            v-on:click="chooseTopic(topic)"
          >{{topic}}</a>
        </div>
      </div>
    </div>

      <div class="sounds-container">
        <div
          class="custom-box"
          v-for="topic in sounds.topics[activeTopic]"
          v-bind:key="topic"
          @click.prevent="playSound(topic.sound)"
        ><h1>{{ topic.title }}</h1></div>
      </div>
  </div>
</template>

<script>
// ReadMe
// Farben random verteilen
// JSON muss ausgelagert werden, sollte beim kompilieren auch gestasht werden
import json from '@/sounds.json'

export default {
  name: 'Mainpage',
  data () {
    return{
      sounds: json,
      dropdownIsActive: false,
      activeTopic: 'animals' // remove
      // activeTopic: 'choose a topic...'
    }
  },
  methods: {
    toggleDropdownIsActive () {
      this.dropdownIsActive = !this.dropdownIsActive
    },
    chooseTopic (topic) {
      this.activeTopic = topic
      this.toggleDropdownIsActive()
    },
    playSound (sound) {
      if(sound) {
        var audio = new Audio(sound)
        audio.play()
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .dropdown {
    width: 100%;
  }

  .dropdown-trigger {
    width: 100%;
  }

  .button {
    display: flex;
    width: 100%;
    justify-content: center;
    background-color: #03A9F4;
    color: white;
  }

  .custom-box {
    box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
    color: #4a4a4a;
    background-color: #E1F5FE;
    width: 100px;
    height: 100px;
    border-radius: 5px;
    margin-top: 20px;
    margin-right: 10px;
    margin-left: 10px;

    display: flex;
    justify-content: center;
    align-items: center;
  }

  .sounds-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-bottom: 20px;
  }
</style>
