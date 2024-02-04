<template>
  <div class="max-w-screen">
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
      <div class="lg:w-2">
        <!-- Treść z lewej strony... -->
      </div>

      <div
        class="fb-page"
        data-href="https://www.facebook.com/MaxVerstappen"
        data-tabs="timeline,events,messages"
        data-width="290"
        data-height="600"
        data-small-header="false"
        data-adapt-container-width="false"
        data-hide-cover="false"
        data-show-facepile="true"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FacebookPage",

  mounted() {
    this.loadFacebookSdk();
  },

  methods: {
    loadFacebookSdk() {
      if (document.getElementById("facebook-jssdk")) return;

      window.fbAsyncInit = function () {
        FB.init({
          appId: "your-app-id", // Opcjonalnie, jeśli używasz funkcji wymagających appId
          xfbml: true,
          version: "v10.0",
        });
        FB.XFBML.parse(); // Wywołanie tego, aby zainicjalizować wtyczki na stronie
      };

      (function (d, s, id) {
        var js,
          fjs = d.getElementsByTagName(s)[0];
        if (d.getElementById(id)) return;
        js = d.createElement(s);
        js.id = id;
        js.src = "https://connect.facebook.net/en_US/sdk.js";
        fjs.parentNode.insertBefore(js, fjs);
      })(document, "script", "facebook-jssdk");
    },
  },
};
</script>
