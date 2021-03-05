<template>
  <div class="q-px-lg q-pb-md">
    <q-timeline color="secondary">
      <q-timeline-entry heading tag="h5" class="text-bold">
        {{ title }}
      </q-timeline-entry>

      <q-timeline-entry
        v-for="item in workExperience"
        :key="item.companyName"
        :title="item.companyName"
        :subtitle="item.duringDate"
        
        icon=""
      >
        <div>
            <p>{{responsibilitiesTitle}}</p>

            <q-list>
                <q-item
                    v-for="responsibility in item.responsibilities"
                    :key="responsibility.id"
                    class="text-h6" >
                    ★ {{ responsibility.describe}}
                    <!-- <q-chip class="text-h6">
                        <q-avatar
                            icon="bookmark"
                            color="#979797"
                            text-color="grey-6" />
                        {{ responsibility.describe}}
                    </q-chip> -->
                </q-item>
            </q-list>
        </div>
      </q-timeline-entry>
    </q-timeline>
  </div>
</template>

<script>
export default {
    name: "i-work-experience",
    props: {
        workExperience: {
            type: Array,
            required: true
        },
        title: {
            type: String,
            default: "工作經驗 Work experience"
        },
        responsibilitiesTitle: {
            type: String,
            default: "職務內容："
        }
    }
}
</script>
