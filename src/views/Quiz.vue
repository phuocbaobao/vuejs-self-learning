<template>
  <div class="quiz">
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"
    />
    <h3>Pick three of your favorite Star Wars films</h3>
    <div class="md-layout md-gutter question-row">
      <!-- 25 is 1/4 screen resolution -->
      <question
        class="md-layout-item md-small-size-45 md-size-35"
        v-for="(film, index) in films"
        v-bind:key="index"
        @change="onChecked"
        :film="film"
        :maxTimes="times.length"
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
  }
})
export default class Quiz extends Vue {
  private films: String[] = [
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
  private times: String[] = new Array();

  private onChecked(data: any): void {
    const times = this.times;
    if (data.isChecked && times.length < 3) {
      times.push(data.film);
    } else if (!data.isChecked) {
      const deleteIndex = times.indexOf(data.film);
      if (deleteIndex != -1) {
        times.splice(deleteIndex, 1);
      }
    }
  }

  private get getMaxTimesLength(): number {
    return this.times.length;
  }
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
