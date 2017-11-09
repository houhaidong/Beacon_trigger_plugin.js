# Beacon_trigger_plugin.js
beacon触发自定义规则插件

# 示例代码
 B.timeout  = 10000;
 B.beaconTouchOn = function(){

     var neatBeacon  =  this.accpetBeaon.length > 0 ? this.accpetBeaon[0] : null;
     var debugInfo = B.findTriggerByMinor(B.initBeacons[0].minor)

     if( !B.timer[neatBeacon.minor]  ){
         //Code 
         B.timeInBeacon(neatBeacon);
     }else if( B.timer[neatBeacon.minor] &&  parseInt( new Date().getTime()- B.timer[neatBeacon.minor].start ) > B.timeout  ){
         //Code
         B.timeInBeacon(neatBeacon);
     }

 }


 B.ready(function(){

     var self = this;

     B.startSearchBeacons(function(argv){
             //Code
     );


     wx.onSearchBeacons({
         complete:function(argv){

             self.sortByDistance(argv);
             self.findIndex()

         }
     });

 }.bind(B))
