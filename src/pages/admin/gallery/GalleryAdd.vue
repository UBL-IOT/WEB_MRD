<template>
  <q-page>
    <q-card class="q-pa-md q-ma-md">
      <q-breadcrumbs>
        <q-breadcrumbs-el
          class="text-indigo-10"
          label="Gallery"
          icon="extension"
        />
        <q-breadcrumbs-el
          class="text-grey-7"
          label="Add Gallery"
          icon="library_add"
        />
      </q-breadcrumbs>
    </q-card>

    <div class="q-pa-md">
      <div class="row q-gutter-md">
        <div class="col">
          <q-card class="my-card">
            <q-card-section>
              <div class="text-h6 text-indigo-10">Form Data</div>
              <div class="text-caption text-grey">Digunakan untuk melakukan pengisian data kegiatan.</div>
            </q-card-section>
          </q-card>

          <q-card class="my-card q-mt-md">
            <q-form @submit="onSubmit">
              <q-card-section horizontal>
                <q-card-section class="q-gutter-md fit">
                  <q-badge class="q-pa-sm" color="primary">Upload Photo</q-badge>
                  <q-input type="file" class="q-mr-xs" v-model="thumbnail" dense borderless @change="onFileChange" />
                  <div id="preview">
                    <q-img v-if="url" :src="url" style="border-radius: 10px;" />
                  </div>
                </q-card-section>
                <q-separator vertical />
                <q-card-section class="q-gutter-md fit">
                  <q-input
                    dense
                    outlined
                    label="Judul Kegiatan"
                  />
                  <q-input
                    dense
                    outlined
                    type="textarea"
                    label="Deskripsi Kegiatan"
                  />
                </q-card-section>
              </q-card-section>

              <q-separator />

              <q-card-actions>
                <q-btn flat color="blue-10" type="submit">Simpan Data</q-btn>
              </q-card-actions>
            </q-form>
          </q-card>
        </div>
        <div class="col-4">
          <div class="row">
            <div class="col">
              <div class="text-subtitle2 text-indigo-10">Informasi Pengguna Layanan</div>
              <div class="text-caption text-grey">Masukan data foto kegiatan serta nama kegiatan dan juga deskripsi kegiatan.</div>
            </div>
            <div class="col-4">
              <lottie style='width: 80px; margin-left: 10px; margin-top: -0px;' :options="defaultOptions"/>
            </div>
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
import Lottie from './../../../components/lottie.vue'
import * as animationData from './../../../../public/gallery.json'

export default {
  name: 'PageIndex',
  components: {
    lottie: Lottie
  },
  data () {
    return {
      defaultOptions: { animationData: animationData.default },
      animationSpeed: 2,
      thumbnail: null,
      url: null
    }
  },
  methods: {
    onFileChange(e) {
      const file = e.target.files[0];
      this.url = URL.createObjectURL(file);
      console.log(file)
    }
  }
}
</script>
<style scoped>
#preview {
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}

#preview img {
  margin-top: -10px;
  max-width: 100%;
  max-height: 500px;
}
</style>
