<template>
    <div class="max-w-sm w-full lg:max-w-full lg:flex mt-4">
        <div
          class="h-48 lg:h-auto lg:w-48 flex-none bg-cover rounded-t lg:rounded-t-none lg:rounded-l text-center overflow-hidden"
          :style="'background-image: url(https://fwemoviedb.herokuapp.com/img/w188_and_h282_bestv2'+SLBox.poster_path+');'"
          title="Star Wars"
        ></div>
        <div
          class="border-r border-b border-l border-gray-400 lg:border-l-0 lg:border-t lg:border-gray-400 bg-white rounded-b lg:rounded-b-none lg:rounded-r p-4 flex flex-col justify-between leading-normal"
        >
            <div class="mb-8">
                <div class="text-gray-900 font-bold text-xl mb-2">
                {{SLBox.title}}
                </div>
                <p class="text-gray-700 text-base">
                {{SLBox.overview}}
                </p>
            </div>
            <div class="text-sm">
                <p class="text-gray-600">{{SLBox.release_date}}</p>
            </div>
        </div>
    </div>          
</template>
<script>
export default {
    name : 'SearchListBox',
    props : ["SLBox","id"],
    methodes : {
      checkImage(){
        if(prop.SLBox.poster_path==null){
          return false
        }
      }
    }
}
</script>