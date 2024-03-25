# Hill climbing algorithm
it is an algorithm based on local search and greedy technique.
## 流程/想法:
### 1. 讀取問題所需檔案及轉換格式(本code運行於colab上，且相關檔案至於雲端上，因此描述和使用方式不同)
### 2. 定義希望所求解的問題(for 1 iteration):
本問題為0/1 knapsacks problem, 原始的問題定義function(for profits in pack):
$$f(x)=\sum_{k=1}^n x_k v_k=profit \$$  



$$x_k=\begin{cases}
 1, &item_k&be&chosed \\
 0, &item_k&is't&chosed 
 \end{cases}\$$

 (x此處為一長度為n，代表物品取或不取的tuple)  
根據所給定的capcity，進一步限制function所允許的可行解區域，進一步我們設計以下function,g(x),當輸入的物品選取組合的總重超過capcity我們定義結果為0(因為本問題為最佳化問題)，否則結果為選取物品價值總和(對應到程式中的knapsack_func_sign_extend)   

$$g(x) = \begin{dcases}
    \sum_{k=1}^{n} x_{k} v_{k}  & \text{if $\sum_{k=1}^{n} x_{k} w_{k} \leq capcity $}\\
    0 & \text{otherwise}
\end{dcases}\$$

### 3. 每次iteration的操作
在一次的iteration中，我們希望針對當前解，找出是否能夠藉由一次移動(climbing)來找到一個更好的解，因此我們在每一次的iteration，會先針對當前解(注意: 並不一定是當前最佳解)，的每一件物品執行一次選與不選的操作，因此所產生的所有neighbor只會有一件物品的選取狀況和當前解不同，接著我們找出在所有neighbor中，knapsack_sign_extend_func結果最好的點做為下一次iteration的可能起始點。由於Hill climbing algorithm是一種建立在local search and greedy的方法，0/1 knapsacks problem是一個並不具global optimize=local optimize特性的問題，也就是我們可能會因為random挑選的起始點而被困在local maxima無法找到一個更好的global maxima，因此在這邊我選用了random start作為一種策略，在每次iteration要結束前，我會隨機決定下一個iteration的起始點要是當前決定的當前解，或是一個隨機產生的可行解，並在每一次的iteration紀錄目前為止所找到的最佳解。 
### 4. result
![image](https://github.com/liuyihung/NCHU_CS_CH_hw0/blob/main/hill_climbing/hill_climbing%20result.png)
