<template>
    <p>Hello World</p>
</template>
<script>
import moment from "moment";
export default {
    mounted(){
    let date = moment().startOf("month");
    const youbiNum = date.day();
    console.log(youbiNum)

    console.log(date.subtract(youbiNum, "days"));

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
  mounted(){
    console.log(this.getStartDate())
  } 

  
  } 
}
</script>