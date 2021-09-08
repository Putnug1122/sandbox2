<template>
  <div class="input-group">
    <input
      v-model="val"
      type="text"
      :placeholder="name"
      class=" form-control rounded-pill m-3"
      @keyup.enter="add"
    />
    <div class="input-group-append">
      <button
        class="btn btn-outline-primary rounded-pill m-3"
        @click="peringatan(val, name)"
      >
        <i class="fas fa-plus" />
      </button>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    name: {
      type: String,
      default: "inputText"
    },
    val: {
      type: String,
      default: "input Text"
    }
  },
  methods: {
    add() {
      if (this.val != "") {
        this.$emit("ValueInput", this.val);
        this.val = "";
      }
    },
    peringatan(value, name) {
      swal({
        title: "Apa Kamu Yakin?",
        text: "Kamu menambah " + value + " Sebagai " + name + " Baru",
        icon: "warning",
        buttons: true,
        dangerMode: true
      }).then(willAdd => {
        if (willAdd) {
          this.add();
        }
      });
    }
  }
};
</script>
