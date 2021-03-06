# Áp dụng các phương pháp phân lớp (Classification) trên tập dữ liệu Mushroom

Trong bài viết này, ta sẽ áp dụng các phương pháp phân lớp (classification) lên tập dữ liệu Mushroom. Đây là tập dữ liệu mô tả các đặc tính vật lý của nấm, cùng với nhãn phân loại có độc hoặc ăn được. Các thuật toán được sử dụng gồm Naive Bayes, Nearest neighbor, ID3, J48. Để dễ tiếp cận, các phương pháp được thực hiện với Weka.

- **Tập dữ liệu:** mushroom
- **Địa chỉ:** https://archive.ics.uci.edu/ml/machine-learning-databases/mushroom/agaricus-lepiota.data
- **Mô tả:** https://archive.ics.uci.edu/ml/machine-learning-databases/mushroom/agaricus-lepiota.names

# Mô tả sơ lược về dữ liệu

Đây là tập dữ liệu mô tả các đặc tính vật lý của nấm, cùng với nhãn phân loại có độc hoặc ăn được (thuộc tính class đầu tiên: p (poisonous) – có độc, e (edible) – ăn được).

- Số lượng mẫu: 8124.
- Số lượng thuộc tính: 22.
- Kiểu của mỗi thuộc tính: nomial.
- Thuộc tính thiếu giá trị: stalk-root, số lượng mẫu bị thiếu giá trị: 2480 (31%).
- Sự phân bố của dữ liệu vào các phân lớp khá cân bằng. Số lượng các phân lớp không áp đảo nhau (imbalanced).
- Ta dùng filter > unsupervised > attribute > ReplaceMissingValues để điền các giá trị thiếu.

# Tiến hành xây dựng và đánh giá mô hình

Ta phân chia tập dữ liệu để đánh giá mô hình theo hai phương pháp Hold-out và K-fold cross validation.
Ta chọn thuộc tính phân lớp là “class”, chọn các Classifer tương ứng, sau đó bấm Start để tiến hành xây dựng mô hình và đánh giá độ chính xác.

# Đánh giá mô hình bằng phương pháp Hold-out

Chúng ta sẽ chia dữ liệu thành 2 phần: 50% để xây dựng mô hình phân lớp (tập train), 50% để kiểm tra (tập test).

|Classifier|Precision|Recall|F-measure|
|---|---|---|---|---|
|Naive Bayes|0.946|0.942|0.942|
|KNN (k=1)|1|1|1|1|
|ID3 decision tree|1|1|1|1|
|J48 decision tree|1|1|1|1|

# Đánh giá mô hình bằng phương pháp k-fold cross validation

Ta chọn k=10, nghĩa là chia tập dữ liệu thành 10 phần, 1 phần dùng làm tập kiểm tra (test set), 9 phần dùng để huấn luyện (train set).

|Classifier|Precision|Recall|F-measure|
|---|---|---|---|---|
|Naive Bayes|0.958|0.956|0.956|
|KNN (k=1)|1|1|1|1|
|ID3 decision tree|1|1|1|1|
|J48 decision tree|1|1|1|1|

Riêng thuật toán J48, ta có thể sử dụng chức năng Visualize Tree để xem hình ảnh cây quyết định.
![Decision tree visualization] (https://ongxuanhong.files.wordpress.com/2015/08/hold-out-j48.png)

# Kết luận

Qua kết quả phân lớp trên, ta thấy ngoài mô hình Naive Bayes, các mô hình còn lại đều cho kết quả phân lớp rất tốt (100% phân lớp chính xác). Dựa vào cây quyết định, ta có thể biết được một loại nấm có độc hay không nhờ vào đặc điểm mùi và màu sắc của nó.

Về đặc điểm mùi, nấm nào ăn được thường có mùi hạnh nhân và mùi hoa hồi, nấm độc thường có mùi hôi, tanh, và cay. Còn đặc điểm màu sắc, chỉ có nấm màu xanh lá cây mới ăn được, các loài nấm có màu loè loạt như cam, vàng, tím đều là nấm độc.

Thật thú vị phải không nào, nhờ mô hình phân lớp ta có thể phân biệt được đâu là nấm độc, đâu là nấm ăn được chỉ thông qua một số đặc điểm nhận diện qua mùi và màu sắc.
