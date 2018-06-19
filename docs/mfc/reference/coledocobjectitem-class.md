---
title: Klasa COleDocObjectItem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
dev_langs:
- C++
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af2b13b8da5f70cf55b47ddf3b7864f9f9151a40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373582"
---
# <a name="coledocobjectitem-class"></a>Klasa COleDocObjectItem
Zawieranie dokumentów aktywnych implements.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleDocObjectItem : public COleClientItem  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Konstruuje `COleDocObject` elementu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Drukuje dokument aplikacji kontenera przy użyciu domyślnych ustawień drukarek.|  
|[COleDocObjectItem::ExecCommand](#execcommand)|Wykonuje polecenie określone przez użytkownika.|  
|[COleDocObjectItem::GetActiveView](#getactiveview)|Pobiera aktywny widok dokumentu.|  
|[COleDocObjectItem::GetPageCount](#getpagecount)|Pobiera liczbę stron w aplikacji kontenera dokumentów.|  
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Przygotowanie aplikacji kontenera dokumentów do drukowania.|  
|[COleDocObjectItem::OnPrint](#onprint)|Drukuje dokument aplikacji kontenera.|  
|[COleDocObjectItem::QueryCommand](#querycommand)|Zapytania dotyczące stanu co najmniej jedno polecenie generowanych przez zdarzenia interfejsu użytkownika.|  
|[COleDocObjectItem::Release](#release)|Zwalnia połączenia OLE połączonych elementów, a następnie zamyka go, jeśli był otwarty. Nie niszczy element klienta.|  
  
## <a name="remarks"></a>Uwagi  
 W MFC aktywny dokument jest podobnie jak w zwykłym, w miejscu edytowalne osadzanie, z następującymi różnicami:  
  
-   `COleDocument`— Klasa pochodna nadal prowadzi listę elementów aktualnie osadzonych; jednak te elementy mogą być `COleDocObjectItem`-elementów pochodnych.  
  
-   Aktywny dokument jest aktywny, go zajmuje obszaru klienckiego całego widoku, gdy jest aktywny w miejscu.  
  
-   Kontener dokumentów aktywnych ma pełną kontrolę nad **pomocy** menu.  
  
-   **Pomocy** menu zawiera elementy menu dla kontenera dokumentów aktywnych i serwera.  
  
 Ponieważ jest właścicielem kontenera dokumentów aktywnych **pomocy** menu kontenera jest odpowiedzialny za przekazywanie serwera **pomocy** menu komunikaty do serwera. Integracja ta jest obsługiwany przez `COleDocObjectItem`.  
  
 Aby uzyskać więcej informacji na scalanie menu i dokumentów aktywnych aktywacji, zobacz Omówienie [zawieranie dokumentów aktywnych](../../mfc/active-document-containment.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="coledocobjectitem"></a>  COleDocObjectItem::COleDocObjectItem  
 Wywołanie tej funkcji Członkowskich zainicjować `COleDocObjectItem` obiektu.  
  
```  
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pContainerDoc`  
 Wskaźnik do `COleDocument` obiektu działający jako kontener dokumentów aktywnych. Ten parametr musi być **NULL** umożliwiające **IMPLEMENT_SERIALIZE**. Zwykle elementy OLE są konstruowane z innej **NULL** wskaźnik dokumentu.  
  
##  <a name="dodefaultprinting"></a>  COleDocObjectItem::DoDefaultPrinting  
 Wywoływane przez platformę, by dokumentu przy użyciu ustawień domyślnych.  
  
```  
static HRESULT DoDefaultPrinting(
    CView* pCaller,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `pCaller`  
 Wskaźnik do [CView](../../mfc/reference/cview-class.md) obiektu, który wysyła polecenie drukowania.  
  
 `pInfo`  
 Wskaźnik do [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) obiekt, który opisano zadania, które ma być drukowana.  
  
##  <a name="execcommand"></a>  COleDocObjectItem::ExecCommand  
 Wywołanie tej funkcji członkowskich można wykonać polecenia określone przez użytkownika.  
  
```  
HRESULT ExecCommand(
    DWORD nCmdID,  
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,  
    const GUID* pguidCmdGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nCmdID`  
 Identyfikator polecenia do wykonania. Musi należeć do grupy identyfikowanej przez `pguidCmdGroup`.  
  
 `nCmdExecOpt`  
 Określa opcje wykonywania polecenia. Domyślnie można wykonać polecenia bez monitowania użytkownika. Zobacz [OLECMDEXECOPT](http://msdn.microsoft.com/library/windows/desktop/ms683930) listę wartości.  
  
 `pguidCmdGroup`  
 Unikatowy identyfikator grupy polecenia. Domyślnie **NULL**, określającej grupę standardów. Polecenie przekazano `nCmdID` musi należeć do grupy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia; w przeciwnym razie zwraca jedną z następujących kodów błędów.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**E_UNEXPECTED**|Wystąpił nieoczekiwany błąd.|  
|**E_FAIL**|Wystąpił błąd.|  
|**E_NOTIMPL**|Wskazuje MFC sam powinien próbować tłumaczenie i wysyłać polecenia.|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup` ma wartość inną niż **NULL** , ale nie określa grupę rozpoznanego polecenia.|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID` Nie rozpoznano jako prawidłowego polecenia w pGroup grupy.|  
|**OLECMDERR_DISABLED**|Polecenie identyfikowane przez `nCmdID` jest wyłączona i nie może zostać wykonana.|  
|**OLECMDERR_NOHELP**|Obiekt wywołujący w opiniach pomocy w polecenie identyfikowane przez `nCmdID` , ale nie jest dostępna Pomoc.|  
|**OLECMDERR_CANCELLED**|Użytkownik anulował wykonywania.|  
  
### <a name="remarks"></a>Uwagi  
 `pguidCmdGroup` i `nCmdID` parametry razem identyfikują polecenie do wywołania. `nCmdExecOpt` Parametr określa dokładne akcję do wykonania.  
  
##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView  
 Wywołanie tej funkcji Członkowskich otrzymywać wskaźnik do `IOleDocumentView` interfejsu aktualnie aktywnego widoku.  
  
```  
LPOLEDOCUMENTVIEW GetActiveView() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [IOleDocumentView](http://msdn.microsoft.com/library/windows/desktop/ms678455) interfejsu aktualnie aktywnego widoku. Jeśli nie istnieje żadne bieżący widok, zwraca **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Liczba odwołań w zwróconym `IOleDocumentView` wskaźnik nie jest zwiększany, zanim zostanie zwrócony przez tę funkcję.  
  
##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount  
 Wywołanie tej funkcji Członkowskich, aby pobrać liczbę stron w dokumencie.  
  
```  
BOOL GetPageCount(
    LPLONG pnFirstPage,  
    LPLONG pcPages);
```  
  
### <a name="parameters"></a>Parametry  
 *pnFirstPage*  
 Wskaźnik do numer pierwszej strony dokumentu. Może być **NULL**, co oznacza obiekt wywołujący nie wymaga tego numeru.  
  
 *pcPages*  
 Wskaźnik do całkowita liczba stron w dokumencie. Może być **NULL**, co oznacza obiekt wywołujący nie wymaga tego numeru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="onprepareprinting"></a>  COleDocObjectItem::OnPreparePrinting  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by przygotowywania dokumentu do druku.  
  
```  
static BOOL OnPreparePrinting(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pCaller`  
 Wskaźnik do [CView](../../mfc/reference/cview-class.md) obiektu, który wysyła polecenie drukowania.  
  
 `pInfo`  
 Wskaźnik do [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) obiekt, który opisano zadania, które ma być drukowana.  
  
 `bPrintAll`  
 Określa, czy ma być drukowana całego dokumentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="onprint"></a>  COleDocObjectItem::OnPrint  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by wydrukować dokument.  
  
```  
static void OnPrint(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pCaller`  
 Wskaźnik do obiektu CView, który wysyła polecenie drukowania.  
  
 `pInfo`  
 Wskaźnik do [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) obiekt, który opisano zadania, które ma być drukowana.  
  
 `bPrintAll`  
 Określa, czy ma być drukowana całego dokumentu.  
  
##  <a name="querycommand"></a>  COleDocObjectItem::QueryCommand  
 Zapytania dotyczące stanu co najmniej jedno polecenie generowanych przez zdarzenia interfejsu użytkownika.  
  
```  
HRESULT QueryCommand(
    ULONG nCmdID,  
    DWORD* pdwStatus,  
    OLECMDTEXT* pCmdText =NULL,  
    const GUID* pguidCmdGroup =NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nCmdID`  
 Identyfikator polecenia, którego dotyczy zapytanie.  
  
 `pdwStatus`  
 Wskaźnik do flagi zwrócone w wyniku zapytania. Aby uzyskać listę możliwych wartości, zobacz [OLECMDF](http://msdn.microsoft.com/library/windows/desktop/ms695237).  
  
 `pCmdText`  
 Wskaźnik do [OLECMDTEXT](http://msdn.microsoft.com/library/windows/desktop/ms693314) struktury, do której należy zwrócić nazwę oraz informacje o stanie dla pojedynczego polecenia. Może być **NULL** wskazująca, czy obiekt wywołujący nie jest konieczne te informacje.  
  
 `pguidCmdGroup`  
 Unikatowy identyfikator grupy polecenia; może być **NULL** do określenia standardowe grupy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Aby uzyskać pełną listę wartości zwrotnych, zobacz [IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje [IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491) metody, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="release"></a>  COleDocObjectItem::Release  
 Zwalnia połączenia OLE połączonych elementów, a następnie zamyka go, jeśli był otwarty. Nie niszczy element klienta.  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCloseOption`  
 Flaga określenie, w jakich okolicznościach elementu OLE jest zapisywana, gdy powraca do stanu załadowany. Aby uzyskać listę możliwych wartości, zobacz [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).  
  
### <a name="remarks"></a>Uwagi  
 Nie niszczy element klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MFCBIND](../../visual-cpp-samples.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Klasa CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)
