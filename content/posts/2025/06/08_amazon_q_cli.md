---
title: "Amazon Q CLIでゲームを作成する"
date: "2025-06-08"
tags: ["amazon Q"]

---

[Amazon Q CLI でゲームを作ろう Tシャツキャンペーン](https://aws.amazon.com/jp/blogs/news/build-games-with-amazon-q-cli-and-score-a-t-shirt/)に乗っかってAmazon Q CLIを試してみた。

環境はWindows11でWSL2(Ubuntu)。

```
🤖 You are chatting with claude-3.7-sonnet

> Ebitengineを使ったゲームを作って
Ebitengineを使ったゲームを作りましょう。Ebitengineは、Goで書かれた2Dゲーム開発のためのシンプルなライブラリです。ま
ずは基本的なゲームを作成してみましょう。

まず、プロジェクトディレクトリを作成し、必要なパッケージをインストールします：


🛠️  Using tool: execute_bash
 ⋮
 ● I will run the following shell command:
mkdir -p ebiten-game && cd ebiten-game && go mod init ebiten-game
 ⋮
 ↳ Purpose: ゲームプロジェクトのディレクトリを作成し、Go moduleを初期化


Allow this action? Use 't' to trust (always allow) this tool for the session. [y/n/t]:

> t
bash: line 1: go: command not found

 ⋮
 ● Completed in 0.103s
すみません、Goがインストールされていないようです。まずはGoをインストールする必要があります。


🛠️  Using tool: execute_bash (trusted)
 ⋮
 ● I will run the following shell command:
which go || echo "Go is not installed"
 ⋮
 ↳ Purpose: Goがインストールされているか確認

Go is not installed

 ⋮
 ● Completed in 0.110s
Ebitengineを使ったゲームを作るには、まずGoをインストールする必要があります。Goをインストールした後、以下の手順でシ
ンプルなゲームを作成できます。

### Goのインストール方法

Linuxでは、以下のコマンドでGoをインストールできます：

bash
# Ubuntuの場合
sudo apt update
sudo apt install golang-go

# Fedoraの場合
sudo dnf install golang

# Arch Linuxの場合
sudo pacman -S go


### Goをインストールした後の手順

1. プロジェクトディレクトリを作成し、Go moduleを初期化
2. Ebitengineパッケージをインストール
3. シンプルなゲームコードを作成

### シンプルなゲームのコード例

Goをインストールした後、以下のようなコードでシンプルなゲームを作成できます：

go
package main

import (
        "image/color"
        "log"
        "math/rand"

        "github.com/hajimehoshi/ebiten/v2"
        "github.com/hajimehoshi/ebiten/v2/ebitenutil"
        "github.com/hajimehoshi/ebiten/v2/inpututil"
)

const (
        screenWidth  = 640
        screenHeight = 480
        playerSize   = 20
        enemySize    = 15
        enemyCount   = 5
)

type Game struct {
        playerX, playerY float64
        enemies          []enemy
        score            int
}

type enemy struct {
        x, y          float64
        speedX, speedY float64
}

func (g *Game) Update() error {
        // プレイヤーの移動
        if ebiten.IsKeyPressed(ebiten.KeyUp) {
                g.playerY -= 4
        }
        if ebiten.IsKeyPressed(ebiten.KeyDown) {
                g.playerY += 4
        }
        if ebiten.IsKeyPressed(ebiten.KeyLeft) {
                g.playerX -= 4
        }
        if ebiten.IsKeyPressed(ebiten.KeyRight) {
                g.playerX += 4
        }

        // 画面端の処理
        if g.playerX < 0 {
                g.playerX = 0
        }
        if g.playerX > screenWidth-playerSize {
                g.playerX = screenWidth - playerSize
        }
        if g.playerY < 0 {
                g.playerY = 0
        }
        if g.playerY > screenHeight-playerSize {
                g.playerY = screenHeight - playerSize
        }

        // 敵の移動
        for i := range g.enemies {
                g.enemies[i].x += g.enemies[i].speedX
                g.enemies[i].y += g.enemies[i].speedY

                // 画面端での反射
                if g.enemies[i].x <= 0 || g.enemies[i].x >= screenWidth-enemySize {
                        g.enemies[i].speedX = -g.enemies[i].speedX
                }
                if g.enemies[i].y <= 0 || g.enemies[i].y >= screenHeight-enemySize {
                        g.enemies[i].speedY = -g.enemies[i].speedY
                }

                // 衝突判定
                if g.playerX < g.enemies[i].x+enemySize &&
                        g.playerX+playerSize > g.enemies[i].x &&
                        g.playerY < g.enemies[i].y+enemySize &&
                        g.playerY+playerSize > g.enemies[i].y {
                        // 敵を新しい位置に
                        g.enemies[i].x = rand.Float64() * (screenWidth - enemySize)
                        g.enemies[i].y = rand.Float64() * (screenHeight - enemySize)
                        g.score++
                }
        }

        // Rキーでリセット
        if inpututil.IsKeyJustPressed(ebiten.KeyR) {
                g.init()
        }

        return nil
}

func (g *Game) Draw(screen *ebiten.Image) {
        // 背景
        screen.Fill(color.RGBA{40, 40, 60, 255})

        // プレイヤー
        ebitenutil.DrawRect(screen, g.playerX, g.playerY, playerSize, playerSize, color.RGBA{0, 255, 0, 255})

        // 敵
        for _, e := range g.enemies {
                ebitenutil.DrawRect(screen, e.x, e.y, enemySize, enemySize, color.RGBA{255, 0, 0, 255})
        }

        // スコア表示
        ebitenutil.DebugPrint(screen, "Score: "+string(rune('0'+g.score)))
}

func (g *Game) Layout(outsideWidth, outsideHeight int) (int, int) {
        return screenWidth, screenHeight
}

func (g *Game) init() {
        g.playerX = screenWidth / 2
        g.playerY = screenHeight / 2
        g.score = 0
        g.enemies = make([]enemy, enemyCount)

        for i := range g.enemies {
                g.enemies[i] = enemy{
                        x:      rand.Float64() * (screenWidth - enemySize),
                        y:      rand.Float64() * (screenHeight - enemySize),
                        speedX: (rand.Float64()*2 - 1) * 2,
                        speedY: (rand.Float64()*2 - 1) * 2,
                }
        }
}

func main() {
        ebiten.SetWindowSize(screenWidth, screenHeight)
        ebiten.SetWindowTitle("Simple Ebiten Game")

        game := &Game{}
        game.init()

        if err := ebiten.RunGame(game); err != nil {
                log.Fatal(err)
        }
}


このゲームは、緑色の四角（プレイヤー）を矢印キーで動かして、赤い四角（敵）に当たるとスコアが増えるシンプルなもので
す。Rキーを押すとゲームをリセットできます。

Goをインストールした後、以下のコマンドでEbitengineをインストールし、ゲームを実行できます：

bash
go get github.com/hajimehoshi/ebiten/v2
go run main.go


Goのインストールが完了したら、お知らせください。その後、詳細な手順でゲーム作成をサポートします。

>
```

goをインストールして再実行

```
> Ebitengineを使ったゲームを作って
Ebitengineを使ったゲームを作りましょう。Ebitengineは、Goで書かれた2Dゲーム開発用のライブラリです。まずは、基本的な
プロジェクトを作成していきましょう。

まず、現在のディレクトリを確認します。


🛠️  Using tool: execute_bash (trusted)
 ⋮
 ● I will run the following shell command: pwd
 ⋮
 ↳ Purpose: 現在のディレクトリを確認

/home/umemak/q

 ⋮
 ● Completed in 0.1s
では、Ebitengineを使った簡単なゲームプロジェクトを作成します。まず、必要なディレクトリとファイルを作成しましょう。


🛠️  Using tool: execute_bash
 ⋮
 ● I will run the following shell command:
mkdir -p ebiten-game && cd ebiten-game && go mod init ebiten-game
 ⋮
 ↳ Purpose: Goのモジュールを初期化


Allow this action? Use 't' to trust (always allow) this tool for the session. [y/n/t]:

> t
go: creating new go.mod: module ebiten-game

 ⋮
 ● Completed in 0.202s



🛠️  Using tool: execute_bash (trusted)
 ⋮
 ● I will run the following shell command:
cd ebiten-game && go get github.com/hajimehoshi/ebiten/v2
 ⋮
 ↳ Purpose: Ebitengineをインストール

go: downloading github.com/hajimehoshi/ebiten/v2 v2.8.8
go: downloading github.com/hajimehoshi/ebiten v1.12.12
go: downloading github.com/ebitengine/gomobile v0.0.0-20240911145611-4856209ac325
go: downloading golang.org/x/sync v0.8.0
go: downloading github.com/ebitengine/hideconsole v1.0.0
go: downloading github.com/ebitengine/purego v0.8.0
go: downloading github.com/jezek/xgb v1.1.1
go: downloading golang.org/x/sys v0.25.0
go: added github.com/ebitengine/gomobile v0.0.0-20240911145611-4856209ac325
go: added github.com/ebitengine/hideconsole v1.0.0
go: added github.com/ebitengine/purego v0.8.0
go: added github.com/hajimehoshi/ebiten/v2 v2.8.8
go: added github.com/jezek/xgb v1.1.1
go: added golang.org/x/sync v0.8.0
go: added golang.org/x/sys v0.25.0

 ⋮
 ● Completed in 6.901s
それでは、簡単な四角形を動かすゲームを作成しましょう。以下のコードを作成します：


🛠️  Using tool: fs_write
 ⋮
 ● Path: /home/umemak/q/ebiten-game/main.go

+      1: package main
+      2:
+      3: import (
+      4:       "log"
+      5:       "math/rand"
+      6:
+      7:       "github.com/hajimehoshi/ebiten/v2"
+      8:       "github.com/hajimehoshi/ebiten/v2/ebitenutil"
+      9:       "github.com/hajimehoshi/ebiten/v2/inpututil"
+     10: )
+     11:
+     12: const (
+     13:       screenWidth  = 640
+     14:       screenHeight = 480
+     15:       playerSize   = 30
+     16: )
+     17:
+     18: // Game はゲームの状態を管理する構造体
+     19: type Game struct {
+     20:       playerX      float64
+     21:       playerY      float64
+     22:       playerSpeed  float64
+     23:       targetX      float64
+     24:       targetY      float64
+     25:       score        int
+     26:       targetActive bool
+     27: }
+     28:
+     29: // Update は毎フレーム呼ばれる更新処理
+     30: func (g *Game) Update() error {
+     31:       // プレイヤーの移動
+     32:       if ebiten.IsKeyPressed(ebiten.KeyUp) {
+     33:               g.playerY -= g.playerSpeed
+     34:       }
+     35:       if ebiten.IsKeyPressed(ebiten.KeyDown) {
+     36:               g.playerY += g.playerSpeed
+     37:       }
+     38:       if ebiten.IsKeyPressed(ebiten.KeyLeft) {
+     39:               g.playerX -= g.playerSpeed
+     40:       }
+     41:       if ebiten.IsKeyPressed(ebiten.KeyRight) {
+     42:               g.playerX += g.playerSpeed
+     43:       }
+     44:
+     45:       // 画面外に出ないように制限
+     46:       if g.playerX < 0 {
+     47:               g.playerX = 0
+     48:       }
+     49:       if g.playerX > screenWidth-playerSize {
+     50:               g.playerX = screenWidth - playerSize
+     51:       }
+     52:       if g.playerY < 0 {
+     53:               g.playerY = 0
+     54:       }
+     55:       if g.playerY > screenHeight-playerSize {
+     56:               g.playerY = screenHeight - playerSize
+     57:       }
+     58:
+     59:       // ターゲットがなければ新しいターゲットを生成
+     60:       if !g.targetActive {
+     61:               g.targetX = float64(rand.Intn(screenWidth - playerSize))
+     62:               g.targetY = float64(rand.Intn(screenHeight - playerSize))
+     63:               g.targetActive = true
+     64:       }
+     65:
+     66:       // ターゲットとの当たり判定
+     67:       if g.playerX < g.targetX+playerSize &&
+     68:               g.playerX+playerSize > g.targetX &&
+     69:               g.playerY < g.targetY+playerSize &&
+     70:               g.playerY+playerSize > g.targetY {
+     71:               g.score++
+     72:               g.targetActive = false
+     73:       }
+     74:
+     75:       // スペースキーでリセット
+     76:       if inpututil.IsKeyJustPressed(ebiten.KeySpace) {
+     77:               g.score = 0
+     78:       }
+     79:
+     80:       return nil
+     81: }
+     82:
+     83: // Draw は毎フレーム呼ばれる描画処理
+     84: func (g *Game) Draw(screen *ebiten.Image) {
+     85:       // プレイヤーの描画（青い四角）
+     86:       ebitenutil.DrawRect(screen, g.playerX, g.playerY, playerSize, playerSize, 0x0000FFFF)
+     87:
+     88:       // ターゲットの描画（赤い四角）
+     89:       if g.targetActive {
+     90:               ebitenutil.DrawRect(screen, g.targetX, g.targetY, playerSize, playerSize, 0xFF0000FF)
+     91:       }
+     92:
+     93:       // スコアとヘルプの表示
+     94:       ebitenutil.DebugPrint(screen, "Score: "+string(rune('0'+g.score)))
+     95:       ebitenutil.DebugPrintAt(screen, "矢印キー: 移動, スペース: リセット", 10, screenHeight-20)
+     96: }
+     97:
+     98: // Layout はウィンドウサイズを返す
+     99: func (g *Game) Layout(outsideWidth, outsideHeight int) (int, int) {
+    100:       return screenWidth, screenHeight
+    101: }
+    102:
+    103: func main() {
+    104:       ebiten.SetWindowSize(screenWidth, screenHeight)
+    105:       ebiten.SetWindowTitle("Simple Ebiten Game")
+    106:
+    107:       game := &Game{
+    108:               playerX:     screenWidth / 2,
+    109:               playerY:     screenHeight / 2,
+    110:               playerSpeed: 4,
+    111:       }
+    112:
+    113:       if err := ebiten.RunGame(game); err != nil {
+    114:               log.Fatal(err)
+    115:       }
+    116: }


Allow this action? Use 't' to trust (always allow) this tool for the session. [y/n/t]:

> t
Creating: /home/umemak/q/ebiten-game/main.go

 ⋮
 ● Completed in 0.0s



🛠️  Using tool: execute_bash (trusted)
 ⋮
 ● I will run the following shell command:
cd ebiten-game && go run main.go
 ⋮
 ↳ Purpose: ゲームを実行

# github.com/hajimehoshi/ebiten/v2/internal/glfw
In file included from ../../go/pkg/mod/github.com/hajimehoshi/ebiten/v2@v2.8.8/internal/glfw/native_linbsd.go:14:
./glfw3native_unix.h:105:12: fatal error: X11/Xlib.h: No such file or directory
  105 |   #include <X11/Xlib.h>
      |            ^~~~~~~~~~~~
compilation terminated.

 ⋮
 ● Completed in 6.524s
X11の依存関係が不足しているようです。必要なライブラリをインストールしましょう。


🛠️  Using tool: fs_write (trusted)
 ⋮
 ● Path: ebiten-game/main.go

  93, 93:       // スコアとヘルプの表示
- 94    :       ebitenutil.DebugPrint(screen, "Score: "+string(rune('0'+g.score)))
+     94:       ebitenutil.DebugPrint(screen, "Score: "+fmt.Sprintf("%d", g.score))
  95, 95:       ebitenutil.DebugPrintAt(screen, "矢印キー: 移動, スペース: リセット", 10, screenHeight-20)

Updating: ebiten-game/main.go

 ⋮
 ● Completed in 0.1s



🛠️  Using tool: fs_write (trusted)
 ⋮
 ● Path: ebiten-game/main.go

   1,  1: package main
   2,  2:
   3,  3: import (
+      4:       "fmt"
   4,  5:       "log"
   5,  6:       "math/rand"
   6,  7:
   7,  8:       "github.com/hajimehoshi/ebiten/v2"
   8,  9:       "github.com/hajimehoshi/ebiten/v2/ebitenutil"
   9, 10:       "github.com/hajimehoshi/ebiten/v2/inpututil"
  10, 11: )

Updating: ebiten-game/main.go

 ⋮
 ● Completed in 0.0s



🛠️  Using tool: execute_bash (trusted)
 ⋮
 ● I will run the following shell command:
sudo apt-get update && sudo apt-get install -y libx11-dev libxcursor-dev libxrandr-dev libxinerama-dev libxi-dev libgl1-mesa-dev libgl1-mesa-dev xorg-dev
 ⋮
 ↳ Purpose: X11の依存関係をインストール

[sudo] password for umemak:
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:4 https://download.docker.com/linux/ubuntu jammy InRelease
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
libxcursor-dev is already the newest version (1:1.2.0-2build4).
libxi-dev is already the newest version (2:1.8-1build1).
libxinerama-dev is already the newest version (2:1.1.4-3).
libxrandr-dev is already the newest version (2:1.5.2-1build1).
xorg-dev is already the newest version (1:7.7+23ubuntu2).
libgl1-mesa-dev is already the newest version (23.2.1-1ubuntu3.1~22.04.3).
libx11-dev is already the newest version (2:1.7.5-1ubuntu0.3).
0 upgraded, 0 newly installed, 0 to remove and 183 not upgraded.

 ⋮
 ● Completed in 91.324s



🛠️  Using tool: execute_bash (trusted)
 ⋮
 ● I will run the following shell command:
cd ebiten-game && go run main.go
 ⋮
 ↳ Purpose: ゲームを実行

# command-line-arguments
./main.go:87:76: cannot use 0x0000FFFF (constant 65535 of type int) as color.Color value in argument to ebitenutil.DrawRect: int does not implement color.Color (missing method RGBA)
./main.go:91:77: cannot use 0xFF0000FF (constant 4278190335 of type int) as color.Color value in argument to ebitenutil.DrawRect: int does not implement color.Color (missing method RGBA)

 ⋮
 ● Completed in 4.217s




🛠️  Using tool: fs_write (trusted)
 ⋮
 ● Path: ebiten-game/main.go

    1,   1: package main
    2,   2:
    3,   3: import (
    4,   4:     "fmt"
+        5:     "image/color"
    5,   6:     "log"
    6,   7:     "math/rand"
    7,   8:
    8,   9:     "github.com/hajimehoshi/ebiten/v2"
    9,  10:     "github.com/hajimehoshi/ebiten/v2/ebitenutil"
   10,  11:     "github.com/hajimehoshi/ebiten/v2/inpututil"
   11,  12: )
   12,  13:
   13,  14: const (
   14,  15:     screenWidth  = 640
   15,  16:     screenHeight = 480
   16,  17:     playerSize   = 30
   17,  18: )
   18,  19:
   19,  20: // Game はゲームの状態を管理する構造体
   20,  21: type Game struct {
   21,  22:     playerX      float64
   22,  23:     playerY      float64
   23,  24:     playerSpeed  float64
   24,  25:     targetX      float64
   25,  26:     targetY      float64
   26,  27:     score        int
   27,  28:     targetActive bool
   28,  29: }
   29,  30:
   30,  31: // Update は毎フレーム呼ばれる更新処理
   31,  32: func (g *Game) Update() error {
   32,  33:     // プレイヤーの移動
   33,  34:     if ebiten.IsKeyPressed(ebiten.KeyUp) {
   34,  35:             g.playerY -= g.playerSpeed
   35,  36:     }
   36,  37:     if ebiten.IsKeyPressed(ebiten.KeyDown) {
   37,  38:             g.playerY += g.playerSpeed
   38,  39:     }
   39,  40:     if ebiten.IsKeyPressed(ebiten.KeyLeft) {
   40,  41:             g.playerX -= g.playerSpeed
   41,  42:     }
   42,  43:     if ebiten.IsKeyPressed(ebiten.KeyRight) {
   43,  44:             g.playerX += g.playerSpeed
   44,  45:     }
   45,  46:
   46,  47:     // 画面外に出ないように制限
   47,  48:     if g.playerX < 0 {
   48,  49:             g.playerX = 0
   49,  50:     }
   50,  51:     if g.playerX > screenWidth-playerSize {
   51,  52:             g.playerX = screenWidth - playerSize
   52,  53:     }
   53,  54:     if g.playerY < 0 {
   54,  55:             g.playerY = 0
   55,  56:     }
   56,  57:     if g.playerY > screenHeight-playerSize {
   57,  58:             g.playerY = screenHeight - playerSize
   58,  59:     }
   59,  60:
   60,  61:     // ターゲットがなければ新しいターゲットを生成
   61,  62:     if !g.targetActive {
   62,  63:             g.targetX = float64(rand.Intn(screenWidth - playerSize))
   63,  64:             g.targetY = float64(rand.Intn(screenHeight - playerSize))
   64,  65:             g.targetActive = true
   65,  66:     }
   66,  67:
   67,  68:     // ターゲットとの当たり判定
   68,  69:     if g.playerX < g.targetX+playerSize &&
   69,  70:             g.playerX+playerSize > g.targetX &&
   70,  71:             g.playerY < g.targetY+playerSize &&
   71,  72:             g.playerY+playerSize > g.targetY {
   72,  73:             g.score++
   73,  74:             g.targetActive = false
   74,  75:     }
   75,  76:
   76,  77:     // スペースキーでリセット
   77,  78:     if inpututil.IsKeyJustPressed(ebiten.KeySpace) {
   78,  79:             g.score = 0
   79,  80:     }
   80,  81:
   81,  82:     return nil
   82,  83: }
   83,  84:
   84,  85: // Draw は毎フレーム呼ばれる描画処理
   85,  86: func (g *Game) Draw(screen *ebiten.Image) {
   86,  87:     // プレイヤーの描画（青い四角）
-  87     :     ebitenutil.DrawRect(screen, g.playerX, g.playerY, playerSize, playerSize, 0x0000FFFF)
+       88:     ebitenutil.DrawRect(screen, g.playerX, g.playerY, playerSize, playerSize, color.RGBA{0, 0, 255, 255})
   88,  89:
   89,  90:     // ターゲットの描画（赤い四角）
   90,  91:     if g.targetActive {
-  91     :             ebitenutil.DrawRect(screen, g.targetX, g.targetY, playerSize, playerSize, 0xFF0000FF)
+       92:             ebitenutil.DrawRect(screen, g.targetX, g.targetY, playerSize, playerSize, color.RGBA{255, 0, 0, 255})
   92,  93:     }
   93,  94:
   94,  95:     // スコアとヘルプの表示
   95,  96:     ebitenutil.DebugPrint(screen, "Score: "+fmt.Sprintf("%d", g.score))
   96,  97:     ebitenutil.DebugPrintAt(screen, "矢印キー: 移動, スペース: リセット", 10, screenHeight-20)
   97,  98: }
   98,  99:
   99, 100: // Layout はウィンドウサイズを返す
  100, 101: func (g *Game) Layout(outsideWidth, outsideHeight int) (int, int) {
  101, 102:     return screenWidth, screenHeight
  102, 103: }
  103, 104:
  104, 105: func main() {
  105, 106:     ebiten.SetWindowSize(screenWidth, screenHeight)
  106, 107:     ebiten.SetWindowTitle("Simple Ebiten Game")
  107, 108:
  108, 109:     game := &Game{
  109, 110:             playerX:     screenWidth / 2,
  110, 111:             playerY:     screenHeight / 2,
  111, 112:             playerSpeed: 4,
  112, 113:     }
  113, 114:
  114, 115:     if err := ebiten.RunGame(game); err != nil {
  115, 116:             log.Fatal(err)
  116, 117:     }
- 117     : }
+      118: }

Replacing: ebiten-game/main.go

 ⋮
 ● Completed in 0.0s



🛠️  Using tool: execute_bash (trusted)
 ⋮
 ● I will run the following shell command:
cd ebiten-game && go run main.go
 ⋮
 ↳ Purpose: ゲームを実行

XGB: conn.go:47: Could not get authority info: open /home/umemak/.Xauthority: no such file or directory
XGB: conn.go:48: Trying connection without authority info...
XGB: conn.go:47: Could not get authority info: open /home/umemak/.Xauthority: no such file or directory
XGB: conn.go:48: Trying connection without authority info...

```

{{< figure src="../08_game.png" title="生成されたゲーム" class="center" width="320" height="640" >}}

青い四角をカーソルキーで動かして、赤い四角にぶつけるとスコアが増えるゲームができた。

ゲームのウィンドウを閉じたら続きが

```

 ⋮
 ● Completed in 203.623s
Ebitengineを使った簡単なゲームを作成しました！このゲームは以下の特徴を持っています：

1. 青い四角形のプレイヤーを矢印キーで操作できます
2. 赤い四角形のターゲットを取ると得点が増えます
3. スペースキーでスコアをリセットできます

## ゲームの説明

• **操作方法**：
  • 矢印キー：プレイヤー（青い四角形）を上下左右に移動
  • スペースキー：スコアをリセット

• **ゲームの目的**：
  • 赤い四角形（ターゲット）を取ってスコアを増やす
  • ターゲットを取ると、新しいターゲットがランダムな位置に出現

## コードの説明

1. Game構造体：ゲームの状態（プレイヤーの位置、ターゲットの位置、スコアなど）を管理

2. Update関数：毎フレーム呼ばれる更新処理
   • キー入力の処理
   • プレイヤーの移動と画面外に出ないための制限
   • ターゲットとの当たり判定
   • スコアのリセット処理

3. Draw関数：毎フレーム呼ばれる描画処理
   • プレイヤーとターゲットの描画
   • スコアと操作方法の表示

4. Layout関数：ウィンドウサイズの設定

このゲームは基本的なものですが、Ebitengineの基本的な使い方を理解するのに役立ちます。さらに機能を追加したい場合は、
以下のような拡張が考えられます：

• 複数のターゲット
• 時間制限の追加
• 障害物の追加
• アニメーションの追加
• サウンドエフェクトの追加

何か特定の機能を追加したい場合は、お知らせください！

>
```

とりあえずここまでで30分かからないくらい（諸々インストールも含めて）。
X11の依存関係をインストールはCLI内でできたのに、goのインストールは一度CLIを終了させないといけなかったのが惜しい。
あとゲームの説明はゲーム起動する前に出してほしかった。

とはいえゲームエンジンを指定しただけで、何かしら作り出してくれるのはすばらしい。
