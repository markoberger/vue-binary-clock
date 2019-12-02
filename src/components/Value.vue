<template>
    <div class="indicator-row">
        
        <div class="bulb" v-for="(indicator, index) in indicators" v-bind:key="index" v-bind:class="{ green: indicator !== 0}"></div> 
    </div>
</template>

<script>
    export default {
        name: 'Value',
        data() {
            return {
                indicators: [0,0,0,0,0]

            }
        },
        props: {
            inputValue: {
                type: Number,
                default: () => '',
            },
            indicatorLength: {
                type: Number,
                default: () => 5
            }
        },
        methods:{
            transformator(){
                const valurRevers = this.inputValue.toString(2).split('').reverse();
                this.indicators = this.indicators.reverse().map((v, i) => valurRevers[i] ? +valurRevers[i] : 0 ).reverse();                 
            }
        },
        created() {
            if(this.indicatorLength === 5){
                this.indicators = new Array(5).fill(0);
            } else {
                this.indicators = new Array(6).fill(0);
            }
        },
        watch: {
            inputValue: function () { 
                this.transformator();    
            }
        }

    }
</script>

<style scoped>
    .indicator-row {
        display: flex; 
        align-content: center;
        justify-content: flex-end;
    }
    .bulb {
        width: 100px;
        height: 100px;
        margin: 1rem;
        border-radius: 50%;
        background-color: #393e46;
    }
    .green {
        background-color: #29a19c;
        box-shadow: 0 0 15px 5px #a3f7bf;
        
    }
    
</style>