<template>
  <Page class="page">
    <ActionBar title="NativeScript-Vue Theme Swap Sample" class="action-bar"/>
    <ScrollView>
      <GridLayout columns="*,*" rows="auto,auto,auto,auto,auto,auto,auto,auto,auto,auto,auto" margin="10">
        <Label class="h2" :text="msg" col="0" row="0" colSpan="2"/>
        <Label class="h2" :text="currentTheme" col="0" row="1" colSpan="2" marginBottom="20"/>

        <Label class="h2" width="100%" textAlignment="center" text="CSS files" col="0" row="2" />
        <Label class="h2" width="100%" textAlignment="center" text="Webpack" col="1" row="2" />

        <Button class="btn btn-primary" col="0" row="3" @tap="switchThemeFile('core.light.css')" text="core.light.css"></Button>
        <Button class="btn btn-outline" col="1" row="3" @tap="switchThemeWebpack('light.scss')" text="light.scss"></Button>

        <Button class="btn btn-primary" col="0" row="4" @tap="switchThemeFile('core.dark.css')" text="core.dark.css"></Button>
        <Button class="btn btn-outline" col="1" row="4" @tap="switchThemeWebpack('dark.scss')" text="dark.scss"></Button>

        <Button class="btn btn-primary" col="0" row="5" @tap="switchThemeFile('aqua.css')" text="aqua.css"></Button>
        <Button class="btn btn-outline" col="1" row="5" @tap="switchThemeWebpack('aqua.scss')" text="aqua.scss"></Button>

        <Button class="btn btn-primary" col="0" row="6" @tap="switchThemeFile('brown.css')" text="brown.css"></Button>
        <Button class="btn btn-outline" col="1" row="6" @tap="switchThemeWebpack('brown.scss')" text="brown.scss"></Button>

        <Button class="btn btn-primary" col="0" row="7" @tap="switchThemeFile('forest.css')" text="forest.css"></Button>
        <Button class="btn btn-outline" col="1" row="7" @tap="switchThemeWebpack('forest.scss')" text="forest.scss"></Button>

        <Button class="btn btn-primary" col="0" row="8" @tap="switchThemeFile('grey.css')" text="grey.css"></Button>
        <Button class="btn btn-outline" col="1" row="8" @tap="switchThemeWebpack('grey.scss')" text="grey.scss"></Button>

        <Button class="btn btn-primary" col="0" row="9" @tap="switchThemeFile('lemon.css')" text="lemon.css"></Button>
        <Button class="btn btn-outline" col="1" row="9" @tap="switchThemeWebpack('lemon.scss')" text="lemon.scss"></Button>

        <Button class="btn btn-primary" col="0" row="10" @tap="switchThemeFile('ruby.css')" text="ruby.css"></Button>
        <Button class="btn btn-outline" col="1" row="10" @tap="switchThemeWebpack('ruby.scss')" text="ruby.scss"></Button>
      </GridLayout>
    </ScrollView>
  </Page>
</template>

<script>
import Themes from 'nativescript-themes'

export default {
  data() {
    return {
      msg: 'Current Theme:',
      currentTheme: Themes.getAppliedTheme()
        .split('/')
        .reverse()[0],
    }
  },
  methods: {
    switchThemeFile(themeFile) {
      Themes.applyTheme('./assets/cssThemes/' + themeFile)
      this.currentTheme = Themes.getAppliedTheme()
        .split('/')
        .reverse()[0]
    },
    switchThemeWebpack(themeFile) {
      const cssText = require('~/assets/scssThemes/' + themeFile)
      Themes.applyThemeCss(cssText, themeFile)
      this.currentTheme = Themes.getAppliedTheme()
        .split('/')
        .reverse()[0]
    },
  },
}
</script>

<style scoped>
.message {
  vertical-align: center;
  text-align: center;
  font-size: 20;
  color: #333333;
}
</style>
