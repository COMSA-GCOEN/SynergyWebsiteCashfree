<script lang="ts">
  import {openModal} from 'svelte-modals';
  import EventModal from '$lib/components/EventModal.svelte';
	import { goto } from '$app/navigation';
  // openModal(EventModal, { title: "Alert", message: "This is an alert" })
  
  export let name:string, desc:string, id:string, image: string; 
  let onLearnMore = () => {
    openModal(EventModal, {id: id})
  }
</script>

<div class="card max-w-xs md:max-w-md lg:max-w-lg aspect-video bg-base-200 shadow-xl image-full max-h-60 my-4">
    <figure><img src="{image ? image : 'https://placeimg.com/400/225/tech'}" alt="Shoes" /></figure>
    <div class="card-body">
      <h2 class="card-title vimh">{name}</h2>
      <p class="min-h-16">{desc}</p>
      <div class="card-actions justify-end">
        <button on:click={()=>{goto(`/register/${id}`)}} class="btn btn-primary">Register</button>
        <button on:click={onLearnMore} class="btn">Explore</button>
      </div>
    </div>
  </div>

<style>
  .card {
    min-height: clamp(20vh, 25vh, 30vh);
  }
</style>