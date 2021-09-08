<template>
  <div>
    <h1 class="text-center">SANDBOX FRONTEND 1</h1>
    <div class="row">
      <div class="col-4">
        <task-addReader
          @ValueInput="val => this.books.push(val)"
          name="Judul Buku"
          :val="inputBook"
        />
        <ul class="list-group m-3">
          <li
            v-for="(book, i) in books"
            :key="i"
            class="list-group-item d-flex justify-content-between align-items-center rounded-pill mt-2"
          >
            {{ book }}
            <button
              type="buton"
              class="btn btn-outline-danger rounded-pill"
              @click="peringatan('book', book, i)"
            >
              <i class="fas fa-minus" />
            </button>
          </li>
        </ul>
      </div>
      <div class="col-4">
        <task-addReader
          @ValueInput="val => this.Names.push(val)"
          name="Nama Pembaca"
          :val="inputNama"
        />
        <ul class="list-group m-3">
          <li
            v-for="(nama, i) in Names"
            :key="i"
            class="list-group-item d-flex justify-content-between align-items-center rounded-pill mt-2"
          >
            {{ nama }}
            <button
              type="buton"
              class="btn btn-outline-danger rounded-pill"
              @click="peringatan('name', nama, i)"
            >
              <i class="fas fa-minus" />
            </button>
          </li>
        </ul>
      </div>

      <div class="col-4">
        <task-selection
          :valbook="books"
          :valname="Names"
          namebook="Book Name"
          namePembaca="Reader Name"
          @valueData="
            (valbook, valname) => this.dataPembaca.push([valbook, valname])
          "
        />

        <ul class="list-group m-3">
          <li
            v-for="(secbook, i) in dataPembaca"
            :key="i"
            class="list-group-item d-flex justify-content-between align-items-center rounded-pill mt-2"
          >
            {{ secbook[0] }}
            <button
              type="buton"
              class="btn btn-outline-danger rounded-pill"
              @click="peringatan('pembaca', secbook[0], i)"
            >
              <i class="fas fa-minus" />
            </button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      books: [],
      Names: [],
      inputNama: "",
      inputBook: "",
      dataPembaca: []
    };
  },
  methods: {
    setValue(val) {
      this.books.push(val);
    },
    removeBooks(index) {
      this.books = this.books.filter((book, i) => i !== index);
    },
    removeNames(index) {
      this.Names = this.Names.filter((nama, i) => i !== index);
    },
    removeData(index) {
      this.dataPembaca = this.dataPembaca.filter((secbook, i) => i !== index);
    },

    peringatan(hapus, data, i) {
      swal({
        title: "Apakah Kamu Yakin",
        text: "Hapus " + data,
        icon: "warning",
        buttons: true,
        dangerMode: true
      }).then(willDelete => {
        if (hapus == "book") {
          this.removeBooks(i);
        } else if (hapus == "name") {
          this.removeNames(i);
        } else {
          this.removeData(i);
        }
      });
    }
  }
};
</script>
