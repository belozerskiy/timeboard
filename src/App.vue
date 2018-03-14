<template>
  <div id="app">
    <navbar :title="title"></navbar>
    <container>
      <date-time-info></date-time-info>
      <two-side-block>
        <btn-group slot="left" 
          :about="courses" 
          :active="currentCourse"
          @select="selectCourse">
        </btn-group>
        <btn-group slot="right"
          v-if="isCourseSelected" 
          :about="groups" 
          :active="currentGroup"
          @select="selectGroup">
          
        </btn-group>
      </two-side-block>
      <b-row>
        <template v-if="isCourseSelected && isGroupSelected">
          <time-board 
            v-for="{ weekday, lessons } in timeboard" 
            :weekday="weekday"
            :lessons="lessons"
            :key="weekday"
          >
          </time-board>
        </template>
        <template v-else>
          <message>{{ infoMessage }}</message>
        </template>
      </b-row>
      <developed />
    </container>
  </div>
</template>

<script>
import Navbar from './components/Reusable/Navbar';
import Container from './components/Reusable/Container';
import BRow from './components/Reusable/BRow';
import BtnGroup from './components/Reusable/BtnGroup';
import TwoSideBlock from './components/Reusable/TwoSideBlock';
import Message from './components/Message';

import DateTimeInfo from './components/DateTimeInfo';
import TimeBoard from './components/TimeBoard';
import Developed from './components/Developed';

import { getTimeboardByGroup, getGroups, getCourses } from './api';

export default {
  name: 'app',
  data () {
    return {
      timeboard: [],
      title: "Мое расписание",
      courses: { label: 'Курсы', items: [] },
      groups: { label: 'Группы', items: [] },
      currentCourse: false,
      currentGroup: false,
    } 
  },
  async created() {
    this.courses.items = await getCourses();
    this.groups.items = await getGroups();
    this.timeboard = await getTimeboardByGroup();
  },
  computed: {
    isCourseSelected(){
      return this.currentCourse != false;
    },
    isGroupSelected(){
      return this.currentGroup != false;
    },
    infoMessage(){
      let message = ""
      if(!this.isCourseSelected) message = 'Пожалуйста укажите ваш курс.'
      if(!this.isGroupSelected) message = 'Пожалуйста укажите вашу группу.'
      if(!this.isCourseSelected && !this.isGroupSelected) message = 'Пожалуйста, укажите ваш курс и группу.'
      return message
    }
  },
  methods: {
    selectCourse(course){
      this.currentCourse = course ? `${course}` : false;
      this.currentGroup = false;
      console.log(`Course: ${course}`)
    },
    selectGroup(group){
      this.currentGroup = group ? `${group}` : false;
      console.log(`Group: ${group}`)
    }
  },
  components: {
    Navbar, 
    DateTimeInfo, 
    TwoSideBlock,
    Message,
    TimeBoard,
    Container, 
    BtnGroup,
    Developed,
    BRow,
  }
}
</script>

<style>
  body {
    background: #eee;
    overflow-y: scroll;
  }
  .navbar {
    border-radius: 0px;
  }
</style>
