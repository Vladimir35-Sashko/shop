<template>
    <div class="v-catalog">
        <h1>Catalog</h1>
        <div class="v-catalog__list">
            <v-catalog-item
            v-for="product in this.$store.state.products"
            :key="product.article"
            :product_data="product"
            @addToCart="addToCart"/>
        </div>
        
    </div>
</template>

<script>
import vCatalogItem from './v-catalog-item.vue'
import {mapActions} from 'vuex'

export default {
    name:"v-catalog",
    components:{
        vCatalogItem
    },
    props: {},
    data() {
        return {
        }
    },
    computed: {},
    methods: {
        ...mapActions([
            'GET_PRODUCTS_FROM_API',
            'ADD_TO_CART'

        ]),
        addToCart(data) {
            this.ADD_TO_CART(data)
        }
    },
    mounted() {
        this.GET_PRODUCTS_FROM_API()
    }
}
</script>

<style>
   .v-catalog {
        /* display: flex; */
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    }
    .v-catalog__list {
        display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    
    }
    
</style>
