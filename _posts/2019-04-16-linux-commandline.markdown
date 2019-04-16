---
layout: post
title:  "Linux Commandline小工具"
date:   2019-04-16 22:49:59 +0800
categories: linux
---

# 在Commandline查看天氣

在快下班的時候，座位附近沒有窗戶，又想知道外面有沒有下雨，需不需要穿雨衣

這個時候通常有幾種選擇

 * 走到窗戶旁邊看一下
 * 用手機查看天氣的app
 * 用電腦網頁去氣象局網站
 * 直接問資淺的同事，請他幫你看

但不管哪一種，如果在terminal工作的話，或多或少都會中斷工作的進行，此時，我們只要在 bash 命令列下鍵入

```bash
curl wttr.in
```

就能看到現在所在位置的天氣（位置是根據你的IP去對應的)

<pre><font color="#8AE234"><b>➜  </b></font><font color="#34E2E2"><b>~</b></font> curl wttr.in
Weather report: Taipei, Taiwan

 <font color="#FFFF00">   \  /</font>       Partly cloudy
 <font color="#FFFF00"> _ /&quot;&quot;</font><font color="#BCBCBC">.-.    </font> <font color="#D7FF00">19</font> °C          
 <font color="#FFFF00">   \_</font><font color="#BCBCBC">(   ).  </font> <b>←</b> <font color="#FF8700">26</font> km/h      
 <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> 10 km          
               0.3 mm         
                                                       ┌─────────────┐                                                       
┌──────────────────────────────┬───────────────────────┤  Mon 15 Apr ├───────────────────────┬──────────────────────────────┐
│            Morning           │             Noon      └──────┬──────┘     Evening           │             Night            │
├──────────────────────────────┼──────────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Patchy rain po…│
│ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#D7FF00">19</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#D7FF00">20</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#AFFF00">18</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#AFFF00">16</font> °C          │
│ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>↙</b> <font color="#FFD700">19</font>-<font color="#FFAF00">22</font> km/h   │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>↙</b> <font color="#FFAF00">21</font>-<font color="#FF8700">24</font> km/h   │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>←</b> <font color="#FFD700">17</font>-<font color="#FFAF00">21</font> km/h   │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>←</b> <font color="#FFFF00">14</font>-<font color="#FFAF00">22</font> km/h   │
│ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 13 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 18 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 18 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 17 km          │
│ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.4 mm | 72%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.4 mm | 65%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.3 mm | 88%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.3 mm | 72%   │
└──────────────────────────────┴──────────────────────────────┴──────────────────────────────┴──────────────────────────────┘
                                                       ┌─────────────┐                                                       
┌──────────────────────────────┬───────────────────────┤  Tue 16 Apr ├───────────────────────┬──────────────────────────────┐
│            Morning           │             Noon      └──────┬──────┘     Evening           │             Night            │
├──────────────────────────────┼──────────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#BCBCBC">     .-.     </font> Light rain     │ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Patchy rain po…│
│ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#D7FF00">21</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#FFFF00">23</font>..<font color="#FFD700">25</font> °C      │ <font color="#BCBCBC">    (   ).   </font> <font color="#D7FF00">19</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#D7FF00">19</font> °C          │
│ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>→</b> <font color="#5FFF00">3</font>-<font color="#87FF00">4</font> km/h     │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>↘</b> <font color="#87FF00">5</font>-<font color="#AFFF00">7</font> km/h     │ <font color="#BCBCBC">   (___(__)  </font> <b>↘</b> <font color="#AFFF00">9</font>-<font color="#FFFF00">13</font> km/h    │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>↘</b> <font color="#AFFF00">9</font>-<font color="#FFFF00">14</font> km/h    │
│ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 13 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 13 km          │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 12 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 16 km          │
│ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 1.0 mm | 81%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 1.2 mm | 67%   │ <font color="#87AFFF">   ‘ ‘ ‘ ‘   </font> 0.9 mm | 69%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.7 mm | 82%   │
└──────────────────────────────┴──────────────────────────────┴──────────────────────────────┴──────────────────────────────┘
                                                       ┌─────────────┐                                                       
┌──────────────────────────────┬───────────────────────┤  Wed 17 Apr ├───────────────────────┬──────────────────────────────┐
│            Morning           │             Noon      └──────┬──────┘     Evening           │             Night            │
├──────────────────────────────┼──────────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ <font color="#FFFF00">    \   /    </font> Sunny          │ <font color="#FFFF00">    \   /    </font> Sunny          │ <font color="#FFFF00">   \  /</font>       Partly cloudy  │ <font color="#FFFF00">   \  /</font>       Partly cloudy  │
│ <font color="#FFFF00">     .-.     </font> <font color="#FFFF00">22</font>..<font color="#FFFF00">23</font> °C      │ <font color="#FFFF00">     .-.     </font> <font color="#FFD700">25</font>..<font color="#FFD700">26</font> °C      │ <font color="#FFFF00"> _ /&quot;&quot;</font><font color="#BCBCBC">.-.    </font> <font color="#FFFF00">23</font>..<font color="#FFD700">25</font> °C      │ <font color="#FFFF00"> _ /&quot;&quot;</font><font color="#BCBCBC">.-.    </font> <font color="#D7FF00">21</font> °C          │
│ <font color="#FFFF00">  ― (   ) ―  </font> <b>↙</b> <font color="#AFFF00">9</font>-<font color="#D7FF00">10</font> km/h    │ <font color="#FFFF00">  ― (   ) ―  </font> <b>↙</b> <font color="#FFFF00">13</font>-<font color="#FFFF00">15</font> km/h   │ <font color="#FFFF00">   \_</font><font color="#BCBCBC">(   ).  </font> <b>←</b> <font color="#FFFF00">13</font>-<font color="#FFFF00">15</font> km/h   │ <font color="#FFFF00">   \_</font><font color="#BCBCBC">(   ).  </font> <b>←</b> <font color="#D7FF00">12</font>-<font color="#FFFF00">15</font> km/h   │
│ <font color="#FFFF00">     `-’     </font> 19 km          │ <font color="#FFFF00">     `-’     </font> 20 km          │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> 20 km          │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> 20 km          │
│ <font color="#FFFF00">    /   \    </font> 0.1 mm | 52%   │ <font color="#FFFF00">    /   \    </font> 0.0 mm | 0%    │               0.0 mm | 0%    │               0.0 mm | 0%    │
└──────────────────────────────┴──────────────────────────────┴──────────────────────────────┴──────────────────────────────┘

Follow <span style="background-color:#06989A"><font color="#2E3436">@igor_chubin</font></span> for wttr.in updates
</pre>

我們能使用 bash alias 來設定天氣的指令，來設定短指令看天氣

```bash
echo "alias weather='curl wttr.in'" >> ~/.bashrc
source ~/.bashrc
```

之後在bash下鍵入`weather`，就會顯示現在的天氣囉

<pre><font color="#8AE234"><b>➜  </b></font><font color="#34E2E2"><b>~</b></font> weather
Weather report: Taipei, Taiwan

 <font color="#FFFF00">   \  /</font>       Partly cloudy
 <font color="#FFFF00"> _ /&quot;&quot;</font><font color="#BCBCBC">.-.    </font> <font color="#D7FF00">19</font> °C          
 <font color="#FFFF00">   \_</font><font color="#BCBCBC">(   ).  </font> <b>←</b> <font color="#FF8700">26</font> km/h      
 <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> 10 km          
               0.3 mm         
                                                       ┌─────────────┐                                                       
┌──────────────────────────────┬───────────────────────┤  Mon 15 Apr ├───────────────────────┬──────────────────────────────┐
│            Morning           │             Noon      └──────┬──────┘     Evening           │             Night            │
├──────────────────────────────┼──────────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Patchy rain po…│
│ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#D7FF00">19</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#D7FF00">20</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#AFFF00">18</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#AFFF00">16</font> °C          │
│ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>↙</b> <font color="#FFD700">19</font>-<font color="#FFAF00">22</font> km/h   │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>↙</b> <font color="#FFAF00">21</font>-<font color="#FF8700">24</font> km/h   │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>←</b> <font color="#FFD700">17</font>-<font color="#FFAF00">21</font> km/h   │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>←</b> <font color="#FFFF00">14</font>-<font color="#FFAF00">22</font> km/h   │
│ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 13 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 18 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 18 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 17 km          │
│ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.4 mm | 72%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.4 mm | 65%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.3 mm | 88%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.3 mm | 72%   │
└──────────────────────────────┴──────────────────────────────┴──────────────────────────────┴──────────────────────────────┘
                                                       ┌─────────────┐                                                       
┌──────────────────────────────┬───────────────────────┤  Tue 16 Apr ├───────────────────────┬──────────────────────────────┐
│            Morning           │             Noon      └──────┬──────┘     Evening           │             Night            │
├──────────────────────────────┼──────────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Light rain sho…│ <font color="#BCBCBC">     .-.     </font> Light rain     │ <font color="#FFFF00"> _`/&quot;&quot;</font><font color="#BCBCBC">.-.    </font> Patchy rain po…│
│ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#D7FF00">21</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#FFFF00">23</font>..<font color="#FFD700">25</font> °C      │ <font color="#BCBCBC">    (   ).   </font> <font color="#D7FF00">19</font> °C          │ <font color="#FFFF00">  ,\_</font><font color="#BCBCBC">(   ).  </font> <font color="#D7FF00">19</font> °C          │
│ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>→</b> <font color="#5FFF00">3</font>-<font color="#87FF00">4</font> km/h     │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>↘</b> <font color="#87FF00">5</font>-<font color="#AFFF00">7</font> km/h     │ <font color="#BCBCBC">   (___(__)  </font> <b>↘</b> <font color="#AFFF00">9</font>-<font color="#FFFF00">13</font> km/h    │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> <b>↘</b> <font color="#AFFF00">9</font>-<font color="#FFFF00">14</font> km/h    │
│ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 13 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 13 km          │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 12 km          │ <font color="#87AFFF">     ‘ ‘ ‘ ‘ </font> 16 km          │
│ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 1.0 mm | 81%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 1.2 mm | 67%   │ <font color="#87AFFF">   ‘ ‘ ‘ ‘   </font> 0.9 mm | 69%   │ <font color="#87AFFF">    ‘ ‘ ‘ ‘  </font> 0.7 mm | 82%   │
└──────────────────────────────┴──────────────────────────────┴──────────────────────────────┴──────────────────────────────┘
                                                       ┌─────────────┐                                                       
┌──────────────────────────────┬───────────────────────┤  Wed 17 Apr ├───────────────────────┬──────────────────────────────┐
│            Morning           │             Noon      └──────┬──────┘     Evening           │             Night            │
├──────────────────────────────┼──────────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ <font color="#FFFF00">    \   /    </font> Sunny          │ <font color="#FFFF00">    \   /    </font> Sunny          │ <font color="#FFFF00">   \  /</font>       Partly cloudy  │ <font color="#FFFF00">   \  /</font>       Partly cloudy  │
│ <font color="#FFFF00">     .-.     </font> <font color="#FFFF00">22</font>..<font color="#FFFF00">23</font> °C      │ <font color="#FFFF00">     .-.     </font> <font color="#FFD700">25</font>..<font color="#FFD700">26</font> °C      │ <font color="#FFFF00"> _ /&quot;&quot;</font><font color="#BCBCBC">.-.    </font> <font color="#FFFF00">23</font>..<font color="#FFD700">25</font> °C      │ <font color="#FFFF00"> _ /&quot;&quot;</font><font color="#BCBCBC">.-.    </font> <font color="#D7FF00">21</font> °C          │
│ <font color="#FFFF00">  ― (   ) ―  </font> <b>↙</b> <font color="#AFFF00">9</font>-<font color="#D7FF00">10</font> km/h    │ <font color="#FFFF00">  ― (   ) ―  </font> <b>↙</b> <font color="#FFFF00">13</font>-<font color="#FFFF00">15</font> km/h   │ <font color="#FFFF00">   \_</font><font color="#BCBCBC">(   ).  </font> <b>←</b> <font color="#FFFF00">13</font>-<font color="#FFFF00">15</font> km/h   │ <font color="#FFFF00">   \_</font><font color="#BCBCBC">(   ).  </font> <b>←</b> <font color="#D7FF00">12</font>-<font color="#FFFF00">15</font> km/h   │
│ <font color="#FFFF00">     `-’     </font> 19 km          │ <font color="#FFFF00">     `-’     </font> 20 km          │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> 20 km          │ <font color="#FFFF00">   /</font><font color="#BCBCBC">(___(__) </font> 20 km          │
│ <font color="#FFFF00">    /   \    </font> 0.1 mm | 52%   │ <font color="#FFFF00">    /   \    </font> 0.0 mm | 0%    │               0.0 mm | 0%    │               0.0 mm | 0%    │
└──────────────────────────────┴──────────────────────────────┴──────────────────────────────┴──────────────────────────────┘

Follow <span style="background-color:#06989A"><font color="#2E3436">@igor_chubin</font></span> for wttr.in updates
</pre>

# Commandline 瀏覽器

這次出於好奇試了 terminal 的瀏覽器 w3m，想試試看在terminal中如果可以直接上網，是否能夠增加工作效率

在 Debian/Ubuntu 上的安裝只要簡單地鍵入 

```bash
apt-get install -y w3m

# 如果想要顯示圖片的話可以再安裝
apt-get install -y w3m-img
```

至於使用的方式也很簡單，只要打`w3m <url>`，就能連去想要的網站

```bash
w3m https://www.google.com
```

出來的結果則是

<pre><b>搜尋</b> <font color="#3465A4">圖片</font> <font color="#3465A4">地圖</font> <font color="#3465A4">Play</font> <font color="#3465A4">YouTube</font> <font color="#3465A4">新聞</font> <font color="#3465A4">Gmail</font> <font color="#3465A4">雲端硬碟</font> <font color="#3465A4"><u style="text-decoration-style:single">更多</u></font><font color="#3465A4"> »</font>
<font color="#3465A4">網頁記錄</font> | <font color="#3465A4">設定</font> | <font color="#3465A4">登入</font>

                                                                        <font color="#4E9A06">Google</font>

                                             [<font color="#CC0000"><u style="text-decoration-style:single">                                                         </u></font>] <font color="#3465A4">進階搜尋語言工具</font>

                                                                <font color="#CC0000">[Google 搜尋][好手氣]</font>

                                                                Google 提供： <font color="#3465A4">English</font>
                                                   <font color="#3465A4">廣告服務商業解決方案Google 完全手冊Google.com.tw</font>

                                                              © 2019 - <font color="#3465A4">隱私權</font> - <font color="#3465A4">服務條款</font>
</pre>

剛開始使用的時候，最不熟悉地就是在瀏覽的時候應該怎麼操作，這邊列出一些熱鍵，幫助大家第一次使用就上手

## 熱鍵

 * \<shift\> + h: 大寫H，開啟說明，在裡面按下 / 可以搜尋想要關鍵字，按下\<shift\> + b 返回
 * \<shift\> + b: 大寫B，返回上一頁
 * /: 搜尋網頁內容，之後按下 n/N 往下尋找/往上尋找
 * j, k, h, l: 上下左右，習慣vim的人應該會很適應
 * 空白鍵: page down
 * b: page up
 * \<shift\> + j: 大寫J，向下一行
 * \<shift\> + k: 大寫K，向上一行
 * \<TAB\>: 下一個 link
 * \<ctrl\> + u: 上一個 link
 * \[: 頁面第一個 link
 * \]: 頁面最後一個 link
 * g: 頁面第一行
 * \<shift\> + g: 大寫G，頁面最後一行
 * \<ctrl\> + h: 歷史紀錄
 * s: 緩存的頁面，可以回到之前或之後的頁面

**參考資料**

 * [5 cool command lind tools](https://www.putorius.net/5-cool-command-line-tools.html)
