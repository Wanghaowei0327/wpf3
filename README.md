# WPF視窗飲料訂購系統ver 1
2026/9/23

## 本週進度

### WPF佈局元件：Grid

- Grid.RowDefinitions, Grid.ColumnDefinitions
- Grid.RowSpan, Grid.ColumnSpan

### WPF佈局元件：StackPanel

- Stack.Orientation：Vertical(垂直排列), Horizontal(水平排列)

### C#選擇結構：if-else, switch case, 三元運算子

### TextBox.TextChanged事件

### 透過事件來取得呼叫的元件：

```csharp
var targetTextBox = sender as TextBox;
var targetStackPanel = targetTextBox.Parent as StackPanel;
var targetNameLabel = targetStackPanel.Children[0] as Label;
```

### 將字串轉換成整數
```csharp
int.TryParse()
Convert.ToInt32()
```

# WPF視窗飲料訂購系統ver 2
2026/9/30

## 功能更新
1. 使用Slider避免使用者入數值錯誤
2. 加上RadioButton和CheckBox來記錄購買方式以及選購飲料品項
3. 將Slider和Label以資料繫結(data binding)連動
4. 使用Dictionary資料結構來儲存飲料品項和訂單內容
5. 動態取得使用者選取的訂單品項
6. 加上售價折扣算法

## 本週進度
### 輸入控制項：
- RadioButton 與 CheckBox：理解單選（GroupName）與複選／三態（IsThreeState）邏輯。
- Slider：學習數值範圍（Minimum / Maximum）、刻度控制（TickPlacement / IsSnapToTickEnabled）與事件監聽。

### Data Binding（資料繫結）：
- 學習 Binding 4 大要素、流向模式（TwoWay / OneWay）與更新時機（UpdateSourceTrigger）。
- 實作 Element Binding：在 XAML 中無需 Code-Behind，將 Label 的 Content 綁定至 Slider 的 Value，並使用 StringFormat 進行數字格式化。


# WPF視窗飲料訂購系統ver 3
2026/10/07

## 功能更新
1. 使用OpenFileDialog來讀取飲料csv檔案
1. 程式執行時動態加入飲料品項的視窗元件
1. 程式執行時動態設定Slider和Label的資料繫結
1. 使用SaveFileDialog來寫入訂單文字檔案
1. 學習檔案IO

## 教學內容
- 集合型態 Dictionary<TKey, TValue>：說明鍵值對結構、雜湊表機制（$O(1)$ 查詢效率）、Key 的唯一性，以及使用 TryGetValue 進行安全讀取的方法。
- 檔案 I/O（System.IO）：高階靜態類別：說明 File（ReadAllLines、WriteAllText）與 Directory 的快速檔案操作。   串流處理：介紹處理大型檔案的 StreamReader / StreamWriter（搭配 using 自動釋放資源）與處理二進位檔的 FileStream。路徑處理：強調使用 Path.Combine() 處理跨平台路徑連線。
- 標準對話方塊（Microsoft.Win32）：
- OpenFileDialog：說明檔案過濾器 Filter 語法與 ShowDialog() 流程，用於開啟並讀取檔案。
- SaveFileDialog：說明 DefaultExt 與 OverwritePrompt 設定，用於指定路徑匯出檔案。

#### 動態生成 UI
讀取 CSV 檔資料後，用 C# 實例化 StackPanel、CheckBox、Label 與 Slider，並加入畫面容器中。
#### 動態 Data Binding
透過 C# 程式碼 lb_amount.SetBinding(...) 建立 Label 與 Slider 的連動。
#### 視窗樹狀走訪
透過 DrinkMenuStackPanel.Children 走訪動態加入的列元件，取值計算訂購總金額與折扣。   