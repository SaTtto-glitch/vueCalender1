<template>
  <p>Hello World</p>
</template>
<script>
import moment from "moment";


export default {
    data() {
    return {
      currentDate: moment(),
    };
  },
  methods: {
    getStartDate() {
      let date = moment(this.currentDate);
      date.startOf("month");
      const youbiNum = date.day();
      return date.subtract(youbiNum, "days");
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
  },
};
</script>
