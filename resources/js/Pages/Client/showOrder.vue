<template>
<div>
    <div>
        <main class="w-full flex-grow p-6">
            <h1 class="text-3xl text-black">Order View</h1>
            <!-- component -->
                <div class="py-5">
                    <!-- component -->
                    <div class="flex items-center justify-center mx-5">
                    <div class="w-full  mb-2 justify-center rounded-lg text-white bg-blue-900">
                    <h3 class="text-white p-3 md:text-2xl lg:text-2xl text-lg"></h3>
                    <div v-for="vendor in vendorDetails" :key="vendor.account_id" class="p-5 pt-1 flex-wrap  flex items-center gap-2 justify-center">
                        <div class="bg-gradient-to-r flex-auto  w-42 h-42  from-blue-800 to-indigo-700    shadow-lg    rounded-lg">
                            <div class="md:p-7 p-4">
                                <h2 class="text-xl text-center text-gray-400 capitalize">Client Name</h2>
                                <h3 class="text-sm  text-white  text-center"> <i class="fa fa-user ml-3 text-black"></i> {{ vendor.name }} </h3>
                            </div>
                        </div>
                        <div class="bg-gradient-to-r flex-auto w-42 h-42  from-blue-800 to-indigo-700    shadow-lg    rounded-lg">
                            <div class="md:p-5 p-4">
                                <h2 class="text-xl text-center text-gray-400 capitalize">Client Contacts</h2>
                                <h3 class="text-sm  text-white  text-center"> <i class="fa fa-phone ml-3 text-black"></i> {{ vendor.phone }} </h3>
                                <h3 class="text-sm  text-white  text-center">  <i class="fa fa-envelope ml-3 text-black"></i> {{ vendor.email }} </h3>
                            </div>
                        </div>
                        <div class="bg-gradient-to-r flex-auto  w-42 h-42  from-blue-800 to-indigo-700    shadow-lg    rounded-lg">
                            <div class="md:p-5 p-4">
                                <h2 class="text-lg text-center text-gray-400 capitalize">Shop Address</h2>
                                <h3 class="text-sm  text-white  text-center"> <i class="fa fa-map-marker-alt ml-3 text-black"></i> {{ vendor.location }} </h3>
                                <h3 class="text-sm  text-white  text-center">  <i class="fa fa-route ml-3 text-black"></i> {{ vendor.address }} </h3>
                            </div>
                        </div>
                        <div class="bg-gradient-to-r flex-auto  w-42 h-42  from-blue-800 to-indigo-700    shadow-lg    rounded-lg">
                            <div class="md:p-7 p-4">
                                <h2 class="text-lg text-center text-gray-400 capitalize" style="">Order Amount</h2>
                                <h3 class="text-sm text-white  text-center capitalize"> <i class="fa fa-wallet ml-3 text-black"></i> {{ orderDetails.payment }}</h3>
                                <h3 class="text-sm text-white  text-center capitalize"> <i class="fa fa-money-bill-wave ml-3 text-black"></i> <span class="text-gray-400 text-xs">KSHS.</span> {{ orderTotals }}</h3>
                            </div>
                        </div>
                    </div>
                    </div>
                    </div>
                </div>
            <!-- Products -->
            <main class="px-3">
                <div class="text-2xl sm:text-2xl text-center my-5">Products Ordered</div>
                <div class="grid md:grid-cols-3 gap-8 m-2 max-w-5xl m-auto">
                    <div v-for="product in orderDetails.products" :key="product._id" class="bg-white">
                    <img :src="'/' + product.photos" alt="" class="w-full h-48 sm:h-56 object-cover" />
                    <div class="px-1 py-1 mb-2 text-center">
                        <div class="text-md font-bold text-blue-700 mb-5">{{ product.title }}</div>

                        <div class="text-sm font-bold text-gray-700"><span class="text-blue-700 text-sm">Quantity:</span> {{product.quantity }}</div>
                        <div class=" text-sm font-bold text-gray-700"><span class="text-blue-700 text-sm">Price: </span><span class="text-gray-400 text-xs">KSHS.</span> {{product.price }}</div>
                        <div class="text-sm font-bold text-gray-700"><span class="text-blue-700 text-sm">Total: </span><span class="text-gray-400 text-xs">KSHS.</span> {{product.total }}</div>

                        <span class="text-sm">{{ product.description }}</span>
                    </div>

                    <button class="w-full text-md h-8 text-white font-extrabold bg-blue-800">More Product Details</button>
                    </div>
                </div>
            </main>
            
        </main>
    </div>
</div>
</template>

<script>
import Layout from '../Dashboard'
import moment from 'moment';

export default {
    name:'ClientOrder',
    layout: Layout,
    props: {
        orderDetails:Object,
        vendorDetails:Object,
    },
    created() {
        this.setOrders()
    },
    computed: {
        orderTotals(){
            var cartCalculation = this.orderDetails.products.reduce(function(prev, cur) {
                return prev + cur.total;
            }, 0);
            return cartCalculation
        },
    },
    data () {
        return {
            products:[],
            name:'',
            phone:'',
            address:''
        }
    },
    methods: {
        setOrders(){
            console.log(this.orderDetalls.products)
            this.products = []
            var prods = this.orderDetails.products
            this.products.push(prods)
            console.log(this.products)

        },
        moment: function (time) {
            return moment(time);
            },

    }
    
}
</script>

<style scoped>

</style>