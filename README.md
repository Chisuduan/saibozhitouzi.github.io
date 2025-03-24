# saibozhitouzi.github.io
<!DOCTYPE html>
<html lang="zh-CN">

<head>
    <!-- 设置字符编码为 UTF - 8 -->
    <meta charset="UTF-8">
    <!-- 设置视口，确保在不同设备上有良好的显示效果 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 网页标题 -->
    <title>中国赛博掷骰子网</title>
    <style>
        /* 设置页面整体字体和居中对齐，背景颜色 */
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f9;
        }

        /* 设置标题的颜色 */
        h1 {
            color: #333;
        }

        /* 设置按钮样式，包括内边距、字体大小、背景颜色、文字颜色、边框和圆角等 */
        button {
            padding: 10px 20px;
            font-size: 16px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 20px;
        }

        /* 设置禁用状态下按钮的样式，背景颜色和光标样式 */
        button:disabled {
            background-color: #ccc;
            cursor: not - allowed;
        }

        /* 设置显示掷骰结果区域的字体大小和颜色 */
        #result {
            font-size: 36px;
            color: #333;
            margin-top: 20px;
        }
    </style>
</head>

<body>
    <!-- 网页标题 -->
    <h1>中国赛博掷骰子网</h1>
    <!-- 开始按钮 -->
    <button id="startButton" onclick="startRolling()">开始</button>
    <!-- 显示掷骰结果的区域 -->
    <div id="result"></div>
    <!-- 显示倒计时的区域 -->
    <div id="countdown"></div>

    <script>
        // 获取开始按钮元素
        const startButton = document.getElementById('startButton');
        // 获取显示结果的元素
        const resultDiv = document.getElementById('result');
        // 获取显示倒计时的元素
        const countdownDiv = document.getElementById('countdown');
        // 倒计时时间，单位为秒
        let countdown = 10;
        // 定时器变量
        let timer;

        // 开始掷骰的函数
        function startRolling() {
            // 禁用开始按钮，防止在倒计时期间再次点击
            startButton.disabled = true;
            // 生成 1 - 6 之间的随机整数
            const randomNumber = Math.floor(Math.random() * 6) + 1;
            // 显示掷骰结果
            resultDiv.textContent = randomNumber;
            // 启动倒计时
            startCountdown();
        }

        // 开始倒计时的函数
        function startCountdown() {
            countdown = 10;
            countdownDiv.textContent = `下次掷骰还需 ${countdown} 秒`;
            // 设置定时器，每秒执行一次更新倒计时的函数
            timer = setInterval(updateCountdown, 1000);
        }

        // 更新倒计时的函数
        function updateCountdown() {
            countdown--;
            if (countdown > 0) {
                // 显示剩余倒计时时间
                countdownDiv.textContent = `下次掷骰还需 ${countdown} 秒`;
            } else {
                // 倒计时结束，清除定时器
                clearInterval(timer);
                // 启用开始按钮
                startButton.disabled = false;
                // 清空倒计时显示
                countdownDiv.textContent = '';
            }
        }
    </script>
</body>

</html>    
