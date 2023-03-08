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
  } 
}
</script>