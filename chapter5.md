# 키움증권 API 시세조회

여기부터는 좀 어려운데요.

대량 코드 을 써야 하는데 일단 제가 쉬운 방법으로 해드리겠습니다.

먼저 아래 소스를 가져다 붙입니다.

```
//*******************************************************************/
// BEGIN_EVENTSINK_MAP
//*******************************************************************/
BEGIN_EVENTSINK_MAP(CXXXXXXXX, CDialogEx)
    ON_EVENT(CXXXXXXXX, IDC_KHOPENAPICTRL1, 1, OnReceiveTrDataKhopenapictrl,    VTS_BSTR VTS_BSTR VTS_BSTR VTS_BSTR VTS_BSTR VTS_I4 VTS_BSTR VTS_BSTR VTS_BSTR)
    ON_EVENT(CXXXXXXXX, IDC_KHOPENAPICTRL1, 2, OnReceiveRealDataKhopenapictrl,    VTS_BSTR VTS_BSTR VTS_BSTR)
    ON_EVENT(CXXXXXXXX, IDC_KHOPENAPICTRL1, 3, OnReceiveMsgKhopenapictrl,        VTS_BSTR VTS_BSTR VTS_BSTR VTS_BSTR )
    ON_EVENT(CXXXXXXXX, IDC_KHOPENAPICTRL1, 4, OnReceiveChejanData,                VTS_BSTR VTS_I4 VTS_BSTR)
    ON_EVENT(CXXXXXXXX, IDC_KHOPENAPICTRL1, 5, OnEventConnect,                    VTS_I4)
    ON_EVENT(CXXXXXXXX, IDC_KHOPENAPICTRL1, 7, OnReceiveRealCondition,            VTS_BSTR VTS_BSTR VTS_BSTR VTS_BSTR)
    ON_EVENT(CXXXXXXXX, IDC_KHOPENAPICTRL1, 8, OnReceiveTrCondition,            VTS_BSTR VTS_BSTR VTS_BSTR VTS_I2 VTS_I2)
    ON_EVENT(CXXXXXXXX, IDC_KHOPENAPICTRL1, 9, OnReceiveConditionVer,            VTS_I4 VTS_BSTR)
END_EVENTSINK_MAP()
```

여기서 주의해야 할점은 CXXXXXX 부분을 고쳐야 한다는것입니다.

붙이고 xxx수정하면 다음과 같이 되는데요,자세하게 얘기하면 DoDataExchange 함수 밑에 BEGIN\_MESSAGE\_MAP  메세지 맵

영어 뜻 그래도 메세지들어오면 대응한 함수를 실행한다는뜻입니다. 키움증권 메세지는 윈더우 창 메세지랑 다르므로 키움증권에 제공한 메세지 정의를 만들고 대응 함수를 입력하면 됩니다.

![](/assets/import41.png)

붙이고 또 붙이고





