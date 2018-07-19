---
title: Klasa COleDispatchDriver | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 927ac1c73bee38257396a98a7f7ce1487d0c134d
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026948"
---
# <a name="coledispatchdriver-class"></a>Klasa COleDispatchDriver
implementuje po stronie klienta automatyzację OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleDispatchDriver  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Konstruuje `COleDispatchDriver` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Dołącza `IDispatch` połączenie `COleDispatchDriver` obiektu.|  
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Tworzy `IDispatch` połączenia i dołącza je do `COleDispatchDriver` obiektu.|  
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Odłącza `IDispatch` połączenia bez zwalniania go.|  
|[COleDispatchDriver::GetProperty](#getproperty)|Pobiera właściwość automatyzacji.|  
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Pomocnik wywoływania metod automatyzacji.|  
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Wersje `IDispatch` połączenia.|  
|[COleDispatchDriver::SetProperty](#setproperty)|Ustawia właściwość automatyzacji.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDispatchDriver::operator =](#operator_eq)|Kopiuje zawartość źródła do `COleDispatchDriver` obiektu.|  
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|Uzyskuje dostęp do podstawowych `IDispatch` wskaźnika.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Określa, czy ma zostać zwolniony `IDispatch` podczas `ReleaseDispatch` lub zniszczenia obiektu.|  
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Wskazuje, wskaźnik do `IDispatch` interfejs podłączony do tego `COleDispatchDriver`.|  
  
## <a name="remarks"></a>Uwagi  
 `COleDispatchDriver` nie ma klasy bazowej.  
  
 Interfejsach wysyłki OLE zapewniają dostęp do metod i właściwości obiektu. Funkcje elementów członkowskich `COleDispatchDriver` dołączania, odłącz, tworzenie i wersji wysyłania połączenie typu `IDispatch`. Innych funkcji Członkowskich uprościć wywołanie za pomocą listy zmiennych argumentów `IDispatch::Invoke`.  
  
 Ta klasa może być używana bezpośrednio, ale zazwyczaj jest używane tylko przez klasy tworzone przez Kreatora dodawania klasy. Po utworzeniu nowych klas C++ przez importowanie biblioteki typów nowych klas są uzyskiwane z `COleDispatchDriver`.  
  
 Aby uzyskać więcej informacji na temat korzystania z `COleDispatchDriver`, zobacz następujące artykuły:  
  
- [Klienci automatyzacji](../../mfc/automation-clients.md)  
  
- [Serwery automatyzacji](../../mfc/automation-servers.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `COleDispatchDriver`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="attachdispatch"></a>  COleDispatchDriver::AttachDispatch  
 Wywołaj `AttachDispatch` funkcja elementu członkowskiego, aby dołączyć `IDispatch` wskaźnik do `COleDispatchDriver` obiektu. Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
```  
void AttachDispatch(
        LPDISPATCH lpDispatch,  
        BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDispatch*  
 Wskaźnik do OLE `IDispatch` obiektu do podłączenia do `COleDispatchDriver` obiektu.  
  
 *bAutoRelease*  
 Określa, czy wysyłki ma zostać zwolniona, gdy ten obiekt wykracza poza zakres tej asysty.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zwolni dowolne `IDispatch` wskaźnika, który jest już dołączony do `COleDispatchDriver` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]  
  
##  <a name="coledispatchdriver"></a>  COleDispatchDriver::COleDispatchDriver  
 Konstruuje `COleDispatchDriver` obiektu.  
  
```  
COleDispatchDriver();  
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);  
  COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDispatch*  
 Wskaźnik do OLE `IDispatch` obiektu do podłączenia do `COleDispatchDriver` obiektu.  
  
 *bAutoRelease*  
 Określa, czy wysyłki ma zostać zwolniona, gdy ten obiekt wykracza poza zakres tej asysty.  
  
 *dispatchSrc*  
 Odwołanie do istniejącego `COleDispatchDriver` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Formularz `COleDispatchDriver`( `LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **TRUE**) łączy [IDispatch](http://msdn.microsoft.com/0e171f7f-0022-4e9b-ac8e-98192828e945) interfejsu.  
  
 Formularz `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) kopiuje istniejącą `COleDispatchDriver` obiektu i zwiększa liczbę odwołań.  
  
 Formularz `COleDispatchDriver`() tworzy `COleDispatchDriver` obiektu, ale nie łączy się `IDispatch` interfejsu. Przed rozpoczęciem korzystania z `COleDispatchDriver`() bez argumentów, należy połączyć się `IDispatch` do niej przy użyciu [COleDispatchDriver::CreateDispatch](#createdispatch) lub [COleDispatchDriver::AttachDispatch](#attachdispatch). Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::CreateDispatch](#createdispatch).  
  
##  <a name="createdispatch"></a>  COleDispatchDriver::CreateDispatch  
 Tworzy [IDispatch](http://msdn.microsoft.com/0e171f7f-0022-4e9b-ac8e-98192828e945) obiektu interfejsu i dołącza je do `COleDispatchDriver` obiektu.  
  
```  
BOOL CreateDispatch(
        REFCLSID clsid,  
        COleException* pError = NULL);

 
BOOL CreateDispatch(
    LPCTSTR lpszProgID,  
    COleException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator klasy*  
 Identyfikator klasy `IDispatch` obiekt połączenia, które ma zostać utworzony.  
  
 *pError*  
 Wskaźnik do obiektu wyjątku OLE, której będą przechowywane kod stanu, wynikające z tworzenia.  
  
 *lpszProgID*  
 Wskaźnik do identyfikator programowy, takie jak "Excel.Document.5" obiektu automatyzacji, dla którego ma być tworzony obiekt wysyłania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]  
  
##  <a name="detachdispatch"></a>  COleDispatchDriver::DetachDispatch  
 Odłącza bieżącą `IDispatch` połączenie z tym obiektem.  
  
```  
LPDISPATCH DetachDispatch();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do poprzednio dołączonych OLE `IDispatch` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `IDispatch` Nie została wydana.  
  
 Aby uzyskać więcej informacji o typie LPDISPATCH, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/0e171f7f-0022-4e9b-ac8e-98192828e945) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]  
  
##  <a name="getproperty"></a>  COleDispatchDriver::GetProperty  
 Pobiera określony przez właściwość obiektu *dwDispID*.  
  
```  
void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Umożliwia określenie właściwości, które mają zostać pobrane.  
  
 *vtProp*  
 Określa właściwość, które mają zostać pobrane. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](#invokehelper).  
  
 *pvProp*  
 Adres zmiennej, która otrzyma wartość właściwości. Musi być zgodny z typem określonym przez *vtProp*.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]  
  
##  <a name="invokehelper"></a>  COleDispatchDriver::InvokeHelper  
 Wywołuje metodę obiektu lub właściwości określone przez *dwDispID*, w kontekście określonej przez *wFlags*.  
  
```  
void AFX_CDECL InvokeHelper(
        DISPID dwDispID,  
        WORD wFlags,  
        VARTYPE vtRet,  
        void* pvRet,  
        const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Określa metodę lub właściwość do wywołania.  
  
 *wFlags*  
 Flagi opisujące Kontekst wywołania `IDispatch::Invoke`. . Aby uzyskać listę możliwych wartości, zobacz *wFlags* parametru w [uwzględniając](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) w zestawie Windows SDK.  
  
 *vtRet*  
 Określa typ wartości zwracanej. Możliwe wartości znajduje się w sekcji uwag.  
  
 *pvRet*  
 Adres zmiennej, która będzie odbierać wartość właściwości lub wartości zwracanej. Musi być zgodny z typem określonym przez *vtRet*.  
  
 *pbParamInfo*  
 Wskaźnik na ciąg zakończony znakiem null bajtów, określając typy parametrów, zgodnie z *pbParamInfo*.  
  
 *...*  
 Zmiennej listy parametrów typów określonych w *pbParamInfo*.  
  
### <a name="remarks"></a>Uwagi  
 *PbParamInfo* parametr określa typy parametrów przekazanych do metody lub właściwości. Listy zmiennych argumentów jest reprezentowany przez **...**  w składni deklaracji.  
  
 Możliwe wartości dla *vtRet* argument są pobierane z wyliczenia VARENUM. Dopuszczalne są następujące wartości:  
  
|Symbol|Zwracany typ|  
|------------|-----------------|  
|VT_EMPTY|**void**|  
|VT_I2|**short**|  
|VT_I4|**long**|  
|VT_R4|**float**|  
|VT_R8|**double**|  
|VT_CY|**CY**|  
|VT_DATE|**DATA**|  
|VT_BSTR|BSTR|  
|VT_DISPATCH|LPDISPATCH|  
|VT_ERROR|SCODE|  
|VT_BOOL|**BOOL**|  
|VT_VARIANT|**VARIANT**|  
|VT_UNKNOWN|LPUNKNOWN|  
  
 *PbParamInfo* argument jest listę rozdzielonych spacjami **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielone spacjami (nie przecinki) określa listę parametrów funkcji. Możliwe wartości są wyświetlane z [EVENT_CUSTOM](event-maps.md#event_custom) makra.  
  
 Ta funkcja konwertuje parametry VARIANTARG wartości, a następnie wywołuje [uwzględniając](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) metody. Jeśli wywołanie `Invoke` zakończy się niepowodzeniem, ta funkcja spowoduje zgłoszenie wyjątku. Jeśli SCODE (kod stanu) jest zwracany przez `IDispatch::Invoke` jest DISP_E_EXCEPTION, ta funkcja zgłosi [COleException](../../mfc/reference/coleexception-class.md) obiektu; w przeciwnym razie wyniku weryfikacji zgłasza wyjątek [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [VARIANTARG](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [implementowania interfejsu IDispatch](http://msdn.microsoft.com/library/windows/desktop/ms221037\(v=vs.85\).aspx), [uwzględniając](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx), i [struktury z COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::CreateDispatch](#createdispatch).  
  
##  <a name="m_bautorelease"></a>  COleDispatchDriver::m_bAutoRelease  
 W przypadku opcji TRUE obiektu COM uzyskiwał dostęp do [m_lpDispatch](#m_lpdispatch) zostaną automatycznie wydane po [ReleaseDispatch](#releasedispatch) nosi nazwę lub gdy to `COleDispatchDriver` niszczony jest obiekt.  
  
```  
BOOL m_bAutoRelease;  
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `m_bAutoRelease` jest ustawiona na wartość TRUE w konstruktorze.  
  
 Aby uzyskać więcej informacji na temat zwalnianie obiektów COM, zobacz [Implementowanie zliczanie odwołań](http://msdn.microsoft.com/library/windows/desktop/ms693431) i [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]  
  
##  <a name="m_lpdispatch"></a>  COleDispatchDriver::m_lpDispatch  
 Wskaźnik do `IDispatch` interfejs podłączony do tego `COleDispatchDriver`.  
  
```  
LPDISPATCH m_lpDispatch;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_lpDispatch` Element członkowski danych jest publiczną zmienną typu LPDISPATCH.  
  
 Aby uzyskać więcej informacji, zobacz [IDispatch](http://msdn.microsoft.com/0e171f7f-0022-4e9b-ac8e-98192828e945) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::AttachDispatch](#attachdispatch).  
  
##  <a name="operator_eq"></a>  COleDispatchDriver::operator =  
 Kopiuje zawartość źródła do `COleDispatchDriver` obiektu.  
  
```  
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *dispatchSrc*  
 Wskaźnik do istniejącego `COleDispatchDriver` obiektu.  
  
##  <a name="operator_lpdispatch"></a>  COleDispatchDriver::operator LPDISPATCH  
 Uzyskuje dostęp do podstawowych `IDispatch` wskaźnika `COleDispatchDriver` obiektu.  
  
```  
operator LPDISPATCH();
```   
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]  
  
##  <a name="releasedispatch"></a>  COleDispatchDriver::ReleaseDispatch  
 Wersje `IDispatch` połączenia. Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/0e171f7f-0022-4e9b-ac8e-98192828e945)  
  
```  
void ReleaseDispatch();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli został ustawiony automatycznie wydania dla tego połączenia, ta funkcja wywołuje `IDispatch::Release` przed zwolnieniem interfejsu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::AttachDispatch](#attachdispatch).  
  
##  <a name="setproperty"></a>  COleDispatchDriver::SetProperty  
 Ustawia właściwości obiektu OLE, które są określone przez *dwDispID*.  
  
```  
void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDispID*  
 Określa właściwość, który ma zostać ustawiona.  
  
 *vtProp*  
 Określa typ właściwości do ustawienia. Aby uzyskać możliwych wartości, zobacz sekcję Spostrzeżenia, aby [COleDispatchDriver::InvokeHelper](#invokehelper).  
  
 *...*  
 Pojedynczy parametr typu określonego przez *vtProp*.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC CALCDRIV](../../visual-cpp-samples.md)   
 [Próbki MFC acdual —](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
