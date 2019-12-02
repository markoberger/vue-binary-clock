<template>
  <div class="clock">
    <Value :inputValue="hours" />
    <Value :inputValue="minutes" :indicatorLength="6" />
    <Value :inputValue="seconds" :indicatorLength="6" />
  </div>
</template>

<script>

import Value from '@/components/Value';

export default {
  name: 'app',
  components: {
    Value,
    
  },
  data() {
    return {
      hours: 0,
      minutes: 0, 
      seconds: 0

    }
  },
  created() {
    this.loadTime();
  },
  methods: {
    loadTime() {
      setInterval(()=>{
        const timenow = new Date();
        this.hours = timenow.getHours();
        this.minutes = timenow.getMinutes();
        this.seconds = timenow.getSeconds();
      },1000);
    }
  }
  
}
</script>

<style>
  body {
    display: flex;
  justify-content: center;
  align-items: center;
  background-color: #222831;
  }
  .clock{
    width: 800px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
  }
</style>
