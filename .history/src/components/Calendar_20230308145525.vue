<template>
  <p>Hello World</p>
</template>
<script>
import moment from "moment";
export default {
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
