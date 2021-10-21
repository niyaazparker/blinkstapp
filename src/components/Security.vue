

<template>

<div id="wrapper">

        <div id="content-wrapper" class="d-flex flex-column">

            <div id="content">

                <div class="container-fluid" >

                    <!-- Page Heading -->
                    <div class="d-sm-flex align-items-center pt-4 mb-4">
                        <div class="sidebar-brand d-flex align-items-center justify-content-center">
                            <div class="sidebar-brand-icon">
                                <img src="images/canary_logo.png" width="40">
                            </div>
                            <div class="sidebar-brand-text mx-2">Canary</div>
                        </div>
                    </div>
                     <div class="row mb-3"><div class="col-2"><hr class="sidebar-divider my-0"></div></div>
                    <div class="sidebar-heading">
                        Devices
                    </div>
                    
                        <div class="">
                            
                                
                                <div class="row" v-for="item in device_alert_list" v-bind:key="item.node_id">
                                    <div class="col-2">
                                        <a href="#" class="device_link" @click='show = item.node_id'>
                                            {{item.description}}
                                            <i class="fa fa-chevron-right" aria-hidden="true"></i>
                                    
                                        </a>
                                        <hr class="sidebar-divider my-0">
                                    </div>
                                    
                                    
                                    <div class="col-10 px-0" style="position:absolute; top:0;right:0">
                                        <nav class="navbar navbar-expand navbar-light bg-white topbar mb-4 static-top shadow">

                    

                    <!-- Topbar Search -->
                    <form class="d-none d-sm-inline-block form-inline mr-auto ml-md-3 my-2 my-md-0 mw-100 navbar-search">
                        <div class="input-group">
                            <input type="text" v-model="searchbox" class="form-control bg-light border-0 small" placeholder="Search for..." aria-label="Search" aria-describedby="basic-addon2">
                            <div class="input-group-append">
                                <button class="btn btn-primary" type="button">
                                    <i class="fa fa-search fa-sm"></i>
                                </button>
                            </div>
                        </div>
                    </form>

                    <!-- Topbar Navbar -->
                    <ul class="navbar-nav ml-auto">

                        <!-- Nav Item - Search Dropdown (Visible Only XS) -->
                        <li class="nav-item dropdown no-arrow d-sm-none">
                            <a class="nav-link dropdown-toggle" href="#" id="searchDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                                <i class="fa fa-search fa-fw"></i>
                            </a>
                            <!-- Dropdown - Messages -->
                            <div class="dropdown-menu dropdown-menu-right p-3 shadow animated--grow-in" aria-labelledby="searchDropdown">
                                <form class="form-inline mr-auto w-100 navbar-search">
                                    <div class="input-group">
                                        <input type="text" class="form-control bg-light border-0 small" placeholder="Search for..." aria-label="Search" aria-describedby="basic-addon2">
                                        <div class="input-group-append">
                                            <button class="btn btn-primary" type="button">
                                                <i class="fa fa-search fa-sm"></i>
                                            </button>
                                        </div>
                                    </div>
                                </form>
                            </div>
                        </li>

                        <!-- Nav Item - Alerts -->
                        <li class="nav-item dropdown no-arrow mx-1">
                            <a class="nav-link dropdown-toggle" href="#" id="alertsDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                                <i class="fa fa-bell fa-fw"></i>
                                <!-- Counter - Alerts -->
                                <span class="badge badge-danger badge-counter">3+</span>
                            </a>
                            <!-- Dropdown - Alerts -->
                            <div class="dropdown-list dropdown-menu dropdown-menu-right shadow animated--grow-in" aria-labelledby="alertsDropdown">
                                <h6 class="dropdown-header">
                                    Alerts Center
                                </h6>
                                <a class="dropdown-item d-flex align-items-center" href="#">
                                    <div class="mr-3">
                                        <div class="icon-circle bg-alert">
                                            <i class="fa fa-exclamation-triangle text-white"></i>
                                        </div>
                                    </div>
                                    <div>
                                        <div class="small text-gray-500">October 12, 2021</div>
                                        <span class="font-weight-bold">HTTP Login Attempt!</span>
                                    </div>
                                </a>
                                <a class="dropdown-item d-flex align-items-center" href="#">
                                    <div class="mr-3">
                                        <div class="icon-circle bg-warning">
                                            <i class="fa fa-exclamation-triangle text-white"></i>
                                        </div>
                                    </div>
                                    <div>
                                        <div class="small text-gray-500">October 7, 2021</div>
                                        Canary Disconnected!
                                    </div>
                                </a>
                                <a class="dropdown-item d-flex align-items-center" href="#">
                                    <div class="mr-3">
                                        <div class="icon-circle bg-warning">
                                            <i class="fa fa-exclamation-triangle text-white"></i>
                                        </div>
                                    </div>
                                    <div>
                                        <div class="small text-gray-500">October 2, 2021</div>
                                        HTTP Proxy Request!
                                    </div>
                                </a>
                                <a class="dropdown-item text-center small text-gray-500" href="#">Show All Alerts</a>
                            </div>
                        </li>

                       

                        <div class="topbar-divider d-none d-sm-block"></div>

                        <!-- Nav Item - User Information -->
                        <li class="nav-item dropdown no-arrow">
                            <a class="nav-link dropdown-toggle" href="#" id="userDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                                <span class="mr-2 d-none d-lg-inline text-gray-600 small">Niyaaz Parker</span>
                                <img class="img-profile rounded-circle" src="images/profile.svg">
                            </a>

                            <!-- Dropdown - User Information -->
                            <div class="dropdown-menu dropdown-menu-right shadow animated--grow-in" aria-labelledby="userDropdown">
                                <a class="dropdown-item" href="#">
                                    <i class="fa fa-user fa-sm fa-fw mr-2 text-gray-400"></i>
                                    Profile
                                </a>
                                <a class="dropdown-item" href="#">
                                    <i class="fa fa-cogs fa-sm fa-fw mr-2 text-gray-400"></i>
                                    Settings
                                </a>
                                <div class="dropdown-divider"></div>
                                <a class="dropdown-item" href="#" data-toggle="modal" data-target="#logoutModal">
                                    <i class="fa fa-sign-out-alt fa-sm fa-fw mr-2 text-gray-400"></i>
                                    Logout
                                </a>
                            </div>
                        </li>

                    </ul>

                </nav>



                                        <div class="row mx-1">
                                         <div  class="card mb-4 col-lg-4 col-md-6 col-sm-6 col-12 px-0 mr-1 border-0 radius-0 background-none" v-for="alert in item.alerts" v-bind:key="alert.alert_count" v-show="show === alert.node_id" >
                                             
                                             <div class="px-2">
                                                <div class="border-radius shadow border-left-primary"> 
                                            <div class="card-header py-3">
                                                <h6 class="m-0 font-weight-bold text-primary">{{alert.description}}</h6>
                                            </div>
                                            <div class="card-body">
                                                <div class="alert-card">
                                                    <ul>
                                                        <li><span>DST-HOST:</span> {{alert.dst_host}}</li>
                                                        <li><span>KEY:</span> {{alert.key}}</li>
                                                        <li><span>SRC-HOST:</span> {{alert.src_host}}</li>
                                                        <li><span>Created:</span> {{alert.created}}</li>
                                                        <li><span>Age:</span> {{alert.age}}</li>
                                                    </ul>
                                                </div>
                                            </div>
                                </div>

                                        </div>
                                         </div>
                                         </div>
                                    </div>

                                </div>
                                
                           
                            
                          
                           

                        </div>

                   


                </div>
                <!-- /.container-fluid -->

            </div>
            <!-- End of Main Content -->

            

        </div>
        <!-- End of Content Wrapper -->
        <div id="background"></div>
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
                show: null,
                searchbox: "",
                
            };
            
             
        },

        computed:{
            alert_count: function() {
                    return this.alerts.filter((alert) => {
                        return alert.description.match(this.searchbox);
                    })
            }
        }
      
        
    }
</script>
