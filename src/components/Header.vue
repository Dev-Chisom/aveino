<template>
  <header class="content">
    <!-- <h1>AQUILA &nbsp; AVEINO</h1> -->
    <h1>{{ name }}</h1>
    <img src="../assets/images/aveon.png" class="img-1" alt="aveon" />
    <div class="socials">
      <i class="fab fa-instagram"></i>
      <i class="fab fa-twitter-square"></i>
      <i class="fab fa-snapchat-square"></i>
      <i class="fas fa-envelope-square"></i>
    </div>

    <nav>
      <ul>
        <li v-for="(list, index) in lists" :key="index">
          <span v-if="list.src">
            <img :src="list.src" alt="girl" />
          </span>
          <span v-else>
            <a href="">{{ list.name }}</a>
          </span>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Header',

  data() {
    return {
      name: '',
      twitter: '',
      snapchat: '',
      instagram: '',
      email: '',

      lists: [
        { id: 1, name: 'Home' },
        { id: 2, name: 'About' },
        { id: 3, name: '', src: './images/girl.png' },
        { id: 4, name: 'Gallery' },
        {
          name: 'Contact',
        },
      ],
    };
  },
  mounted() {
    axios
      .get('https://hirng-x2021.glitch.me/api')
      .then((response) => console.log(response.data))
      .then((data) => {
        this.info = data;
        this.name = data.name;
        this.twitter = 'https://twitter.com/' + data.social_media.twitter;
        this.snapchat =
          'https://www.snapchat.com/add/' + data.social_media.snapchat;
        this.instagram =
          'https://www.instagram.com/' + data.social_media.instagram;
        this.email = 'mailto:' + data.social_media.email;
        // console.log(data);
      });
  },
};
</script>

<style>
.content {
  position: relative;
}
.content h1 {
  text-align: center;
  font-size: 1.7rem;
  font-weight: 200;
  margin: 1.5rem;
  letter-spacing: 0.4rem;
}
.content .img-1 {
  display: block;
  margin: 3rem auto;
  transition: 0.4s ease-out;
  box-shadow: 10px 10px 2px 2px rgba(0, 0, 0, 0.3);
}
.content .img-1:hover {
  transform: translateY(20px);
}
ul {
  display: flex;
  align-items: center;
  justify-content: center;
  list-style: none;
  margin-top: 1.5rem;
}
a {
  text-decoration: none;
  color: #fff;
  padding: 2rem;
  font-weight: 300;
  text-transform: uppercase;
  letter-spacing: 0.3rem;
}
/* .model img {
  position: fixed;
  border-radius: 50%;
  position: absolute;
  bottom: -40px;
  right: 40rem;
  height: 100px;
  width: 100px;
  object-fit: cover;
} */
.socials {
  position: fixed;
  top: 220px;
  right: 10px;
  display: flex;
  flex-direction: column;
}
.socials i {
  padding: 0.5rem;
  font-size: 2rem;
}
</style>
