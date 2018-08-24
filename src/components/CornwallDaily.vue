<template>
<div id="printable">
  <v-jumbotron :gradient="gradient"
  :height=100000
  class="jumbo">
      <v-container fill-height>
        <v-layout align-center>
          <v-flex>
           <br><br><br><br>
  <h1 data-title="Cornwall Daily Status Meeting" id="font" class="cards" ><a href="">Cornwall Daily Status Meeting</a></h1>
  <!-- Summary table starts -->
   <br><br><br><br>
  <h1 data-title="Summary"class="cards"></h1>
  <br>
  <v-card
  class="cards"
  :hover=true
  :width="wt">
   <v-data-table
   id="odd"
    :headers="summaryHeaders"
    :items="summaryData"
    hide-actions
    class="elevation-24"
  >
    <template class="color" id="tem" slot="items" slot-scope="props">
      <td class="text-xs-left">{{ props.item.summary }}</td>
      <td class="text-xs-left">{{ props.item.mc }}</td>
      <td class="text-xs-left">{{ props.item.nonmc }}</td>
      <td class="text-xs-left">{{ props.item.total }}</td>
      <td class="text-xs-left">{{ props.item.active }}</td>
      <td class="text-xs-left">{{props.item.nonactive }}</td>
    </template>
  </v-data-table>
  </v-card>
  <!-- Summary table ends -->
  <!-- Incidents table starts -->
   <br><br><br><br>
  <h1 data-title="Incidents"class="cards"></h1>
  <br>
  <v-card
  class="cards"
  :hover=true
  :width="wt">
   <v-data-table
    :headers="head1Headers"
    :items="head1Information"
    hide-actions
    class="elevation-24"
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.head1 }}</td>
      <td>{{ props.item.head2 }}</td>
      <td>{{ props.item.head3 }}</td>
      <td><v-checkbox
            :input-value="props.item.option"
            primary
            hide-details
          ></v-checkbox></td>
    </template>
  </v-data-table>
  </v-card>
  <!-- Incidents table ends -->
  <!-- Interactions table starts -->
   <br><br><br><br>
  <h1 data-title="Interactions" class="cards"></h1>
  <br>
  <v-card
  class="cards"
  :hover=true
  :width="wt">
   <v-data-table
    :headers="head1Headers"
    :items="head1Information"
    hide-actions
    class="elevation-24"
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.head1 }}</td>
      <td>{{ props.item.head2 }}</td>
      <td>{{ props.item.head3 }}</td>
      <td><v-checkbox
            :input-value="props.item.option"
            primary
            hide-details
          ></v-checkbox></td>
    </template>
  </v-data-table>
  </v-card>
  <!-- Interactions table ends -->
  <!-- Tasks table starts -->
   <br><br><br><br>
  <h1 data-title="Tasks"class="cards"></h1>
  <br>
  <v-card
  class="cards"
  :hover=true
  :width="wt">
   <v-data-table
    :headers="head1Headers"
    :items="head1Information"
    hide-actions
    class="elevation-24"
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.head1 }}</td>
      <td>{{ props.item.head2 }}</td>
      <td>{{ props.item.head3 }}</td>
      <td><v-checkbox
            :input-value="props.item.option"
            primary
            hide-details
          ></v-checkbox></td>
    </template>
  </v-data-table>
  </v-card>
  <br><br><br><br>
  <div id="editor"></div>
  <!-- Tasks table ends -->
          </v-flex>
        </v-layout>
      </v-container>
    </v-jumbotron>
</div>
</template>
<script>
import pdf from 'vue-pdf'
import * as jsPDF from 'jspdf';
//import { autoTable } from 'jspdf-autotable'; 

export default {
  name: 'home',
  components: {
    pdf
  },
    data () {
      return {
        wt: '65%',
        gradient: 'to top right, #99C5DC, #0064E5 ',
        name: 'hola',
        summaryHeaders: [
          { text: 'Summary', value: 'summary'},
          { text: 'MC', value: 'mc'},
          { text: 'nonMC', value: 'nonmc'},
          { text: 'Total', value: 'total'},
          { text: 'Active', value: 'active'},
          { text: 'nonActive', value: 'nonACTIVE'},
        ],
        summaryData: [
          {
            value: false,
            summary: 'DBCI',
            mc: 75,
            nonmc: 1500.46,
            total: 10,
            active: 20,
            nonactive: 44,
          },
          {
            value: false,
            summary: 'DBCI',
            mc: 75,
            nonmc: 1500.46,
            total: 10,
            active: 20,
            nonactive: 44,
          },
          {
            value: false,
            summary: 'DBCI',
            mc: 75,
            nonmc: 1500.46,
            total: 10,
            active: 20,
            nonactive: 44,
          }
        ],
        head1Headers: [
          { text: 'Head 1',value: 'head1'},
          { text: 'Head 2', value: 'head2' },
          { text: 'Head 3', value: 'head3' },
          { text: 'Option', value: 'option'},
        ],
        head1Information: [
          {
            value: false,
            head1: 'riki',
            head2: 262,
            head3: 16.0,
            option: true
          },
          {
            value: false,
            head1: 'riki',
            head2: 262,
            head3: 16.0,
            option: false
          },
          {
            value: false,
            head1: 'riki',
            head2: 262,
            head3: 16.0,
            option: true
          }
        ]
      }
    },
methods: {
  print(){
   var vm = this
   var columns = [
     {title: "Title", dataKey: "title"},
     {title: "Description", dataKey: "description"},
   ]
   var doc = new jsPDF('p', 'pt')
   doc.autoTable(columns, vm.head1Information)
   doc.save('table.pdf')
  }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cards{
  margin-left: 5%;
  margin-right: 5%;
}

body {
		background: #666;
		padding: 1em;
	}
/* #font{
  font-size: 250%;
  font-weight: bold;
} */
#odd #tem td:nth-child(odd){
  background: white
}

h1 {
		position: relative;
		font-size: 250%;
		margin-top: 0;
		font-family: 'Myriad Pro', 'Myriad', helvetica, arial, sans-serif;
		text-shadow: 2px 3px 3px #292929;
		letter-spacing: auto;
		-webkit-text-stroke: 1px white;
	}
	h1 a {
		text-decoration: none;
		color: #ffffff;
		position: absolute;

		-webkit-mask-image: -webkit-gradient(linear, left top, left bottom, from(rgba(0,0,0,1)), color-stop(50%, rgba(0,0,0,0)), to(rgba(0,0,0,1)));
		text-shadow: 0 2px 0 #e9e9e9;
		-webkit-transition: all .3s;
		-moz-transition: all .3s;
		transition: all .3s;
	}
	h1 a:hover {
		color: #00BCD4;
		-webkit-mask-image: -webkit-gradient(linear, left top, left bottom, from(rgba(0,0,0,1)), color-stop(50%, rgba(0,0,0,.3)), to(rgba(0,0,0,1)));	
	}

	h1:after {
		color: #dbdbdb;
		content : attr(data-title);
	}
 
</style>
