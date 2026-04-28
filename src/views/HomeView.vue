<template>
    <div>
        <vue-esign
            ref="esign"
            :width="800"
            :height="300"
            :isCrop="isCrop"
            :lineWidth="lineWidth"
            :lineColor="lineColor"
            :bgColor.sync="bgColor"
        />

        <button @click="handleReset">清空画板</button>

        <button @click="handleGenerate">生成图片3</button>
    </div>
</template>

<script>
export default {
    name: "App",
    data() {
        return {
            lineWidth: 3,

            lineColor: "#000000",

            bgColor: "",

            resultImg: "",

            isCrop: false,
        };
    },
    // created(){
    //   this._isMobile()
    // },
    mounted() {
        // this._isMobile()
    },
    methods: {
        handleReset() {
            this.$refs["esign"].reset(); //清空画布
        },

        handleGenerate() {
            this.$refs["esign"]
                .generate()
                .then((res) => {
                    this.resultImg = res; // 得到了签字生成的base64图片

                    // let imgFile = this.base64ImgtoFile(res, 'file') //得到文件格式
                    // console.log(imgFile)
                    const a = document.createElement("a");
                    a.href = res;
                    a.download = "签名.png";
                    a.click();
                    a.remove();
                })
                .catch((err) => {
                    // 没有签名，点击生成图片时调用

                    this.$message({
                        message: err + " 未签名！",

                        type: "warning",
                    });

                    alert(err); // 画布没有签字时会执行这里 'Not Signned'
                });
        },
        base64ImgtoFile(dataurl, filename = "file") {
            const arr = dataurl.split(",");
            const mime = arr[0].match(/:(.*?);/)[1];
            const suffix = mime.split("/")[1];
            const bstr = atob(arr[1]);
            let n = bstr.length;
            const u8arr = new Uint8Array(n);
            while (n--) {
                u8arr[n] = bstr.charCodeAt(n);
            }
            return new File([u8arr], `${filename}.${suffix}`, {
                type: mime,
            });
        },
    },
};
</script>
<style lang="scss" scoped>
// html,
// body,
// #app,
.banner {
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
    overflow: hidden;
}
.banner {
    background-image: url("../views/../assets/img/1689216752944.png");
    background-repeat: no-repeat;
    // background-size: 100% 100%;
    background-size: cover;
    .box {
        width: 80%;
        height: 70%;
        // height: 80%;
        // width: 1000px;
        // height: 640px;
        position: absolute;
        left: 0;
        top: 0;
        bottom: 0;
        right: 0;
        margin: auto;
        display: flex;
        justify-content: space-between;
        .left {
            background-color: #000000b2;
            width: 320px;
            overflow: auto;
            .banner1 {
                width: 100%;
            }
            .bott {
                width: 80%;
                padding: 10px 30px;
                margin: 0 auto;
            }
            .bott1,
            .bott2 {
                height: 45px;
                background-color: #30c2ca;
                display: flex;
                align-items: center;
                border-radius: 10px;
                padding: 10px 20px;
                color: white;
                font-weight: 700;
                white-space: nowrap;
                cursor: pointer;
                img {
                    width: 35px;
                    height: 35px;
                    margin-right: 10px;
                }
            }
            .erweimaBox {
                display: flex;
                justify-content: space-between;
                .erweima {
                    width: 48%;
                    display: flex;
                    flex-direction: column;
                    p {
                        padding: 5px 0;
                        margin: 0;
                        width: 100%;
                        border-radius: 0 0 10px 10px;
                        background-color: #637174;
                        text-align: center;
                        color: white;
                        font-size: 12px;
                    }
                    img {
                        width: 100%;
                        border-radius: 10px 10px 0 0;
                    }
                }
            }
            .botmP {
                padding: 10px 0;
                margin: 15px 0 0;
                width: 100%;
                border-radius: 10px;
                background-color: #637174;
                text-align: center;
                color: white;
                font-size: 12px;
            }
        }
        .right {
            width: 65%;
            display: flex;
            // align-items: flex-end;
            position: absolute;
            // left:30%;
            right: 0;
            bottom: 0;
            animation-name: example;
            animation-duration: 1s;
            .way {
                flex: 1;
                height: 30vh;
                margin: 0 3px;
                border-radius: 10px;
                background-color: #000000b2;
                display: flex;
                justify-content: center;
                align-items: center;
                cursor: pointer;
                img {
                    width: 60%;
                    height: 60%;
                }
            }
        }
        .rights {
            display: none;
        }
    }
}
@keyframes example {
    0% {
        right: 0px;
        bottom: -500px;
    }
    // 25%  {background-color:yellow; right:200px; top:0px;}
    // 50%  {background-color:blue; left:200px; top:200px;}
    // 75%  {background-color:green; left:0px; top:200px;}
    100% {
        right: 0px;
        bottom: 0px;
    }
}
</style>
