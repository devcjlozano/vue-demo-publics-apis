<template>
  <div class="search-characters">
    <div class="search-characters__form">
        <FormSearch @searchCharacter="searchCharacter"></FormSearch>
    </div>
    <div class="search-characters__title-character">
        <h1> {{ character }}</h1>
    </div>
    <div class="search-characters__list">
        <CharacterList/>
    </div>
  </div>
</template>

<script>
import FormSearch from '../components/FormSearch'
import CharacterList from '../components/CharacterList'

export default {
  name: 'SearchCharacters',
  components: {
    FormSearch,
    CharacterList
  },
  data () {
    return {
      msg: 'Buscador de personajes Marvel',
      character: '',
      characters: []
    }
  },
  methods: {
    searchCharacter (characterName) {
      this.$store.dispatch('marvel/FETCH_CHARACTERS', characterName)
      this.character = characterName
    }
  }
}
</script>

<style scoped>
.search-characters {
    display:flex;
    flex-direction: column;
    align-items: center;
}
.search-characters__form {
    width: 60%;
}
.search-characters__list {
    width: 100%;
}
</style>
