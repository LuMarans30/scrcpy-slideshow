<template>
    <video style="padding: 20px;" id="scrcpy-webcam" autoplay muted></video>
    <button id="start-button">Start stream</button>
</template>

<script>
export default {
    mounted() {
        let button = document.getElementById('start-button');
        let video = document.getElementById('scrcpy-webcam');
        button.addEventListener('click', function() {
            const facingMode = "environment"; // Webcam frontale: "user", Altra webcam: "environment"
            const constraints = {
                audio: false,
                video: {
                    facingMode: facingMode,
                    width: { ideal: 2336 },
                    height: { ideal: 1080 },
                }
            };
            navigator.mediaDevices.getUserMedia(constraints)
                .then(stream => {
                    video.srcObject = stream;
                })
                .catch(error => {
                    console.error("Error accessing the camera", error);
                });
        })
    }
}
</script>

<style scoped>

#scrcpy-webcam {
    justify-content: center;
    align-items: center;
    display: flex;
    margin: 0 auto;
}

#start-button {
    background-color: #54B052;
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    border-radius: 10px;
}
</style>