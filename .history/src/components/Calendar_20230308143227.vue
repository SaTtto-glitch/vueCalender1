<template>
    <p>Hello World</p>
</template>
<script>
export default {
    mounted(){
    let date = moment().startOf("month");
    const youbiNum = date.day();
    console.log(youbiNum)
  } 
}
</script>