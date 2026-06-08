# m-and-n
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gửi Người Tôi Thương 💕</title>
    <style>
        /* Toàn bộ giao diện màu hồng pastel Hello Kitty */
        :root {
            --pink-bg: #FFE5EC;
            --pink-card: #FFC2D1;
            --pink-dark: #FB6F92;
            --pink-light: #FFEBF0;
        }

        body {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--pink-bg);
            color: #4a4a4a;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* Hình nền Hello Kitty ẩn nhẹ phía sau */
        body::before {
            content: "";
            position: fixed;
            top: 10px;
            right: 10px;
            width: 80px;
            height: 80px;
            background: url('https://i.pinimg.com/originals/a0/78/3e/a0783e1577908b981600f72295551ec4.png') no-repeat center/contain;
            opacity: 0.6;
            pointer-events: none;
        }

        h1 {
            color: var(--pink-dark);
            margin-top: 30px;
            text-shadow: 2px 2px #fff;
            font-size: 2rem;
            text-align: center;
        }

        /* Khu vực 3 bức thư */
        .letters-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-top: 40px;
            z-index: 10;
        }

        .envelope {
            width: 100px;
            height: 80px;
            background-color: var(--pink-card);
            border-radius: 5px;
            position: relative;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: transform 0.3s, background-color 0.3s;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            color: white;
            font-size: 1.2rem;
        }

        /* Nắp bức thư */
        .envelope::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 50px solid transparent;
            border-right: 50px solid transparent;
            border-top: 40px solid var(--pink-dark);
            border-radius: 5px 5px 0 0;
            transform-origin: top;
            transition: transform 0.3s;
            z-index: 2;
        }

        .envelope:hover {
            transform: scale(1.1) translateY(-5px);
            background-color: var(--pink-dark);
        }

        /* Nội dung chi tiết hiển thị bên dưới */
        .content-container {
            margin-top: 40px;
            width: 90%;
            max-width: 500px;
            min-height: 300px;
            z-index: 10;
            margin-bottom: 50px;
        }

        .content-box {
            background: white;
            border: 3px solid var(--pink-card);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.05);
            display: none;
            animation: fadeIn 0.5s ease-in-out forwards;
            text-align: center;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .active {
            display: block;
        }

        /* Thư 1: Ảnh bọn mình */
        .img-couple {
            width: 100%;
            max-height: 350px;
            object-fit: cover;
            border-radius: 15px;
            border: 5px solid var(--pink-light);
        }

        /* Thư 2: Đĩa nhạc quay tròn */
        .music-box {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
        }

        .disc-container {
            position: relative;
            width: 150px;
            height: 150px;
        }

        .disc {
            width: 100%;
            height: 100%;
            background: #222;
            border-radius: 50%;
            border: 5px solid var(--pink-dark);
            animation: spin 4s linear infinite;
            animation-play-state: paused;
            object-fit: cover;
        }

        /* Lỗ nhỏ giữa đĩa nhạc */
        .disc-container::after {
            content: "";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 25px;
            height: 25px;
            background-color: white;
            border-radius: 50%;
            border: 2px solid #222;
        }

        @keyframes spin {
            100% { transform: rotate(360deg); }
        }

        audio {
            width: 100%;
            margin-top: 10px;
        }

        /* Thư 3: Tâm tư dài */
        .love-letter {
            font-family: 'Dancing Script', cursive, sans-serif;
            font-size: 1.15rem;
            line-height: 1.6;
            text-align: left;
            white-space: pre-line;
            color: #555;
            background: var(--pink-light);
            padding: 15px;
            border-radius: 10px;
        }

        /* Hiệu ứng trái tim khi click vào màn hình */
        .heart-click {
            position: absolute;
            font-size: 24px;
            color: var(--pink-dark);
            pointer-events: none;
            animation: flyUp 1s ease-out forwards;
            z-index: 9999;
        }

        @keyframes flyUp {
            0% { transform: translate(-50%, -50%) scale(0.5); opacity: 1; }
            100% { transform: translate(-50%, -150px) scale(1.5); opacity: 0; }
        }
    </style>
</head>
<body>

    <h1>Gửi Em Bé Của Anh 🎀</h1>

    <div class="letters-container">
        <div class="envelope" onclick="openLetter(1)">✉ 1</div>
        <div class="envelope" onclick="openLetter(2)">✉ 2</div>
        <div class="envelope" onclick="openLetter(3)">✉ 3</div>
    </div>

    <div class="content-container">
        
        <div id="letter1" class="content-box">
            <h3 style="color: var(--pink-dark);">Khoảnh khắc của chúng mình 💕</h3>
            <img class="img-couple" src="https://images.unsplash.com/photo-1516589178581-6cd7833ae3b2?q=80&w=500" alt="Ảnh tụi mình">
            <p style="margin-top: 10px; font-style: italic;">"Nơi nào có em, nơi đó có hạnh phúc."</p>
        </div>

        <div id="letter2" class="content-box">
            <h3 style="color: var(--pink-dark);">Giai điệu tụi mình thích 🎵</h3>
            <div class="music-box">
                <div class="disc-container">
                    <img id="musicDisc" class="disc" src="https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?q=80&w=300" alt="Disc">
                </div>
                <audio id="myAudio" controls>
                    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
                    Trình duyệt của bạn không hỗ trợ phát nhạc công nghệ này rồi :<
                </audio>
                <p style="font-size: 0.9rem; color: #888;">(Bấm nút phát nhạc để đĩa xoay nhé!)</p>
            </div>
        </div>

        <div id="letter3" class="content-box">
            <h3 style="color: var(--pink-dark);">Tâm tư gửi đến em 📝</h3>
            <div class="love-letter">
                Chào em bé đáng yêu của anh,

                Anh viết những dòng này để nói với em rằng anh thương em nhiều lắm. Cảm ơn em đã xuất hiện và làm cho cuộc sống của anh tràn ngập những gam màu hồng ngọt ngào như Hello Kitty vậy đó! 

                Mong rằng chúng mình sẽ luôn nắm tay nhau đi qua thêm nhiều ngày tháng bình yên nữa nhé. Chúc em bé luôn cười thật tươi!

                Yêu em rất nhiều! 💖
            </div>
        </div>

    </div>

    <script>
        // Hàm đóng/mở nội dung các bức thư
        function openLetter(index) {
            // Ẩn tất cả các hộp thư trước
            for (let i = 1; i <= 3; i++) {
                document.getElementById('letter' + i).classList.remove('active');
            }
            // Hiện hộp thư được chọn
            document.getElementById('letter' + index).classList.add('active');
        }

        // Xử lý hiệu ứng đĩa nhạc quay khi nhấn Play
        const audio = document.getElementById('myAudio');
        const disc = document.getElementById('musicDisc');

        audio.onplay = function() {
            disc.style.animationPlayState = 'running';
        };
        audio.onpause = function() {
            disc.style.animationPlayState = 'paused';
        };

        // Hiệu ứng nhấp chuột ra trái tim bay lên
        document.addEventListener('click', function(e) {
            // Tạo một thẻ span chứa hình trái tim
            const heart = document.createElement('span');
            heart.classList.add('heart-click');
            heart.innerHTML = '💖'; // Hoặc các icon khác như 💕, 💝, 🐱
            
            // Đặt vị trí xuất hiện ngay tại đầu ngón tay/chuột click
            heart.style.left = e.pageX + 'px';
            heart.style.top = e.pageY + 'px';

            // Random kích thước một chút cho tự nhiên
            const size = Math.random() * 15 + 15; // từ 15px đến 30px
            heart.style.fontSize = size + 'px';

            document.body.appendChild(heart);

            // Tự động xóa trái tim sau 1 giây khi hiệu ứng kết thúc để tránh nặng máy
            setTimeout(() => {
                heart.remove();
            }, 1000);
        });
    </script>
</body>
</html>
