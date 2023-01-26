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
