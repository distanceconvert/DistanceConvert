# DistanceConvert
km=1
hm=10
dnm=100
m=1000
dm=10000
cm=100000
mm=1000000
w=0
function(x,y,z,w){
if(x==0)
w=0
w=x*(z/y);
return(w)
