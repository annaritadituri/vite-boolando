<script>
    export default {
        name: 'Product',
        props: ['image', 'discount', 'isGreen', 'brandName', 'productName', 'price', 'priceOnSale'],
    }
</script>

<template>

    <div class="product">

        <img :src="image" alt="img">

        <div class="on-image">

            <span
                class="discount-percent p-1 px-2 me-1"
                v-show="discount !== 0"
            >
                {{ discount }}
            </span>
            <span
                class="label p-1 px-2"
                v-show="isGreen !== ''"
            >
                {{ isGreen }}
            </span>

        </div>

        <p class="brand-name m-0 mt-1">{{ brandName }}</p>
        <p class="product-name m-0 fw-bold">{{ productName }}</p>
        <span class="sale">&euro;{{ priceOnSale }}</span>
        <span class="price">&euro;{{ price }}</span>

    </div>
   
</template>

<style scoped lang="scss">

@import '../assets/styles/main.scss';

.product {
    text-align: start;
    position: relative;

    img {
        width: 100%
    }

    .on-image {
        position: absolute;
        bottom: 100px;

        span {
            font-size: 0.7rem;
            font-weight: 600;
            color: $white;
        };

        .discount-percent {
            background-color: $bg_discount;
        }

        .label {
            background-color: $bg_label;
        }
    }

    .brand-name {
        color: gray;
        font-size: 0.8rem;
    }

    >span {
        font-size: 0.8rem;

        &.sale {
            color: $bg_discount;
            font-weight: 600;
        }

        &.price {
            text-decoration: line-through;
            color: gray;
            margin-left: 0.2rem;
        }
    }

}

</style>