<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>3D Rotating Gallery</title>

<style>
body {
    margin: 0;
    background: radial-gradient(circle, #0f0f0f, #000000);
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    font-family: Arial, sans-serif;
}

.gallery {
    width: 300px;
    height: 300px;
    position: relative;
    transform-style: preserve-3d;
    animation: rotate 15s linear infinite;
}

.gallery img {
    position: absolute;
    width: 200px;
    height: 130px;
    object-fit: cover;
    border-radius: 12px;
    box-shadow: 0 10px 20px rgba(0,0,0,0.5);
    transition: transform 0.5s;
}

.gallery img:hover {
    transform: scale(1.2);
}

@keyframes rotate {
    from { transform: rotateY(0deg); }
    to { transform: rotateY(360deg); }
}

</style>
</head>

<body>

<div class="gallery" id="gallery"></div>

<script>
// You can replace these images with your own URLs
const images = [
    "https://picsum.photos/300/200?random=1",
    "https://picsum.photos/300/200?random=2",
    "https://picsum.photos/300/200?random=3",
    "https://picsum.photos/300/200?random=4",
    "https://picsum.photos/300/200?random=5",
    "https://picsum.photos/300/200?random=6",
];

const gallery = document.getElementById("gallery");
const radius = 300;

images.forEach((img, i) => {
    const element = document.createElement("img");
    element.src = img;
    const angle = (i / images.length) * (2 * Math.PI);
    const x = Math.cos(angle) * radius;
    const z = Math.sin(angle) * radius;
    element.style.transform = `translateX(${x}px) translateZ(${z}px)`;
    gallery.appendChild(element);
});
</script>

</body>
</html>
