<template lang="html">
    <button @click="addToCart" type="button" name="button" class="btn btn-success">{{ message }}</button>
</template>

<script>
export default {
    data(){
        return {
            message: 'Agregar al carrito',
            endpoint: '/in_shopping_carts'
        }
    },
    props: { product: { type:Object } },
    methods:{
        addToCart(){
            axios({
                method: 'POST',
                url: this.endpoint,
                data: {
                    product_id: this.product.id
                },
                headers: {
                    'Accept' : 'application/json',
                    'Content-Type' : 'application/json'
                }
            }).then(() => {
                console.log('Se agrego el producto');
            }).then(() => {
                window.store.commit('incremet')
            })
        }
    }
}
</script>

<style lang="css">
</style>
