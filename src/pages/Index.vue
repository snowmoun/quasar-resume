<template>
  <div style="width:100%;text-align:center">
    <div style="display:inline-block;width:100%">
      <i-user-avatar
        imgSrc="statics/icons/head-shot.jpg"
        :userName="userName"
        mail="your-mail-address@gmail.com"
        phoneNumber="09xx-xxxxxx"
      />

      <q-space style="display:inline-block;" />

      <q-btn v-if="$q.screen.gt.xs" dense flat class="q-mr-sm float-right">
        <div class="row items-center no-wrap">
          <q-avatar>
            <img :src="currentLanguage.img" />
          </q-avatar>
          <q-icon
            name="arrow_drop_down"
            size="16px"
            style="margin-left: -2px"
          />
        </div>
        <q-menu auto-close>
          <q-list dense style="min-width: 100px">
            <q-item
              v-for="curLang in languages"
              :key="curLang.value"
              clickable
              @click="lang = curLang.value"
            >
              <q-item-section top avatar>
                <q-avatar>
                  <img :src="curLang.img" />
                </q-avatar>
              </q-item-section>
              <q-item-section>{{ curLang.label }}</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </q-btn>
    </div>

    <q-card
      :class="getClass()"
      style="background: radial-gradient(circle, #EEEEEE 0%, #CCCCCC 100%);"
    >
      <!-- <q-card-section>
            <div class="text-h6">Our Changing Planet</div>
        </q-card-section> -->

      <q-card-section
        v-for="(item, index) in paragraphs"
        :key="index"
        class="text-left text-paragraph"
      >
        {{ paragraphs[index] }}
      </q-card-section>
    </q-card>

    <div class="row justify-start">
      <h5 class="text-bold" style="margin-left:10px">{{ skills }}</h5>
    </div>
    <div class="row justify-center">
      <i-card-skill :skill="FrontEndSKill" />
      <q-separator color="white" />
      <i-card-skill :skill="BackEndSkill" />
      <q-separator color="white" />
      <i-card-skill :skill="DatabaseSkill" />
    </div>

    <div class="row justify-start">
      <i-card-skill :skill="AppSkill" />
      <q-separator color="white" />
      <i-card-skill :skill="CISkill" />
      <q-separator color="white" />
      <i-card-skill :skill="VCSSkill" />
      <q-separator color="white" />
      <i-card-skill :skill="OtherSkill" />
    </div>

    <i-work-experience
      :title="workExperienceTitle"
      :workExperience="workExperience"
      :responsibilitiesTitle="responsibilitiesTitle"
      style="text-align:left;"
    />
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  components: {
    IWorkExperience: require("components/timeline/i-work-experience/index.js")
      .default,
    ICardSkill: require("components/card/i-card-skill/index.js").default,
    IUserAvatar: require("components/avatar/i-user-avatar/index.js").default
  },
  computed: {
    ...mapGetters("systemConfig", ["languages", "currentLanguage"]),
    userName: function() {
      return this.$t("name");
    },
    skills: function() {
      return this.$t("skills");
    },
    workExperienceTitle: function() {
      return this.$t("workExperienceTitle");
    },
    FrontEndSKill: function() {
      return {
        skillType: this.$t("frontEnd"),
        details: [
          { name: "Vue.js" },
          { name: "Quasar" },
          { name: "javascript" },
          { name: "HTML5" },
          { name: "CSS" },
          { name: "jQuery" },
          { name: "Node.js" },
          { name: "Ajax" },
          { name: "Razor" },
          { name: "Bootstrap" },
          { name: "C# Windows Form" }
        ]
      };
    },
    BackEndSkill: function() {
      return {
        skillType: this.$t("backEnd"),
        details: [
          { name: "C#.Net MVC" },
          { name: "ASP.Net Web API" },
          { name: "EntityFramework Code First" },
          { name: "LINQ" }
        ]
      };
    },
    DatabaseSkill: function() {
      return {
        skillType: this.$t("database"),
        details: [{ name: "MSSQL" }, { name: "MySQL" }, { name: "Firebase" }]
      };
    },
    CISkill: function() {
      return {
        skillType: this.$t("ci"),
        details: [{ name: "gitlab-ci/cd" }, { name: "TeamCity" }]
      };
    },
    VCSSkill: function() {
      return {
        skillType: this.$t("versionControl"),
        details: [{ name: "Git" }, { name: "SVN" }]
      };
    },
    OtherSkill: function() {
      return {
        skillType: this.$t("other"),
        details: [
          { name: "Json" },
          { name: "Protobuf" },
          { name: "ESXI" },
          { name: "Linux" },
          { name: "Docker" },
          { name: "IIS" }
        ]
      };
    },
    responsibilitiesTitle: function() {
      return this.$t("responsibilities");
    },
    workExperience: function() {
      return [
        {
          companyName: this.$t("company1"),
          duringDate: this.$t("company1DuringDate"),
          responsibilities: [
            { id: 1, describe: this.$t("company1Responsibilities1") },
            { id: 2, describe: this.$t("company1Responsibilities2") },
            { id: 3, describe: this.$t("company1Responsibilities3") },
            { id: 4, describe: this.$t("company1Responsibilities4") },
            { id: 5, describe: this.$t("company1Responsibilities5") }
          ]
        },
        {
          companyName: this.$t("company2"),
          duringDate: this.$t("company2DuringDate"),
          responsibilities: [
            { id: 1, describe: this.$t("company2Responsibilities1") },
            { id: 2, describe: this.$t("company2Responsibilities2") },
            { id: 3, describe: this.$t("company2Responsibilities3") }
          ]
        },
        {
          companyName: this.$t("company3"),
          duringDate: this.$t("company2DuringDate"),
          responsibilities: [
            { id: 1, describe: this.$t("company3Responsibilities1") },
            { id: 2, describe: this.$t("company3Responsibilities2") },
            { id: 3, describe: this.$t("company3Responsibilities3") },
            { id: 4, describe: this.$t("company3Responsibilities4") }
          ]
        }
      ];
    },
    paragraphs: function() {
      return [this.$t("summary1"), this.$t("summary2"), this.$t("summary3")];
    }
  },
  watch: {
    lang(lang) {
      this.$i18n.locale = this.lang;

      let curLang = this.lang;
      let langObj = this.languages.find(x => x.value === curLang);
      this.setLanguage(langObj);

      import(`quasar/lang/${this.lang}`).then(language => {
        this.$q.lang.set(language.default);
      });
    }
  },
  data() {
    return {
      lang: this.$i18n.locale,
      AppSkill: {
        skillType: "APP",
        details: [{ name: "Xamarin" }, { name: "JAVA" }]
      }
    };
  },
  methods: {
    ...mapActions("systemConfig", ["setLanguage"]),
    getClass() {
      if (this.$q.screen.lt.sm) {
        return "text-black q-mx-sm q-my-md text-h6";
      } else {
        return "text-black q-mx-xl q-my-md text-h6";
      }
    }
  },
  mounted() {
    let defaultLanguage = "zh-hant";
    this.$i18n.locale = defaultLanguage;
    this.lang = defaultLanguage;
  }
};
</script>
