# 入力された文字を移動パラメータへ
RTCコンポーネントである  
実行コマンド
```
python NameToWay.py
```

関数`onExecute`を編集して進行方向を決める.  
例 : 入力が['a', 'b', 'c', 'd']の時以下を編集する.  

```
def onExecute(self, ec_id):
    if self._inIn.isNew():
        data = self._inIn.read()
        print(data.data)
        # 入力データの文字列に応じてロボットを操作する
        if data.data == "a":
            print("Go straight")
            self._d_out.data.vx = 0.3
            data.data = ""

        elif data.data == "b":
            print("Back!!")
            self._d_out.data.vx = -0.3
            data.data = ""

        elif data.data == "c:
            print("Turn left")
            self._d_out.data.va = 0.3
            data.data = ""

        elif data.data == "d":
            print("Turn right")
            self._d_out.data.va = -0.3
            data.data = ""

        else:
            self._d_out.data.vx = 0
            self._d_out.data.vy = 0
            self._d_out.data.va = 0

        self._outOut.write()

    return RTC.RTC_OK
```