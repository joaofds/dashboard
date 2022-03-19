<template>
  <el-container>
    <el-header height="100px" :style="{ 'background-color': primaryColor }">
      <img src="@/assets/img/logo.svg" alt="store-logo" class="header-logo">
      <span class="logo-title">{{ langConfig.header.title[lang] }}</span>
      <ul class="header-operations">
        <li >{{ langConfig.header.theme[lang] }}</li>
        <li>{{ langConfig.header.help[lang] }}</li>
        <li>
          <span @click="switchLang('/pt-BR')" class="header-lang"
          :class="{ 'is-active' : lang === '/pt-BR' }">
            PT
          </span>
          <span>/</span>
          <span @click="switchLang('/en-US')" class="header-lang"
          :class="{ 'is-active' : lang === '/en-US' }">
            EN
          </span>
        </li>
      </ul>
    </el-header>
  </el-container>
</template>

<script>
import { use } from "element-ui/lib/locale";
import ptLocale from "element-ui/lib/locale/lang/pt-br";
import enLocale from "element-ui/lib/locale/lang/en";
import langConfig from "@/lang";

export default {
    name: "app-header",
    data() {
      return {
        primaryColor: '#409eff',
        langConfig,
      }
    },
    methods: {
      switchLang (lang) {
        let url = window.location.href;
        let lastSegment = url.split("/").pop();
        if ('/'+lastSegment !== lang) {
          this.$router.push(lang)
        }
      },
    },
    computed: {
      lang () {
        const lang = this.$route.path
        use(lang === '/pt-br' ? ptLocale : enLocale)
        return lang
      }
    },
}
</script>

<style lang="scss">
header {
  width: 100%;
  padding: 0 20px;
  z-index: 1;
  box-sizing: border-box;
}

header::after {
  display: inline-block;
  content: "";
  height: 100%;
  vertical-align: middle;
}

.header-logo {
  display: inline-block;
  vertical-align: middle;
  max-height: 75%;
  margin-right: 0.5em;
  cursor: pointer;
}

.logo-title {
  font-weight: 600;
  color: #fff;
  letter-spacing: 5px;
  cursor: pointer;
}

.header-operations {
  display: inline-block;
  float: right;
  padding-right: 30px;
  height: 100%;
  & li {
    color: #fff;
    display: inline-block;
    vertical-align: middle;
    padding: 0 10px;
    margin: 0 10px;
    line-height: 80px;
    cursor: pointer;
    &:last-child {
      cursor: default;
    }
  }
  .header-download {
    opacity: 0.4;
    cursor: default;
    &.is-available {
      opacity: 1;
      cursor: pointer;
    }
  }
  span {
    opacity: 0.7;
  }
  .header-lang {
    cursor: pointer;
    &.is-active {
      opacity: 1;
    }
  }
}

.header-operations::after {
  display: inline-block;
  content: "";
  height: 100%;
  vertical-align: middle;
}

</style>