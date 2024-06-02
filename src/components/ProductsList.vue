<script>
    import Product from './ProductComponent.vue'
    export default {
        name: 'Products List',
        components: {
            Product,
        },
        data() {

            return {

                image: this.fillArrayImg(),
                discount: [50, 30, 30, 50, 0, 0],
                isGreen: [true, false, false, true, false, true],
                brandName: ["Levi's", "Guess", "Come Zucchero Filato", "Levi's", "Maya Deluxe", "Esprit"],
                productName: ["Relaxed fit tee unisex", "Roses tee", "Voglia di colori pastello", "Tee unisex", "Stripe bodice", "Maglione - Black"],
                price: [29.99, 29.99, 184.99, 29.99, 99.99, 29.99],
                priceOnSale: [],

            };

        },

        methods: {

            fillArrayImg() {

                let img = []

                for(let i = 0; i < 6; i++) {
                    img[i] = `/img/${i + 1}.webp`;
                }
                return img;

            },

            groupCard() {

                let cardsList = [];

                for(let i = 0; i < 6; i++) {

                    let card = {
                        image: "",
                        discount: 0,
                        isGreen: false,
                        brandName: "",
                        productName: "",
                        price: 0,
                        priceOnSale: 0,

                    };
                    card.image = this.image[i];
                    card.discount = this.discount[i];
                    card.isGreen = this.isGreen[i];
                    card.brandName = this.brandName[i];
                    card.productName = this.productName[i].toUpperCase();
                    card.price = this.price[i];
                    if(this.discount[i] > 0) {
                        card.priceOnSale = (this.price[i] - ( (this.discount[i]) / 100) * this.price[i]).toFixed(2);
                    } else {
                        card.priceOnSale = this.price[i];
                    }
                    cardsList.push(card);

                };

                return cardsList;

            },

        }
    }
</script>

<template>

    <div class="list container text-center px-0 my-5">

        <div class="row">
            <div 
                class="col-4"
                v-for="(card, index) in groupCard()"
                :key="index"
                v-show="index >= 0 && index < 3"
            >

                <Product
                    :image="card.image"
                    :discount="card.discount"
                    :isGreen="card.isGreen"
                    :brandName="card.brandName"
                    :productName="card.productName"
                    :price="card.price"
                    :priceOnSale="card.priceOnSale"
                />

            </div>
        </div>
        <div class="row mt-5">
            <div
                class="col-4"
                v-for="(card, index) in groupCard()"
                :key="index"
                v-show="index >= 3 && index < 6"
            >

                <Product
                    :image="card.image"
                    :discount="card.discount"
                    :isGreen="card.isGreen"
                    :brandName="card.brandName"
                    :productName="card.productName"
                    :price="card.price"
                    :priceOnSale="card.priceOnSale"
                />
                
            </div>
        </div>

    </div>
    
</template>

<style scoped lang="scss">

@import '../assets/styles/main.scss';

</style>