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
    
