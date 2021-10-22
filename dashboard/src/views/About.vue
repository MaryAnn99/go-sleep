<template>
  <div>
    <ImageBarcodeReader
      @decode="onDecode"
      @error="onError"
    ></ImageBarcodeReader>
    <hr>
    <div>
      <button type="button" class="btn btn-primary" v-on:click="postBarcode">Submit</button>
    </div>
  </div>
  
</template>


<script>
  import Vue from "vue";
  import axios from "axios";
  import { ImageBarcodeReader } from "vue-barcode-reader";

  export default Vue.extend({
  name: "Scanner",
  props: {
    msg: String,
  },
  components: {
    ImageBarcodeReader,
  },
  data(){
    return{
      model: {
        name: 'Daniel',
        barcode: null
      },

    }
  },
  methods: {
    onDecode (result) {
      console.log(result)
      this.model.barcode = result;
    },
    onError (result) {
      console.log(result)
    },
    postBarcode(){
      console.log('hola');
      axios.post("https://", this.model)
        .then(response => this.articleId = response.data.id);
    }

  }
  });
</script>