<template>
  <div class="quiz">
    <h3>Pick three of your favorite Star Wars films</h3>
    <div class="md-layout md-gutter question-row">
      <!-- 25 is 1/4 screen resolution -->
      <question
        class="md-layout-item md-small-size-45 md-size-35"
        v-for="(film, index) in films"
        v-bind:key="index"
        v-on:click="onChecked"
        :film="film"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import Question from "@/components/Question.vue";

@Component({
  components: {
    question: Question
  },
  computed: {
    onChecked: () => console.log("Hello World")
  }
})
export default class Quiz extends Vue {
  films: String[] = [
    "Episode I – The Phantom Menace (1999)",
    "Episode II – Attack of the Clones (2002)",
    "Episode III – Revenge of the Sith (2005)",
    "Episode IV – A New Hope (1977)",
    "Episode V – The Empire Strikes Back (1980)",
    "Episode VI – Return of the Jedi (1983)",
    "Episode VII – The Force Awakens (2015)",
    "Episode VIII – The Last Jedi (2017)",
    "Episode IX – The Rise of Skywalker (2019)"
  ];
}
</script>

<style lang="scss" scoped>
h3 {
  font-size: 25px;
  line-height: initial;
}

.question-row {
  padding: 5px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
