# ブルートフォース（総当たり攻撃）から守る
<!-- position: 2 -->

## ブルートフォース攻撃とは
この種の攻撃は、攻撃者が最終的に正しく推測できることを期待して、多数のパスワードまたはパスフレーズを試すことでおこなわれます。

## その仕組みは？
Bluditでは、この種の攻撃を軽減するためにブルートフォース保護が提供されており、この保護はデフォルトで有効になっています。

ログインに失敗するたびに、Bluditは認証に失敗したユーザーのIPをブラックリストに追加します。ユーザーが何度もログインに失敗すると、Bluditは一定期間、問題のあるIPをブロックし、ブロックの期限が切れるまでユーザーはログインできなくなります。

## クラスとオブジェクト
`$security`という`Security Object`があり、オブジェクトのクラスは`/bl-kernel/security.class.php`です。クラス内の変数を参照してください。

<pre><code data-language="php">
private $dbFields = array(
    'minutesBlocked'=>5,
    'numberFailuresAllowed'=>10,
    'blackList'=>array()
);
</code></pre>

- `minutesBlocked`: IPがブロックされる時間(分)。
- `numberFailuresAllowed`: ブロックがトリガーしようとして失敗した回数。
- `blackList`: ブロックされたIPのリスト。

<div class="note">
<div class="title">メモ</div>
これらの値は、自分の好きな値に変更できます。
</div>
