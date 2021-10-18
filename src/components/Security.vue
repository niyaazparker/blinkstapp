<style>
  h3 {
    margin-bottom: 5%;
  }
</style>

<template>
  <div class="container">
    <h3>Users:</h3>
 
    <div class="row">
        <!--<div class="col-3">
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
        <div class="col-3">
            <table>
                <tr>
                    <td>Device_status</td>
                    <td>Description</td>
                    <td>Device ID</td>
                </tr>
               <tr v-for="item in devicelist" v-bind:key="item.id">
                    <td>{{item.device_live}}</td>
                    <td>{{item.description}}</td>
                    <td>{{item.node_id}}</td>
                </tr>
             </table>
        </div>
        <div class="col-3" v-for="item in devicelist" v-bind:key="item.id">
            <div>{{item.description}}</div>
        </div>-->
        
    </div>
    
  

    <div class="row">
        <div class="col-3" v-for="item in device_alert_list" v-bind:key="item.id" style="background:#f3f3f3; padding:10px;margin-bottom:10px; border:5px solid #fff">
                <div>
                    <span>{{item.description}}</span>&nbsp;&nbsp;|&nbsp;&nbsp;
                    <span>{{item.created}}</span>
                </div>
                <div><span>{{item.node_id}}</span></div>
        </div>
    </div>
  </div>
</template>

<script>
    import Vue from 'vue';
    import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'

    // Import Bootstrap an BootstrapVue CSS files (order is important)
    import 'bootstrap/dist/css/bootstrap.css'
    import 'bootstrap-vue/dist/bootstrap-vue.css'

    // Make BootstrapVue available throughout your project
    Vue.use(BootstrapVue)
    // Optionally install the BootstrapVue icon components plugin
    Vue.use(IconsPlugin)

    import axios from 'axios';
    import VueAxios from 'vue-axios';
    Vue.use(VueAxios,axios)

  export default {
        name: 'Incidents',
        data() {

            Vue.axios.get('https://thinkst-frontend-resources.s3-eu-west-1.amazonaws.com/incidents/data.json')
                .then((resp) => {
                    this.alertslist=resp.data.alerts;
                    this.devicelist=resp.data.device_list;

                    // Not sure how to call functions that have been defined outside of axios call here.
                    let device_alert_list = this.devicelist
                    let alerts_list = this.alertslist

                    //console.log(alerts_list)

                    for (let x = 0; x < device_alert_list.length; x++) {
                        device_alert_list[x].alerts = []
                        for (let i = 0; i < alerts_list.length; i++) {
                            // console.log(alerts_list[i].node_id)
                            if (device_alert_list[x].created === alerts_list[i].created) {
                                // console.log(device_alert_list[x])
                                device_alert_list[x].alerts.push(
                                    {
                                        created: alerts_list[x].created,
                                        description: alerts_list[x].description,
                                        age: alerts_list[x].created_age,
                                        node_id: alerts_list[x].node_id,
                                    }
                                )
                            }
                        }
                        console.log(device_alert_list[x].alerts);
                        this.device_alert_list=resp.data.alerts;
                        this.device_alert_list = device_alert_list
                    }
                     
                })

            return { 
                alertslist: this.alertlist,
                devicelist: this.devicelist,
                device_alert_list: this.device_alert_list,
                
            };
        },
    }
</script>