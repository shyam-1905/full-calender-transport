<script>
import FullCalendar from '@fullcalendar/vue'
import dayGridPlugin from '@fullcalendar/daygrid'
import timeGridPlugin from '@fullcalendar/timegrid'

import { INITIAL_EVENTS, createEventId } from '../event-utils'
import resourceTimeGridPlugin from '@fullcalendar/resource-timegrid';
import interactionPlugin from '@fullcalendar/interaction';
import  { Draggable } from '@fullcalendar/interaction';
import swal from 'sweetalert';

export default {

        
  components: {
    FullCalendar // make the <FullCalendar> tag available
  },
   
  data: function() {
    
    return {
     filter:'',
      checkbox: true,
     trailersinfo:[
       {
         trailerid:124,
         p1:"text-success",
         equipmenttype:"van",
         miles:0.00
       },
        {
         trailerid:125,
         p1:"text-success",
         equipmenttype:"van",
         miles:0.00
       },
        {
          trailerid:126,
          p1:"text-success",
         equipmenttype:"van",
         miles:0.00
       },
        {
         trailerid:127,
         p1:"text-success",
         equipmenttype:"van",
         miles:0.00
       },
        {
         trailerid:128,
         p1:"text-success",
         equipmenttype:"van",
         miles:0.00
       },
        {
         trailerid:129,
         p1:"text-success",
         equipmenttype:"van",
         miles:0.00
       },
        {
         trailerid:130,
         p1:"text-success",
         equipmenttype:"van",
         miles:0.00
       }
     ],
      calendarOptions: {
        plugins: [
          dayGridPlugin,
          timeGridPlugin,
          interactionPlugin,
          resourceTimeGridPlugin // needed for dateClick
        ],
        headerToolbar: {
          left: 'prev,next today',
          center: 'title',
          right: 'dayGridMonth,timeGridWeek,timeGridDay'
        },
        initialView: 'resourceTimeGridDay',
        resources: [{"id":"a","title":"1"},{"id":"b","title":"2"},{"id":"c","title":"3"},{"id":"d","title":"4"}],
        initialEvents: INITIAL_EVENTS, // alternatively, use the `events` setting to fetch from a feed
        editable: true,
        selectable: true,
        selectMirror: true,
        dayMaxEvents: true,
        weekends: true,
        select: this.handleDateSelect,
        eventClick: this.handleEventClick,
        eventsSet: this.handleEvents,
        droppable:true,
        
        drop: function(dropInfo) {
      //alert(dropInfo.draggedEl.data + " is dropped at " + dropInfo.date);
      //console.log(dropInfo.draggedEl.innerText + " is dropped at " + dropInfo.date);
      
     console.log(INITIAL_EVENTS);
     if(dropInfo.resource.id==INITIAL_EVENTS[0].resourceId){
          swal( dropInfo.draggedEl.innerText + " is dropped at " + INITIAL_EVENTS[0].title );
     }
     else if(dropInfo.resource.id==INITIAL_EVENTS[1].resourceId) {
        swal( dropInfo.draggedEl.innerText + " is dropped at " + INITIAL_EVENTS[1].title );
     }
     
     
    }
    
        /* you can update a remote database when these fire:
        eventAdd:
        eventChange:
        eventRemove:
        */
       
      },
      currentEvents: []
    }
  },
  computed: {
  filteredtrailerinfo() {
    return this.trailersinfo.filter(info => {
     
      const equipmenttype = info.equipmenttype;
      const searchTerm = this.filter;

      return equipmenttype.includes(searchTerm);
    });
  }
},
    mounted(){
      
       let draggableEl = document.getElementById('external-events-list');
            new Draggable(draggableEl, {
      itemSelector: '.fc-event',
      eventData: function(eventEl) {
        return {
         // title: eventEl.innerText.trim()
        };
      }
    });
     let draggableE2 = document.getElementById('external-events-list-2');
            new Draggable(draggableE2, {
      itemSelector: '.fc-event',
      eventData: function(eventEl) {
        return {
         // title: eventEl.innerText.trim()
        };
      }
    });
    },
  methods: {
     toggleCheckbox() {
      this.checkbox = !this.checkbox
     
    },

    handleWeekendsToggle() {
      this.calendarOptions.weekends = !this.calendarOptions.weekends // update a property
    },
      
      
    handleDateSelect(selectInfo) {
      let title = prompt('Please enter a new title for your event')
      let calendarApi = selectInfo.view.calendar

      calendarApi.unselect() // clear date selection

      if (title) {
        calendarApi.addEvent({
          id: createEventId(),
          title,
          start: selectInfo.startStr,
          end: selectInfo.endStr,
          allDay: selectInfo.allDay
        })
      }
    },

    handleEventClick(clickInfo) {
      if (confirm(`Are you sure you want to delete the event '${clickInfo.event.title}'`)) {
        clickInfo.event.remove()
      }
    },
     
    handleEvents(events) {
      this.currentEvents = events
    },
     
    
  }
}
</script>

<template>
<div id="app">
  <div class='demo-app'>
  <div class="container-fluid">
    <div class="row">
      <div class="col-md-12">
        <div class='demo-app-main'>
      
      <FullCalendar
        class='demo-app-calendar'
        :options='calendarOptions'
      >
        <template v-slot:eventContent='arg'>
          <b>{{ arg.timeText }}</b>
          <i>{{ arg.event.title1 }}</i>
        </template>
      </FullCalendar>
      
    </div>
      </div>
     </div>
     <div class="row">
      <div class="col-md-6">
       <div id='external-events'>
         
          <div class="table-header" style="background:lightblue">
             <p>TRACTORS</p>
            <span>Search<input type="text" id="myInput"  placeholder="Search for drivers.." title="Type in a name"></span>
            <div>
              <label class="switch">
                    <input type="checkbox" checked>
                    <span class="slider round"></span>
                  </label>
            </div>
          </div>
<table class="myTable" id="external-events-list">
  <tr class="header">
    <th>Tractor ID</th>
    <th>P1</th>
    <th>HR</th>
    <th>L</th>
    <th>DRIVER</th>
    <th>STATUS</th>
    <th>MILES</th>
    <th>MAP</th>
  </tr>
  <tr>
    <td>3</td>
    <td class="text-success"><i class="fas fa-circle"></i></td>
    <td class="text-danger"><i class="fas fa-circle"></i></td>
    <td class="text-warning"><i class="fas fa-circle"></i></td>
    <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr1">Revanth</div></td>
    <td></td>
    <td>7</td>
    <td>Hyd</td>
  </tr>
  <tr>
    <td>5</td>
    <td class="text-success"><i class="fas fa-circle"></i></td>
    <td class="text-danger"><i class="fas fa-circle"></i></td>
    <td class="text-warning"><i class="fas fa-circle"></i></td>
    <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr1">kumar</div></td>
    <td></td>
    <td>7</td>
    <td>Hyd</td>
  </tr>
  <tr>
    <td>8</td>
    <td class="text-success"><i class="fas fa-circle"></i></td>
    <td class="text-danger"><i class="fas fa-circle"></i></td>
    <td class="text-warning"><i class="fas fa-circle"></i></td>
    <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr2">shyam</div></td>
    <td></td>
    <td>7</td>
    <td>Hyd</td>
  </tr>
  <tr>
    <td>9</td>
    <td class="text-success"><i class="fas fa-circle"></i></td>
    <td class="text-danger"><i class="fas fa-circle"></i></td>
    <td class="text-warning"><i class="fas fa-circle"></i></td>
    <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr4">prasad</div></td>
    <td></td>
    <td>7</td>
    <td>Hyd</td>
  </tr>
  <tr>
    <td>11</td>
    <td class="text-success"><i class="fas fa-circle"></i></td>
    <td class="text-danger"><i class="fas fa-circle"></i></td>
    <td class="text-warning"><i class="fas fa-circle"></i></td>
    <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr5">abri</div></td>
    <td></td>
    <td>7</td>
    <td>Hyd</td>
  </tr>
  <tr>
    <td>15</td>
    <td class="text-success"><i class="fas fa-circle"></i></td>
    <td class="text-danger"><i class="fas fa-circle"></i></td>
    <td class="text-warning"><i class="fas fa-circle"></i></td>
   <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr6">gosh</div></td>
    <td></td>
    <td>7</td>
    <td>Hyd</td>
  </tr>
  <tr>
    <td>16</td>
    <td class="text-success"><i class="fas fa-circle"></i></td>
    <td class="text-danger"><i class="fas fa-circle"></i></td>
    <td class="text-warning"><i class="fas fa-circle"></i></td>
    <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr7">Renu</div></td>
    <td></td>
    <td>7</td>
    <td>Hyd</td>
  </tr>
  
</table> 

       </div>
     </div>
      <div class="col-md-6">
        <div id='external-events'>
           <div class="table-header" style="background:grey">
             <p>TRAILERS</p>
            <span>Search<input type="text" v-model="filter" placeholder="Search for drivers.." id="myInput"></span>
           
            <div>
              <label class="switch">
                <input type="checkbox" @click="toggleCheckbox">
                <div class="slider round"></div>
              </label>
            </div>
          </div>
          <table  class="myTable" id="external-events-list-2" v-if="checkbox" >
          <tr>
            <th>Trailerid</th>
            <th>P1</th>
            <th>equipmenttype</th>
            <th>MILES</th>
          </tr>
          <tr v-for="{ trailerid,p1,equipmenttype,miles} in filteredtrailerinfo" :key="trailerid" >
           <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr1">{{trailerid}}</div></td>
             <td :class="p1"><i class="fas fa-circle"></i></td>
            <td>{{equipmenttype}}</td>
            <td>{{miles}}</td>
          </tr>
          </table>   
  
        </div>
     </div>
     
    </div>
  </div>
    
    
  </div>
</div>
</template>

<style lang='css'>
.table-header{
  display: flex;
 
  justify-content: space-around;

}
.table-header p{
  font-size:30px;
  margin:3px
  ;
}
table.dataTable thead .sorting:after,
table.dataTable thead .sorting:before,
table.dataTable thead .sorting_asc:after,
table.dataTable thead .sorting_asc:before,
table.dataTable thead .sorting_asc_disabled:after,
table.dataTable thead .sorting_asc_disabled:before,
table.dataTable thead .sorting_desc:after,
table.dataTable thead .sorting_desc:before,
table.dataTable thead .sorting_desc_disabled:after,
table.dataTable thead .sorting_desc_disabled:before {
  bottom: .5em;
}
* {
  box-sizing: border-box;
}

 #myInput {
 
  font-size: 10px;
  padding: 12px 20px 12px 40px;
  border: 1px solid #ddd;
 margin-top:10px;
  margin-left:2px;
  width:300px;
  height: 30px;;

} 

.myTable {
  border-collapse: collapse;
  width:100%;
  border: 1px solid #ddd;
  font-size: 18px;
}

.myTable th, .myTable td {
  text-align: left;
  padding: 12px;
}

.myTable tr {
  border-bottom: 1px solid #ddd;
  cursor:pointer;
}

.myTable tr.header, .myTable tr:hover {
  background-color: #f1f1f1;
}

/* #external-events {
   position: relative;
    
    right: 40px;
    top: 20px;
    
    padding: 0 10px;
    border: 1px solid #ccc;
    background: #eee;
    text-align: left;
  }
  #external-events-2 {
   position: relative;
    
    right: 40px;
    top: 80px;
    
    padding: 0 10px;
    border: 1px solid #ccc;
    background: #eee;
    text-align: left;
  }
  #external-events h4 {
    font-size: 16px;
    margin-top: 0;
    padding-top: 1em;
  }

  #external-events .fc-event {
    margin: 3px 0;
    cursor: move;
  }

  #external-events p {
    margin: 1.5em 0;
    font-size: 11px;
    color: #666;
  }

  #external-events p input {
    margin: 0;
    vertical-align: middle;
  }
  #external-events-2 h4 {
    font-size: 16px;
    margin-top: 0;
    padding-top: 1em;
  }

  #external-events-2 .fc-event {
    margin: 3px 0;
    cursor: move;
  }

  #external-events-2 p {
    margin: 1.5em 0;
    font-size: 11px;
    color: #666;
  }

  #external-events-2 p input {
    margin: 0;
    vertical-align: middle;
  }

  
.wrap-right{
  float: right;
}
h2 {
  margin: 0;
  font-size: 16px;
}

ul {
  margin: 0;
  padding: 0 0 0 1.5em;
}

li {
  margin: 1.5em 0;
  padding: 0;
} */

b { /* used for event dates/times */
  margin-right: 3px;
}

.demo-app {
  display: flex;
  min-height: 100%;
  font-family: Arial, Helvetica Neue, Helvetica, sans-serif;
  font-size: 14px;
}



.demo-app-main {
  flex-grow: 1;
  padding: 3em;
}

.fc { /* the calendar root */
  max-width: 1000px;
   max-height: 400px;
  margin: 0 auto;
}

.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
  margin-top:10px;
}

.switch input { 
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: .4s;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
}

input:checked + .slider {
  background-color: #2196F3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196F3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}

</style>
