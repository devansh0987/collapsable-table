<template>
<div>
  <table class="table table-dark">
  <thead>
    <tr>
      <th scope="col" v-for="header in title" :key="header.id">{{ header.description }}</th>
    </tr>
  </thead>
  <tbody>
    <template v-for="tableData in rows">
    <tr :key="tableData.id" @click="toggle(tableData.id)">
      <td >{{ tableData.date }}</td>
      <td >{{ tableData.trans_vol }}</td>
      <td >{{ tableData.post_count }}</td>
      <td >{{ tableData.cap_util }}</td>
      <td >{{ tableData.pnl }}</td>
      <td >{{ tableData.epv }}</td>
    </tr>
    <tr  v-if="opened.includes(tableData.id)" :key="tableData.transc_id">
      <td colspan="6">
      <div @click="openTransaction(tableData.transc_id)"> 
        > Transactions
      </div>
      <div v-if="openTransactions.includes(tableData.transc_id)">
        <table class="table table-dark">
          <thead>
            <tr>
              <th scope="col">Equity Id</th>
              <th scope="col">Equity Label</th>
              <th scope="col">Trigger</th>
              <th scope="col">Price</th>
              <th scope="col">Quantity</th>
              <th scope="col">Capital Used</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td >Bajaj Auto</td>
              <td>Bajaj Auto LTD</td>
              <td>95</td>
              <td>100</td>
              <td>10</td>
              <td>50</td>
            </tr>
          </tbody>
        </table>
      </div>
      </td>
    </tr>
    </template>
  </tbody>
</table>

</div>
</template>

<script>
/* eslint-disable */
export default {
data(){
  return{
  	opened: [],
    openTransactions:[],
    showTransactions:false,
  	rows: [
      { id: 1, date: '2021-01-01' , trans_vol: "2" , post_count:"5", cap_util:"5000",pnl:"400",epv:"10400",transc_id:10},
      { id: 2, date: '2021-01-01' , trans_vol: "2" , post_count:"5", cap_util:"5000",pnl:"400",epv:"10400",transc_id:11},
      { id: 3, date: '2021-01-01' , trans_vol: "2" , post_count:"5", cap_util:"5000",pnl:"400",epv:"10400",transc_id:12},
      { id: 4, date: '2021-01-01' , trans_vol: "2" , post_count:"5", cap_util:"5000",pnl:"400",epv:"10400",transc_id:13},
      { id: 5, date: '2021-01-01' , trans_vol: "2" , post_count:"5", cap_util:"5000",pnl:"400",epv:"10400",transc_id:14}
  	],
    title:[
      {id:1,description:"Date"},
      {id:2,description:"Transaction volume"},
      {id:3,description:"Position count"},
      {id:4,description:"Capital Utilized"},
      {id:5,description:"Profit & loss"},
      {id:6,description:"Ending portfolio value"}
    ]
  }
  },
  methods: {
  	toggle(id) {
    	const index = this.opened.indexOf(id);
      if (index > -1) {
      	this.opened.splice(index, 1)
      } else {
      	this.opened.push(id)
      }
    },
    openTransaction(id){
      const index = this.openTransactions.indexOf(id);
      if (index > -1) {
      	this.openTransactions.splice(index, 1)
      } else {
      	this.openTransactions.push(id)
      }
    }
  },
}
</script>

<style>

</style>