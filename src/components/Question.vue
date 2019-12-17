<template>
  <md-card
    class="md-card"
    md-with-hover
    v-bind:style="[
      isChecked
        ? { 'background-color': 'currentColor' }
        : { 'background-color': 'white' }
    ]"
  >
    <md-checkbox v-model="isChecked" @change="onItemChecked">{{
      film
    }}</md-checkbox>
  </md-card>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";

@Component
export default class Question extends Vue {
  @Prop() film!: String;
  @Prop() maxTimes!: number;
  isChecked: boolean = false;

  onItemChecked(): void {
    if (this.maxTimes == 3) this.isChecked = false;
    const data = {
      isChecked: this.isChecked,
      film: this.film
    };
    this.$emit("change", data);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="css" scoped>
.md-card {
  display: flex;
  align-items: center;
  border-radius: 5px;
  margin: 5px 10px 5px 10px;
  width: 100%;
}

.md-checkbox {
  display: flex;
  align-content: space-between;
  width: inherit;
  margin: 0;
  padding: 16px 16px 16px 0;
}

.md-checkbox >>> label {
  display: flex;
  position: absolute;
  height: 100%;
  top: 0;
  margin-left: 16px;
  padding-right: 16px;
  align-items: center;
  width: 100%;
  text-align: left;
}

.md-checkbox >>> .md-checkbox-container {
  border-radius: 100%;
  border-color: black;
  align-self: center;
}

.md-checked >>> .md-checkbox-container {
  background-color: burlywood;
}

.md-checked >>> label {
  color: white;
}

@media (max-width: 599px) {
  .md-card {
    padding-left: 10px !important;
    padding-top: 16px;
    padding-bottom: 16px;
  }
}
</style>
