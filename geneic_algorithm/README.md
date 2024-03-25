# Genetic algorithm
it is an algorithm based on local search and greedy technique.
## 流程/想法:
### 1. 讀取問題所需檔案及轉換格式(本code運行於colab上，且相關檔案至於雲端上，因此描述和使用方式不同)
### 2. 定義希望所求解的問題(for 1 generation):
本問題為0/1 knapsacks problem, 原始的問題定義function(for profits in pack):
$$f(x)=\sum_{k=1}^n x_k v_k=profit \$$  

$$f(x)=\sum_{k=1}^n x_k v_k\$$

$$x_k=\begin{cases}
 1, &item_k&be&chosed \\
 0, &item_k&is't&chosed 
 \end{cases}\$$

 (x此處為一長度為n，代表物品取或不取的tuple)  
根據所給定的capcity，進一步限制function所允許的可行解區域，進一步我們設計以下function,g(x),當輸入的物品選取組合的總重超過capcity我們定義結果為0(因為本問題為最佳化問題)，否則結果為選取物品價值總和(對應到程式中的knapsack_sign_extend_func)   

$$g(x) = \begin{dcases}
    \sum_{k=1}^{n} x_{k} v_{k}  & \text{if $\sum_{k=1}^{n} x_{k} w_{k} \leq capcity $}\\
    0 & \text{otherwise}
\end{dcases}\$$

### 3. 每次iteration的操作
