<template>
  <div class="hello">
    <a id="fork-me" href="https://github.com/zachwatkins-tfwebco/lego-library"><img loading="lazy" width="149" height="149" src="https://github.blog/wp-content/uploads/2008/12/forkme_left_orange_ff7600.png?resize=149%2C149" class="attachment-full size-full" alt="Fork me on GitHub" data-recalc-dims="1"></a>
    <h1>{{ msg }}</h1>
    <p>
      <a href="https://github.com/zachwtx/lego-library">Check out the source code on Github!</a>
    </p>
    <p>
      This application uses the following features of the Vue framework:
    </p>
    <ul>
      <li><a href="https://router.vuejs.org/guide/">Vue Router</a> for making a single-page application with multiple "pages"</li>
      <li><a href="https://vuejs.org/v2/guide/components.html">Components Basics</a></li>
      <li><a href="https://vuejs.org/v2/guide/single-file-components.html">Single file components</a></li>
      <li><a href="https://vuejs.org/v2/guide/components-custom-events.html">Custom event handlers</a></li>
      <li><a href="https://stackoverflow.com/questions/45565349/how-to-access-external-json-file-objects-in-vue-js-app">File reading for better performance</a></li>
      <li><a href="https://vuejs.org/v2/guide/forms.html">Form input bindings</a></li>
      <li><a href="https://vuejs.org/v2/guide/list.html">List Rendering (apply template to array)</a></li>
      <li><a href="https://vuejs.org/v2/guide/list.html#Replacing-an-Array">Array Change Detection (mutation methods)</a></li>
      <li><a href="https://cli.vuejs.org/guide/css.html#pre-processors">CSS Pre-Processors</a> being compiled in single file components</li>
      <li><a href="https://vue-loader.vuejs.org/guide/pre-processors.html#sass">More information about Sass Preprocessors</a></li>
    </ul>
    <p>
      The following challenges were encountered during research, development, and implementation:
    </p>
    <ol>
      <li><a href="https://github.com/microsoft/Oryx">Microsoft Oryx</a> does not automatically and accurately detect that an unbuilt VueJS application is a static web application, even when deploying to the Azure Static Web App service. The deploy *.yml file and other files declare settings to build the application properly. The solution involves installing dependencies and building the application before the Oryx step runs at all. This allows it to detect the built files and determine what kind of application it is deploying.</li>
      <li>All dependencies must be installed during the build process, so if the application is built by Github Actions or some other CI/CD process then it will take a little more time. This may be 25 seconds or so and I have not yet determined if there is a way to cache dependencies to speed this up.</li>
      <li>VueJS documentation for components does not typically show examples of single file components and how to write features specific for that approach.</li>
      <li>Azure only supports certain versions of Node on Ubuntu, and the supported version must be declared in your application's .npmrc file and/or package.json for Oryx to complete the deployment. Otherwise it will emit an error regarding version support. <a href="https://github.com/microsoft/Oryx/blob/main/doc/supportedPlatformVerions.md">View the version support list here</a>.</li>
      <li>You can use CSS preprocessors in components, but currently in order to avoid dependency conflicts with Webpack v4 you need to install a specific version of the "sass loader" package. Run <code>$ npm install -D sass-loader@^10 sass</code>. See the <a href="https://cli.vuejs.org/guide/css.html#pre-processors">Note on webpack 4</a> in the CSS Pre-Processors section for more information.</li>
    </ol>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul class="unset">
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul class="unset">
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul class="unset">
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
#fork-me {
  position: absolute;
  top: 0;
  left: 0;
}
h3 {
  margin: 40px 0 0;
}
ul,
ol {
  &:not(.unset) {
    text-align: left;
    max-width: 640px;
    margin-left: auto;
    margin-right: auto;
  }
}
ul.unset {
  list-style-type: none;
  padding: 0;
}
ul.unset li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
