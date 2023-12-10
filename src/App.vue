<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <form @submit.prevent="submitForm">
        <div class="col-6">
          <label class="form-label" for="name">სახელი, გვარი</label>
          <input type="text" class="form-control" placeholder="სახელი, გვარი" v-model="formData.name" required><br>

          <label class="form-label" for="position">თანამდებობა</label>
          <input type="text" class="form-control" v-model="formData.position" required><br>

          <label class="form-label" for="mobile">საკონტაქტო ნომერი</label>
          <input type="text" class="form-control" v-model="formData.mobile" required><br>

          <label class="form-label" for="email">ელ.ფოსტა</label>
          <input type="email" class="form-control" v-model="formData.email" required><br>

          <label class="form-label" for="activity">საქმიანობის სფერო</label>
          <input type="text" class="form-control" v-model="formData.activity" required><br>

          <label class="form-label" for="recomendation">რეკომენდაცია</label>
          <input type="text" class="form-control" v-model="formData.recomendation" required><br>

          <label class="form-label" for="comment">კომენტარი</label>
          <textarea class="form-control" v-model="formData.comment" required></textarea><br>
        </div>

        <div class="card col-6 p-4" v-for="(detail, index) in dynamicFields" :key="index">
          <label class="form-label" for="company_name">კომპანიის დასახელება</label>
          <input type="text" class="form-control" v-model="detail.company_name"><br>

          <label class="form-label" for="activity_name">საქმიანობის სფერი</label>
          <input type="text" class="form-control" v-model="detail.activity_name"><br>

          <label class="form-label" for="country">ქვეყანა</label>
          <input type="text" class="form-control" v-model="detail.country"><br>

          <button class="btn btn-default" @click="removeField(index)">Remove</button>

        </div>

        <button class="btn btn-default" @click.prevent="addField">Add Detail</button>

      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        name: '',
        position: '',
        mobile: '',
        email: '',
        activity: '',
        recomendation: '',
        comment: ''
      },

      dynamicFields: [] // Array to hold dynamic fields
    };
  },

  methods: {
    submitForm() {
      const allData = {
        ...this.formData,
        dynamicFields: this.dynamicFields
      };

      console.log('All Data:', allData);
      this.resetForm();
    },

    addField() {
      this.dynamicFields.push({
        detail_id: '',
        company_name: '',
        activity_name: '',
        country: '',
      });
    },
    
    removeField(index) {
      this.dynamicFields.splice(index, 1);
    },

    resetForm() {
      this.formData = {
        exhibition_id: '',
        product_info_id: '',
        name: '',
        position: '',
        mobile: '',
        email: '',
        activity: '',
        recomendation: '',
        comment: ''
      };

      this.dynamicFields = [];
    }
  },

  mounted() {
    this.addField()
  }
};
</script>

<style scoped>
  body {
    background-color: #f7f7f7;
  }
</style>