<template>
  <div class="date-time-info">
    <div class="pull-left">
      <div class="date-time-current-day">
        <span> {{ currentDay | capitalize }}</span>
      </div>
      <div class="date-time-current-date">
        <strong class="label label-primary">{{ currentDate }}</strong>
        <span :class="['label', { 'label-success': isEvenWeek }, { 'label-danger': !isEvenWeek }]">{{ currentWeek }} неделя</span>
      </div>
    </div>
    <div class="clearfix"></div>
  </div>
</template>

<script>
import moment from "moment"

moment.locale('ru')
const currentDate = moment().format('LL');
const currentDay = moment().format('dddd');  
const numOfWeek = moment().format('W') 

export default {
  name: 'date-time-info',
  data(){
    return {
      currentDate,
      currentDay,   
      numOfWeek
    }
  },
  computed: {
    currentWeek() {
      return this.numOfWeek % 2 == 0 ? "Четная" : "Нечетная";
    },
    isEvenWeek(){
      return this.numOfWeek % 2 == 0;
    }
  },
  filters: {
    capitalize(value){
      return value[0].toUpperCase() + value.slice(1);
    }
  },
}
</script>

<style>
  .date-time-info { padding-bottom: 10px; border-bottom: 1px solid #ddd; margin-bottom: 0px;}
  .date-time-current-day { font-size: 30px; }
  .date-time-current-date { font-size: 18px; }
</style>
