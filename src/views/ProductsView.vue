 <template>
    <div class="container">
        <div class="row">
            <h2>Products</h2>
        </div>
        <div class="row gap-2 justify-content-center" v-if="products?.length">
            <Card v-for="product in products" :key="product.id">
                <template #cardHeader>
                    <img :src="product.ImageUrl" :alt="product.flowerName" loading="lazy" class="img-fluid">
                </template>
                <template #cardBody>
                    <h5 class="card-title">{{ product.Description }}
                    </h5>
                    <p class="lead">{{ product.Price }}</p>
                    <!-- <p class="shadow">R {{ product.amount }}</p> -->
                </template>
            </Card>
        </div>
        <div v-else class="d-flex justify-content-center">
            <div class="spinner-border" role="status">
            </div>
        </div>
    </div>
</template>
<script>
import Card from '@/components/Card.vue';
export default {
    components: {
        Card
    },
    computed: {
        products() {
            return this.$store.state.products
        }
    },
    beforeCreate(){
       alert("Before create");
    },
    created(){ 
        alert("Created")
    },
    beforeMount(){
        alert("Before mount")
    },
    mounted() {
        this.$store.dispatch('fetchProducts')
    },
    updated(){

    },
    unmounted(){
        alert("unmounted")
    }
}
</script>
<style scoped>

</style>