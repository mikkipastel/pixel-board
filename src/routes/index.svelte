<script lang="ts">
    const width = 32
    const height = 32

    export const board: string[][] = Array(height)
        .fill(0)
        .map(() => Array(width).fill(""))

    function paint(x: number, y: number, color: string) {
        board[y][x] = color
    }

    function clear() {
        board.forEach(row => {
            row.fill("")
        })
    }
</script>

<main>
    <div>
        <h1 class="text-center my-12">Pixel Art Board!</h1>

        <!-- color picker and clear board -->
        <div class="flex my-8">
            <button type="button" class="border-slate-500" on:click="{() => clear()}">clear</button>
        </div>
        
        <!-- board 32 x 32 -->
        {#each board as row, rowIndex}
            <div class="flex">
            {#each row as column, columnIndex}
                <div 
                    class="flex flex-row border h-4 w-4 border-gray-100" 
                    style={`background-color: #${column}; border-color: #${column}`}
                    on:click={() => 
                        paint(columnIndex, rowIndex, Math.floor(Math.random() * 16777215).toString(16))}
                >
                </div>
            {/each}
            </div>
        {/each}
        
        <!-- import, export, save, mint :P -->
    </div>
</main>
