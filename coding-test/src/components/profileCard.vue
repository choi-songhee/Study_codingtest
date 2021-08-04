<template>
  <ul class="profile-wrap">
    <li
      v-for="(item, index) in shuffleIndex"
      :key="index"
    >
      <figure class="profile-image">
        <img :src="item.image" alt="">
      </figure>
      <h4 class="profile-name">{{ item.name }}</h4>
      <p class="profile-desc">{{ item.desc }}</p>
      <a :href="item.url" class="profile-link">Learn more</a>
    </li>
  </ul>
</template>

<script>
import _ from 'lodash';

export default {
  data() {
    return {
      profileList: [
        {
          image: "/profile_01.png",
          name: "Sed ut perspiciatis",
          desc: "Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem.",
          url: "#"
        },
        {
          image: "/profile_02.png",
          name: "Lorem ipsum dolor",
          desc: "Amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis.",
          url: "#"
        },
        {
          image: "/profile_03.png",
          name: "Nemo enim ipsam",
          desc: "Consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor.",
          url: "#"
        }
      ]
    }
  },
  computed: {
    shuffleIndex() {
      return _.shuffle(this.profileList)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.profile-wrap {
  display: flex;
  margin-top: 70px;
  padding: 0;
  font-size: 0;
  li {
    flex: 1 0 33.33%;
    padding: 0 10px;
    list-style: none;
    box-sizing: border-box;
    .profile {
      &-image {
        width: 108px;
        height: 108px;
        margin: 0;
        img {
          width: 100%;
          height: auto;
        }
      }
      &-name {
        margin-top: 2.381vw;
        font-size: 24px;
        line-height: 1.5;
        letter-spacing: -0.36px;
        font-family: 'Montserrat';
        font-weight: bold;
      }
      &-desc {
        max-width: 493px;
        max-height: 90px;
        margin: 1.429vw 0;
        font-size: 18px;
        line-height: 1.67;
        letter-spacing: -0.27px;
        color: rgba(0, 0, 0, 0.8);
        font-family: 'Montserrat';
        font-weight: normal;
        display: -webkit-box;
        word-wrap: break-word;
        -webkit-line-clamp: 3;
        -webkit-box-orient: vertical;
        overflow: hidden;
        text-overflow: ellipsis;
        height: 90px;
      }
      &-link {
        font-size: 18px;
        line-height: 1.67;
        letter-spacing: -0.27px;
        color: #18a0fb;
        text-decoration: none;
        font-family: 'Exo2';
        font-weight: bold;
      }
    }
  }
}

@media (max-width: 767px) {
  .profile-wrap {
    flex-wrap: wrap;
    li {
      flex: 1 0 auto;
      margin-top: 50px;
      &:first-child {
        margin-top: 0;
      }
    }
  }
}
</style>
