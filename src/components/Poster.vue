<template>
    <div>
        <div 
            id="poster-dowload"
            :style="{
                width: '2480px', 
                height: '3508px', 
                backgroundColor: 'yellow' 
            }"
            
        >
            <div class="d-flex justify-center align-center container-header h-25" :class="{'mb-16': !productDescription}">
                <svg v-if="showHeader" viewBox="0 0 500 180" class="svg1">
                    <path d="M0,0 L500,0 L500,120 L250,180 L0,120 Z" fill="red"/>
                </svg>
                <h1 id="header-text" class="text-center header-text" :style="{color: showHeader ? 'white' : 'red'}">
                    {{ headerText }}
                </h1>
            </div>
            <div class="d-flex flex-column align-center">
                <div v-if="productDescription" id="description" class="text-center descrption-text">{{ productDescription }}</div>
                <div class="container-price">
                    <div class="price-from-text">
                        <div>
                            <div v-if="showPriceFrom">
                                DE: 
                                <span class="text-decoration-line-through">
                                    R${{ productPriceFrom.replace('.', ',') }}
                                </span>
                            </div>
                            <span class="desc-text">POR APENAS:</span>
                        </div>
                        <div>
                            <div v-if="showPriceFrom" class="percentage-poster">
                                <svg viewBox="0 0 735.02 736.34">
                                    <path d="M388.53,721.06c3.58-4.39,8.66-7.11,14.28-7.68l.19-.03c.34-.02.67-.06,1-.1,5.96-.61,11.9,1.31,16.35,5.3,3.76,3.37,6.16,7.96,6.83,12.94,11.09-1.81,22.03-4.09,32.76-6.86-1.51-5.21-1-10.71,1.49-15.56,2.58-5.03,6.96-8.76,12.36-10.49.37-.13.75-.24,1.13-.36,2.13-.7,4.34-1.05,6.55-1.05,8.98,0,16.91,5.62,19.92,14.05,10.44-4.08,20.65-8.63,30.6-13.61-2.57-4.78-3.22-10.25-1.79-15.51,1.47-5.47,4.98-10.03,9.89-12.84.34-.2.69-.4,1.03-.59,3.21-1.87,6.88-2.87,10.59-2.87,7.33,0,14.16,3.84,18,10.04,9.34-6.15,18.38-12.71,27.1-19.66-3.5-4.14-5.28-9.37-4.98-14.81.31-5.64,2.8-10.83,7.03-14.6l.32-.3c.19-.18.37-.34.56-.5,3.9-3.51,8.93-5.46,14.17-5.46,5.78,0,11.32,2.4,15.31,6.56,7.85-7.94,15.36-16.22,22.47-24.84-4.29-3.34-7.11-8.09-7.94-13.47-.87-5.59.5-11.19,3.84-15.75l.71-.97c3.97-5.46,10.38-8.72,17.14-8.72,4.29,0,8.39,1.3,11.93,3.72,6.03-9.37,11.63-19.05,16.81-28.98-10.24-4.98-14.77-17.26-10.06-27.72l.49-1.08c3.4-7.64,11-12.57,19.36-12.57,2.76,0,5.45.56,8.01,1.61,3.93-10.4,7.41-21.02,10.4-31.84-5.26-1.3-9.77-4.48-12.72-9.06-3.08-4.75-4.11-10.42-2.93-15.95l.25-1.16c1.01-4.79,3.66-9.1,7.48-12.15,4.75-3.8,11.04-5.38,17.03-4.29,1.66-10.95,2.82-22.06,3.49-33.31-5.42-.17-10.49-2.35-14.33-6.22-3.99-4.01-6.18-9.33-6.15-14.99v-1.97c-.01-5.67,2.18-10.99,6.17-15,3.85-3.85,8.92-6.03,14.34-6.2-.66-11.24-1.81-22.35-3.46-33.3-1.25.22-2.52.36-3.77.36-4.79,0-9.48-1.67-13.24-4.67-3.8-3.06-6.45-7.38-7.46-12.16-.08-.39-.16-.77-.24-1.16-.31-1.46-.47-2.94-.47-4.41-.01-4.77,1.63-9.48,4.63-13.24,2.91-3.65,6.97-6.21,11.5-7.33-2.98-10.83-6.44-21.45-10.36-31.85-2.55,1.05-5.23,1.6-7.99,1.6-8.37,0-15.97-4.95-19.37-12.58l-.49-1.08c-1.22-2.74-1.84-5.63-1.86-8.6-.02-8.15,4.66-15.58,11.96-19.12-5.16-9.93-10.74-19.6-16.75-28.97-3.54,2.41-7.63,3.7-11.91,3.7-6.78,0-13.19-3.26-17.16-8.75-.24-.32-.47-.64-.71-.96-2.67-3.65-4.07-7.96-4.07-12.46-.01-6.55,3.05-12.76,8.2-16.76-7.1-8.63-14.59-16.92-22.43-24.86-3.99,4.15-9.51,6.53-15.28,6.53-5.26,0-10.29-1.94-14.19-5.47l-1.01-.91c-4.4-4-6.92-9.69-6.92-15.65,0-5.02,1.78-9.84,5.02-13.66-8.71-6.96-17.75-13.54-27.08-19.7-3.86,6.18-10.69,10.01-18,10.01-3.71,0-7.39-1-10.62-2.87-.26-.16-.52-.31-.78-.46l-.25-.14c-6.55-3.77-10.61-10.83-10.61-18.39,0-3.48.89-6.91,2.53-9.98-9.94-4.99-20.14-9.55-30.57-13.64-3.02,8.41-10.94,14.02-19.92,14.02-2.23,0-4.45-.35-6.58-1.05l-.26-.09c-.29-.09-.59-.19-.87-.29l-.39-.11h.01c-8.56-2.94-14.29-10.93-14.31-20,0-2.01.3-4,.87-5.95-10.74-2.79-21.67-5.09-32.77-6.91-.68,5-3.08,9.56-6.84,12.93-3.89,3.48-8.9,5.39-14.09,5.39-.75,0-1.51-.04-2.26-.11-.2-.02-.39-.05-.59-.06-.2-.02-.4-.05-.6-.07-5.26-.54-10.09-2.99-13.61-6.91-3.5-3.9-5.43-8.92-5.43-14.14,0-.51.05-1.03.08-1.54-5.55-.25-11.13-.4-16.75-.4s-11.18.15-16.73.39c.82,11.37-7.54,21.43-18.95,22.59-.22.02-.46.05-.69.07l-.51.05c-.73.07-1.49.12-2.24.12-5.2,0-10.2-1.92-14.1-5.41-3.75-3.36-6.16-7.94-6.83-12.93-11.09,1.82-22.03,4.12-32.76,6.91,3.17,10.94-2.9,22.53-13.82,26.06-.3.1-.6.19-.88.29l-.25.09c-2.14.7-4.35,1.05-6.58,1.05-8.99,0-16.9-5.61-19.92-14.03-10.44,4.09-20.63,8.65-30.58,13.64,5.39,10.03,1.86,22.63-8.07,28.36-.35.2-.69.4-1.03.6-3.23,1.88-6.89,2.87-10.6,2.87-7.32,0-14.16-3.82-18-10.01-9.33,6.16-18.36,12.73-27.07,19.69,7.35,8.7,6.52,21.76-2.02,29.42l-.25.24c-.21.19-.42.37-.64.56-3.9,3.53-8.95,5.47-14.19,5.47-5.77,0-11.29-2.4-15.28-6.55-7.85,7.95-15.34,16.24-22.45,24.87,9.01,6.99,10.89,19.95,4.12,29.21-.24.32-.47.65-.7.97-3.97,5.47-10.39,8.73-17.17,8.73-4.28,0-8.37-1.28-11.91-3.7-6.02,9.38-11.6,19.06-16.77,28.99,10.25,4.97,14.79,17.25,10.09,27.71-.16.36-.32.73-.49,1.1-3.4,7.64-11,12.58-19.36,12.58-2.76,0-5.44-.56-8-1.6-3.92,10.4-7.38,21.03-10.36,31.86,11.06,2.71,18.06,13.76,15.67,24.98-.09.39-.16.77-.25,1.17-1.01,4.78-3.65,9.09-7.46,12.15-3.75,3.02-8.46,4.67-13.24,4.67-1.25,0-2.52-.13-3.76-.35-1.65,10.95-2.8,22.05-3.46,33.29,11.38.37,20.53,9.73,20.51,21.2v1.2c.01,11.48-9.15,20.83-20.54,21.17.65,11.24,1.79,22.35,3.43,33.3,5.98-1.05,12.26.52,16.99,4.33,3.8,3.05,6.45,7.38,7.45,12.17.06.26.11.54.17.81l.07.35c.31,1.45.46,2.93.46,4.4.01,4.78-1.63,9.48-4.65,13.24-2.91,3.65-6.99,6.22-11.51,7.32,2.97,10.83,6.41,21.46,10.32,31.86,2.55-1.04,5.23-1.59,7.97-1.59,8.38,0,15.99,4.95,19.37,12.61.16.36.32.72.49,1.08,1.22,2.73,1.84,5.62,1.84,8.6.02,8.15-4.67,15.58-11.97,19.11,5.15,9.93,10.72,19.6,16.72,28.98,3.53-2.4,7.62-3.68,11.9-3.68,6.78,0,13.19,3.28,17.17,8.76.15.2.29.4.42.59l.29.4c2.65,3.65,4.06,7.95,4.06,12.45,0,6.55-3.07,12.76-8.22,16.75,7.09,8.63,14.56,16.93,22.39,24.88,3.99-4.14,9.5-6.51,15.27-6.51,5.26,0,10.3,1.94,14.22,5.48.14.14.29.26.44.4.15.14.29.26.44.4,4.47,4.01,7.03,9.77,7.01,15.77,0,5.01-1.79,9.83-5.03,13.65,8.7,6.97,17.73,13.56,27.06,19.73,3.84-6.17,10.68-9.98,17.98-9.98,3.72,0,7.41.98,10.64,2.88.35.2.69.4,1.03.6l.2.11c6.43,3.81,10.4,10.79,10.39,18.29-.01,3.47-.89,6.91-2.54,9.97,9.94,5,20.13,9.58,30.55,13.68,3.03-8.4,10.94-14.01,19.92-14.01,2.23,0,4.45.36,6.59,1.06.27.1.55.19.82.27l.32.1c8.76,2.84,14.65,10.93,14.65,20.13,0,2.01-.3,4-.87,5.94,10.73,2.8,21.66,5.12,32.76,6.95.69-4.99,3.09-9.56,6.84-12.92,4.46-3.97,10.42-5.89,16.37-5.27.2.02.41.05.62.07l.56.05c5.26.55,10.08,3,13.61,6.94,3.49,3.9,5.41,8.92,5.39,14.14,0,.51-.04,1.03-.08,1.54,5.69.26,11.42.41,17.17.41s10.9-.14,16.31-.38c-.39-5.41,1.25-10.67,4.69-14.9Z" fill="red"/>
                                </svg>
                                <span id="discount" class="discount-poster">
                                    <p>-{{ percentageDifference }}%</p>
                                </span>
                            </div>
                        </div>
                    </div>
                    <div class="price-to-text">
                        <div id="price">
                            <div id="real" class="real">
                                <span class="rcifrao">R$</span>{{ productPriceTo.toString().split(',')[0] }}
                            </div>
                            <div id="cents" class="cents">
                                <span>
                                    ,{{ productPriceTo.toString().split(',')[productPriceTo.toString().split(',').length - 1] }}
                                </span>
                                <span id="quantity" class="quantity">{{ quantity }}</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="valid">
                    {{ promoValid }}
                </div>
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">
import { onMounted, watch, computed } from 'vue';

const props = defineProps<{
    showHeader: boolean
    headerText: string
    productDescription: string
    productPriceFrom: string
    productPriceTo: string
    promoValid: string
    quantity: string
}>()

const adjustFontSize = () => {
    const priceReal = document.getElementById('real')
    const priceCents = document.getElementById('cents')
    const quantity = document.getElementById('quantity')

    const textLength = props.productPriceTo.toString().split(',')[0]?.replace('.','').length

    if(priceReal && priceCents && quantity) {
        switch (textLength) {
            case 1: 
                priceReal.style.fontSize = '106rem'
                priceReal.style.transform = 'scale(1, 1.2) translateY(-6rem)';
                priceCents.style.transform = 'translateY(5rem)'
                priceCents.style.fontSize = '26rem'
                quantity.style.fontSize = '20rem'
                break

            case 2:
                priceReal.style.fontSize = '70rem'
                priceReal.style.transform = 'scale(1, 1.7) translateY(7rem)';
                priceCents.style.transform = 'translateY(7rem)'
                priceCents.style.fontSize = '16rem'
                quantity.style.fontSize = '10rem'
                break

            case 3:
                priceReal.style.fontSize = '50rem'
                priceReal.style.transform = 'scale(1, 2.5) translateY(9rem)';
                priceCents.style.transform = 'translateY(5rem)'
                priceCents.style.fontSize = '16rem'
                quantity.style.fontSize = '10rem'
                break
        }
        
    }
    
}

watch(() => {
    if(props.productPriceTo) return props.productPriceTo
}, () => {
    adjustFontSize()
})

const showPriceFrom = computed(() => {
    const priceFrom = parseFloat(props.productPriceFrom.replace(/\./g, "").replace(",", "."))
    const priceTo = parseFloat(props.productPriceTo.replace(/\./g, "").replace(",", "."))
    if(priceFrom > priceTo) {
        return true
    }
    return false
})

const percentageDifference = computed(() => {
    const priceFrom = parseFloat(props.productPriceFrom.replace(/\./g, "").replace(",", "."))
    const priceTo = parseFloat(props.productPriceTo.replace(/\./g, "").replace(",", "."))
    const difference = Math.abs(priceFrom - priceTo)

    const base = Math.abs(priceFrom)
    const percentageDifference = (difference / base) * 100

    return percentageDifference.toFixed(0)
});


watch(() => {
    if(props.productDescription) return props.productDescription
}, () => {
    const description = document.getElementById('description')
    if(description && props.productDescription.length > 30) {
        description.style.fontSize = '10rem'
    } else if(description) {
        description.style.fontSize = '16rem'
    }
})

watch(() => {
    if(props.headerText) return props.headerText
}, () => {
    const header = document.getElementById('header-text')
    if(header && props.headerText.length > 8 && props.headerText.length < 13) {
        header.style.fontSize = '22rem'
    } else if(header && props.headerText.length >= 13) {
        header.style.fontSize = '18rem'
    } else if(header) {
        header.style.fontSize = '35rem'
    }
})

onMounted(() => {
    adjustFontSize()
    const description = document.getElementById('description')
    if(description && props.productDescription.length > 30) {
        description.style.fontSize = '10rem'
    } else if(description) {
        description.style.fontSize = '16rem'
    }

})
</script>
<style scoped>
.svg1 {
    display: inline-block;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
}

.container-header {
    display: inline-block;
    position: relative;
    bottom: 0;
    left: 0;
    width: 100%;
}

.header-text {
    position: relative;
    top: -70px;
    font-size: 35rem; 
    z-index: 2; 
    font-family: "Archivo Black", sans-serif;
    font-weight: 400;
    font-style: normal;
}

.descrption-text {
    display: flex;
    align-items: center;
    justify-content: center;
    color: black;
    width: 95%;
    overflow: hidden;
    line-height: normal;
    font-family: "Archivo Black", sans-serif;
    font-weight: 400;
    font-style: normal;
}

.container-price {
    width: 90%;
}

.price-from-text {
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: black;
    font-size: 8rem; 
}

.price-from-text div {
    position: relative;
    font-family: "Archivo Black", sans-serif;
    font-weight: 400;
    font-style: normal;
    text-align: left;
}

.desc-text {
    color: black;
    font-size: 10rem; 
    font-family: "Archivo Black", sans-serif;
    font-weight: 400;
    font-style: normal;
}

.price-to-text div {
    display: -webkit-box;
    text-align: center;
    line-height: normal;
}

.rcifrao {
    font-size: 18%; 
    text-align: left;
    font-weight: bold;
    font-family: "Archivo Black", sans-serif;
    font-weight: 400;
    font-style: normal;
}

.percentage-poster {
    position: relative;
    transform: rotate(25deg) scale(1.3);
    width: 400px;
    height: 400px;
}

.discount-poster {
    top: -390px;
    position: relative;
    text-align: center;
    color: yellow;
    font-weight: bold;
    font-size: larger;
}

.to-text {
    text-align: center;
    font-size: .45em;
    line-height: 10px;
}

.price-to-text .real {
    color: red;
    font-family: "Archivo Black", sans-serif;
    font-weight: 400;
    font-style: normal;
}

.price-to-text .cents {
    height: 100%;
    color: red;
    font-family: "Archivo Black", sans-serif;
    font-weight: 400;
    font-style: normal;
    display: grid !important;
    justify-content: space-between;
    align-items: center;
}

.price-to-text .quantity {
    font-size: 10rem;
    font-family: "Archivo Black", sans-serif;
    font-weight: 400;
    font-style: normal;
    color: black;
}

.valid {
    font-size: 8rem;
    font-weight: bold;
    position: relative;
    bottom: 0px;
}
</style>