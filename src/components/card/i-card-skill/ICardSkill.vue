<template>
    <q-card
        :class="cardClass"
        flat >
        <q-separator style="width:95%"/>
        <q-card-section>
            <div class="text-h6">
                <!-- <q-icon name="storage" style="font-size: 1.5rem;" /> -->
                {{ skill.skillType }}
            </div>
        </q-card-section>

        <q-card-section
            v-for="detail in skill.details"
            :key="detail.name">
            {{ detail.name }}
        </q-card-section>
    </q-card>
</template>

<script>
export default {
    props: {
        cardClass: {
            type: String,
            default: "col-3"
        },
        skill: {
            type: Object,
            required: true,
            default: {
                skillType: "Language",
                details: [{
                    name: "Vue.js"
                },
                {
                    name: "Quasar"
                }]
            }
        }
    }
}
</script>

<style scoped>
.q-separator {
    height: 5px !important;
    background-color: '#979797';
}
</style>
