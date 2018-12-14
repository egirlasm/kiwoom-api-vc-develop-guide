# 키움증권 API 시세조회

여기부터는 좀 어려운데요.

대량 코드 을 써야 하는데 일단 제가 쉬운 방법으로 해드리겠습니다.

먼저 아래 소스를 가져다 붙입니다.

```
//*******************************************************************/
// BEGIN_EVENTSINK_MAP
//*******************************************************************/
BEGIN_EVENTSINK_MAP(CXXXXXXXX, CDialogEx)
    ON_EVENT(CshootStockDlg, IDC_KHOPENAPICTRL1, 1, OnReceiveTrDataKhopenapictrl,    VTS_BSTR VTS_BSTR VTS_BSTR VTS_BSTR VTS_BSTR VTS_I4 VTS_BSTR VTS_BSTR VTS_BSTR)
    ON_EVENT(CshootStockDlg, IDC_KHOPENAPICTRL1, 2, OnReceiveRealDataKhopenapictrl,    VTS_BSTR VTS_BSTR VTS_BSTR)
    ON_EVENT(CshootStockDlg, IDC_KHOPENAPICTRL1, 3, OnReceiveMsgKhopenapictrl,        VTS_BSTR VTS_BSTR VTS_BSTR VTS_BSTR )
    ON_EVENT(CshootStockDlg, IDC_KHOPENAPICTRL1, 4, OnReceiveChejanData,                VTS_BSTR VTS_I4 VTS_BSTR)
    ON_EVENT(CshootStockDlg, IDC_KHOPENAPICTRL1, 5, OnEventConnect,                    VTS_I4)
    ON_EVENT(CshootStockDlg, IDC_KHOPENAPICTRL1, 7, OnReceiveRealCondition,            VTS_BSTR VTS_BSTR VTS_BSTR VTS_BSTR)
    ON_EVENT(CshootStockDlg, IDC_KHOPENAPICTRL1, 8, OnReceiveTrCondition,            VTS_BSTR VTS_BSTR VTS_BSTR VTS_I2 VTS_I2)
    ON_EVENT(CshootStockDlg, IDC_KHOPENAPICTRL1, 9, OnReceiveConditionVer,            VTS_I4 VTS_BSTR)
END_EVENTSINK_MAP()
```

여기서 주의해야 할점은 CXXXXXX 부분을 고쳐야 한다는것입니다.

jenkins 테스트

워크스페이스 테스트

