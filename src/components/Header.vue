<template>
  <header class="content">
    <!-- <h1>AQUILA &nbsp; AVEINO</h1> -->
    <h1>{{ name }}</h1>
    <img src="../assets/images/aveon.png" class="img-1" alt="aveon" />
    <div class="socials">
      <a :href="instagram" target="_blank"><i class="fab fa-instagram"></i></a>
      <a :href="twitter" target="_blank"
        ><i class="fab fa-twitter-square"></i
      ></a>
      <a :href="snapchat" target="_blank"
        ><i class="fab fa-snapchat-square"></i
      ></a>
      <a :href="email" target="_blank"
        ><i class="fas fa-envelope-square"></i
      ></a>
    </div>

    <nav>
      <ul>
        <li class="mb" v-for="(list, index) in lists" :key="index">
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
        { id: 3, name: '', src: '/girl.png' },
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
      // .then((response) => console.log(response.data))
      .then(({ data }) => {
        console.log(data);
        this.info = data;
        this.name = data.name;
        this.twitter = 'https://twitter.com/' + data.social_media.twitter;
        this.snapchat =
          'https://www.snapchat.com/add/' + data.social_media.snapchat;
        this.instagram =
          'https://www.instagram.com/' + data.social_media.instagram;
        this.email = 'mailto:' + data.social_media.email;
      });
  },
};
</script>

<style>
.mb {
  margin-bottom: 1rem;
}
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
  box-shadow: 3px 3px 3px 6px rgba(0, 0, 0, 0.3);
  /* box-shadow: 10px 10px 2px 2px rgba(0, 0, 0, 0.3); */
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
nav a {
  text-decoration: none;
  color: #fff;
  padding: 1.5rem;
  font-weight: 300;
  text-transform: uppercase;
  letter-spacing: 0.2rem;
  position: relative;
}

nav a::after {
  bottom: -4px;
  content: '';
  display: block;
  height: 2px;
  left: 0;
  position: absolute;
  background: #fff;
  opacity: 0.6;
  transition: width 0.3s ease 0s, opacity 0.3s ease 0s;
  width: 0;
}

nav a:hover::after {
  width: 100%;
  opacity: 0.9;
}

.socials {
  position: fixed;
  top: 220px;
  right: 10px;
  display: flex;
  flex-direction: column;
}
.socials a {
  color: #fff;
  text-decoration: none;
  padding: 0.5rem;
  font-size: 2rem;
}
.socials a:hover {
  background-color: #fff;
  color: #bd0f4d;
}

.socials a:hover:after {
  transition: scale(1);
  opacity: 1;
}

@media screen and (max-width: 764px) {
  .content h1 {
    font-size: 1.2rem;
    margin: 1rem;
    letter-spacing: 0.3rem;
  }
  .content .img-1 {
    width: 50%;
  }

  ul {
    flex-direction: column;
    margin-top: 1rem;
  }
  nav a {
    padding-bottom: 1.5rem;
  }
  .socials {
    top: 180px;
  }
  .socials a {
    font-size: 1rem;
  }
}
</style>
