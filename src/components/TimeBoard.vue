<template> 
  <b-col sm12 md6 lg4> 
    <panel>
      <panel-heading>
        <strong>{{ weekday }}</strong>
      </panel-heading>
        <list-group>
          <list-group-item 
            v-for="{ id, name, start, end, room } in lessons" 
            :key="id"
          >    
            <p class="list-group-item-heading">
              {{ name }}
            </p>
            <div class="pull-left">
              <i class="fa fa-clock-o" aria-hidden="true"></i>
              <span class="list-group-item-text">{{ start }} - {{ end }}</span>
              <i class="fa fa-sign-in" style="margin-right: 2px; margin-left: 10px;" aria-hidden="true"></i>  
              <strong class="list-group-item-text">{{ room }}</strong>
            </div>
            <div class="clearfix"></div>
          </list-group-item>
        </list-group>
    </panel>
  </b-col>
</template>

<script>
import BCol from './Reusable/BCol';
import Panel from './Reusable/Panel';
import PanelHeading from './Reusable/PanelHeading';
import ListGroup from './Reusable/ListGroup';
import ListGroupItem from './Reusable/ListGroupItem';

export default {
  name: 'time-board',
  props: { 
    weekday: { type: String, required: true },
    lessons: { type: Array, required: true },
  },
  components: {
    Panel, PanelHeading, ListGroup, ListGroupItem, BCol,
  },
}
</script>
