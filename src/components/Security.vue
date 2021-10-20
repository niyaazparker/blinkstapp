

<template>

<div id="wrapper">

        <!-- Sidebar -->
        
        <!-- End of Sidebar -->

        <!-- Content Wrapper -->
        <div id="content-wrapper" class="d-flex flex-column">

            <!-- Main Content -->
            <div id="content">

                <!-- Topbar -->
                <nav class="navbar navbar-expand navbar-light bg-white topbar mb-4 static-top shadow">

                    <!-- Sidebar Toggle (Topbar) -->
                    <button id="sidebarToggleTop" class="btn btn-link d-md-none rounded-circle mr-3">
                        <i class="fa fa-bars"></i>
                    </button>

                    <!-- Topbar Search -->
                    <form class="d-none d-sm-inline-block form-inline mr-auto ml-md-3 my-2 my-md-0 mw-100 navbar-search">
                        <div class="input-group">
                            <input type="text" class="form-control bg-light border-0 small" placeholder="Search for..." aria-label="Search" aria-describedby="basic-addon2">
                            <div class="input-group-append">
                                <button class="btn btn-primary" type="button">
                                    <i class="fas fa-search fa-sm"></i>
                                </button>
                            </div>
                        </div>
                    </form>

                    <!-- Topbar Navbar -->
                    <ul class="navbar-nav ml-auto">

                        <!-- Nav Item - Search Dropdown (Visible Only XS) -->
                        <li class="nav-item dropdown no-arrow d-sm-none">
                            <a class="nav-link dropdown-toggle" href="#" id="searchDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                                <i class="fas fa-search fa-fw"></i>
                            </a>
                            <!-- Dropdown - Messages -->
                            <div class="dropdown-menu dropdown-menu-right p-3 shadow animated--grow-in" aria-labelledby="searchDropdown">
                                <form class="form-inline mr-auto w-100 navbar-search">
                                    <div class="input-group">
                                        <input type="text" class="form-control bg-light border-0 small" placeholder="Search for..." aria-label="Search" aria-describedby="basic-addon2">
                                        <div class="input-group-append">
                                            <button class="btn btn-primary" type="button">
                                                <i class="fas fa-search fa-sm"></i>
                                            </button>
                                        </div>
                                    </div>
                                </form>
                            </div>
                        </li>

                        <!-- Nav Item - Alerts -->
                        <li class="nav-item dropdown no-arrow mx-1">
                            <a class="nav-link dropdown-toggle" href="#" id="alertsDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                                <i class="fas fa-bell fa-fw"></i>
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
                                        <div class="icon-circle bg-primary">
                                            <i class="fas fa-file-alt text-white"></i>
                                        </div>
                                    </div>
                                    <div>
                                        <div class="small text-gray-500">December 12, 2019</div>
                                        <span class="font-weight-bold">A new monthly report is ready to download!</span>
                                    </div>
                                </a>
                                <a class="dropdown-item d-flex align-items-center" href="#">
                                    <div class="mr-3">
                                        <div class="icon-circle bg-success">
                                            <i class="fas fa-donate text-white"></i>
                                        </div>
                                    </div>
                                    <div>
                                        <div class="small text-gray-500">December 7, 2019</div>
                                        $290.29 has been deposited into your account!
                                    </div>
                                </a>
                                <a class="dropdown-item d-flex align-items-center" href="#">
                                    <div class="mr-3">
                                        <div class="icon-circle bg-warning">
                                            <i class="fas fa-exclamation-triangle text-white"></i>
                                        </div>
                                    </div>
                                    <div>
                                        <div class="small text-gray-500">December 2, 2019f</div>
                                        Spending Alert: We've noticed unusually high spending for your account.
                                    </div>
                                </a>
                                <a class="dropdown-item text-center small text-gray-500" href="#">Show All Alerts</a>
                            </div>
                        </li>


                    </ul>

                </nav>
                <!-- End of Topbar -->

                <!-- Begin Page Content -->
                <div class="container-fluid" >

                    <!-- Page Heading -->
                    <div class="d-sm-flex align-items-center justify-content-between mb-4">
                        <h1 class="h3 mb-0 text-gray-800">Cards</h1>
                    </div>

                    <div class="row">

                        <!-- Earnings (Monthly) Card Example -->
                        <div class="col-xl-3 col-md-6 mb-4" >
                            <div class="card border-left-primary shadow h-100 py-2">
                                <div class="card-body">
                                    <div class="row no-gutters align-items-center">
                                        <div class="col mr-2">
                                            <div class="text-xs font-weight-bold text-primary text-uppercase mb-1">
                                                ddd</div>
                                            <div class="h5 mb-0 font-weight-bold text-gray-800">$40,000</div>
                                        </div>
                                        <div class="col-auto">
                                            <i class="fas fa-calendar fa-2x text-gray-300"></i>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                    </div>

                    <div class="row">

                        

                        <div class="col-xl-3 col-md-6 mb-4" v-for="item in device_alert_list" v-bind:key="item.id" v-on:click="isHidden = !isHidden">
                                <a href="#"  class="d-block card-header py-3">
                                    <h6 class="m-0 font-weight-bold text-primary">{{item.description}}</h6>
                                </a>
                            <div class="container" v-if="!isHidden">
                                <div v-for="alert in item.alerts" v-bind:key="alert.alert_count" >
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
                <!-- /.container-fluid -->

            </div>
            <!-- End of Main Content -->

            <!-- Footer -->
            <footer class="sticky-footer bg-white">
                <div class="container my-auto">
                    <div class="copyright text-center my-auto">
                        <span>Copyright © Your Website 2020</span>
                    </div>
                </div>
            </footer>
            <!-- End of Footer -->

        </div>
        <!-- End of Content Wrapper -->

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
                 isHidden: true
            };
             
        },
        
    }
</script>
