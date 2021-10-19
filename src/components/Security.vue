

<template>
  <div class="container">
    <h3>Users:</h3>

  
<div id="accordion" class="accordion">
   
        <div v-for="(item, index) in device_alert_list" v-bind:key="item.id" style="background:#f3f3f3; padding:10px;margin-bottom:10px; border:5px solid #fff">
                <button data-toggle="collapse" :data-target="'#collapse'+index" aria-expanded="true" aria-controls="">
                    <span>{{item.description}}</span>
                </button>
               
                <div  :id="'collapse'+index" class="row collapse" aria-labelledby="headingOne" data-parent="#accordion">
                    <div class="col-2" v-for="alert in item.alerts" v-bind:key="alert.alert_count" style="overflow-wrap: break-word; background-color: pink;">
                        <hr>
                        <!-- <span>Alert count: {{alert.alert_count}}<br></span> -->
                        <span>DST-HOST: {{alert.dst_host}}<br><br></span>
                        <span>KEY: {{alert.key}}<br><br></span>
                        <span>SRC-HOST: {{alert.src_host}}<br><br></span>
                        <span>Description: {{alert.description}}<br><br></span>
                        <span>Created: {{alert.created}}<br><br></span>
                        <span>Age: {{alert.age}}<br><br></span>
                    </div>
                </div>
        </div>
    
  </div>
  </div>
</template>

<script>
    import Vue from 'vue';
    import { BootstrapVue, IconsPlugin  } from 'bootstrap-vue'

    // Import Bootstrap an BootstrapVue CSS files 
    import 'bootstrap/dist/css/bootstrap.css'
    import 'bootstrap/dist/js/bootstrap.min.js'

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

                    for (let x = 0; x < device_alert_list.length; x++) {
                        device_alert_list[x].alerts = []
                    }
                    //console.log(alerts_list)
                    let alert_count = 0
                    for (let x = 0; x < device_alert_list.length; x++) {
                        for (let i = 0; i < alerts_list.length; i++) {
                            if (device_alert_list[x].node_id === alerts_list[i].node_id) {
                                    device_alert_list[x].alerts.push(
                                        {
                                            created: alerts_list[i].created,
                                            description: alerts_list[i].description,
                                            age: alerts_list[i].created_age,
                                            node_id: alerts_list[i].node_id,
                                            dst_host: alerts_list[i].dst_host,
                                            key: alerts_list[i].key,
                                            ip_address: alerts_list[i].ip_address,
                                            src_host: alerts_list[i].src_host,
                                            alert_count: alert_count++,
                                        }
                                )
                            }
                        }  
                    }

                    this.device_alert_list = device_alert_list

                    console.log(this.device_alert_list[0].alerts)
                     
                })

                

            return { 
                alertslist: this.alertlist,
                devicelist: this.devicelist,
                device_alert_list: this.device_alert_list,
                
            };
        },
    }
</script>
