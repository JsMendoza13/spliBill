<script setup>
import { getGrandTotal, store } from "../store/store";
import Label from "./Label.vue";
import Person from "./Person.vue";
</script>
<template>
  <div class="no-item" v-if="store.people.length == 0">No items</div>
  <div class="people-view" v-if="store.people.length > 0">
    <div class="header">
      <div>
        <Label title="Total + Tip: " :value="getGrandTotal()" />
      </div>
      <div>
        <Label title="Remaining: " :value="store.params.remaining" />
      </div>
    </div>
    <div class="people-container">
      <Person
        v-for="person in store.people"
        :key="person.id"
        :id="person.id"
        :number-of-person="person.numberOfPerson"
        :total-per-person="person.totalPerPerson"
        :paid="person.paid"
      />
    </div>
  </div>
</template>
<style scoped>
.no-item {
  border: solid 0.5px rgb(3, 78, 3);
  border-radius: 5.5px;
  color: #cccccc5b;
  width: 100%;
  height: 90vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  margin: 10px;
}

.people-view {
  margin: 10px;
  display: flex;
  align-items: center;
  flex-direction: column;
  border: solid 0.5px rgb(3, 78, 3);
  border-radius: 5.5px;
  padding: 0 5px;
}

.people-container {
  width: 800px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: auto;
  gap: 10px;
}

.header {
  color: whitesmoke;
  font-weight: bolder;
  padding: 20px 0;
  font-size: 28px;
  display: flex;
  justify-content: space-between;
  gap: 10px;
  flex-direction: column;
}
</style>
