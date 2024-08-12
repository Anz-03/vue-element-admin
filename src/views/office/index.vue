<template>
  <div>
    <input type="file" @change="handleFileUpload">
    <div v-if="documentUrl">
      <iframe :src="documentUrl" width="100%" height="600px" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      documentUrl: null
    }
  },
  methods: {
    handleFileUpload(event) {
      const file = event.target.files[0]
      if (file) {
        const reader = new FileReader()
        reader.onload = (e) => {
          // Convert file to a data URL
          this.documentUrl = `https://view.officeapps.live.com/op/embed.aspx?src=${encodeURIComponent(e.target.result)}`
        }
        reader.readAsDataURL(file)
      }
    }
  }
}
</script>

<style scoped>
iframe {
  border: none;
}
</style>

