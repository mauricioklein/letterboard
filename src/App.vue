<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col md="9">
          <v-text-field
            v-for="(phrase, id) in phrases"
            v-model="phrases[id]"
            :key="id"
            :label="'Phrase #' + (id + 1)"
          />

          <v-col md="4" offset="4">
            <center>
              <Result v-bind:missing="missing" />
            </center>
          </v-col>

        </v-col>

        <v-col md="3">
          <Chars v-bind:dictionary="board" />
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
  import Vue from 'vue'
  import { Chars, Result } from  './components';

  export default Vue.component('App', {
    data: () => ({
      phrases: ["", ""],
      board: {
        'a': 8, 'b': 6, 'c': 6, 'd': 6,
        'e': 8, 'f': 4, 'g': 6, 'h': 6,
        'i': 8, 'j': 4, 'k': 6, 'l': 8,
        'm': 6, 'n': 6, 'o': 6, 'p': 6,
        'q': 2, 'r': 8, 's': 8, 't': 8,
        'u': 6, 'v': 4, 'w': 2, 'x': 4,
        'y': 4, 'z': 4, '&': 2, '!': 2,
        '?': 2, '#': 2, '@': 2
      }
    }),

    components: {
      Chars,
      Result
    },

    computed: {
      missing: function() {
        return this.calculate_missing(this.phrases, Object.assign({}, this.board))
      }
    },

    methods: {
      calculate_missing: (phrases, dictionary) => {
        const missing = {}

        // Discount from the dictionary the letters
        // used in the phrases
        for (const phrase of phrases) {
          phrase
            .toLowerCase()
            .split('')
            .filter(ch => ch in dictionary)
            .forEach(ch => {
              dictionary[ch]--

              if (dictionary[ch] < 0) {
                missing[ch] = -dictionary[ch]
              }
            })
        }

        return missing
      }
    }
  });
</script>
