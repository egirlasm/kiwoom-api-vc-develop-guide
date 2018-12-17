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

```
    void MainOnReceiveTrDataKhopenapictrl(LPCTSTR sScrNo, LPCTSTR sRQName, LPCTSTR sTrcode, LPCTSTR sRecordName, LPCTSTR sPrevNext, long nDataLength, LPCTSTR sErrorCode, LPCTSTR sMessage, LPCTSTR sSplmMsg);
    void OnReceiveTrDataKhopenapictrl(LPCTSTR sScrNo, LPCTSTR sRQName, LPCTSTR sTrcode, LPCTSTR sRecordName, LPCTSTR sPrevNext, long nDataLength, LPCTSTR sErrorCode, LPCTSTR sMessage, LPCTSTR sSplmMsg);
    void MainOnReceiveRealDataKhopenapictrl(LPCTSTR sJongmokCode, LPCTSTR sRealType, LPCTSTR sRealData);
    void OnReceiveRealDataKhopenapictrl(LPCTSTR sJongmokCode, LPCTSTR sRealType, LPCTSTR sRealData);
    void OnReceiveMsgKhopenapictrl(LPCTSTR sScrNo, LPCTSTR sRQName, LPCTSTR sTrCode, LPCTSTR sMsg);
    void MainOnReceiveChejanData(LPCTSTR sGubun, LONG nItemCnt, LPCTSTR sFidList);
    void OnReceiveChejanData(LPCTSTR sGubun, LONG nItemCnt, LPCTSTR sFidList);
    void OnEventConnect(LONG nItemCnt);
    void OnReceiveRealCondition(LPCTSTR strCode, LPCTSTR strType, LPCTSTR strConditionName, LPCTSTR strConditionIndex);            //조건검색 실시간 삽입,삭제되는 종목을 받는다
    void OnReceiveTrCondition(LPCTSTR sScrNo, LPCTSTR strCodeList, LPCTSTR strConditionName, int nIndex, int nNext);    //조건검색 종목리스트를 받는다.
    void OnReceiveConditionVer(long lRet, LPCTSTR sMsg);
    DECLARE_EVENTSINK_MAP()
```

또붙이고

```
// CMFCApplication2Dlg message handlers
void CMFCApplication2Dlg::MainOnReceiveTrDataKhopenapictrl(LPCTSTR sScrNo, LPCTSTR sRQName, LPCTSTR sTrcode, LPCTSTR sRecordName, LPCTSTR sPrevNext, long nDataLength, LPCTSTR sErrorCode, LPCTSTR sMessage, LPCTSTR sSplmMsg) {

}



//*******************************************************************/
//! Function Name : OnReceiveTrDataKhopenapictrl
//! Function      : 조회 응답 처리
//! Param         : LPCTSTR sScrNo, LPCTSTR sRQName, LPCTSTR sTrcode, LPCTSTR sRecordName, LPCTSTR sPrevNext, long nDataLength, LPCTSTR sErrorCode, LPCTSTR sMessage, LPCTSTR sSplmMsg
//! Return        : void
//! Create        : , 2014/06/02
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::OnReceiveTrDataKhopenapictrl(LPCTSTR sScrNo, LPCTSTR sRQName, LPCTSTR sTrcode, LPCTSTR sRecordName, LPCTSTR sPrevNext, long nDataLength, LPCTSTR sErrorCode, LPCTSTR sMessage, LPCTSTR sSplmMsg)
{

}

//*******************************************************************/
//! Function Name : OnReceiveMsgKhopenapictrl
//! Function      : 조회 에러 처리
//! Param         : LPCTSTR sScrNo, LPCTSTR sRQName, LPCTSTR sTrCode, LPCTSTR sMsg
//! Return        : void
//! Create        : , 2014/06/02
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::OnReceiveMsgKhopenapictrl(LPCTSTR sScrNo, LPCTSTR sRQName, LPCTSTR sTrCode, LPCTSTR sMsg)
{
}
//*******************************************************************/
//! Function Name : OnReceiveRealDataKhopenapictrl
//! Function      : 실시간 처리
//! Param         : LPCTSTR sJongmokCode, LPCTSTR sRealType, LPCTSTR sRealData
//! Return        : void
//! Create        : , 2014/06/02
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::MainOnReceiveRealDataKhopenapictrl(LPCTSTR sJongmokCode, LPCTSTR sRealType, LPCTSTR sRealData)
{


}
//*******************************************************************/
//! Function Name : OnReceiveRealDataKhopenapictrl
//! Function      : 실시간 처리
//! Param         : LPCTSTR sJongmokCode, LPCTSTR sRealType, LPCTSTR sRealData
//! Return        : void
//! Create        : , 2014/06/02
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::OnReceiveRealDataKhopenapictrl(LPCTSTR sJongmokCode, LPCTSTR sRealType, LPCTSTR sRealData)
{

}
//*******************************************************************/
//! Function Name : OnReceiveChejanData
//! Function      : 체결잔고 실시간 처리
//! Param         : LPCTSTR sGubun, LONG nItemCnt, LPCTSTR sFidList
//! Return        : void
//! Create        : , 2014/06/02
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::MainOnReceiveChejanData(LPCTSTR sGubun, LONG nItemCnt, LPCTSTR sFidList) {
    CString strGuBun(sGubun), strAccNo, strAcc;

}
//*******************************************************************/
//! Function Name : OnReceiveChejanData
//! Function      : 체결잔고 실시간 처리
//! Param         : LPCTSTR sGubun, LONG nItemCnt, LPCTSTR sFidList
//! Return        : void
//! Create        : , 2014/06/02
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::OnReceiveChejanData(LPCTSTR sGubun, LONG nItemCnt, LPCTSTR sFidList)
{

}

//*******************************************************************/
//! Function Name : OnReceiveRealCondition
//! Function      : 조건검색 실시간 종목 삽입/삭제
//! Param         : LPCTSTR strCode, LPCTSTR strType, LPCTSTR strConditionName, LPCTSTR strConditionIndex
//! Return        : void
//! Create        : , 2015/04/20
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::OnReceiveRealCondition(LPCTSTR strCode, LPCTSTR strType, LPCTSTR strConditionName, LPCTSTR strConditionIndex)
{

}

//*******************************************************************/
//! Function Name    : OnReceiveTrCondition
//! Function            : 조건검색 종목조회 응답
//! Param                : LPCTSTR sScrNo                    - 화면번호
//!                        : LPCTSTR strCodeList            - 종목리스트
//!                        : LPCTSTR strConditionName    - 조건명
//!                        : int nIndex                                - 조건명인덱스
//!                        : int nNext                                - 연속조회여부(2: 연속조회, 0:연속조회없음)
//! Return        : void
//! Create        : , 2015/04/20
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::OnReceiveTrCondition(LPCTSTR sScrNo, LPCTSTR strCodeList, LPCTSTR strConditionName, int nIndex, int nNext)
{

}
//*******************************************************************/
//! Function Name    : OnReceiveConditionVer
//! Function            : 사용자 조건식 응답
//! Param                : BOOL bRet                            - 성공(TRUE), 실패(FALSE)
//!                        : LPCTSTR sMsg                    - 메세지(reserved)
//! Return        : void
//! Create        : , 2015/04/20
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::OnReceiveConditionVer(long lRet, LPCTSTR sMsg)
{

}

//*******************************************************************/
//! Function Name : OnEventConnect
//! Function      : 접속 통보 처리
//! Param         : LONG nItemCnt
//! Return        : void
//! Create        : , 2014/06/02
//! Comment       : 
//******************************************************************/
void CMFCApplication2Dlg::OnEventConnect(LONG nItemCnt)
{ 
    if (nItemCnt == 0)
    {
        // 접속 정상처리
        OutputDebugString(L"키움증권서버에 성공적으로 연결되었습니다.");
        CString m_AccNo = m_khOpenApi.GetLoginInfo(L"ACCLIST");
        m_AccNo.Replace(L";", L"");
    }
}
```

이렇게 다 붙이고 나서 ,또 빌드 합니다.

즉 F5 키를 누르면 프로그램이 실행됩니다.

그리고나서 디버깅 창을 보며는 연결이 됬는지 안됏는지 나옵니다.

순서: F5빌드실행 -&gt; OK -&gt; 비밀번호입력 -&gt; 로그인 -&gt; 콘솔창 보면 저렇게 연결이 됬다고 뜹니다.

![](/assets/import52.png)

일단 여기에가 오류코드 리스트

> ```
>        0         // 정상처리
>
>         -10        // 실패
>
>         -11        // 조건번호 없슴                                                                
>
>         -12        // 조건번호와 조건식 불일치                                                     
>
>         -13        // 조건검색 조회요청 초과                                                       
>
>       -100        // 사용자정보교환 실패                                                           
>
>       -101        // 서버 접속 실패                                                                
>
>       -102        // 버전처리 실패                                                                 
>
>       -103        // 개인방화벽 실패                                                               
>
>       -104        // 메모리 보호실패                                                               
>
>       -105        // 함수입력값 오류                                                               
>
>       -106        // 통신연결 종료                                                                 
>
>       -107        // 보안모듈 오류                                                                 
>
>       -108        // 공인인증 로그인 필요                                                          
>
>                                                                                                 
>
>       -200        // 시세조회 과부하                                                               
>
>       -201        // 전문작성 초기화 실패.                                                         
>
>       -202        // 전문작성 입력값 오류.                                                         
>
>       -203        // 데이터 없음.                                                                  
>
>       -204        // 조회가능한 종목수 초과. 한번에 조회 가능한 종목개수는 최대 100종목.           
>
>       -205        // 데이터 수신 실패                                                              
>
>       -206        // 조회가능한 FID수 초과. 한번에 조회 가능한 FID개수는 최대 100개.               
>
>       -207        // 실시간 해제오류                                                               
>
>       -209        // 시세조회제한                                                               
>
>                                                                                                 
>
>       -300        // 입력값 오류                                                                   
>
>       -301        // 계좌비밀번호 없음.                                                            
>
>       -302        // 타인계좌 사용오류.                                                            
>
>       -303        // 주문가격이 주문착오 금액기준 초과.                                                     
>
>       -304        // 주문가격이 주문착오 금액기준 초과.                                                     
>
>       -305        // 주문수량이 총발행주수의 1% 초과오류.                                          
>
>       -306        // 주문수량은 총발행주수의 3% 초과오류.                                          
>
>       -307        // 주문전송 실패                                                                 
>
>       -308        // 주문전송 과부하                                                               
>
>       -309        // 주문수량 300계약 초과.                                                        
>
>       -310        // 주문수량 500계약 초과.                                                        
>
>       -311        // 주문전송제한 과부하
>
>       -340        // 계좌정보 없음.                                                                
>
>       -500        // 종목코드 없음.
> ```



