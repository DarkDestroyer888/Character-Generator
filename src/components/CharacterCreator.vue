<template>
  <div class="character-creator">
      <h1>Character Creator</h1>
      <label for="character-name">Character Name: </label>
      <input type="text" id="character-name" v-model="name" placeholder="Enter a name" /> <br /><br />
      <label for="Element">Element: </label>
      <select id="Element-list" v-model="Element">
          <option value="Firen">Fire</option>
          <option value="Water">Water</option>
          <option value="Earth">Earth</option>
          <option value="Air">Air</option>
      </select><br /><br />
      <button v-on:click="postCharacter">Create Character</button>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
      name: 'CharacterCreator',
      data: function () {
          return {
              name: null,
              profession: null
          }
      },
      methods: {
          postCharacter: function () {
              axios
                  .post('http://localhost:3000/characters', {
                      name: this.name,
                      profession: this.profession
                  });
          }
      }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
