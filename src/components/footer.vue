<template>
  <footer class="page-footer font-small indigo">
    <div class="container text-center text-md-left">
      <div class="row py-5">
        <div class="col-md-4 mx-auto text-center justify-content-center">
          <h5 class="font-weight-bold text-uppercase my-3">購買方式解說</h5>
          <hr />
          <!-- <facebook /> -->
          <p class="text-left">WAP-D官網僅供展示 購買請前往社群連結，洽詢線上客服及門市</p>
          <p class="text-left">為了提供您最好的服務品質，建議可選擇【門市預約】。
但需要預約時間，以便提供造型服務、量身修改等服務。
(預約時間造型師24H內會與您聯繫，請留意來電)</p>
        </div>
        <!-- Grid column -->
        <div class="col-md-4 mx-auto text-center">
          <!-- Links -->
          <h5 class="font-weight-bold text-uppercase my-3">聯絡我們</h5>
          <hr />
          <ul class="list-unstyled">
            <li>
              <p>
                <font-awesome-icon :icon="['fas', 'map-marker']" size="1x" />台中市太平區太順路403號
              </p>
            </li>
            <li>
              <p>
                <font-awesome-icon :icon="['fas', 'phone']" size="1x" /> Dream man (04)23937584
              </p>
            </li>
                        <li>
              <p>
                <font-awesome-icon :icon="['fas', 'phone']" size="1x" /> Apex（04）22254702
              </p>
            </li>
            <!-- <li>
              <p>
                <font-awesome-icon :icon="['fas', 'envelope']" size="1x" />root@example.com
              </p>
            </li> -->
          </ul>
        </div>
        <div class="col-md-4 text-center">
          <h5 class="font-weight-bold text-uppercase my-3">社群連結</h5>
          <hr />
          <div class="row justify-content-center">
            <!-- <div>
              <a class="mr-4" href="#">
                <font-awesome-icon :icon="['fab', 'line']" size="3x" />
              </a>
            </div> -->
            <div>
              <a class="mr-4" href="https://www.instagram.com/dreamman0831/?hl=zh-tw">
                <font-awesome-icon :icon="['fab', 'instagram']" size="3x" />
              </a>
            </div>
            <div>
              <a
                class="mr-4"
                href="https://www.facebook.com/KGT-%E5%B0%8F%E5%BA%B5%E7%9A%84%E5%BA%97-405388429508237/"
                target="_blank"
              >
                <font-awesome-icon :icon="['fab', 'facebook-square']" size="3x" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- <div class="footer-copyright text-center py-3">
      © 2019 Copyright:
      <span>Caesar & Vivian & Eason</span>
    </div> -->
  </footer>
</template>
<script>
// import facebook from "./../components/facebook";
export default {
  components: {
    // facebook
  }
};
</script>
<style>
footer {
  background-color: white;
  color: rgb(125, 125, 125);
  font-size: 16px;
}

footer a {
  color: rgb(125, 125, 125);
  transition: all 0.5s;
}

footer a:hover {
  color: #3b1c15;
}
hr {
  background-color: #222;
}
.footer-copyright {
  background-color: #222;
}
</style>
