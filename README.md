# full-call-transport

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).



<h2>TRACTORS</h2>

<input type="text" id="myInput" onkeyup="myFunction()" placeholder="Search for drivers.." title="Type in a name">

<table class="myTable" id="external-events-list-2">
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
    <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr1">Revanth</div></td>
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
    <td class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'><div  class='fc-event-main' id="tr4"></div></td>
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
















<div id='external-events'>
      <h4>Drivers list</h4>

      <div id='external-events-list'>
        <div class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'>
          <div class='fc-event-main-1' id="dr1">Driver 1</div>
        </div>
        <div class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'>
          <div class='fc-event-main-2' id="dr2">Driver 2</div>
        </div>
        <div class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'>
          <div class='fc-event-main' id="dr3">Driver 3</div>
        </div>
        <div class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'>
          <div class='fc-event-main' id="dr4">Driver 4</div>
        </div>
        <div class='fc-event fc-h-event fc-daygrid-event fc-daygrid-block-event'>
          <div class='fc-event-main' id="dr5">Driver 5</div>
        </div>
      </div>

      <p>
        <input type='checkbox' id='drop-remove' />
        <label for='drop-remove'>remove after drop</label>
      </p>
    </div>