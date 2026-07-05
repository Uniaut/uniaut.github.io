---
layout: default
title: About Me
---

<article>
    <div class="space-y-8">
        <div>
            <h1 class="text-4xl font-semibold leading-tight mb-6">안녕하세요, 최건우입니다.</h1>
            <div class="text-gray-600 leading-relaxed text-lg space-y-2">
                <p>삼성전자에서 Tizen, Tizen Lite의 Native App을 개발하고 있습니다.</p>
                <p>투자, 독서, 클라이밍을 취미라고 주장하고 다니고 있습니다.</p>
                <p>최근에는 모바일/임베디드 앱 개발 및 LLM Serving 최적화에 깊은 관심을 가지고 있습니다.</p>
            </div>
        </div>

        <div class="space-y-8 pt-8">
            <section>
                <h2 class="text-2xl font-semibold mb-4">Career</h2>
                <p class="text-gray-600 leading-relaxed">
                    2024.07 ~ 현재: 삼성전자 (S/W Engineer, Tizen/Tizen Lite Native App 개발)
                </p>
            </section>

            <!-- Game of Life Simulation Section -->
            <section class="pt-8 border-t border-gray-100">
                <h2 class="text-2xl font-semibold mb-2">Conway's Game of Life: R-pentomino</h2>
                <p class="text-gray-500 leading-relaxed text-sm mb-6">
                    단 5개의 세포로 시작하여 매우 길고 역동적인 변화(1,103세대 동안 무수한 글라이더와 잔해를 형성하며 성장)를 보여주는 라이프 게임(Game of Life)의 <strong>R-pentomino</strong> 시뮬레이터입니다. 
                    화면을 드래그하거나 탭하여 세포를 배치하고 생명의 탄생과 소멸을 조작해 보세요!
                </p>

                <div class="bg-gray-950 text-gray-100 p-6 rounded-2xl border border-gray-800 shadow-xl max-w-xl mx-auto my-6">
                    <!-- Visual Display -->
                    <div class="relative flex justify-center items-center bg-gray-900 rounded-xl overflow-hidden border border-gray-800">
                        <canvas id="gameCanvas" class="block w-full cursor-crosshair" style="aspect-ratio: 16/10;"></canvas>
                    </div>

                    <!-- Stats Bar -->
                    <div class="flex justify-between items-center my-4 text-xs font-mono px-1">
                        <div class="flex items-center space-x-2">
                            <span class="text-gray-500">Generation:</span>
                            <span id="genCount" class="text-emerald-400 font-bold text-sm">0</span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <span class="text-gray-500">Population:</span>
                            <span id="popCount" class="text-cyan-400 font-bold text-sm">0</span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <span class="text-gray-500">Speed:</span>
                            <span id="speedVal" class="text-indigo-400 font-semibold">Normal</span>
                        </div>
                    </div>

                    <!-- Controls -->
                    <div class="flex flex-wrap gap-2 justify-center pt-2 border-t border-gray-900">
                        <button id="btnPlay" class="flex-1 min-w-[70px] py-2 px-3 bg-emerald-600 hover:bg-emerald-500 active:bg-emerald-700 text-white rounded-lg text-xs font-semibold transition-all shadow-md focus:outline-none">
                            Start
                        </button>
                        <button id="btnStep" class="py-2 px-3 bg-gray-800 hover:bg-gray-700 active:bg-gray-900 text-gray-300 rounded-lg text-xs font-semibold transition-all focus:outline-none">
                            Step
                        </button>
                        <button id="btnReset" class="py-2 px-3 bg-gray-800 hover:bg-gray-700 active:bg-gray-900 text-gray-300 rounded-lg text-xs font-semibold transition-all focus:outline-none">
                            R-pentomino
                        </button>
                        <button id="btnRandom" class="py-2 px-3 bg-gray-800 hover:bg-gray-700 active:bg-gray-900 text-gray-300 rounded-lg text-xs font-semibold transition-all focus:outline-none">
                            Random
                        </button>
                        <button id="btnClear" class="py-2 px-3 bg-red-950/40 hover:bg-red-950/60 active:bg-red-950/80 text-red-400 rounded-lg text-xs font-semibold transition-all focus:outline-none">
                            Clear
                        </button>
                    </div>

                    <!-- Speed & Wrap Controls -->
                    <div class="flex flex-wrap justify-between items-center mt-4 text-xs text-gray-400 px-1 pt-2 border-t border-gray-900/60 gap-3">
                        <label class="flex items-center space-x-2 cursor-pointer select-none">
                            <input type="checkbox" id="chkWrap" class="rounded border-gray-800 bg-gray-900 text-indigo-600 focus:ring-indigo-600 focus:ring-offset-gray-950" checked>
                            <span>Wrap Borders (Toroidal)</span>
                        </label>
                        <div class="flex items-center space-x-2">
                            <span>Interval:</span>
                            <input type="range" id="rngSpeed" min="20" max="500" value="80" class="w-20 accent-indigo-500 bg-gray-800 h-1 rounded-lg appearance-none cursor-pointer">
                        </div>
                    </div>
                </div>
            </section>

            <!-- Contact Section -->
            <section class="pt-8 border-t border-gray-100">
                <h2 class="text-2xl font-semibold mb-4">연락처</h2>
                <ul class="space-y-2 text-gray-500">
                    <li>
                        <a href="mailto:{{ site.email }}" class="hover:text-black transition-colors">
                            {{ site.email }}
                        </a>
                    </li>
                    <li>
                        <a href="https://github.com/{{ site.github_username }}" target="_blank" class="hover:text-black transition-colors">
                            GitHub
                        </a>
                    </li>
                    <li>
                        <a href="https://www.linkedin.com/in/{{ site.linkedin_username }}" target="_blank" class="hover:text-black transition-colors">
                            LinkedIn
                        </a>
                    </li>
                </ul>
            </section>
        </div>
    </div>
</article>

<script>
(function() {
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    const btnPlay = document.getElementById('btnPlay');
    const btnStep = document.getElementById('btnStep');
    const btnReset = document.getElementById('btnReset');
    const btnRandom = document.getElementById('btnRandom');
    const btnClear = document.getElementById('btnClear');
    const chkWrap = document.getElementById('chkWrap');
    const rngSpeed = document.getElementById('rngSpeed');
    
    const genCountSpan = document.getElementById('genCount');
    const popCountSpan = document.getElementById('popCount');
    const speedValSpan = document.getElementById('speedVal');

    // Grid size setup
    const cellSize = 6;
    const cols = 90;
    const rows = 60;
    canvas.width = cols * cellSize;
    canvas.height = rows * cellSize;

    // States: 0 = dead, 1+ = alive with age
    let board = Array(rows).fill(null).map(() => Array(cols).fill(0));
    let generation = 0;
    let isRunning = false;
    let timer = null;

    // R-pentomino coordinates relative to center
    function loadRPentomino() {
        clearBoard();
        const cy = Math.floor(rows / 2);
        const cx = Math.floor(cols / 2);
        
        // R-pentomino pattern:
        //  . X X
        //  X X .
        //  . X .
        board[cy - 1][cx]     = 1;
        board[cy - 1][cx + 1] = 1;
        board[cy][cx - 1]     = 1;
        board[cy][cx]         = 1;
        board[cy + 1][cx]     = 1;

        generation = 0;
        updateUI();
        draw();
    }

    function clearBoard() {
        board = Array(rows).fill(null).map(() => Array(cols).fill(0));
        generation = 0;
        updateUI();
        draw();
    }

    function randomizeBoard() {
        for (let r = 0; r < rows; r++) {
            for (let c = 0; c < cols; c++) {
                board[r][c] = Math.random() < 0.25 ? 1 : 0;
            }
        }
        generation = 0;
        updateUI();
        draw();
    }

    function countNeighbors(r, c, toroidal) {
        let count = 0;
        for (let i = -1; i <= 1; i++) {
            for (let j = -1; j <= 1; j++) {
                if (i === 0 && j === 0) continue;
                let nr = r + i;
                let nc = c + j;
                
                if (toroidal) {
                    nr = (nr + rows) % rows;
                    nc = (nc + cols) % cols;
                    if (board[nr][nc] > 0) count++;
                } else {
                    if (nr >= 0 && nr < rows && nc >= 0 && nc < cols) {
                        if (board[nr][nc] > 0) count++;
                    }
                }
            }
        }
        return count;
    }

    function step() {
        const toroidal = chkWrap.checked;
        const nextBoard = Array(rows).fill(null).map(() => Array(cols).fill(0));
        let population = 0;

        for (let r = 0; r < rows; r++) {
            for (let c = 0; c < cols; c++) {
                const neighbors = countNeighbors(r, c, toroidal);
                const currentAge = board[r][c];

                if (currentAge > 0) {
                    if (neighbors === 2 || neighbors === 3) {
                        nextBoard[r][c] = Math.min(currentAge + 1, 10); // Keep alive, increment age
                        population++;
                    } else {
                        nextBoard[r][c] = 0; // Over/under population
                    }
                } else {
                    if (neighbors === 3) {
                        nextBoard[r][c] = 1; // Born
                        population++;
                    } else {
                        nextBoard[r][c] = 0;
                    }
                }
            }
        }
        
        board = nextBoard;
        generation++;
        updateUI();
        draw();

        // Auto pause if stabilized/empty
        if (population === 0 && isRunning) {
            pauseGame();
        }
    }

    // Color mapper based on cell age
    function getCellColor(age) {
        if (age === 1) return '#10b981'; // Emerald (Newly born)
        if (age === 2) return '#06b6d4'; // Cyan
        if (age === 3) return '#3b82f6'; // Blue
        if (age === 4) return '#6366f1'; // Indigo
        return '#8b5cf6'; // Violet (Stable old cells)
    }

    function draw() {
        ctx.fillStyle = '#111827'; // Dark slate-900 background
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        // Draw grid lines subtly
        ctx.strokeStyle = '#1f2937'; // gray-800
        ctx.lineWidth = 0.5;
        for (let r = 0; r <= rows; r++) {
            ctx.beginPath();
            ctx.moveTo(0, r * cellSize);
            ctx.lineTo(canvas.width, r * cellSize);
            ctx.stroke();
        }
        for (let c = 0; c <= cols; c++) {
            ctx.beginPath();
            ctx.moveTo(c * cellSize, 0);
            ctx.lineTo(c * cellSize, canvas.height);
            ctx.stroke();
        }

        // Draw cells
        for (let r = 0; r < rows; r++) {
            for (let c = 0; c < cols; c++) {
                const age = board[r][c];
                if (age > 0) {
                    ctx.fillStyle = getCellColor(age);
                    ctx.fillRect(c * cellSize + 0.5, r * cellSize + 0.5, cellSize - 1, cellSize - 1);
                }
            }
        }
    }

    function getPopulationCount() {
        let count = 0;
        for (let r = 0; r < rows; r++) {
            for (let c = 0; c < cols; c++) {
                if (board[r][c] > 0) count++;
            }
        }
        return count;
    }

    function updateUI() {
        genCountSpan.textContent = generation;
        popCountSpan.textContent = getPopulationCount();
        
        const speed = rngSpeed.value;
        if (speed <= 50) {
            speedValSpan.textContent = "Fast";
            speedValSpan.className = "text-red-400 font-semibold";
        } else if (speed >= 250) {
            speedValSpan.textContent = "Slow";
            speedValSpan.className = "text-amber-400 font-semibold";
        } else {
            speedValSpan.textContent = "Normal";
            speedValSpan.className = "text-indigo-400 font-semibold";
        }
    }

    // Toggle cell on click/drag
    function handleCanvasInteraction(e) {
        const rect = canvas.getBoundingClientRect();
        const scaleX = canvas.width / rect.width;
        const scaleY = canvas.height / rect.height;
        const x = (e.clientX - rect.left) * scaleX;
        const y = (e.clientY - rect.top) * scaleY;
        
        const c = Math.floor(x / cellSize);
        const r = Math.floor(y / cellSize);

        if (r >= 0 && r < rows && c >= 0 && c < cols) {
            board[r][c] = board[r][c] > 0 ? 0 : 1;
            updateUI();
            draw();
        }
    }

    let isDrawing = false;
    canvas.addEventListener('mousedown', (e) => {
        isDrawing = true;
        handleCanvasInteraction(e);
    });
    canvas.addEventListener('mousemove', (e) => {
        if (isDrawing) handleCanvasInteraction(e);
    });
    window.addEventListener('mouseup', () => {
        isDrawing = false;
    });

    canvas.addEventListener('touchstart', (e) => {
        isDrawing = true;
        const touch = e.touches[0];
        handleCanvasInteraction(touch);
        e.preventDefault();
    }, {passive: false});
    canvas.addEventListener('touchmove', (e) => {
        if (isDrawing) {
            const touch = e.touches[0];
            handleCanvasInteraction(touch);
        }
        e.preventDefault();
    }, {passive: false});
    canvas.addEventListener('touchend', () => {
        isDrawing = false;
    });

    // Game loop control
    function playGame() {
        if (isRunning) return;
        isRunning = true;
        btnPlay.textContent = "Pause";
        btnPlay.className = btnPlay.className.replace("bg-emerald-600 hover:bg-emerald-500 active:bg-emerald-700", "bg-amber-600 hover:bg-amber-500 active:bg-amber-700");
        runLoop();
    }

    function pauseGame() {
        if (!isRunning) return;
        isRunning = false;
        btnPlay.textContent = "Start";
        btnPlay.className = btnPlay.className.replace("bg-amber-600 hover:bg-amber-500 active:bg-amber-700", "bg-emerald-600 hover:bg-emerald-500 active:bg-emerald-700");
        clearTimeout(timer);
    }

    // Run calculation loop
    function runLoop() {
        if (!isRunning) return;
        step();
        timer = setTimeout(runLoop, rngSpeed.value);
    }

    btnPlay.addEventListener('click', () => {
        if (isRunning) {
            pauseGame();
        } else {
            playGame();
        }
    });

    btnStep.addEventListener('click', () => {
        pauseGame();
        step();
    });

    btnReset.addEventListener('click', () => {
        pauseGame();
        loadRPentomino();
    });

    btnRandom.addEventListener('click', () => {
        pauseGame();
        randomizeBoard();
    });

    btnClear.addEventListener('click', () => {
        pauseGame();
        clearBoard();
    });

    rngSpeed.addEventListener('input', () => {
        updateUI();
        if (isRunning) {
            clearTimeout(timer);
            runLoop();
        }
    });

    // Initialize with R-pentomino
    loadRPentomino();
})();
</script>
