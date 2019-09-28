<template>
  <div class="container">
    <div class="card">
      <div class="comment">
        <div class="comment__img">
          <img src="../assets/ts.jpg" alt="Profile picture" />
        </div>
        <div class="comment__content">
          <ul class="comment-list">
            <li v-for="(item ,index) in comments " :key = "index">
              <span>{{item}}</span>
            </li>
          </ul>
          <div class="no-comments">
            <p v-if="comments.length < 1">No Comment Added yet</p>
            <!-- <p v-if="comments.length < 1 " >No comments added yet</p>
        
            <div v-for="comment in comments " :key ="comment">
           {{comment}}
           
            </div> -->
           
          </div>
        </div>
        <div class="comment-box">
          <textarea v-model.trim="comment"  @keyup.enter="addComment" class="form-control" rows="3" placeholder="Write a comment"></textarea>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { METHODS } from 'http'
export default {
  name: "PhotoComment",
  data(){
    return{
      comment:"",
      comments :[],
    }

  },
  methods:{
    addComment(){
      if (this.comment){
      this.comments.push(this.comment)
      this.comment = ""
      }
    }

  }
};
</script>

<style scoped lang="scss">
.container {
  margin: 0 auto;
  max-width: 768px;
}

.card {
  box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
}

.comment {
  &__img {
    > img {
      width: 100%;
    }
  }
  &__content {
    padding: 18px;

    .comment-list {
      > li {
        &:not(:last-child) {
          margin-bottom: 12px;
        }
        > span {
          background-color: #f2f3f5;
          border-radius: 68px;
          padding: 8px 12px;
          font-size: 14px;
          display: inline-block;
        }
      }
    }
  }
  .comment-box {
    textarea {
      border: 1px solid #f2f2f2;
      width: 100%;
      padding: 12px;
    }
  }
}
</style>
