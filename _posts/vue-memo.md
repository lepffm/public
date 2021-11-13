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
