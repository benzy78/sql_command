# SQLのコマンドまとめ

## 起動・ログイン・ロウアウト
* MySQLの起動： `brew services start mysql@5.7` ＊任意のバージョンで
* ルートユーザーとしてのログイン： `mysql --user=root --password`
* MySQLからのログアウト： `exit;`
* MySQLの停止： `brew services stop mysql@5.7` ＊任意のバージョンで

## 基本的な構文とか
* データの取得： `select カラム名 from テーブル名;`
* 条件付け： `where カラム名 = レコード`
* ある文字を含む：　`where カラム名 like "%任意の文字列%"`
* 前方一致： `where カラム名 like "任意の文字列%"`
* 後方一致： `where カラム名 like "%任意の文字列"`
* Xを含まない： `where not カラム名 like "%X%"`
* nullのデータ取得： `where カラム名 null` ＊注：nullは`where カラム名 = null`とすることができない。
* nullではないデータの取得： `where カラム名 is not null`
* and, orを用いたデータ取得： `where 条件1 and 条件2`または `where 条件1 or 条件2` ＊注：andは「かつ」、orは「または」
* データの並べ替え：昇順（小さい順） `order by カラム名 asc` ＊注：ascはascending orderの略
* データの並べ替え：降順（大きい順）`order by カラム名 desc`　＊注：descはdescending orderの略
* データ取得数の制限： `limit 任意のデータ件数`
* 重複データを省く： `select distinct(カラム名) from テーブル名;`
* 合計を求めるsum関数： `select sum(カラム名) from テーブル名;`
* 平均を求めるavg関数： `select avg(カラム名) from テーブル名;`
* データの個数の合計を求めるcount関数： `select count(カラム名) from テーブル名;`
* 最大値を求めるmax関数： `select max(カラム名) from テーブル名;`
* 最小値を求めるmin関数： `select min(カラム名) from テーブル名;`
* グループ化： `group by カラム名`
* グループ化されたものをさらにグループ化： `having 条件`
* クエリの中にもう一つクエリを作るサブクエリ：例 `select カラム1 from テーブル1 where カラム2 > (select カラム3 from テーブル1);`のように()の中に処理を書く。
* カラム名などに別名を定義する： `select カラム名 as "任意のカラム名"`
* テーブルの結合：　`join テーブル名 on テーブル1.カラム1 = テーブル2.カラム2` *注：on以降は結合の条件
* nullのレコードを取得したい時： `left join テーブル名 on 結合条件`
* データの追加： `insert into テーブル名 (カラム1, カラム2) values("データ1", "データ2");`
* データの更新： `update テーブル名 set カラム1 = "データ1", カラム2 = "データ2" where id = x;` ＊注：whereでどこのデータを更新するかを書かないとテーブル全てが更新されるので注意。
* データの削除： `delete from テーブル名 where id = x` ＊注：whereでどこのデータを更新するかを書かないとテーブル全てが更新されるので注意。

* テーブルの作成： `create table テーブル名(カラム名1 型, カラム名2　型);`
* テーブルの削除： `drop table テーブル名;`

## 実行の順番
  1. where
  2. group by
  3. 関数：sum, countなど
  4. having
  5. select, distinct
  6. order by
  7. limit
  
