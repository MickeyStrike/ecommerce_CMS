<template>
<div class="container">
  <div class="box mt-5 ml-5">
  <h1>Add Product Form</h1>
    <form>
      <div class="form-row">
        <label class="ml-3 mb-4">Name Product</label>
        <div class="form-group text-align-center col-md-12">
          <input type="text" class="form-control" placeholder="Input Name Product ..." v-model="name">
        </div>
      </div>
      <div class="form-row">
        <label class="ml-3 mb-4">Image-Url</label>
        <div class="form-group text-align-center col-md-12">
          <input type="text" class="form-control" placeholder="Input Image Url ..." v-model="image">
        </div>
      </div>
      <div class="form-row">
        <label class="ml-3 mb-4">Price</label>
        <div class="form-group text-align-center col-md-12">
          <input type="text" class="form-control" placeholder="Input Price ..." v-model="price">
        </div>
      </div>
      <div class="form-row">
        <label class="ml-3 mb-4">Stock</label>
        <div class="form-group text-align-center col-md-12">
          <input type="text" class="form-control" placeholder="Input Stock ..." v-model="stock">
        </div>
      </div>
      <button type="submit" class="btn btn-primary" @click.prevent="addProduct">Add Product</button>
    </form>
  </div>
</div>
</template>

<script>
export default {
  data () {
    return {
      name: '',
      image: '',
      price: '',
      stock: ''
    }
  },
  methods: {
    addProduct () {
      const name = this.name
      const image = this.image
      const price = this.price
      const stock = this.stock
      this.$store.dispatch('addProduct', {
        name,
        image,
        price,
        stock
      })
        .then((result) => {
          this.$notify({
            group: 'foo',
            title: 'Hello',
            text: 'Success Add Product'
          })
          this.$router.push('/product')
        }).catch((err) => {
          this.$notify({
            group: 'foo',
            title: 'Hello',
            text: err.response.data.message,
            type: 'error'
          })
        })
        .finally(() => {
          this.$store.commit('SET_ISLOADING', false)
        })
    }
  }
}
</script>

<style scoped>
  .box {
    width: 80%;
  }
  .form-control {
    border-top: white;
    border-right: white;
    border-left: white;
  }
  .form-control:focus {
    outline: none;
    border: none;
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 3px 0px rgba(255, 0, 0, 0.322);
  }
</style>
