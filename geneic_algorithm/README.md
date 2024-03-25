# Genetic algorithm
it is an algorithm based on local search and greedy technique.
## 流程/想法:
### 1. 讀取問題所需檔案及轉換格式(本code運行於colab上，且相關檔案至於雲端上，因此描述和使用方式不同)
### 2. 定義希望所求解的問題(for 1 generation):
本問題為0/1 knapsacks problem, 原始的問題定義function(for profits in pack):
$$f(x)=\sum_{k=1}^n x_k v_k=profit \$$  



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

### 3. 每次generation的操作:
在每一次的generation中會進行以下操作(except first generation):
#### 1. 查看上一世代的population中的最佳解是否比當前全局最佳解好，如果較好則更新全局最佳解
#### 2. 由上一代的population中篩選一定數目的較佳解(selection), 並隨機選取部分較差的解併作這一代的parent set
#### 3. 每一次隨機兩個parent set中pair-wise better的解，組合出新的子代併作這一代的population(population由上一代的parent set+子代組合而成)

在這邊，由於Genetic algorithm一樣有被困在local maxima的可能發生，採用了以下策略:  
1. point mutation
2. uniform cross over
3. allow some weaker parent pass selection  
值得注意的是，在我的嘗試中，point mutation似乎是一個較為有利/關鍵的方式去避免困在local maxima的方式
