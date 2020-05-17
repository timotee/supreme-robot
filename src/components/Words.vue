<template>
  <div class="words">
    <b-input v-model.lazy="word"></b-input>
    <b-list-group>
      <b-list-group-item v-for="(word, index) in filteredWords" :key="index">
        {{ word }}
      </b-list-group-item>
    </b-list-group>
  </div>
</template>

<script>
export default {
  name: 'Words',
  async mounted() {
    await import('../services/words.json').then(({ default: words }) => {
      this.words = Object.freeze(words);
    });
  },
  data() {
    return {
      word: '',
      words: [],
      loading: false
    };
  },
  computed: {
    filteredWords() {
      return this.words.filter(dictionaryWord => {
        if (dictionaryWord.length !== this.word.length) {
          return false;
        }

        let dictionaryWordArray = dictionaryWord
          .split('')
          .sort()
          .join('');

        let wordArray = this.word
          .split('')
          .sort()
          .join('');

        return dictionaryWordArray === wordArray;
      });
    }
  }
};
</script>

<style scoped></style>
