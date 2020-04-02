![Serverless with AWS][serverless-aws]
Đặt những bước chân đầu tiên lên cloud với AWS và Serverless.
=====
Bài viết hôm nay mình sẽ giới thiệu với các bạn về AWS: đại gia đang có khẩu phần lớn nhất trên miếng bánh cloud hiện nay.

Trong bài viết này mình sẽ chia sẻ cách tạo một tài khoản AWS free và sử dụng những tính năng free trên đó. AWS Free Tier có một số dịch vụ được miễn phí trọn đời và một số dịch vụ miễn phí trong 12 tháng đầu, cách AWS miễn phí đó là cho người dùng một lượng tài nguyên nhất định (khác nhau đối với mỗi dịch vụ) để sử dụng, khác với Google hay Azure là cho chúng ta một khoản credit để sử dụng các dịch vụ tùy ý.

Trong số những dịch vụ được xuất hiện trọng mục Free Tier của AWS thì đủ để chúng ta có thể xây dựng ứng dụng trên Cloud. Lựa chọn của mình lần này là mang đến cho các bạn ví dụ về AWS API Gateway và AWS Lambda function (Serverless), combo này sẽ cho phép các bạn tạo ra một bộ Restful API để phát triển ứng dụng.

Vậy chúng ta cần chuẩn bị gì cho ngày hôm nay:
  - Một máy tính cá nhân để thao tác
  - Một thẻ tín dụng
  - Một cái bụng no :smile:

## Step1: Tạo tài khoản AWS
Để tạo tài khoản AWS thì các bạn vào link này: https://portal.aws.amazon.com/billing/signup, sau khi điền thông tin tài khoản và ấn `Continue` thì các bạn sẽ được dẫn đến trang điền thông tin cá nhân của bạn:
![Điền thông tin cá nhân][aws-create-acc]

Sau khi hoàn thành điền thông tin cá nhân và tiếp tục thì các bạn sẽ thấy được AWS yêu cầu nhập thông tin 1 thẻ tín dụng, mục đích của việc này là để AWS chắc chắn bạn sẽ trả phí cho những chi phí bạn tạo ra ngoài phần Free Tier.
![Điền thông tin thẻ tín dụng][add-debit-card]

Sau khi bạn điền và ấn `Verify` thì AWS sẽ thực hiện thanh toán khoản tiền $1 vào tài khoản của bạn để đảm bảo đây là 1 thẻ tín dụng hợp lệ.
Và sau đó thì bạn đã có 1 tài khoản AWS để sử dụng. Giờ thì đăng nhập vào AWS Management console để khai phá thôi !!!

## Step2: Chuẩn bị môi trường để  làm việc.

1. Cài đặt Nodejs 10.x
- Đầu tiên cần cài đặt các package
```
sudo apt update

sudo apt -y install curl dirmngr apt-transport-https lsb-release ca-certificates

curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
```
Những câu lệnh này sẽ giúp thêm Nodejs APT repository vào hệ điều hành của các bạn.
- Sau đó tiến hành cài đặt Nodejs thôi:

```
sudo apt update
sudo apt -y install gcc g++ make
sudo apt -y install nodejs
```

Kiểm tra lại phiên bản Nodejs:
```
node -v
v10.15.3
```

2. Tiếp theo sẽ cài đặt `aws-cli`: command line để sử dụng các dịch vụ của AWS. Các bạn làm theo trang chủ nhé: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html

3. Chọn một editor để viết code Nodejs, ở đây mình sử dụng VS Code: https://code.visualstudio.com/

4. Cài đặt `serverless`:

```
sudo npm i -g serverless
```

5. Config credential cho aws-cli:
  Ở phần này chúng ta sẽ cần tạo một IAM user có nhiều quyền để deploy lambda function và API GW lên môi trường của AWS.
- Truy cập vào service IAM trên AWS Management Console: https://console.aws.amazon.com/iam/home?region=ap-southeast-1#
- Vào mục Users và ấn nút Add User
- Điền user name: aws-cli-user
- Lựa chọn access type: Programatic Access, khi chọn mục này thì user mà chúng ta tạo ra sẽ được tạo kèm một cặp access key ID và secret access key để sử dụng với aws-cli
- Sau khi ấn Next sẽ hiện ra giao diện để thêm quyền vào cho user này, ở đây các bạn chọn mục Attach policy directly
- Search PowerUserAccess và tick vào policy này.
- Next đến cuối cùng và chọn Create User. 
- Sau khi create user thì aws sẽ cho các bạn tải về 1 file csv chứa credentials (chính là access key ID và secret access key)
- Các bạn tạo folder .aws ở home, sau đó tạo 1 file credentials trong folder này
- Trong file credentials các bạn thêm 2 dòng chứa key như sau:
```
[default]
aws_access_key_id = Your key here
aws_secret_access_key = your key here
```


[attach-policy]: 
[power-user-access]: 
[serverless-aws]: https://hikariq-article-images.s3-ap-southeast-1.amazonaws.com/serverless-aws.png
[add-debit-card]: https://hikariq-article-images.s3-ap-southeast-1.amazonaws.com/add-debit-card.png
[aws-create-acc]: https://hikariq-article-images.s3-ap-southeast-1.amazonaws.com/aws-create-acc.png