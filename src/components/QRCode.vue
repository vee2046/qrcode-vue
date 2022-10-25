<script setup>
import { onMounted, ref } from 'vue';

/* 
QRCode.vue
var qrcode = new QRCode(document.getElementById("qrcode"), {
	text: "http://jindo.dev.naver.com/collie",
	width: 128,
	height: 128,
	colorDark : "#000000",
	colorLight : "#ffffff",
	correctLevel : QRCode.CorrectLevel.H
});

qrcode.clear(); // clear the code.
qrcode.makeCode("http://naver.com"); // make another code.
*/
const props = defineProps({
    text: {
        default: '',
        type:String,
    },
    domId: {
        default: 'qrcode',
        type:String,
    },
});
const imgData = ref('');
onMounted(() => {
    imgData.value = new QRCode(document.getElementById(props.domId), props.text);
})
</script>
<template>
    <div class="qrcode-container" :id="domId"></div>
</template>
<style>
.qrcode-container img{
    display: block;
    width: 100%;
}
</style>