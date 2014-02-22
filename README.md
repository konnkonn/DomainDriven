==
エリック・エヴァンスのドメイン駆動設計

## モデリングの要素

+ モデルと実装を結びつける
+ モデルに基づいて言語を洗練させる
+ 知識豊富なモデルを開発する
+ モデルを蒸留する
+ ブレストと実験を行う

ドメインを解析するにあたって、モデルは実用的で役に立つものでなければならない。またアプリケーションがシンプルに実装され、
理解しやすくなるように厳密でなければならない。


**サンプルコード例**

    public int makeBooking(Cargo cargo , Voyage voyage) { 
        if (!overbookingPolicy.isAllowed(cargo , voyage)) return -1;
        int confirmation = orderConfirmationSequence.next();
        voyage.addCargo(cargo , confirmation);
        return confirmation;
    }
    puclic boolean isAllowed(Cargo cargo , Voyage voyage){
        return (Cargo.size() + voyage.bookedCargoSize()) <= (voyage.capatiry() * 1.1); 
    }
    
+ レイヤ化アーキテクチャ

+ ユーザーインターフェース : 情報を表示して、ユーザー操作を解釈する役割
+ アプリケーション層 : ルールや知識を含めず、ビジネスの状況を反映させる状態は持たない
+ ドメイン層 : ビジネスルールを表す責務になり、状況を反映させる役割
+ インフラストラクチャ層 : 技術的機能を提供し、メッセージ送信を行う役割

複雑なプログラムはレイヤに分割すること
各レイヤで設計を分割して、上位レイヤに対しては疎結合にする
ドメインモデルに関係するコード全部を１つの層に集中させ、
aユーザーインターフェース等から分離すること
これによって、モデルが明確になる

ドメイン層であって、アプリケーション層ではない

