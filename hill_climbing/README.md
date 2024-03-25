# Hill climbing algorithm
it is an algorithm based on local search and greedy technique.
## 流程/想法:
### 1. 讀取問題所需檔案及轉換格式(本code運行於colab上，且相關檔案至於雲端上，因此描述和使用方式不同)
### 2. 定義希望所求解的問題(for 1 iteration):
本問題為0/1 knapacks problem, 原始的問題定義function(for profits in pack):
$$f(x)=\sum_{k=1}^n x_k v_k=profit \$$  

$$f(x)=\sum_{k=1}^n x_k v_k\$$

$$x_k=\begin{cases}
 1, &item_k&be&chosed \\
 0, &item_k&is't&chosed 
 \end{cases}\$$

 (x此處為一長度為n，代表物品取或不取的tuple)  
根據所給定的capcity，進一步限制function所允許的可行解區域，進一步我們設計以下function, g(x)  

$$g(x)=\begin{case}
f(x), \sum_{k=1}^n x_k w_k > 0\ \\
0, \sum_{k=1}^n x_k w_k <0\
end{cases}\$$
在一次的iteration中，我們希望針對當前解，找出是否能夠藉由一次移動(climbing)來找到一個更好的解


