# aws-cli-s3

AWS CLI の ちょっとした使い方を確認するために作成したリポジトリです.

## 標準入力を受け取って、そのままアップロードする.

echo した文字列を foo.txt としてアップロードする例２つ.

例 1.

```sh
$ echo foobar | aws s3 cp - s3://bucket/foo.txt --endpoint-url=http://localhost:4566
```

例 2.

```sh
$ cat << _EOF_ | aws s3 cp - s3://bucket/foo.json --endpoint-url=http://localhost:4566
{
  "key1": "value1",
  "key2": "value2",
}
_EOF_
```

# localstack にて 事前準備

```sh
$ aws s3 mb s3://bucket/ --endpoint-url=http://localhost:4566
```

# localstack にて 結果の確認

```sh
$ aws s3 ls s3://bucket/ --endpoint-url=http://localhost:4566
$ aws s3 cp s3://bucket/foo.json foo.json --endpoint-url=http://localhost:4566
```

# リファレンス

以下の記事を元にしています.

https://dev.classmethod.jp/articles/aws-cli-s3-streaming/
