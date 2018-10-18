<template>
  <div class="">
    <div v-for="thread in threads"
         class="col-large push-top"
    >
      <h1>{{thread.title}}</h1>
      <div class="post-list">
        <div v-for="postId in thread.posts"
             class="post"
        >
          <div class="user-info">
            <a href="#" class="user-name">{{users[posts[postId].userId].name}}</a>
            <a href="#">
              <img class="avatar-large" :src="users[posts[postId].userId].avatar" alt="">
            </a>
            <p class="desktop-only text-small">107 posts</p>
          </div>
          <div class="post-content">
            <div>
              {{posts[postId].text}}
            </div>
          </div>
          <div class="post-date text-faded">
            {{posts[postId].publishedAt}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import sourceData from '../data.json';

  console.log(sourceData);
  export default {
    name: 'HelloWorld',
    data() {
      return {
        threads: sourceData.threads,
        posts: sourceData.posts,
        users: sourceData.users
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import "../assets/scss/main";

  .post {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    background-color: $white;
    padding: 20px 10px;
    padding-bottom: 7px;
    box-shadow: 2px 2px 1px $color_suva_gray_9_approx;
    margin-bottom: 20px;

    .user-info {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      text-align: center;
      flex: 1 1 15%;
      margin-right: 5px;

      > * {
        margin-bottom: 10px;
      }
    }

    .post-date {
      flex-basis: 100%;
      font-size: 14px;
      text-align: right;
      margin-bottom: 5px;
      padding-right: 7px;
    }
  }

  @media(max-width: 820px) {

    .post {
      padding: 0;

      .user-info {
        order: -2;
        flex-direction: row;
        justify-content: flex-start;
        background: $color_trout_6_approx;
        margin-right: 0;
        padding: 5px;
        padding-left: 10px;

        .avatar-large {
          height: 35px;
          width: 35px;
          margin-right: 5px;
          order: 1;
        }

        .user-name {
          order: 2;
        }

        > * {
          margin-right: 5px;
          margin-bottom: 0;
        }
      }

      .post-date {
        order: -1;
        flex-basis: 40%;
        background: $color_trout_6_approx;
        padding-right: 10px;
        padding-top: 16px;
        margin-bottom: 0;
      }
    }

    .post-content blockquote {

      &.big::before {
        top: -15px;
        left: -18px;
        font-size: 32px;
      }

      &.small::before {
        top: -18px;
        left: -15px;
        font-size: 32px;
      }

      &.simple::before {
        top: -15px;
        left: -18px;
        font-size: 32px;
      }
    }
  }

  @media(max-width: 720px) {
    .post {
      padding: 0;
    }
  }

  .post-content {
    display: flex;
    flex: 1 1 83%;
    padding-left: 15px;
    padding-right: 10px;
    font-size: 16px;
    text-align: justify;
    line-height: 1.5;
    word-break: break-word;

    h1 {
      margin-bottom: 0;
    }

    h2 {
      margin-bottom: 0;
    }

    h3 {
      margin-bottom: 0;
    }

    p {
      margin-bottom: 20px;
    }

    pre {
      display: grid;
      overflow: auto;
      word-wrap: break-word;
      border-radius: 3px;
      padding: 10px;
    }

    blockquote {
      margin: 25px 0;

      &.big {
        display: flex;
        position: relative;

        .quote {
          padding-left: 20px;
          padding-right: 15px;
          flex-basis: 95%;
          font-weight: 100;
          font-style: italic;
          font-size: 17px;
        }

        .author {
          display: flex;
          flex-direction: column;
          align-items: center;
          justify-content: flex-start;
          text-align: center;

          img {
            flex: 1;
            flex-basis: 100%;
            margin-top: 10px;
            width: 80px;
            height: 80px;
          }
        }
      }

      &.big::before {
        position: absolute;
        top: -25px;
        left: -25px;
        font-size: 42px;
        font-family: $font_0;
        content: "\f10e";
        color: $color_cello_approx;
      }

      &.small {
        display: flex;
        position: relative;
        flex-direction: column;
        border: 2px solid $color_mountain_mist_15_approx;
        border-bottom-left-radius: 5px;
        border-bottom-right-radius: 5px;

        .author {
          display: flex;
          flex-basis: 100%;
          padding: 3px 10px 3px 28px;
          background-color: $color_mountain_mist_15_approx;
          justify-content: center;
          align-items: center;

          .time {
            margin-left: 10px;
          }

          .fa {
            margin-left: auto;
            font-size: 20px;

            &:hover {
              cursor: pointer;
            }
          }
        }

        .quote {
          display: flex;
          flex-basis: 100%;
          flex-direction: column;
          padding: 10px;
          font-weight: 100;
          font-style: italic;
          font-size: 17px;
        }
      }

      &.small::before {
        position: absolute;
        top: -20px;
        left: -20px;
        font-size: 42px;
        font-family: $font_0;
        content: "\f10e";
        color: $color_cello_approx;
      }

      &.simple {
        position: relative;
        padding: 0 10px 0 20px;
        font-weight: 100;
        font-style: italic;
        font-size: 17px;
        letter-spacing: .15px;

        .author {
          display: block;
          margin-top: 10px;
          font-weight: normal;

          .time {
            margin-left: 10px;
          }
        }
      }

      &.simple::before {
        position: absolute;
        top: -25px;
        left: -25px;
        font-size: 42px;
        font-family: $font_0;
        content: "\f10e";
        color: $color_cello_approx;
      }
    }

    div:first-of-type {
      width: 100%;
    }
  }
</style>
