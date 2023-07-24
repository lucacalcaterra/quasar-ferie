<script setup>
import { useQuasar } from "quasar";
import { useCounterStore } from "stores/eventi";

const store = useCounterStore();

const $q = useQuasar();

//$q.localStorage.set("nome", "mario");
const value = $q.localStorage.getItem("nome");

console.log(value);
</script>

<template>
  <q-page class="flex flex-center">
    <!--     <q-calendar-month
      ref="calendar"
      v-model="selectedDate"
      :day-min-height="80"
      animated
      bordered
      locale="it"
      @change="onChange"
      @moved="onMoved"
      @click-date="onClickDate"
      @click-day="onClickDay"
      @click-workweek="onClickWorkweek"
      @click-head-workweek="onClickHeadWorkweek"
      @click-head-day="onClickHeadDay"
    /> -->
    <div>{{ store.counter }}</div>
    <q-btn @click="store.increment()" label="prova" />
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  methods: {
    async saveDb() {
      const db = new Dexie("FriendDatabase");
      db.version(1).stores({
        friends: "++id,name,age",
      });

      //
      // Manipulate and Query Database
      //
      try {
        await db.friends.add({ name: "Josephine", age: 21 });
        const youngFriends = await db.friends.where("age").below(25).toArray();
        alert(`My young friends: ${JSON.stringify(youngFriends)}`);
      } catch (e) {
        alert(`Error: ${e}`);
      }
    },
  },
});
</script>
