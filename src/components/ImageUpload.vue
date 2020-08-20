<template>
  <b-container  fluid>
    <div class="main">
        <b-row class="header">
            <b-col sm="4" md="7" lg="9">
                <h2 class="mh"><b>Add Room Photos</b></h2>
            </b-col>

            <b-col sm="4" md="5" lg="3">                 
                <h6 class="sh"><span style="margin:15px;" ><b-icon icon="image" scale="2" aria-hidden="true"></b-icon></span>Add Photos</h6>

            </b-col>
          
        </b-row>

        <b-row class="content">
            <b-col sm="12" md="5" lg="3" >
                <b-card class="imgSelector">  
                    <croppa v-model="myCroppa" 
                        canvas-color="transparent"  
                              
                    >
                    </croppa>
                    <b-button class="bg-light" style="margin:5px;" @click="generateImage"><b-icon icon="plus-circle-fill" scale="1.5" variant="success" aria-hidden="true"></b-icon></b-button>

                </b-card>
            </b-col>
            <b-col sm="12" md="7" lg="9">
                <div class="wrapper">
                    <div class="item border-dark " v-for="(image, index) in imgUrl" :key="index"   > 
                        <img class="card card-img-top" :src="image" alt="" style="height:250px; width:250px;"> 
                    
                        <div class="card-body bg-light text-dark">                 
                            <div style="display: flex; justify-content: center; height:40px;">
                                <b-button class="btn-light  bg-light btn-sm" @click="$delete(imgUrl, index)"><b-icon icon="trash-fill" scale="1.5" variant="danger" aria-hidden="true"></b-icon></b-button>
                            </div>

                        </div> 
                        
                    </div>
                    
                </div>
                

            </b-col>

        </b-row>
    

      </div>
      

  </b-container>
</template>

<script>
export default {
    data() {
        return {
            myCroppa: null,
            imgUrl: []

        }
    
  },
  
    methods: {
        generateImage: function() {
            let url = this.myCroppa.generateDataUrl()
            if(!url) {
                alert('no image')            
            }
            this.imgUrl.push(url);
            
        },
        
    }

}
</script>

<style>
.main {
    padding: 25px;
    border: 1px solid black;
    margin-top: 20px;
    

}
.content {
    border: 2px dotted black;
    padding: 5px;
}

.croppa-container {
  background-color: white;
  border: 1px solid black;
  display: flex;
  justify-content: center;
}

.wrapper {
    overflow-x: auto;    
    display: flex;
    max-height: 350px;
    
    /* margin: 20px; */
}
/* .wrapper::-webkit-scrollbar {
    width: 0;
} */

.wrapper .item {
    /* min-width: 250px; */
    margin-right: 15px;
    background-color: lightgray;
    padding: 1px;
   
}



.header h2 {
    font-size: 20px;
    padding: 5px;
}

.mh {
    float: left;
}
.sh {
    float: right;
    
}

.imgSelector {
     height: 350px;
    /*width: 250px; */
  
    
    
}

.card {
    border: 1px solid black;
    padding: 5px;
    
}
</style>