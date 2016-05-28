# eveonline-market-analyze-embulk
Eve Online のマーケットデータを解析済みファイルをElasticSearchに取り込むためのembulk設定ファイル

# 必要環境
- kibana
- elastic-search
- embulk

# 設定 config/market_config
path_prefix のディレクトリパスを自身の環境に合わせて変更してください

# 設定 mydata/seed_market.yml
path_prefix のディレクトリパスを自身の環境に合わせて変更してください

# データ配置
csv/market に解析済みファイルを配置してください

# 使用方法
Emblukの詳しい使用方法は http://www.embluk.org/docs/recipe/scheduled-csv-load-to-elasticsearch-kibana4.html 参照

1. curl -XPUT localhost:9200/eve_market -d "`cat mapping/mapping_template.json`"
2. embulk run config/market_config.yml -c diff-market.yml

間違った場合
3. curl -XDELETE 'http://localhost:9200/eve-market'
