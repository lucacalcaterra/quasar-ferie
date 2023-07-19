<template>
  <q-page class="flex flex-center">
    <q-calendar-month
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
    />
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
});
</script>
