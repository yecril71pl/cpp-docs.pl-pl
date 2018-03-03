---
title: Klasa COleDispatchDriver | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 059ff922689eaf354d4b4ae9b89fb49ab8c5a885
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coledispatchdriver-class"></a>Klasa COleDispatchDriver
Implementuje automatyzacji OLE po stronie klienta.  
  
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
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Tworzy `IDispatch` połączenia i dołącza go do `COleDispatchDriver` obiektu.|  
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Odłącza `IDispatch` połączenia, bez jego zwolnienia.|  
|[COleDispatchDriver::GetProperty](#getproperty)|Pobiera właściwość automatyzacji.|  
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Pomocnik wywoływania metod automatyzacji.|  
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Wersje `IDispatch` połączenia.|  
|[COleDispatchDriver::SetProperty](#setproperty)|Ustawia właściwość automatyzacji.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDispatchDriver::operator =](#operator_eq)|Kopiuje wartość źródła do `COleDispatchDriver` obiektu.|  
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|Uzyskuje dostęp do podstawowych `IDispatch` wskaźnika.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Określa, czy do zwolnienia `IDispatch` podczas `ReleaseDispatch` lub zniszczenia obiektu.|  
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Wskazuje wskaźnik do `IDispatch` interfejs dołączony do tego `COleDispatchDriver`.|  
  
## <a name="remarks"></a>Uwagi  
 `COleDispatchDriver`nie ma klasy podstawowej.  
  
 Interfejsy modelu OLE wysyłania zapewniają dostęp do metody i właściwości obiektu. Funkcje Członkowskie `COleDispatchDriver` dołączyć, odłączyć, tworzenie i zwolnij typ połączenia wysyłania `IDispatch`. Inne funkcje Członkowskie upraszczanie telefonicznej przy użyciu listy zmiennych argumentów **IDispatch::Invoke**.  
  
 Ta klasa może być używana bezpośrednio, ale jest zwykle używany tylko przez klasy tworzone przez Kreatora dodawania klasy. Podczas tworzenia nowych klas C++ przez zaimportowanie biblioteki typów, nowych klas są uzyskiwane z `COleDispatchDriver`.  
  
 Aby uzyskać więcej informacji na temat używania `COleDispatchDriver`, zobacz następujące artykuły:  
  
- [Klienci automatyzacji](../../mfc/automation-clients.md)  
  
- [Serwery automatyzacji](../../mfc/automation-servers.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `COleDispatchDriver`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch  
 Wywołanie `AttachDispatch` funkcji członkowskiej dołączyć `IDispatch` wskaźnik do `COleDispatchDriver` obiektu. Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
```  
void AttachDispatch(
        LPDISPATCH lpDispatch,  
        BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDispatch`  
 Wskaźnik do OLE `IDispatch` obiektu jest dołączony do `COleDispatchDriver` obiektu.  
  
 `bAutoRelease`  
 Określa, czy wysyłki zwolnione, gdy ten obiekt wykracza poza zakres.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zwolni żadnego `IDispatch` wskaźnika, który jest już dołączony do `COleDispatchDriver` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]  
  
##  <a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver  
 Konstruuje `COleDispatchDriver` obiektu.  
  
```  
COleDispatchDriver();  
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);  
  COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDispatch`  
 Wskaźnik do OLE `IDispatch` obiektu jest dołączony do `COleDispatchDriver` obiektu.  
  
 `bAutoRelease`  
 Określa, czy wysyłki zwolnione, gdy ten obiekt wykracza poza zakres.  
  
 `dispatchSrc`  
 Odwołanie do istniejącej `COleDispatchDriver` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Formularz `COleDispatchDriver`( `LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **TRUE**) łączy [IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) interfejsu.  
  
 Formularz `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) umożliwia skopiowanie istniejącej `COleDispatchDriver` obiektu i zwiększa liczbę odwołania.  
  
 Formularz `COleDispatchDriver`() tworzy `COleDispatchDriver` obiekt, ale nie łączy się `IDispatch` interfejsu. Przed użyciem `COleDispatchDriver`() bez argumentów, należy połączyć `IDispatch` do niej przy użyciu [COleDispatchDriver::CreateDispatch](#createdispatch) lub [COleDispatchDriver::AttachDispatch](#attachdispatch). Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::CreateDispatch](#createdispatch).  
  
##  <a name="createdispatch"></a>COleDispatchDriver::CreateDispatch  
 Tworzy [IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) obiektu interfejsu i dołącza go do `COleDispatchDriver` obiektu.  
  
```  
BOOL CreateDispatch(
        REFCLSID clsid,  
        COleException* pError = NULL);

 
BOOL CreateDispatch(
    LPCTSTR lpszProgID,  
    COleException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Identyfikator klasy `IDispatch` obiektu połączenie ma zostać utworzony.  
  
 `pError`  
 Wskaźnik do obiektu OLE wyjątku, której będą przechowywane kod stanu, w wyniku tworzenia.  
  
 `lpszProgID`  
 Wskaźnik do identyfikator programowy, takie jak "Excel.Document.5", dla której ma być tworzony obiektu dyspozytora obiektu automatyzacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]  
  
##  <a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch  
 Odłącza bieżącego `IDispatch` połączenia z tym obiektem.  
  
```  
LPDISPATCH DetachDispatch();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wcześniej dołączone OLE `IDispatch` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `IDispatch` Nie zostaje zwolniony.  
  
 Aby uzyskać więcej informacji na temat `LPDISPATCH` typu, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]  
  
##  <a name="getproperty"></a>COleDispatchDriver::GetProperty  
 Pobiera określony przez właściwość obiektu `dwDispID`.  
  
```  
void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Określa właściwości, które mają zostać pobrane.  
  
 `vtProp`  
 Określa właściwość, które mają zostać pobrane. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](#invokehelper).  
  
 `pvProp`  
 Adres zmiennej, która otrzyma wartość właściwości. Musi on być zgodny z typem określonym przez `vtProp`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]  
  
##  <a name="invokehelper"></a>COleDispatchDriver::InvokeHelper  
 Wywołuje metodę obiektu lub określona przez właściwość `dwDispID`, w ramach określonej przez `wFlags`.  
  
```  
void AFX_CDECL InvokeHelper(
        DISPID dwDispID,  
        WORD wFlags,  
        VARTYPE vtRet,  
        void* pvRet,  
        const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Określa metody lub właściwości do wywołania.  
  
 `wFlags`  
 Flagi opisujące Kontekst wywołania **IDispatch::Invoke**. . Aby uzyskać listę możliwych wartości, zobacz `wFlags` parametru w [IDispatch::Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) w zestawie Windows SDK.  
  
 `vtRet`  
 Określa typ zwracanej wartości. Możliwe wartości znajduje się w sekcji uwag.  
  
 `pvRet`  
 Adres zmiennej, która będzie odbierać wartość właściwości ani zwracanej wartości. Musi on być zgodny z typem określonym przez `vtRet`.  
  
 `pbParamInfo`  
 Wskaźnik do zerem ciągu bajtów Określanie typów parametrów po `pbParamInfo`.  
  
 *...*  
 Zmiennej listy parametrów typów określonych w `pbParamInfo`.  
  
### <a name="remarks"></a>Uwagi  
 `pbParamInfo` Parametr określa typy parametrów przekazanych do metody lub właściwości. Listy zmiennych argumentów jest reprezentowana przez **...**  w deklaracji składni.  
  
 Możliwe wartości `vtRet` argumentu są pobierane z `VARENUM` wyliczenia. Dopuszczalne są następujące wartości:  
  
|Symbol|Zwracany typ|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATA**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**WARTOŚĆ LOGICZNA**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 `pbParamInfo` Argument jest rozdzieloną spacjami listę **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielając je spacjami (nie przecinkami), określa listę parametrów funkcji. Możliwe wartości są wyświetlane z [event_custom —](event-maps.md#event_custom) makra.  
  
 Ta funkcja konwertuje parametry **VARIANTARG** wartości, a następnie wywołuje [IDispatch::Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) metody. Jeśli wywołanie `Invoke` kończy się niepowodzeniem, ta funkcja spowoduje zgłoszenie wyjątku. Jeśli `SCODE` (kod stanu) zwrócone przez **IDispatch::Invoke** jest `DISP_E_EXCEPTION`, funkcja zwraca [COleException](../../mfc/reference/coleexception-class.md) obiektu; w przeciwnym razie zwraca [ COleDispatchException](../../mfc/reference/coledispatchexception-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [VARIANTARG](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118), [implementowania interfejsu IDispatch](http://msdn.microsoft.com/library/windows/desktop/ms221037\(v=vs.85\).aspx), [IDispatch::Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx), i [struktury z COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w systemie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::CreateDispatch](#createdispatch).  
  
##  <a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease  
 Jeśli **TRUE**, dostęp do obiektu COM [m_lpDispatch](#m_lpdispatch) zostaną automatycznie wydane po [ReleaseDispatch](#releasedispatch) jest wywoływana lub gdy to `COleDispatchDriver` obiekt jest zniszczone.  
  
```  
BOOL m_bAutoRelease;  
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `m_bAutoRelease` ustawiono **TRUE** w konstruktorze.  
  
 Aby uzyskać więcej informacji dotyczących zwalnianie obiektów COM, zobacz [implementacja liczenie odwołań w](http://msdn.microsoft.com/library/windows/desktop/ms693431) i [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]  
  
##  <a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch  
 Wskaźnik do `IDispatch` interfejs dołączony do tego `COleDispatchDriver`.  
  
```  
LPDISPATCH m_lpDispatch;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_lpDispatch` Elementu członkowskiego danych jest publiczny zmiennej typu `LPDISPATCH`.  
  
 Aby uzyskać więcej informacji, zobacz [IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::AttachDispatch](#attachdispatch).  
  
##  <a name="operator_eq"></a>COleDispatchDriver::operator =  
 Kopiuje wartość źródła do `COleDispatchDriver` obiektu.  
  
```  
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `dispatchSrc`  
 Wskaźnik do istniejącej `COleDispatchDriver` obiektu.  
  
##  <a name="operator_lpdispatch"></a>COleDispatchDriver::operator LPDISPATCH  
 Uzyskuje dostęp do odpowiadającego `IDispatch` wskaźnik `COleDispatchDriver` obiektu.  
  
```  
operator LPDISPATCH();
```   
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]  
  
##  <a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch  
 Wersje `IDispatch` połączenia. Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)  
  
```  
void ReleaseDispatch();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli automatycznie wersji został ustawiony dla tego połączenia, wywołania tej funkcji **IDispatch::Release** przed zwolnieniem interfejsu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::AttachDispatch](#attachdispatch).  
  
##  <a name="setproperty"></a>COleDispatchDriver::SetProperty  
 Ustawia właściwości obiektu OLE, określony przez `dwDispID`.  
  
```  
void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDispID`  
 Identyfikuje właściwość ma zostać ustawiona.  
  
 `vtProp`  
 Określa typ właściwości do ustawienia. Możliwe wartości w sekcji uwag dla [COleDispatchDriver::InvokeHelper](#invokehelper).  
  
 *...*  
 Pojedynczy parametr typu określony przez `vtProp`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CALCDRIV](../../visual-cpp-samples.md)   
 [Przykładowe MFC acdual —](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
