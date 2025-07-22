<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="12" md="6" class="text-center">
        <!-- Scan Button -->
        <v-btn color="primary" @click="startScanner" class="mb-4">
          Scan QR Code
        </v-btn>

        <!-- QR Code Reader Target -->
        <div id="reader" style="width: 100%; max-width: 500px; margin: auto;"></div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref } from 'vue'
import { Html5QrcodeScanner } from 'html5-qrcode'

const scannerStarted = ref(false)

const isValidUrl = (text) => {
  try {
    new URL(text)
    return true
  } catch (_) {
    return false
  }
}

const onScanSuccess = (decodedText, decodedResult) => {
  console.log('✅ QR code:', decodedText)

  // Stop scanner
  const readerElement = document.getElementById('reader')
  if (readerElement) readerElement.innerHTML = ''
  scannerStarted.value = false

  // Redirect if it's a valid URL
  if (isValidUrl(decodedText)) {
    window.location.href = decodedText
  } else {
    alert(`Scanned QR (not a URL): ${decodedText}`)
  }
}

const onScanFailure = error => {
  console.warn('⚠️ Scan error:', error)
}

const startScanner = () => {
  if (scannerStarted.value) return

  const scanner = new Html5QrcodeScanner(
    'reader',
    { fps: 10, qrbox: { width: 250, height: 250 } },
    false
  )

  scanner.render(onScanSuccess, onScanFailure)
  scannerStarted.value = true
}
</script>