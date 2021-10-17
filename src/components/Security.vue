<template>
  <div class="container">
    <h3>Users:</h3>
    <div class="row">
        <div class="col-6">
            <table>
                <tr>
                    <td>created</td>
                    <td>Description</td>
                    <td>created age</td>
                </tr>
                <tr v-for="item in alertslist" v-bind:key="item.id">
                    <td>{{item.created}}</td>
                    <td>{{item.description}}</td>
                    <td>{{item.created_age}}</td>
                </tr>
             </table>
        </div>
        <div class="col-6">
            <table>
                <tr>
                    <td>Device_status</td>
                    <td>Description</td>
                    <td>Device ID</td>
                </tr>
               <tr v-for="item in devicelist" v-bind:key="item.id">
                    <td>{{item.device_live}}</td>
                    <td>{{item.description}}</td>
                    <td>{{item.device_id}}</td>
                </tr>
             </table>
        </div>
    </div>
    
  </div>
</template>

<script>
    import Vue from 'vue';
    import axios from 'axios';
    import VueAxios from 'vue-axios';
    Vue.use(VueAxios,axios)

  export default {
    name: 'Incidents',
    data()
    {
        return {alertslist:undefined};
        return {devicelist:undefined};
    },
    mounted()
    {
        Vue.axios.get('https://thinkst-frontend-resources.s3-eu-west-1.amazonaws.com/incidents/data.json')
        .then((resp)=>{
            this.alertslist=resp.data.alerts;
            this.devicelist=resp.data.device_list;
            console.warn(resp.data);
        })
    }
    }
</script>




<style>
  h3 {
    margin-bottom: 5%;
  }
</style>