# v-if , v-show 
  v-if : overhead 발생 , div 대신 <template> tag 사용 가능
  v-show : toggle시 유용 ( template tag 불가) 
  
# v-for 
  v-for='(a1, idx) in [10,20,30]' : index variable 
  
# directive : user define tag 
  lifecycle ( bind - only one called, inserted, update (change before), componentUpdated(change after), unbind) 
  
  
# vue-router
  1) a tag => <router-link to='/'></router-link>   to:: path value 
  2) component 대신 이동만 
  beforeEnter(to,from,next){ next('/home'); } 
  
  
# *mixin*
  공용methods
  
# render function 
  slot : use tag inner text 
  
# scroll pistion to top 
  scrollBehavior on router  
  
# form , submit not use ( remove it ) 

# use vuex
  variable => state : {  var_xxxx : '' }
  // save 
  this.$store.state.var_xxxx = 'value'; 
  // read 
  this.$store.state.var_xxxx
  -> reload 시 날라감.
  ==> use webstorage 
  
# use session storage
  sessionStorage.var_xxx = this.var_xxxx;
  
  beforeCreate 에서 sessionStorage value 읽어서 state에 할당 
  if(sessionStorage.var_xxx != undefined) ... 
  
  // remove storage
  sessionStorage.clear() 
