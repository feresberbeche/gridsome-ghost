<template>
<div>
            <div class="fb-send-to-messenger" 
            messenger_app_id="952995201880936" 
            page_id="353078436675" 
            :data-ref="'Learn_More_'" 
            color="blue" 
            size="large"
            />
</div>
</template>
<script>
export default {
  mounted() {
    console.log('created main');
    window.fbAsyncInit = function() {
      FB.init({
        appId      : '952995201880936',
        xfbml      : true,
        version    : 'v2.7'
      });

      //This function should be here, inside window.fbAsyncInit
      FB.getLoginStatus(function(response) {
        console.log(response);
     });

   };

    (function(d, s, id){
     var js, fjs = d.getElementsByTagName(s)[0];
     if (d.getElementById(id)) {return;}
     js = d.createElement(s); js.id = id;
     js.src = "//connect.facebook.net/en_US/sdk.js";
     fjs.parentNode.insertBefore(js, fjs);
    }(document, 'script', 'facebook-jssdk'));
  }}
</script>