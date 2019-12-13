<template>
  <md-card
    class="md-card"
    v-bind:style="[isChecked ? {'background-color': 'currentColor'} : {'background-color': 'white'}]"
  >
    <md-checkbox v-model="isChecked">{{ film }}</md-checkbox>
  </md-card>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";

@Component
export default class Question extends Vue {
  @Prop() film!: String;
  isChecked: boolean = false;
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
  text-align: left;
  display: inline-table;
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
  }
}
</style>
