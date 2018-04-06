<template>
    <div class="product">
        <form>
            <div class="form-group">
                <label for="Title">Title</label>
                <input type="text" class="form-control" id="title" v-model="product.title">
            </div>

            <div class="form-group">
                <label for="Price">Price</label>
                <input type="number" class="form-control" id="price" v-model="product.price">
            </div>

            <div class="form-group">
                <label for="qt">QT</label>
                <input type="number" class="form-control" id="qt" v-model="product.qt">
            </div>

            <button type="submit" class="btn btn-default" @click.prevent="addProduct"> Добавить продукт</button> 
        </form>
    </div>
</template>

<script>
    import ProductService from './ProductService.js'

    export default {
        data() {
            return {
                product: {}
            }
        },
        methods: {
            addProduct() {
                ProductService.addProduct(this.product.title, this.product.price, this.product.qt);
            }
        }
    }
</script>

<style scoped>
    div.product {
        width: 500px;
        border: 1px solid green;
        border-radius: 10px;
        margin: 10px;
        padding: 10px;
    }
</style>
