<template>
  <div class="overflow-auto" style="max-height: 96vh">
     <div class="overflow-auto" style="max-height: 100vh">
      <div class="row">
      <div class="col-7">
        <h1>Sandbox</h1>
      </div>
      <div class="col-3">
        <a
          type="button"
          class="btn btn-secondary text-white"
          href="/"
          style="
            margin-left: 15%;
            font-weight: bold;
            --bs-btn-padding-y: 0.45rem;
            --bs-btn-padding-x: 0.8rem;
            --bs-btn-font-size: 1.15rem;
          "
          >{{ $t('repoBack') }}
        </a>
        ㅤ
      </div>

      ㅤ
    </div>
    
    <div style="width: 100%;">
      ㅤ
       
      <GitHubCodeSandbox   :url="release.codesandbox_URL" />
    </div>
    ㅤ
  


</div>
</div>

  </template>
  
  <script>
  import GitHubCodeSandbox from "@/components/GitSB.vue";
  
  export default {

    props: ['releaseID'],
    components: {
      GitHubCodeSandbox,
    },

    data() {
      return {
     
        release: {},

      };
    },

    methods: {

    async fetchData() {
      try {
        
        const url = `${import.meta.env.VITE_APP_EXPRESS_URL}/api/release/${this.releaseID}`;
        const response = await this.axios.get(url);
        this.release = response.data;
      } catch (err) {
        console.log('Error fetching data:', err);
      }
    }

  },


    mounted() {
      this.fetchData();
      
    }
  };
  </script>

<style>

.comments-section {
    font-family: Arial, sans-serif;
  }
  
  .comment {
    padding: 1rem;
    margin-bottom: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .comment-author {
    font-weight: bold;
  }
  
  .comment-body {
    margin-top: 0.5rem;
  }
  
  .comment-replies {
    margin-left: 2rem;
    margin-top: 1rem;
  }
</style>