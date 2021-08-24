<script>
import { onMount } from 'svelte';
import { annotate,annotationGroup } from 'rough-notation';

let h1;
// Element of my Name
let p1;
// Paragraph 2
let p2_1;
let p2_2;
let p2_3;
let p2_4;
// Paragraph 3
let p3;
// connet !
let c1;
let buttonConnect;
function generateAnnotationObject(type,color,iterations=1){
  return {
    type: type,
    color: color, 
    rtl:false, 
    animate:true ,
    padding:10,
    animationDuration:500, 
    iterations:iterations, 
  }
}
onMount(()=>{
  // a for annotation
  const a1 = annotate( h1, generateAnnotationObject('underline','#8033FF'));
  const a2 = annotate( p1, generateAnnotationObject('highlight','#51B2FD33' ));
  const Ep2_1 = annotate(p2_1, generateAnnotationObject('highlight','#FE135A44',1));
  const Ep2_2 = annotate(p2_2, generateAnnotationObject('highlight','#FF2E1344',1));
  const Ep2_3 = annotate(p2_3, generateAnnotationObject('highlight','#FF6D1344',1));
  const Ep2_4 = annotate(p2_4, generateAnnotationObject('highlight','#FFB01344',1));
  const Ep3 = annotate(p3, generateAnnotationObject('highlight','#6DE18744',1));
  const ConnetAnnotation = annotate(c1, generateAnnotationObject('underline','#FFF',2));
  const ag = annotationGroup([a1, a2, Ep2_1,Ep2_2,Ep2_3,Ep2_4,Ep3, ConnetAnnotation]);
  ag.show();
  buttonConnect.addEventListener('click',()=>{
    ag.hide();
    ag.show();
  },false)
});
</script>
<article class="relative max-w-xl text-white text-xl selection:text-[#0099ff] selection:bg-[hsla(210,100%,50%,0.2)]">
    <h1 class="text-4xl font-black mb-6">Hi there, I'm <span bind:this={h1}>Shreya</span>.</h1>
    <p class="mb-3 selection:text-blue-500 selection:bg-blue-500/10">
      My passion is to connect teens to there core of happiness, helping them to becoming better themselves,
      through, bringing ancient <span bind:this={p1}>wisdom</span> and tommorows practicality in them .
    </p> 
    <p class="mb-3 selection:text-indigo-500 selection:bg-indigo-500/10">
      Besides, meditation I am also 
      <span bind:this={p2_1}>guitarist</span>, <span bind:this={p2_2}>photographer</span>, <span bind:this={p2_3}>books&nbsp;lover</span> and <span bind:this={p2_4}>Influencer</span>.
    </p>
    <p class="mb-3 selection:text-purple-500 selection:bg-purple-500/10">
      Through my past experience, I can make <span bind:this={p3}>better tommorow</span> 
    </p>
    <a href="/about" >
      <span on:mouseenter={(e)=>{
          annotate(e.target,{type: 'underline',iterations:2,color:'#94F'}).show();
        }} bind:this={c1} class="" >
        More !
      </span>
    </a>
    <button bind:this={buttonConnect} class="absolute -top-8 right-0 hover:bg-white hover:text-lightBlue-500 flex items-center justify-center w-8 h-8 focus:ring focus:ring-offset-2 rounded-xl transition-colors ease-in-out">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline " fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15" />
      </svg>
    </button>
</article>