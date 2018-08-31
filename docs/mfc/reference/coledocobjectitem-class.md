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
ms.openlocfilehash: bebc146994e440d4dbfbd0bd3a5e29f597140d8d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216333"
---
# <a name="coledocobjectitem-class"></a>Klasa COleDocObjectItem
Zawieranie dokumentów aktywnych implementuje.  
  
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
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Drukuje dokument z aplikacji kontenera przy użyciu domyślnych ustawień drukarek.|  
|[COleDocObjectItem::ExecCommand](#execcommand)|Wykonuje polecenie określone przez użytkownika.|  
|[COleDocObjectItem::GetActiveView](#getactiveview)|Pobiera aktywny widok dokumentu.|  
|[COleDocObjectItem::GetPageCount](#getpagecount)|Pobiera liczbę stron w dokumencie aplikacji kontenera.|  
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Przygotowanie aplikacji kontenera dokumentów do drukowania.|  
|[COleDocObjectItem::OnPrint](#onprint)|Drukuje dokument w aplikacji kontenera.|  
|[COleDocObjectItem::QueryCommand](#querycommand)|Zapytania dotyczące stanu co najmniej jedno polecenie generowanych przez zdarzenia interfejsu użytkownika.|  
|[COleDocObjectItem::Release](#release)|Zwalnia połączenia OLE połączony element, a następnie zamyka go, jeśli był otwarty. Niszczy element klienta.|  
  
## <a name="remarks"></a>Uwagi  
 W MFC aktywnego dokumentu odbywa się podobnie do regularnych, w miejscu można edytować osadzanie, z następującymi różnicami:  
  
-   `COleDocument`-Klasy pochodnej nadal utrzymuje listę elementów osadzonych obecnie; jednak te elementy mogą być `COleDocObjectItem`-elementów pochodnych.  
  
-   Po uaktywnieniu aktywnego dokumentu zajmuje całego obszaru klienta widoku, gdy będzie aktywny w miejscu.  
  
-   Kontener dokumentów aktywnych ma pełną kontrolę nad **pomocy** menu.  
  
-   **Pomocy** menu zawiera elementy menu dla aktywnego dokumentu kontenera i serwera.  
  
 Ponieważ kontener dokumentów aktywnych jest właścicielem **pomocy** menu kontener jest odpowiedzialny za przekazywanie serwera **pomocy** menu komunikatów do serwera. Ta integracja jest obsługiwany przez `COleDocObjectItem`.  
  
 Aby uzyskać więcej informacji na temat scalania menu i aktywacji aktywnego dokumentu, zobacz Omówienie [zawieranie dokumentów aktywnych](../../mfc/active-document-containment.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="coledocobjectitem"></a>  COleDocObjectItem::COleDocObjectItem  
 Wywołaj tę funkcję elementu członkowskiego, aby zainicjować `COleDocObjectItem` obiektu.  
  
```  
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pContainerDoc*  
 Wskaźnik do `COleDocument` obiektu, działając jako kontener aktywnego dokumentu. Ten parametr musi mieć wartość NULL, aby włączyć element IMPLEMENT_SERIALIZE. Zazwyczaj elementy OLE są konstruowane za pomocą wskaźnika dokumentów innych niż NULL.  
  
##  <a name="dodefaultprinting"></a>  COleDocObjectItem::DoDefaultPrinting  
 Metoda wywoływana przez platformę, by dokumentu przy użyciu ustawień domyślnych.  
  
```  
static HRESULT DoDefaultPrinting(
    CView* pCaller,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pCaller*  
 Wskaźnik do [CView](../../mfc/reference/cview-class.md) obiekt, który wysyła polecenia drukowania.  
  
 *pInfo*  
 Wskaźnik do [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) obiekt, który opisuje zadania, które ma zostać wydrukowany.  
  
##  <a name="execcommand"></a>  COleDocObjectItem::ExecCommand  
 Wywołaj tę funkcję elementu członkowskiego, aby wykonać polecenie określone przez użytkownika.  
  
```  
HRESULT ExecCommand(
    DWORD nCmdID,  
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,  
    const GUID* pguidCmdGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nCmdID*  
 Identyfikator polecenia do wykonania. Musi należeć do grupy identyfikowane przez *pguidCmdGroup*.  
  
 *nCmdExecOpt*  
 Określa opcje wykonywania polecenia. Domyślnie można wykonać polecenia bez monitowania użytkownika. Zobacz [OLECMDEXECOPT](/windows/desktop/api/docobj/ne-docobj-olecmdexecopt) dla listy wartości.  
  
 *pguidCmdGroup*  
 Unikatowy identyfikator grupy polecenia. Domyślnie wartość NULL, co określa grupę standardowych. Polecenie przekazanej *nCmdID* musi należeć do grupy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia; w przeciwnym razie zwraca następujące kody błędów.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|WARTOŚĆ E_UNEXPECTED|Wystąpił nieoczekiwany błąd.|  
|E_FAIL|Wystąpił błąd.|  
|E_NOTIMPL|Wskazuje MFC sam powinien próbować translacji i wysyłać polecenia.|  
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* jest różna od NULL, ale nie określa grupę rozpoznawanym poleceniem.|  
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* nie rozpoznano jako prawidłowego polecenia w pGroup grupy.|  
|OLECMDERR_DISABLED|Polecenie identyfikowane przez *nCmdID* jest wyłączona i nie można wykonać.|  
|OLECMDERR_NOHELP|Obiekt wywołujący pytanie, aby uzyskać pomoc na polecenie identyfikowane przez *nCmdID* , ale nie jest dostępna żadna pomoc.|  
|OLECMDERR_CANCELLED|Użytkownik anulował wykonanie.|  
  
### <a name="remarks"></a>Uwagi  
 *PguidCmdGroup* i *nCmdID* parametry razem jednoznacznie identyfikują polecenie do wywołania. *NCmdExecOpt* parametr określa dokładną akcję do wykonania.  
  
##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do `IOleDocumentView` interfejsu aktualnie aktywnego widoku.  
  
```  
LPOLEDOCUMENTVIEW GetActiveView() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [IOleDocumentView](/windows/desktop/api/docobj/nn-docobj-ioledocumentview) interfejsu aktualnie aktywnego widoku. Jeśli nie ma bieżącego widoku, zwraca wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Licznik odwołań w zwracanym `IOleDocumentView` wskaźnik nie jest zwiększana, zanim zostanie zwrócony przez tę funkcję.  
  
##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę stron w dokumencie.  
  
```  
BOOL GetPageCount(
    LPLONG pnFirstPage,  
    LPLONG pcPages);
```  
  
### <a name="parameters"></a>Parametry  
 *pnFirstPage*  
 Wskaźnik do liczby pierwszej strony dokumentu. Może to być wartość NULL, co oznacza, że obiekt wywołujący nie potrzebujesz tej liczby.  
  
 *pcPages*  
 Wskaźnik do łączna liczba stron w dokumencie. Może to być wartość NULL, co oznacza, że obiekt wywołujący nie potrzebujesz tej liczby.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
##  <a name="onprepareprinting"></a>  COleDocObjectItem::OnPreparePrinting  
 Ta funkcja członkowska jest wywoływana przez platformę, by przygotować dokument do drukowania.  
  
```  
static BOOL OnPreparePrinting(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pCaller*  
 Wskaźnik do [CView](../../mfc/reference/cview-class.md) obiekt, który wysyła polecenia drukowania.  
  
 *pInfo*  
 Wskaźnik do [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) obiekt, który opisuje zadania, które ma zostać wydrukowany.  
  
 *bPrintAll*  
 Określa, czy ma być drukowana całego dokumentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
##  <a name="onprint"></a>  COleDocObjectItem::OnPrint  
 Ta funkcja członkowska jest wywoływana przez platformę, by wydrukować dokument.  
  
```  
static void OnPrint(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pCaller*  
 Wskaźnik do obiektu CView, która wysyła polecenia drukowania.  
  
 *pInfo*  
 Wskaźnik do [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) obiekt, który opisuje zadania, które ma zostać wydrukowany.  
  
 *bPrintAll*  
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
 *nCmdID*  
 Identyfikator polecenia, którego dotyczy kwerenda dla.  
  
 *pdwStatus*  
 Wskaźnik flagi zwrócone w wyniku kwerendy. Aby uzyskać listę możliwych wartości, zobacz [OLECMDF](/windows/desktop/api/docobj/ne-docobj-olecmdf).  
  
 *pCmdText*  
 Wskaźnik do [OLECMDTEXT](/windows/desktop/api/docobj/ns-docobj-_tagolecmdtext) struktury, w której ma zostać zwrócone nazwę oraz informacje o stanie jednego polecenia. Może mieć wartość NULL, aby wskazać, że obiekt wywołujący nie jest konieczne te informacje.  
  
 *pguidCmdGroup*  
 Unikatowy identyfikator grupy polecenia; może mieć wartość NULL, aby określić grupę standardowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Aby uzyskać pełną listę wartości zwracane, zobacz [IOleCommandTarget::QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcjonalność [IOleCommandTarget::QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) metodę, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="release"></a>  COleDocObjectItem::Release  
 Zwalnia połączenia OLE połączony element, a następnie zamyka go, jeśli był otwarty. Niszczy element klienta.  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>Parametry  
 *dwCloseOption*  
 Flaga, określania, w jakich okolicznościach elementu OLE jest zapisywana, gdy zwraca załadować stan. Aby uzyskać listę możliwych wartości, zobacz [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).  
  
### <a name="remarks"></a>Uwagi  
 Niszczy element klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC MFCBIND](../../visual-cpp-samples.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Klasa CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)
