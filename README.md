            height: 180px;
        }

        .disc {
            width: 100%;
            height: 100%;
            background: #222;
            border-radius: 50%;
            border: 6px solid var(--pink-dark);
            animation: spin 5s linear infinite;
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
            width: 30px;
            height: 30px;
            background-color: white;
            border-radius: 50%;
            border: 3px solid #222;
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
            font-size: 1.1rem;
            line-height: 1.6;
            text-align: left;
            white-space: pre-line;
            color: #555;
            background: var(--pink-light);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 15px;
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
            <img class="img-couple" src="https://i.ibb.co/BVPbRcNm/1000006361.jpg" alt="Ảnh tụi mình xích đu">
            <p style="margin-top: 10px; font-style: italic;">"Nơi nào có em, nơi đó có hạnh phúc."</p>
        </div>

        <div id="letter2" class="content-box">
            <h3 style="color: var(--pink-dark);">Giai điệu tụi mình thích 🎵</h3>
            <div class="music-box">
                <div class="disc-container">
                    <img id="musicDisc" class="disc" src="https://i.ibb.co/4RdYLCLb/1000006263.jpg" alt="Disc">
                </div>
                <audio id="myAudio" controls>
                    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
                    Trình duyệt của bạn không hỗ trợ phát nhạc rồi :<
                </audio>
                <p style="font-size: 0.9rem; color: #888;">(Bấm nút phát nhạc để đĩa xoay nhé!)</p>
            </div>
        </div>

        <div id="letter3" class="content-box">
            <h3 style="color: var(--pink-dark);">Tâm tư gửi đến em 📝</h3>
            <div class="love-letter">
                Chào em bé đáng yêu của anh,

                Anh viết những dòng này để nói với em rằng anh thương em nhiều lắm. Cảm ơn em đã xuất hiện và làm cho cuộc sống của anh tràn ngập những gam màu hồng ngọt ngào như Hello Kitty vậy đó! 

                Mong rằng chúng mình sẽ luôn nắm tay nhau đi qua thêm nhiều ngày tháng bình yên, cùng nhau lưu giữ thật nhiều kỷ niệm đẹp của tuổi học trò nhé. Chúc em bé của anh luôn cười thật tươi!

                Yêu em rất nhiều! 💖
            </div>
            <img class="img-couple" src="https://i.ibb.co/608dSJPj/1000006259.png" alt="Em bé của anh" style="max-height: 320px;">
        </div>

    </div>

    <script>
        // Hàm đóng/mở nội dung các bức thư
        function openLetter(index) {
            for (let i = 1; i <= 3; i++) {
                document.getElementById('letter' + i).classList.remove('active');
            }
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
            const heart = document.createElement('span');
            heart.classList.add('heart-click');
            heart.innerHTML = '💖'; 
            
            heart.style.left = e.pageX + 'px';
            heart.style.top = e.pageY + 'px';

            const size = Math.random() * 15 + 15; 
            heart.style.fontSize = size + 'px';

            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 1000);
        });
    </script>
</body>
</html>
