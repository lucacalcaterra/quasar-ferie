<script setup>
import { useQuasar } from "quasar";
import Dexie from "dexie";

const $q = useQuasar();

//$q.localStorage.set("nome", "mario");
const value = $q.localStorage.getItem("nome");

const db = new Dexie("FriendDatabase");
db.version(1).stores({
  friends: "++id,name,age",
});

//console.log(re);
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
    <q-btn @click="saveDb()" label="prova" />
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  methods: {
    saveDb() {
      console.log("ciao");
    },
  },
});
</script>
