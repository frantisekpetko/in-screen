<script lang="ts">
    import { fade } from 'svelte/transition';
    //import { inview } from 'svelte-inview';
    import { inview } from "../utils/inview";
  
    let isInView;

  </script>
  
  <div
    class="wrapper"
    use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
    on:change={({ detail }) => {
      setTimeout(() => {isInView = detail.inView}, 1000);
    }}
  >
  <div class="box" class:changeBlue={isInView}>
    <h3>Appears from nowhere</h3>
    <p>
      Lorem ipsum, dolor sit amet consectetur adipisicing elit. Error,
      adipisci nihil iste.
    </p>
  </div>
  <!--

        {#if isInView}
 
    {:else}
    <div class="box" class:changeBlue={isInView}>
        <h3>Appears from nowhere</h3>
        <p>
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Error,
          adipisci nihil iste.
        </p>
    </div>
    {/if}
  -->
  </div>
  
  <style>
  

    .wrapper {
      margin-top: 30px;
    }
  
    .box {

      width: 300px;
      border: 1px solid rgb(221, 221, 221);
      padding: 25px;
      border-radius: 10px;
      transition: background-color 1s;
      background-color: red;

    }

    @keyframes changeBlueAnime {
        from {background-color: red}
        to   {background-color: greenyellow;}
    }

    .changeBlue {
        animation-name: changeBlueAnime;
        animation-duration: .2s;
        animation-fill-mode: forwards;
    }

    .box:hover {
        background-color: red;
    }

    .is-non-active {
        background-color: red;
    }

    .is-active {
        background-color: greenyellow;
    }
  </style>