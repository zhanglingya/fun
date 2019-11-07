<template>
  <div class="container">
    <div class="main">
      <div class="top">
        <div class="head">
          <p class="head-left">cold jokes</p>
          <p class="head-middle">check your fortune</p>
          <div class="head-right">
            <img src="~assets/weather.png" />
            <p>{{weather}}</p>
          </div>
        </div>
      </div>

      <div class="foot">
        <div class="bottom">
          <div>
            <p>Believe in yourself</p>
          </div>
        </div>
      </div>
    </div>
    <div class="middle">
      <div class="circle">
        <div class="word">
          <p class="word-top">try your best</p>
          <p class="word-bottom">come on</p>
        </div>
      </div>
    </div>
    <div class="slipe">
      <div class="constellation">
        <p>{{summary}}</p>
      </div>
      <div class="fortune">
        <p>Constellation</p>
      </div>
      <div class="news">
        <p>{{news}}</p>
      </div>
    </div>

    <div class="img">
      <ul class="ul">
        <li class="li">
          <img src="~assets/tomato.jpg" />
        </li>
        <li>
          <img src="~assets/tomato.jpg" />
        </li>
        <li>
          <img src="~assets/tomato.jpg" />
        </li>
      </ul>
      <a href="javascript:;" style="left:10px;" class="a"></a>
      <a href="javascript:;" style="right:10px;" class="a">></a>
    </div>
    <div class="img1"></div>
    <div class="img2"></div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      weather: "",
      summary: "",
      news: "",
      imgList: [
        {
          url: "~assets/tomato.jpg"
        },
        {
          url: "~assets/avocado.jpg"
        }
      ]
    };
  },
  methods: {},
  mounted() {
    /*function getWeather() {
      return axios.get("/simpleWeather/query", {
        params: {
          city: "无锡",
          key: "07b8c29baabc67b6b42ad69f9af84025"
        }
      });
    }
    function getConstellation() {
      return axios.get("/constellation/getAll", {
        params: {
          key: "48cedc691d1497e976cf1ee50a0614de",
          consName: "天蝎座",
          type: "tomorrow"
        }
      });
    }
    function getNews() {
      return axios.get("/toutiao/index", {
        params: {
          key: "e20c37a878aba2620a1bf61e546ce432",
          type: "shishang"
        }
      });
    }
    axios.all([getWeather(), getConstellation(), getNews() ])
     .then(axios.spread((weather, constellation, news)=> { 
        this.weather =weather.data.result.realtime.info;
        this.summary = constellation.data.summary;
        this.news = news.data.result.data[1].title;
        
      })
    )
    */
    window.addEventListener("load", function() {
      console.log("sss");
      var oDiv = document.getElementById("img");
      var oUl = oDiv.getElementById("ul")[0];
      var aLi = oUl.getElementById("li");
      var aA = oDiv.getElementById("a");
      var iSpeed = 1; //正左负右
      var timer = null;
      //计算ul的宽为所有li的宽的和;
      oUl.innerHTML += oUl.innerHTML + oUl.innerHTML;
      oUl.style.width = aLi[0].offsetWidth * aLi.length + "px";
      function Slider() {
        if (oUl.offsetLeft < -oUl.offsetWidth / 2) {
          oUl.style.left = 0;
        } else if (oUl.offsetLeft > 0) {
          oUl.style.left = -oUl.offsetWidth / 2 + "px";
        }
        oUl.style.left = oUl.offsetLeft - iSpeed + "px"; //正负为方向
      }
      timer = setInterval(Slider, 30);
      aA[0].onclick = function() {
        iSpeed = 1; //控制速度的正负
      };
      aA[1].onclick = function() {
        iSpeed = -1;
      };
      oDiv.onmouseover = function() {
        clearInterval(timer);
      };
      oDiv.onmouseout = function() {
        timer = setInterval(Slider, 30);
      };
    });
  }
};
</script>