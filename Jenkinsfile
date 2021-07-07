
def buildhip(slave){
     return{
        node(slave) {
          stage("Source sync"){
            dir("${WORKSPACE}/hip"){
               checkout scm
               }
            dir("${WORKSPACE}/hipamd") {
              git branch: 'amd-master',
              url: 'ssh://gerritgit/compute/ec/hipamd'
            }
         }
          stage("build"){
             echo "Build"
           }
             
         stage("rocm-dev installation"){
                echo "dev instalation"
            }
         
          
          stage("test") {
            echo "testing"
 
        }
    }

 }

}

timestamps {
     node('BS5') {
     build_agents = ["AMD-hipanl-nvidia-01","AMD-hipanl-vg20-01"]
     buildmap =[:]
     agents = []

     for (slave in build_agents) {
        buildmap[slave] = buildhip(slave)
     }

     buildmap['failFast']=false
     parallel  buildmap
  }//closing the node
}//closing the timestamps
