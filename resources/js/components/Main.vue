<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-6" v-for="post in posts" :key="post.id">
          <div class="my_card card mb-3" style="max-width: 540px;">
            <div class="row no-gutters">
              <div class="col-md-4">
                <img class="w-100 p-3" :src="post.url" :alt="post.tilte">
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">{{post.title}}</h5>
                  <p class="card-text">{{post.description}}</p>
                  <div class="category">
                      <span><strong>Category: </strong>{{post.category != null ? post.category.name : 'None'}}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name : 'Main',
    data(){
      return{
        posts : null
      }
    },
    methods:{
      getPost(){
        axios.get('/api/posts').then(response =>{
          this.posts = response.data.response;
          console.log(response.data.response)
        })
      }
    },
    created(){
      this.getPost();
    }
  }
</script>

<style lang="scss" scoped>
  .my_card{
    min-height: 300px;
  }
</style>