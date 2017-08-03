<template>
    <v-ons-page>
      <v-ons-toolbar>
        <div class="center">{{ title }}</div>
        <div class="right">
          <v-ons-toolbar-button>
            <v-ons-icon icon="ion-navicon, material: md-menu"></v-ons-icon>
          </v-ons-toolbar-button>
        </div>
      </v-ons-toolbar>
      <div style="text-align: center; padding-top:10px">Hello World!</div>
      <p style="text-align: center">
        <!--<v-ons-button @click="alert">Click Me!</v-ons-button>-->
          <button onclick="window.plugins.touchid.isAvailable(function(msg) {alert('ok: ' + msg)}, function(msg) {alert('not ok: ' + msg)})">Touch ID available?</button>
          <button onclick="window.plugins.touchid.verifyFingerprint('Scan your fingerprint please', function(msg) {alert('ok: ' + msg)}, function(msg) {alert('not ok: ' + JSON.stringify(msg))})">Scan fingerprint</button>
      </p>
    </v-ons-page>
</template>
<script>


    FingerprintAuth.isAvailable(isAvailableSuccess, isAvailableError);

    /**
     * @return {
 *      isAvailable:boolean,
 *      isHardwareDetected:boolean,
 *      hasEnrolledFingerprints:boolean
 *   }
     */
    function isAvailableSuccess(result) {
        alert("FingerprintAuth available: " + JSON.stringify(result));
        if (result.isAvailable) {
            var encryptConfig = {}; // See config object for required parameters
            FingerprintAuth.encrypt(encryptConfig, encryptSuccessCallback, encryptErrorCallback);
        }
    }

    function isAvailableError(message) {
        alert("isAvailableError(): " + message);
    }

  export default{
    data() {
      return {
        title: 'My app'
      };
    },
    methods: {
      touchpadcheck() {

//        alert('outside = '+this.cordova.device);
        this.$ons.notification.alert('This is an Onsen UI alert notification test.');
      }
    },
      mounted: function(){
          /*this.$ons.notification.alert('aisi');
          document.addEventListener("deviceready", onDeviceReady, false);
          function onDeviceReady() {
              this.$ons.notification.alert('peep');
              this.$ons.notification.alert('obj = '+JSON.stringify(device));
          }*/

          /*window.plugins.touchid.isAvailable(
              function() {alert('available!')}, // success handler: TouchID available
              function(msg) {alert('not available, message: ' + msg)} // error handler: no TouchID available
          );*/
      }
  };
</script>
