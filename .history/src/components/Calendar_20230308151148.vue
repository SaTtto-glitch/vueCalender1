<template>
  <h2>カレンダー{{ currentDate }}</h2>
  <button @click="prevMonth">前の月</button>
  <button @click="nextMonth">次の月</button>
  <div style="max-width: 900px; border-top: 1px solid gray">
    <div v-for="(week, index) in calendars" :key="index" style="display: flex; border-left: 1px solid gray">
      <div v-for="(day, index) in week" :key="index" style="flex: 1; min-height: 125px; border-right: 1px solid gray; border-bottom: 1px solid gray">
        {{ day.date }}
      </div>
    </div>
  </div>
</template>
<script>
import moment from "moment";

export default {
  data() {
    return {
      currentDate: moment(),
    };
  },
  computed: {
    calendars() {
      return this.getCalendar();
    },
  },

  methods: {
    nextMonth() {
      this.currentDate = moment(this.currentDate).add(1, "month");
    },
    prevMonth() {
      this.currentDate = moment(this.currentDate).subtract(1, "month");
    },

    getStartDate() {
      let date = moment(this.currentDate);
      date.startOf("month");
      const youbiNum = date.day();
      return date.subtract(youbiNum, "days");
    },
    getEndDate() {
      let date = moment(this.currentDate);
      date.endOf("month");
      const youbiNum = date.day();
      return date.add(6 - youbiNum, "days");
    },
    getCalendar() {
      let startDate = this.getStartDate();
      const endDate = this.getEndDate();
      const weekNumber = Math.ceil(endDate.diff(startDate, "days") / 7);

      let calendars = [];
      for (let week = 0; week < weekNumber; week++) {
        let weekRow = [];
        for (let day = 0; day < 7; day++) {
          weekRow.push({
            date: startDate.get("date"),
          });
          startDate.add(1, "days");
        }
        calendars.push(weekRow);
      }
      return calendars;
    },
  },

  mounted() {
    let date = moment().startOf("month");
    const youbiNum = date.day();
    console.log(youbiNum);

    const startDate = this.getStartDate();
    const endDate = this.getEndDate();
    const weekNumber = Math.ceil(endDate.diff(startDate, "days") / 7);

    console.log(weekNumber); //5と表示される
    console.log(this.getCalendar());
  },
};
</script>
