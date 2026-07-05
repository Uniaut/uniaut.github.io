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

            <!-- Minimal Conway's Game of Life Simulation Section (Below Contact, No Title) -->
            <section class="pt-8 border-t border-gray-100">
                <div class="w-full bg-white rounded-2xl border border-gray-200 overflow-hidden shadow-sm my-6">
                    <canvas id="gameCanvas" class="block w-full cursor-crosshair bg-white"></canvas>
                </div>
            </section>
        </div>
    </div>
</article>

<script>
(function() {
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    // Grid size setup (Enlarged)
    const cellSize = 6;
    const cols = 120;
    const rows = 80;
    canvas.width = cols * cellSize;
    canvas.height = rows * cellSize;

    // States: 0 = dead, 1 = alive
    let board = Array(rows).fill(null).map(() => Array(cols).fill(0));
    let generation = 0;
    let timer = null;

    // Initialize with R-pentomino centered
    function loadRPentomino() {
        board = Array(rows).fill(null).map(() => Array(cols).fill(0));
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
        draw();
    }

    function countNeighbors(r, c) {
        let count = 0;
        for (let i = -1; i <= 1; i++) {
            for (let j = -1; j <= 1; j++) {
                if (i === 0 && j === 0) continue;
                const nr = r + i;
                const nc = c + j;
                // Bounded borders (no wrapping)
                if (nr >= 0 && nr < rows && nc >= 0 && nc < cols) {
                    if (board[nr][nc] > 0) count++;
                }
            }
        }
        return count;
    }

    function step() {
        const nextBoard = Array(rows).fill(null).map(() => Array(cols).fill(0));
        let population = 0;

        for (let r = 0; r < rows; r++) {
            for (let c = 0; c < cols; c++) {
                const neighbors = countNeighbors(r, c);
                const isAlive = board[r][c] > 0;

                if (isAlive) {
                    if (neighbors === 2 || neighbors === 3) {
                        nextBoard[r][c] = 1;
                        population++;
                    }
                } else {
                    if (neighbors === 3) {
                        nextBoard[r][c] = 1;
                        population++;
                    }
                }
            }
        }
        
        board = nextBoard;
        generation++;
        draw();

        // Auto restart if all cells die or generation reaches 1500 (after R-pentomino stabilizes)
        if (population === 0 || generation >= 1500) {
            loadRPentomino();
        }
    }

    function draw() {
        // Monochromatic white background
        ctx.fillStyle = '#ffffff';
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        // Very subtle grid lines
        ctx.strokeStyle = '#f1f5f9'; // Slate-100
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

        // Draw cells (Minimal slate-800 color)
        ctx.fillStyle = '#1e293b'; 
        for (let r = 0; r < rows; r++) {
            for (let c = 0; c < cols; c++) {
                if (board[r][c] > 0) {
                    ctx.fillRect(c * cellSize + 0.5, r * cellSize + 0.5, cellSize - 1, cellSize - 1);
                }
            }
        }
    }

    // Toggle cell on user click/drag (keep interactive)
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
    canvas.addEventListener('mouseup', () => {
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

    function runLoop() {
        step();
        timer = setTimeout(runLoop, 80); // Consistent normal speed (80ms)
    }

    // Start simulation immediately on page load
    loadRPentomino();
    runLoop();
})();
</script>
