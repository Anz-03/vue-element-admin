<template>
  <div class="office-editor">
    <iframe
      v-if="fileUrl"
      :src="fileUrl"
      width="100%"
      height="100%"
      frameborder="0"
      allowfullscreen
    />
    <div v-else>
      <p>No file selected</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'OfficeEditor',
  data() {
    return {
      fileUrl: null // URL of the document to edit
    }
  },
  mounted() {
    // Example URL, replace with dynamic URL or logic as needed
    this.fileUrl = this.getOfficeFileUrl('example-document-url')
  },
  methods: {
    getOfficeFileUrl(documentId) {
      // Replace with your Office Online URL and parameters
      return `https://view.officeapps.live.com/op/view.aspx?src=${encodeURIComponent(documentId)}`
    }
  }
}
</script>

<style scoped>
.office-editor {
  position: relative;
  width: 100%;
  height: 100%;
}

iframe {
  width: 100%;
  height: 100%;
}
</style>
