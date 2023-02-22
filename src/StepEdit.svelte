<script lang="ts">
    import 'two-up-element'
import {originalImage, modifiedImage} from './store'

let processingImage =true;
let tries= 0
let intervalId: any


$: {
    if(processingImage) {
        clearInterval(intervalId);
        intervalId = setInterval(() => { 
            tries++
         }, 500)
    }
}


</script>


<two-up>
    <img src={$originalImage} alt="User upload "/>
    <img 
    on:load={() => (processingImage =false)}
    on:error={() => (processingImage =true)}
    src={`${$modifiedImage}&t=${tries}`} alt="No BG "/>
</two-up>

<a download href={$modifiedImage} class="block bg-blue-500 mt-10 text-xl text-center w-full font-bold hover:bg-blue-700 text-white rounded-full px-4 py-2">
    Download Image
</a>