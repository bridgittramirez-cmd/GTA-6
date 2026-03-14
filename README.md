<!DOCTYPE html>
<html>
<head>
    <title>GTA VI - HTML Edition</title>
    <style>
        body { margin: 0; overflow: hidden; background: #222; font-family: 'Arial', sans-serif; }
        canvas { display: block; background: #3a3a3a; }
        #ui { position: absolute; top: 20px; left: 20px; color: white; text-shadow: 2px 2px black; pointer-events: none; }
        .wanted { color: #ffff00; font-size: 24px; }
        #controls { position: absolute; bottom: 20px; left: 20px; color: #aaa; font-size: 12px; }
    </style>
</head>
<body>

<div id="ui">
    <div id="location">VICE CITY: SOUTH BEACH</div>
    <div id="money">$1,250,400</div>
    <div class="wanted" id="stars">Wanted: ★☆☆☆☆</div>
</div>

<div id="controls">WASD to Move | F to Enter/Exit Vehicle | Space to Handbrake</div>

<canvas id="gameCanvas"></canvas>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

// Game State
let player = { x: canvas.width/2, y: canvas.height/2, angle: 0, speed: 0, inVehicle: false, color: '#f00' };
let vehicle = { x: canvas.width/2 + 50, y: canvas.height/2 + 50, angle: 0, speed: 0, color: '#00f', width: 40, height: 20 };
let npcs = [{ x: 100, y: 100, angle: 0, speed: 1 }];

const keys = {};
window.addEventListener('keydown', e => { 
    keys[e.key.toLowerCase()] = true; 
    if(e.key.toLowerCase() === 'f') toggleVehicle();
});
window.addEventListener('keyup', e => keys[e.key.toLowerCase()] = false);

function toggleVehicle() {
    let dist = Math.hypot(player.x - vehicle.x, player.y - vehicle.y);
    if (dist < 50) player.inVehicle = !player.inVehicle;
}

function update() {
    // Movement Logic
    if (player.inVehicle) {
        if (keys['w']) vehicle.speed += 0.2;
        if (keys['s']) vehicle.speed -= 0.1;
        if (keys['a']) vehicle.angle -= 0.05;
        if (keys['d']) vehicle.angle += 0.05;
        
        vehicle.speed *= 0.98; // Friction
        vehicle.x += Math.cos(vehicle.angle) * vehicle.speed;
        vehicle.y += Math.sin(vehicle.angle) * vehicle.speed;
        
        // Pin player to vehicle
        player.x = vehicle.x;
        player.y = vehicle.y;
    } else {
        if (keys['w']) player.y -= 3;
        if (keys['s']) player.y += 3;
        if (keys['a']) player.x -= 3;
        if (keys['d']) player.x += 3;
    }

    draw();
    requestAnimationFrame(update);
}

function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    // Draw Road
    ctx.fillStyle = '#444';
    ctx.fillRect(0, canvas.height/2 - 100, canvas.width, 200);

    // Draw Vehicle
    ctx.save();
    ctx.translate(vehicle.x, vehicle.y);
    ctx.rotate(vehicle.angle);
    ctx.fillStyle = vehicle.color;
    ctx.fillRect(-vehicle.width/2, -vehicle.height/2, vehicle.width, vehicle.height);
    // Windshield
    ctx.fillStyle = 'lightblue';
    ctx.fillRect(5, -8, 10, 16);
    ctx.restore();

    // Draw Player (if not in vehicle)
    if (!player.inVehicle) {
        ctx.fillStyle = 'white';
        ctx.beginPath();
        ctx.arc(player.x, player.y, 8, 0, Math.PI * 2);
        ctx.fill();
    }
}

update();
</script>
</body>
</html>
