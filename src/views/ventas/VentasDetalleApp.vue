<template>
    <div>
        <Sidebar />
        <div class="main-content">
            <TopNav />
                        <div class="container-fluid">
                            <div class="row justify-content-center">
                                <div class="col-12 col-lg-10 col-xl-8">

                                    <div class="header mt-md-5">
                        <div class="header-body">
                        <div class="row align-items-center">
                            <div class="col">

                            <!-- Pretitle -->
                            <h6 class="header-pretitle">
                                Ventas
                            </h6>

                            <!-- Title -->
                            <h1 class="header-title">
                                Detalle de venta
                            </h1>

                            </div>
                        </div> <!-- / .row -->
                        <div class="row align-items-center">
                            <div class="col">

                            <!-- Nav -->
                            <ul class="nav nav-tabs nav-overflow header-tabs">
                                <li class="nav-item">
                                <router-link class="nav-link active" to="/ventas">
                                    Ventas
                                </router-link>
                                </li>
                        
                            </ul>

                            </div>
                          </div>
                        </div>
                                    </div>
                                    <div class="row">
                                        <div class="col-12 col-md-6">
                                        <div class="card">
                                        <div class="card-body">

                                        <!-- List group -->
                                        <div class="list-group list-group-flush my-n3">
                                        <div class="list-group-item">
                                            <div class="row align-items-center">
                                            <div class="col">

                                                <!-- Title -->
                                                <h5 class="mb-0">
                                                No Orden
                                                </h5>

                                            </div>
                                            <div class="col-auto">

                                                <!-- Time -->
                                                <time class="small text-muted" v-if="venta.serie">
                                                    {{venta.serie.toString().padStart(4,'0000')}}
                                                </time>

                                            </div>
                                            </div> <!-- / .row -->
                                        </div>
                                        <div class="list-group-item">
                                            <div class="row align-items-center">
                                            <div class="col">

                                                <!-- Title -->
                                                <h5 class="mb-0">
                                                Transaccion
                                                </h5>

                                            </div>
                                            <div class="col-auto">

                                                <!-- Time -->
                                                <time class="small text-muted" >
                                                {{venta.transaccion}}
                                                </time>

                                            </div>
                                            </div> <!-- / .row -->
                                        </div>
                                        <div class="list-group-item">
                                            <div class="row align-items-center">
                                            <div class="col">

                                                <!-- Title -->
                                                <h5 class="mb-0">
                                                Cliente
                                                </h5>

                                            </div>
                                            <div class="col-auto">

                                                <!-- Text -->
                                                <small class="text-muted" v-if="venta.cliente">
                                                {{venta.cliente.nombres}}
                                                </small>

                                            </div>
                                            </div> <!-- / .row -->
                                        </div>

                                        </div>

                                        </div>
                                        </div>
                                        </div>
                                        <div class="col-12 col-md-6">
                                        <div class="card">
                                        <div class="card-body">

                                            <!-- List group -->
                                            <div class="list-group list-group-flush my-n3">
                                            <div class="list-group-item">
                                                <div class="row align-items-center">
                                                <div class="col">

                                                    <!-- Title -->
                                                    <h5 class="mb-0">
                                                    Subtotal
                                                    </h5>

                                                </div>
                                                <div class="col-auto">

                                                    <!-- Time -->
                                                    <time class="small text-muted" datetime="1988-10-24">
                                                    {{convertCurrency(venta.total)}}
                                                    </time>

                                                </div>
                                                </div> <!-- / .row -->
                                            </div>
                                            <div class="list-group-item">
                                                <div class="row align-items-center">
                                                <div class="col">

                                                    <!-- Title -->
                                                    <h5 class="mb-0">
                                                    Envio
                                                    </h5>

                                                </div>
                                                <div class="col-auto">

                                                    <!-- Time -->
                                                    <time class="small text-muted" datetime="2018-10-28">
                                                    {{ convertCurrency(venta.envio) }}
                                                    </time>

                                                </div>
                                                </div> <!-- / .row -->
                                            </div>
                                            <div class="list-group-item">
                                                <div class="row align-items-center">
                                                <div class="col">

                                                    <!-- Title -->
                                                    <h5 class="mb-0">
                                                    Fecha de venta
                                                    </h5>

                                                </div>
                                                <div class="col-auto">

                                                    <!-- Text -->
                                                    <small class="text-muted">
                                                    {{convertDate(venta.createdAt)}}
                                                    </small>

                                                </div>
                                                </div> <!-- / .row -->
                                            </div>

                                            </div>

                                        </div>
                                        </div>
                                        </div>
                                        </div>

                                        <div class="card">
                                            <div class="card-header">

                                                <!-- Title -->
                                                <h4 class="card-header-title mb-0">
                                                    <b>Productos</b>
                                                </h4>

                                            </div>
                                            <div class="table-responsive">
                                                <table class="table table-sm table-nowrap card-table">
                                                <thead>
                                                    <tr>
                                                    <th>Producto</th>
                                                    <th class="text-center">Subtotal</th>
                                                    <th class="text-center">Cantidad</th>
                                                    <th class="text-center">Total</th>
                                                    </tr>
                                                </thead>
                                                <tbody class="fs-base">
                                                    <tr v-for="item in detalles">
                                                    <td class="products-product">
                                                        <div class="d-flex align-items-center">

                                                        <!-- Image -->
                                                        <div class="avatar">
                                                        <img class="avatar-img rounded me-3" :src="$url+'/obtener_portada_producto/'+item.producto.portada" alt="...">
                                                        </div>

                                                        <div class="ms-3">

                                                        <!-- Heading -->
                                                        <h4 class="fw-normal mb-1">{{item.producto.titulo.substr(0,30)}}</h4>

                                                        <!-- Text -->
                                                        <small class="text-muted">{{item.variacion.variacion}}</small>

                                                        </div>

                                                        </div>
                                                    </td>
                                                </td>
                                                    <td class="text-center">
                                                        {{convertCurrency(item.precio_unidad)}}
                                                    </td>
                                                    <td class="text-center">
                                                        {{item.cantidad}}
                                                    </td>
                                                    <td class="text-center">
                                                    {{convertCurrency(item.subtotal)}}
                                                    </td>
                                                    </tr>
                                                </tbody>
                                                </table>
                                            </div>
                                        </div>
                    </div>
                </div> <!-- / .row -->
            </div>
        </div>
    </div>
</template>
  

<script>
import Sidebar from '@/components/Sidebar.vue';
import TopNav from '@/components/TopNav.vue';
import axios from 'axios';
import currency_formatter from 'currency-formatter';
import moment from 'moment';

export default {
    name: 'VentasDetalleApp',
    data() {
        return {
            venta: {},
            detalles: [],
        }
    },
    methods: {
        init_data(){
            axios.get(this.$url+'/obtener_detalles_venta_admin/'+this.$route.params.id,{
                headers:{
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token,
                }
            }).then((result) => {
                this.venta = result.data.venta;
                this.detalles = result.data.detalles;
                console.log(result.data);
            }).catch((err) => {
                console.log(err);
            });
        },
        convertCurrency(number){
          return currency_formatter.format(number, { code: 'COP' });
        },
        convertDate(item){
          return moment(item).format('DD/MM/yyyy')
        },
    },
    beforeMount() {
        this.init_data();
    },
    components: {
      Sidebar,
      TopNav
    }
  }
  </script>
  