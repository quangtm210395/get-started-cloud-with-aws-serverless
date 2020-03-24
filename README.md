![Serverless with AWS][serverless-aws]
Đặt những bước chân đầu tiên lên cloud với AWS và Serverless.
=====
Bài viết hôm nay mình sẽ giới thiệu với các bạn về AWS: đại gia đang có khẩu phần lớn nhất trên miếng bánh cloud hiện nay.

Trong bài viết này mình sẽ chia sẻ cách tạo một tài khoản AWS free và sử dụng những tính năng free trên đó. AWS Free Tier có một số dịch vụ được miễn phí trọn đời và một số dịch vụ miễn phí trong 12 tháng đầu, cách AWS miễn phí đó là cho người dùng một lượng tài nguyên nhất định (khác nhau đối với mỗi dịch vụ) để sử dụng, khác với Google hay Azure là cho chúng ta một khoản credit để sử dụng các dịch vụ tùy ý.

Trong số những dịch vụ được xuất hiện trọng mục Free Tier của AWS thì đủ để chúng ta có thể xây dựng ứng dụng trên Cloud. Lựa chọn của mình lần này là mang đến cho các bạn ví dụ về AWS API Gateway và AWS Lambda function (Serverless), combo này sẽ cho phép các bạn tạo ra một bộ Restful API để phát triển ứng dụng.

Vậy chúng ta cần chuẩn bị gì cho ngày hôm nay:
  - Một máy tính cá nhân để thao tác
  - Một thẻ tín dụng
  - Một cái bụng no (:smile)

## Step1: Tạo tài khoản AWS
Để tạo tài khoản AWS thì các bạn vào link này: https://portal.aws.amazon.com/billing/signup, sau khi điền thông tin tài khoản và ấn `Continue` thì các bạn sẽ được dẫn đến trang điền thông tin cá nhân của bạn:
![Điền thông tin cá nhân][aws-create-acc]
Sau khi hoàn thành điền thông tin cá nhân và tiếp tục thì các bạn sẽ thấy được AWS yêu cầu nhập thông tin 1 thẻ tín dụng, mục đích của việc này là để AWS chắc chắn bạn sẽ trả phí cho những chi phí bạn tạo ra ngoài phần Free Tier.
![Điền thông tin thẻ tín dụng][add-debit-card]
Sau khi bạn điền và ấn `Verify` thì AWS sẽ thực hiện thanh toán khoản tiền $1 vào tài khoản của bạn để đảm bảo đây là 1 thẻ tín dụng hợp lệ.
Và sau đó thì bạn đã có 1 tài khoản AWS để sử dụng. Hãy đăng nhập vào AWS Management console để khai phá thôi !!!

## Step2: Chuẩn bị môi trường để  làm việc.



[serverless-aws]: https://hikariq-article-images.s3-ap-southeast-1.amazonaws.com/serverless-aws.png
[add-debit-card]: https://hikariq-article-images.s3-ap-southeast-1.amazonaws.com/add-debit-card.png
[aws-create-acc]: https://hikariq-article-images.s3-ap-southeast-1.amazonaws.com/aws-create-acc.png