<template>
    <v-container>
        <v-row justify="center">
            <v-col cols="12" md="6">
                <div id="reader" style="width: 100; max-width: 500px; margin: auto;"></div>
            </v-col>
        </v-row>
    </v-container>
</template>

<script setup>
import { onMounted } from 'vue'
import { Html5QrcodeScanner } from 'html5-qrcode'

const onScanSuccess = ( decodedtext, decodeResult) => {
    console.log('✅ QR code', decodedtext)

}
const onScanFailer = error =>{
    console.warn('scan error', error)
}

onMounted(()=>{
    const Scanner = new Html5QrcodeScanner (
        'reader',
        { fps: 10, qrbox: { width: 250, heigth: 250}},
        false
    )
    Scanner.render(onScanSuccess, onScanFailer)
})
</script>