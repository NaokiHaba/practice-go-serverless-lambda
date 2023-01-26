### Serverless Frameworkのインストール

```shell
$ npm install -g serverless

# インストール確認
$ serverless -v
```

### プロジェクトの作成

```shell
$ npx sls create -u https://github.com/serverless/serverless-golang/ -p lambda-test
$ cd lambda-test
```

### Go Modulesの初期化

```shell
$ go mod init lambda-test
```

### AWS Lambdaパッケージのインストール

```shell
$ go get github.com/aws/aws-lambda-go/lambda
```

### ビルド

`GOOS=linux go build -o bin/main main.go` でビルドする。

```shell
$ GOOS=linux go build -o bin/main main.go
```

### AWS IAMユーザーの作成

AWS IAMユーザーを作成する。

![スクリーンショット 2023-01-27 2.27.40.png](..%2F..%2F..%2F..%2Fvar%2Ffolders%2Fc2%2Ftdjhjspj49z20lszz484xd8w0000gn%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_41TkbY%2F%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-01-27%202.27.40.png)

### クレデンシャルの設定

`~/.aws/credentials` にクレデンシャルを設定する。

```shell
serverless config credentials \
  --provider aws \
  --key xxx \
  --secret xx/x
```

### デプロイ

```shell
$ sls deploy

Deploying lambda-test to stage master (ap-northeast-1)

✔ Service deployed to stack lambda-test-master (104s)

functions:
  test_function: lambda-test-test_function (5.2 MB)

2 deprecations found: run 'serverless doctor' for more details

Need a better logging experience than CloudWatch? Try our Dev Mode in console: run "serverless --console"
```

### 実行
![スクリーンショット 2023-01-27 2.34.30.png](..%2F..%2F..%2F..%2Fvar%2Ffolders%2Fc2%2Ftdjhjspj49z20lszz484xd8w0000gn%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_l5RwTR%2F%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-01-27%202.34.30.png)