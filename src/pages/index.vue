<template>
    <v-snackbar v-model="snackbar" color="success">
        <span>Cartaz baixado com sucesso</span>
        <template v-slot:actions>
            <v-btn
                variant="text"
                icon="mdi-close"
                @click="snackbar = false"
            />
        </template>
    </v-snackbar>
    <div class="text-center">
        <div>
            <v-toolbar class="bg-background mt-lg-0" border height="50">
                <v-toolbar-title class="text-center text-h5 font-weight-bold">Printfy</v-toolbar-title>
            </v-toolbar>
            <div class="d-flex flex-column-reverse flex-lg-row bg-background" style="height: 94vh;">
                <div class="w-lg-25 pa-2 h-75 h-lg-100 overflow-auto">
                    <h3 class="ma-2">Criaçao de Cartaz</h3>
                    <v-text-field variant="outlined" label="Cabeçalho" :rules="headerRules"  v-model="headerText"/>
                    <v-text-field variant="outlined" label="Descrição do produto" v-model="productDescription"/>
                    <v-text-field variant="outlined" label="Preço DE" v-model="productPriceFrom" v-mask-decimal.br="2"></v-text-field>
                    <v-text-field variant="outlined" label="Preço POR" v-model="productPriceTo" v-mask-decimal.br="2"></v-text-field>
                    <v-text-field variant="outlined" label="Quantidade" v-model="quantity"/>
                    <v-text-field variant="outlined" label="Validade da promoção" v-model="promoValid"/>
                    <div class="w-100 d-flex flex-column align-center justify-center">
                        <v-switch hide-details label="Exibir Cabecalho" color="success" v-model="showHeader"></v-switch>
                        <v-btn elevation="0" :loading="loading" color="success" class="rounded-lg w-50 mb-10" @click="imprimirPDF">
                            <v-icon icon="mdi-tray-arrow-down"/>
                            Baixar PDF
                        </v-btn>
                    </div>
                    <v-sheet v-if="width <= 1260 " height="150"/>
                </div>
                <div class="w-lg-75 overflow-auto h-50 h-lg-100">
                    <div class="d-flex justify-center h-100 mt-2" :style="{transform: width <= 1260 ? 'scale(.06)' :  'scale(.2)', transformOrigin: 'top'}">
                        <Poster
                            :showHeader="showHeader"
                            :headerText="headerText"
                            :productDescription="productDescription"
                            :productPriceFrom="productPriceFrom"
                            :productPriceTo="productPriceTo"
                            :promo-valid="promoValid"
                            :quantity="quantity"
                        />
                    </div>
                </div>
            </div>   
        </div>
    </div>
</template>
<script setup lang="ts">
import  { ref } from 'vue'
import { useWindowSize } from '@vueuse/core'
//@ts-ignore
import html2pdf from 'html2pdf.js'

const { width } = useWindowSize()
const headerText = ref<string>('ofertas')
const productDescription = ref<string>('')
const promoValid = ref<string>('')
const quantity = ref<string>('und')
const productPriceFrom = ref<string>('0,00') 
const productPriceTo = ref<string>('0,00')
const showHeader = ref<boolean>(true)
const loading = ref<boolean>(false)
const snackbar = ref(false)

const headerRules = [
    (value: any) => (value && value.length <= 17) || 'O cabeçalho suporta no maximo 16 caracteres.'
]

const imprimirPDF = () => {
    loading.value = true
    const element = document.getElementById('poster-dowload')
    const opt = {
        margin: 0,
        filename: `${productDescription.value}.pdf`,
        image: { type: 'jpeg', quality: 1 },
        html2canvas: { scale: 1 },
        jsPDF: { unit: 'px', format: [2480, 3508], orientation: 'portrait' }
    }
    if(element) {
        setTimeout(() => {
            //@ts-ignore
            html2pdf().from(element).set(opt).save()
            loading.value = false
            snackbar.value = true
        }, 1000)
    }
}
</script>


<style scoped lang="css">
:deep(.v-field) {
  border-radius: 14px;
  margin: 4px;
}
</style>