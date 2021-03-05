<template>
  <div class="q-pa-md q-gutter-sm user-avatar">
    <q-item>
      <q-item-section side>
        <q-avatar size="112px">
          <img :src="imgSrc" />
        </q-avatar>
      </q-item-section>
      <q-item-section>
        <q-item-label class="text-left text-h5">{{ userName }}</q-item-label>
        <a :href="`mailto:${mail}`" class="text-left caption">{{ mail }} </a>
        <q-item-label class="text-left caption">{{ phoneNumber }}</q-item-label>
      </q-item-section>
    </q-item>
  </div>
</template>

<script>
export default {
  name: "user-avatar",
  props: {
    imgSrc: {
      type: String,
      required: true
    },
    userName: {
      type: String,
      required: true
    },
    mail: {
      type: String,
      required: true
    },
    phoneNumber: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.user-avatar {
  display: inline-block;
}

.caption {
  color: #777777;
}
</style>
