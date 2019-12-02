<template>
  <div>
    <div class="logo">
      <img src="./assets/logo.png" />
    </div>
    
  <div class="clock">
    <Value :inputValue="hours" />
    <Value :inputValue="minutes" :indicatorLength="6" />
    <Value :inputValue="seconds" :indicatorLength="6" />
  </div>
  <div class="links">
    <a href="https://github.com/ikonezg"><font-awesome-icon :icon="['fab', 'github']" size="6x"  :style="{ color: '#29a19c' }" /></a>
    <a href="https://dev.to/bergermarko"><font-awesome-icon :icon="['fab', 'dev']" size="6x"  :style="{ color: '#29a19c' }" /></a>
  </div>
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
    flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #222831;
  }
  .logo{
    display: flex;
    justify-content: center;
  }
  .clock{
    width: 800px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
  }
  .links {
    display: flex;
    justify-content: space-evenly;
  }
</style>
