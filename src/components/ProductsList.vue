<script>
    import products from '../data/db.json'
    import Product from './ProductComponent.vue'
    export default {
        name: 'Products List',
        components: {
            Product,
        },
        data() {

            return {

                products: products.products,
                priceOnSale: [],
                discountArray: [],

            };

        },

        methods: {

            displayProducts() {

                console.log(this.products);
                for(let i = 0; i < this.products.length; i++) {
                    console.log(Object.values(this.products));
                }
                return this.products;

            },

            calculateDiscount(index) {

                let i = 0;
                while(i < this.products[index].badges.length) {

                    if(this.products[index].badges[i].type.includes("discount")) {
                        let discount = this.products[index].badges[i].value;
                        discount = Math.abs(parseInt(discount));
                        let sale = (this.products[index].price - (discount / 100) * this.products[index].price).toFixed(2);
                        this.priceOnSale.push(sale);
                    } else {
                        if (this.products[index].badges.length === 1) {
                            this.priceOnSale.push(this.products[index].price);
                        }
                    }

                    i++;

                }
                
                return this.priceOnSale[index];


            },

            displayDiscount(index) {

                let i = 0;
                while(i < this.products[index].badges.length) {

                    if(this.products[index].badges[i].type.includes("discount")) {
                        this.discountArray.push(this.products[index].badges[i].value);
                    } else {
                        if (this.products[index].badges.length === 1) {
                            this.discountArray.push(0);
                        }
                    }

                    i++;

                }
                
                return this.discountArray[index];

            },

            displayTag(index) {

                let tagArray = [];

                for(let i = 0; i < 6; i++) {

                    if(this.products[i].badges[0].type.includes("tag")) {
                        tagArray.push(this.products[i].badges[0].value)
                    } else {
                        tagArray.push('');
                    }

                    console.log(tagArray[index]);

                }

                return tagArray[index];

            },

        }
        
    }
</script>

<template>

    <div class="list container text-center px-0 my-5">

        <div class="row gy-5">
            <div 
                class="col-4"
                v-for="(card, index) in products"
                :key="index"
            >

                <Product
                    :image="`/img/${card.frontImage}`"
                    :brandName="card.brand"
                    :productName="card.name"
                    :priceOnSale="calculateDiscount(index)"
                    :price="card.price"
                    :discount="displayDiscount(index)"
                    :isGreen="displayTag(index)"
                />

            </div>
        </div>

    </div>
    
</template>

<style scoped lang="scss">

@import '../assets/styles/main.scss';

</style>