<template>
  <div class="container-fluid">
    <div class="row no-gutter">
        <!-- The image half -->
        <div class="col-md-6 d-none d-md-flex bg-image"></div>


        <!-- The content half -->
        <div class="col-md-6 bg-light" id="box">
            <div class="login d-flex align-items-center py-5">

                <!-- Demo content-->
                <div class="container">
                    <div class="row">
                        <div class="col-lg-10 col-xl-7 mx-auto">
                            <h3 class="loginTitle">Login</h3>
                            <form>
                                <div class="form-group mb-3">
                                
                                    <input v-model="form.email"
                                    name="email"  
                                    type="email" placeholder="Email address"
                                    autofocus="" class="form-control rounded-pill border-3"
                                    required="required">
                                    
                                </div>
                                <div class="form-group mb-3">
                                    <input v-model="form.password"
                                     id="password" name="password"
                                      type="password" placeholder="Password" 
                                      class="form-control rounded-pill border-3"
                                      required="required">
                                </div>
                                
                                <button type="submit" @click.prevent="login" class="btn btn-success btn-block text-uppercase mb-2 rounded-pill">Login</button>
                                
                            </form>
                                      <p class="has-text-grey">
            <a>Not registered ? please registere as</a> &nbsp;·&nbsp;
            <router-link to="/retailer">Retailer</router-link> &nbsp;·&nbsp;
            <a href="/consumer">Consumer</a>
          </p>
                        </div>
               
                    </div>
                </div><!-- End -->

            </div>
        </div><!-- End -->

    </div>
</div>
</template>

<script>

  export default {
      data () {
          return{
    form: {
       email:null,
       password:null
}
          }
      },
      validations: {
        
   form: {
    email: {
           
    },
    password:{
           
    }
} 
      },
      methods: {
          login () {
   this.$v.form.$touch()
   console.log(this.$v)
   this.$store.dispatch('auth/loginWithCredentials',this.form)
 }
      }
  }
</script>

<style scoped>
  .login,
.image {
  min-height: 100vh;
}

.bg-image {
  background-image: url('../assets/welcomeImage.jpg');
  background-size: cover;
  background-position: center center;
  margin-top: 40px;
}
.loginTitle
{
  margin-bottom: 35px;
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  text-align: center;
  font-size: xx-large;
 color: rgb(14, 23, 34);
  text-shadow: 1px 1px 1px rgb(70, 43, 43), 0 0 25px rgb(49, 68, 37), 0 0 5px rgb(83, 126, 151);

}
</style>