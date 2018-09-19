# Chrome User Experience Report | Tools for Web Developers | Google Developers

![](https://developers.google.com/web/tools/chrome-user-experience-
report/images/dataset.png)

Chrome User Experience Report cung cấp các số liệu của trải nghiệm người dùng về các mà người dùng chrome trong thế giới thực trải nghiệm trên các điểm đến phổ biến trên web.


## Phương pháp

Báo cáo trải nghiệm người dùng Chrome được hỗ trợ bởi việc đo lường số liệu trải nghiệm người dùng chính trên các trang web được public. Được tổng hợp từ những người dùng đã chọn tham gia đồng bộ hóa lịch sử duyệt web của họ, ko thiết lập mật khẩu đồng bộ hóa và đã bật báo cáo thống kê sử dụng. Dữ liệu kết quả được cung cấp qua:  
  1. [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/), cung cấp chỉ số trải nghiệm người dùng cấp URL cho các URL phổ biến được trình thu thập dữ liệu web của Google biết đến.  
  2. [Public Google BigQuery project](https://bigquery.cloud.google.com/dataset/chrome-ux-report:all), tổng hợp các chỉ số trải nghiệm người dùng theo nguồn gốc, áp dụng cho tất cả các nguồn gốc được trình thu thập thông tin web của Google biết đến và chia nhỏ theo các mục bên dưới.

### Số liệu

Chỉ số được cung cấp bởi Báo cáo trải nghiệm người dùng Chrome công khai được lưu trữ trên Google BigQuery được cung cấp bởi các API nền tảng web chuẩn được trình duyệt hiện đại hiển thị và được tổng hợp theo phân bổ nguyên thủy. Chủ sở hữu trang web muốn phân tích chi tiết hơn (phân tích cấp độ URL) và hiểu rõ hơn về hiệu suất trang web của họ và có thể sử dụng cùng một API để thu thập dữ liệu đo lường thực tế chi tiết (RUM) cho nguồn gốc của chính họ.  

**Note:** Hiện tại, Chrome User Experience Report tập trung vào hiệu suất tải trang. Thời gian tới, chúng tôi hy vọng sẽ thêm nhiều chỉ số và các thành phần mở rộng hơn, cả hai đều cung cấp thông tin chi tiết hơn về tải trang và [các yếu tố quan trọng ảnh hưởng nhiều nhất đến trải nghiệm người dùng](https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics).


Để được hướng dẫn về số liệu nào cần theo dõi và tối ưu hóa và các phương pháp hay nhất về cách diễn giải dữ liệu đo lường người dùng thực, hãy tham khảo tài liệu [hiệu suất tập trung vào người dùng](https://developers.google.com/web/updates/2017/06/user-centric-
performance-metrics) của chúng tôi.  

#### Khung màn hình đầu tiên

Định nghĩ bởi [Paint Timing API](https://w3c.github.io/paint-timing/#first-
paint) và [available in Chrome
M60+](https://www.chromestatus.com/feature/5688621814251520):

> "First Paint báo cáo thời gian khi trình duyệt được render lần đầu sau khi điều hướng. Điều này không bao gồm background paint mặc định, nhưng bao gồm background paint không mặc định. Đây là thời điểm quan trọng đầu tiên mà các nhà phát triển quan tâm đến khi tải trang - khi trình duyệt bắt đầu hiển thị trang."

#### First Contentful Paint

Định nghĩ bởi [Paint Timing API](https://w3c.github.io/paint-timing/#first-
contentful-paint) và [available in Chrome
M60+](https://www.chromestatus.com/feature/5688621814251520):

> "First Contentful Paint báo cáo thời gian khi trình duyệt render text, ảnh (bao gồm ảnh nền) lần đầu, non-white canvas hoặc SVG. Bao gồm văn bản và webfont, đây là bước đầu người dùng có thể đọc nội dung trang.  

#### DOMContentLoaded

Định nghĩa bởi [HTML specification](https://html.spec.whatwg.org/#event-
domcontentloaded):

> "The DOMContentLoaded reports the time when the initial HTML document has
been completely loaded and parsed, without waiting for stylesheets, images,
and subframes to finish loading." \- [MDN](https://developer.mozilla.org/en-
US/docs/Web/Events/DOMContentLoaded).

> "The DOMContentLoaded báo cáo thời gian khi tài liệu HTML được laod hoàn toàn, mà chưa có style, ảnh và subframe.\- [MDN](https://developer.mozilla.org/en-
US/docs/Web/Events/DOMContentLoaded).  

#### onload

Định nghĩa bởi [HTML specification](https://html.spec.whatwg.org/#event-load):

> "Sự kiện tải được kích hoạt khi trang và các tài nguyên phụ thuộc của nó tải xong." \- [MDN](https://developer.mozilla.org/en-
US/docs/Web/Events/load).

### Những khía cạnh/biểu mẫu

Hiệu suất của nội dung web có thể thay đổi đáng kể dựa trên loại thiết bị, thuộc tính của mạng và các yếu tố khác. Để giúp phân đoạn và hiểu trải nghiệm người dùng trên các phân đoạn chính như vậy, Báo cáo trải nghiệm người dùng Chrome cung cấp các dimension sau  

#### Loại kết nối hiệu quả

Định nghĩa bởi [Network Information API](https://wicg.github.io/netinfo/#dfn-
effective-connection-types) và [available in Chrome
M62+](https://www.chromestatus.com/feature/5108786398232576):

> "Cung cấp loại kết nối hiệu quả (“chậm-2g”, “2g”, “3g”, “4g” hoặc “ngoại tuyến”) được xác định theo giá trị vòng lặp và băng thông dựa trên các quan sát đo lường thực tế của người dùng. ”"

#### Loại thiết bị

Chia loại thiết bị ("phone", "tablet", or "desktop"), như
[communicated via User-Agent](https://developer.chrome.com/multidevice/user-
agent).

#### Quốc gia

Vị trí địa lý của người dùng ở cấp quốc gia, được suy ra theo địa chỉ IP của họ. Các quốc gia được xác định theo [ISO 3166-1 alpha-2 code
s](https://en.wikipedia.org/wiki/ISO_3166-1#Officially_assigned_code_elements)
.

### Data format
Báo cáo được cung cấp qua [Google
BigQuery](https://cloud.google.com/bigquery/) dưới dạng tập hợp các tập dữ liệu chứa các chỉ số trải nghiệm người dùng được tổng hợp thành độ phân giải nguyên thủy. Mỗi tập dữ liệu đại diện cho một quốc gia, quốc gia nắm bắt dữ liệu trải nghiệm người dùng cho người dùng ở Serbia (`rs` là mã ISO 31611-1 cho Serbia). Ngoài ra, có một tập dữ liệu tổng hợp toàn cầu (tất cả) thu thập trải nghiệm trên toàn thế giới. Mỗi hàng trong tập dữ liệu chứa bản ghi trải nghiệm người dùng lồng nhau cho một nguồn gốc cụ thể, được chia cho các dimension chính.

Dimension  
---  
`origin` | "https://example.com"  
`effective_connection_type.name` | 4G  
`form_factor.name` | "phone"  
`first_paint.histogram.start` | 1000  
`first_paint.histogram.end` | 1200  
`first_paint.histogram.density` | 0.123  
  
Ví dụ: ở trên cho thấy một bản ghi mẫu từ Báo cáo trải nghiệm người dùng Chrome, cho biết rằng 12,3% số lần tải trang có đo lường “first paint time” trong khoảng 1000-1200 mili giây khi tải “http://example.com "Trên thiết bị" điện thoại "qua kết nối " 4G ". Để có được giá trị tích lũy của người dùng trải qua first paint time dưới 1200 mili giây, bạn có thể thêm tất cả các bản ghi có giá trị "kết thúc" của biểu đồ nhỏ hơn hoặc bằng 1200.

**Note:** Báo cáo trải nghiệm người dùng Chrome không cung cấp giá trị định lượng (ví dụ: trung vị). Các giá trị như vậy có thể xấp xỉ từ dữ liệu được cung cấp, nhưng không được báo cáo tiếp xúc trực tiếp.

## Getting started

The Chrome User Experience Report được cung cấp như một project công khai [Google
BigQuery](https://cloud.google.com/bigquery/). Để tham gia dự án, bạn cần tài khoản Google và Google Cloud Project: [refer to our step by step
guide](https://developers.google.com/web/tools/chrome-user-experience-report
/getting-started#access-dataset) và [the guided tour of how to query the
project](https://developers.google.com/web/tools/chrome-user-experience-report
/getting-started#example-queries).

## Các mẹo khi phân tích và các phương pháp hay nhất

### Xem xét sự khác biệt về lượng truy cập trên mỗi nguồn 

Các số liệu được cung cấp bởi Báo cáo trải nghiệm người dùng Chrome được cung cấp bởi dữ liệu đo lường người dùng thực. Kết quả là, dữ liệu phản ánh cách người dùng thực sự trải nghiệm nguồn gốc truy cập và không giống như thử nghiệm tổng hợp hoặc địa phương nơi thử nghiệm được thực hiện trong điều kiện cố định và mô phỏng, nắm bắt đầy đủ các yếu tố bên ngoài hình thành và đóng góp cho trải nghiệm người dùng cuối.

Ví dụ: sự khác biệt về dân số người dùng truy cập nguồn gốc cụ thể có thể đóng góp những khác biệt có ý nghĩa cho trải nghiệm người dùng. Nếu trang web thường xuyên được nhiều khách truy cập hơn với các thiết bị hiện đại hơn hoặc thông qua mạng nhanh hơn, kết quả có thể xuất hiện "nhanh" ngay cả khi trang web không được tối ưu hóa tốt. Ngược lại, một trang web được tối ưu hóa tốt thu hút một lượng người dùng rộng hơn hoặc dân số có số lượng người dùng lớn hơn trên các thiết bị hoặc mạng chậm hơn, có thể xuất hiện "chậm".

Khi thực hiện so sánh trực tiếp giữa các nguồn gốc, điều quan trọng là phải tính toán và kiểm soát sự khác biệt về dân số: phân đoạn theo thứ nguyên được cung cấp, chẳng hạn như loại thiết bị và loại kết nối và xem xét các yếu tố bên ngoài như quy mô dân số, quốc gia mà từ đó nguồn gốc được truy cập, v.v.

### Xem xét sự khác biệt kích thước truy cập giữa các nguồn trang

Báo cáo trải nghiệm người dùng Chrome tổng hợp dữ liệu cho mỗi nguồn gốc, với các giá trị "mật độ" trên tất cả các biểu đồ dimension-metric tổng hợp với giá trị là "1.0". Điều này cung cấp thông tin chi tiết về phân phối trải nghiệm trên các thứ nguyên chính cho một nguồn gốc duy nhất.

Tuy nhiên, khi tổng hợp dữ liệu từ nhiều nguồn, ví dụ trong industry vertical hoặc khu vực địa lý, hãy cẩn thận với các loại kết luận được rút ra: việc tăng mật độ cho cùng một chỉ số trên nhiều nguồn gốc không tính đến sự khác biệt về dân số tương đối trên nguồn gốc.

Ví dụ: trang web A có thể có mười triệu khách truy cập, trong khi trang web B có mười nghìn. Trong cả hai trường hợp, mật độ biểu đồ cho mỗi tổng nguồn gốc là “1.0” và tập dữ liệu không cung cấp bất kỳ số liệu tuyệt đối nào về quy mô dân số của nguồn gốc riêng lẻ hoặc sự khác biệt về kích thước dân số tương đối trên nguồn gốc. Kết quả là, nếu bạn cộng các mật độ từ A và B, và trung bình kết quả, bạn sẽ coi chúng là bằng nhau mặc dù A có ba đơn vị lưu lượng truy cập lớn hơn.  

### Cân nhắc sự khác biệt về truy cập của Chrome

Báo cáo trải nghiệm người dùng Chrome, hỗ trợ bởi đo lường người dùng thực được tổng hợp từ những người dùng Chrome đã chọn tham gia đồng bộ hóa lịch sử duyệt web của họ, ko thiết lập mật khẩu đồng bộ hóa và đã bật báo cáo thống kê sử dụng. Số người này có thể không đại diện cho cơ sở người dùng rộng hơn cho một nguồn gốc cụ thể và nhiều nguồn gốc có thể có sự khác biệt về dân số giữa nhau. Hơn nữa, dữ liệu này không tính đến người dùng có trình duyệt khác nhau và sự khác biệt trong việc chấp nhận trình duyệt ở các khu vực địa lý khác nhau.

Do đó, hãy cẩn thận với các loại kết luận được rút ra khi nhìn vào bề mặt của nguồn gốc và khi so sánh nguồn gốc cá nhân: tránh sử dụng so sánh tuyệt đối và xem xét các yếu tố dân số khác được nêu trong các phần ở trên.  

