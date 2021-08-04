<template>
  <section v-if="errored">
    We're sorry, we're not able to retrieve this information at the moment, please try back later
  </section>
  <section v-else>
    <div
      class="fullBleed-wrap"
      :style="{'background-image': `url(${ backImage })`}"
    >
<!--      <img ref="image" :src="backImage.urls.full" />-->
      <div class="text-wrap">
        <h4 class="title">Sed ut perspiciatis unde omnis</h4>
        <p class="sub-title">
          There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form, by injected humour, or randomised words which don't look even slightly believable. If you are going to use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden in the middle of text. All the Lorem Ipsum generators on the Internet tend to repeat predefined chunks as necessary.
        </p>
        <span class="desc">
        Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore.
      </span>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      backImage: '',
      errored: false
    }
  },
  mounted() {
    if ("image" in localStorage) {
      console.log('none')
      this.backImage = localStorage.getItem("image");
    } else {
      axios.get('https://api.unsplash.com/photos/random',
          {
            params: {
              client_id: '3RYSfAoLvRvtXW58xiZm61yYa9bcdavNF9XO3CMHY3k',
            }
          }
      )
        .then(response => {
          this.backImage = response.data.urls.full
          localStorage.setItem("image", this.backImage);
        })
        .catch(error => {
          console.log(error)
          this.errored = true
        })
    }

  },
  methods: {
    // saveImage() {
    //   localStorage.setItem(this.backImage, this.backImage);
    // }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.fullBleed-wrap {
  display: flex;
  align-items: center;
  width: 100%;
  height: 740px;
  margin-top: 110px;
  padding: 0 80px;
  text-align: center;
  box-sizing: border-box;
  background-size: cover;
  background-position: center;
  .title {
    margin: 0;
    font-size: 24px;
    line-height: 1.5;
    letter-spacing: -0.36px;
    color: #fff;
    font-family: 'Montserrat';
    font-weight: bold;
  }
  .sub-title {
    margin: 0;
    padding: 23px 0 32px;
    font-size: 18px;
    line-height: 1.67;
    letter-spacing: -0.27px;
    color: rgba(255, 255, 255, 0.8);
    border-bottom: 1px solid rgba(255, 255, 255, 0.5);
    font-family: 'Montserrat';
    font-weight: normal;
  }
  .desc {
    display: block;
    margin-top: 32px;
    font-size: 14px;
    line-height: 1.57;
    letter-spacing: -0.21px;
    color: rgba(255, 255, 255, 0.6);
    font-family: 'Montserrat';
    font-weight: normal;
  }
}
@media (max-width: 767px) {
  .fullBleed-wrap {
    height: auto;
    margin-top: 50px;
    padding: 25px;
  }
}
</style>
