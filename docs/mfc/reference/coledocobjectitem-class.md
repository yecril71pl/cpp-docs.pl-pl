---
title: Klasa metody COleDocObjectItem
ms.date: 11/04/2016
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
ms.openlocfilehash: c6e00bf42cf20b46c949c218efe1820cc7ce0f9b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504009"
---
# <a name="coledocobjectitem-class"></a>Klasa metody COleDocObjectItem

Implementuje zawieranie dokumentów aktywnych.

## <a name="syntax"></a>Składnia

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Metody COleDocObjectItem:: metody COleDocObjectItem](#coledocobjectitem)|`COleDocObject` Tworzy element.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Metody COleDocObjectItem::D oDefaultPrinting](#dodefaultprinting)|Drukuje dokument aplikacji kontenera przy użyciu domyślnych ustawień drukarki.|
|[Metody COleDocObjectItem:: ExecCommand](#execcommand)|Wykonuje polecenie określone przez użytkownika.|
|[Metody COleDocObjectItem:: GetActiveView](#getactiveview)|Pobiera aktywny widok dokumentu.|
|[COleDocObjectItem::GetPageCount](#getpagecount)|Pobiera liczbę stron w dokumencie aplikacji kontenera.|
|[Metody COleDocObjectItem:: OnPreparePrinting](#onprepareprinting)|Przygotowuje dokument kontenera do drukowania.|
|[COleDocObjectItem::OnPrint](#onprint)|Drukuje dokument aplikacji kontenera.|
|[Metody COleDocObjectItem:: QueryCommand](#querycommand)|Wykonuje zapytania dotyczące stanu jednego lub kilku poleceń generowanych przez zdarzenia interfejsu użytkownika.|
|[Metody COleDocObjectItem:: Release](#release)|Zwalnia połączenie z połączonym elementem OLE i zamyka je, jeśli było otwarte. Nie niszczy elementu klienta.|

## <a name="remarks"></a>Uwagi

W MFC, aktywny dokument jest obsługiwany podobnie do regularnego osadzania edytowalnego w miejscu, z następującymi różnicami:

- Klasa pochodna nadal zachowuje listę aktualnie osadzonych elementów, ale te elementy mogą być `COleDocObjectItem`elementami pochodnymi. `COleDocument`

- Gdy aktywny dokument jest aktywny, zajmuje cały obszar klienta widoku, gdy jest aktywny.

- Kontener aktywnego dokumentu ma pełną kontrolę nad menu **Pomoc** .

- Menu **Pomoc** zawiera elementy menu zarówno dla kontenera dokumentów aktywnych, jak i serwera.

Ponieważ kontener dokumentów aktywnych jest własnością menu **Pomoc** , kontener jest odpowiedzialny za przekazywanie komunikatów menu **pomocy** serwera do serwera. Ta integracja jest obsługiwana przez `COleDocObjectItem`program.

Aby uzyskać więcej informacji na temat scalania menu i aktywacji aktywnego dokumentu, zobacz Omówienie [zawierania dokumentów aktywnych](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="coledocobjectitem"></a>Metody COleDocObjectItem:: metody COleDocObjectItem

Wywołaj tę funkcję elementu członkowskiego `COleDocObjectItem` , aby zainicjować obiekt.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Parametry

*pContainerDoc*<br/>
Wskaźnik do `COleDocument` obiektu działającego jako kontener aktywnego dokumentu. Ten parametr musi mieć wartość NULL, aby można było włączyć IMPLEMENT_SERIALIZE. Normalne elementy OLE są konstruowane przy użyciu wskaźnika dokumentu o wartości innej niż NULL.

##  <a name="dodefaultprinting"></a>Metody COleDocObjectItem::D oDefaultPrinting

Wywoływane przez platformę do dokumentu przy użyciu ustawień domyślnych.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pCaller*<br/>
Wskaźnik do obiektu [CView](../../mfc/reference/cview-class.md) , który wysyła polecenie Print.

*pInfo*<br/>
Wskaźnik do obiektu [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , który opisuje zadanie do wydrukowania.

##  <a name="execcommand"></a>Metody COleDocObjectItem:: ExecCommand

Wywołaj tę funkcję elementu członkowskiego, aby wykonać polecenie określone przez użytkownika.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID*<br/>
Identyfikator polecenia do wykonania. Musi znajdować się w grupie identyfikowanej przez *pguidCmdGroup*.

*nCmdExecOpt*<br/>
Określa opcje wykonywania polecenia. Domyślnie Ustaw, aby wykonać polecenie bez monitowania użytkownika. Zobacz [OLECMDEXECOPT](/windows/win32/api/docobj/ne-docobj-olecmdexecopt) , aby uzyskać listę wartości.

*pguidCmdGroup*<br/>
Unikatowy identyfikator grupy poleceń. Domyślnie wartość NULL, która określa grupę Standard. Polecenie przesłane w *nCmdID* musi należeć do grupy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli pomyślne; w przeciwnym razie zwraca jeden z następujących kodów błędów.

|Wartość|Opis|
|-----------|-----------------|
|E_UNEXPECTED|Wystąpił nieoczekiwany błąd.|
|E_FAIL|Wystąpił błąd.|
|E_NOTIMPL|Wskazuje, że biblioteka MFC powinna próbować przetłumaczyć i wysłać polecenie.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* ma wartość różną od null, ale nie określa uznanej grupy poleceń.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* nie jest rozpoznawana jako prawidłowe polecenie w grupie pGroup.|
|OLECMDERR_DISABLED|Polecenie identyfikowane przez *nCmdID* jest wyłączone i nie można go wykonać.|
|OLECMDERR_NOHELP|Obiekt wywołujący prosi o pomoc dotyczącą polecenia identyfikowanego przez *nCmdID* , ale pomoc nie jest dostępna.|
|OLECMDERR_CANCELLED|Użytkownik anulował wykonywanie.|

### <a name="remarks"></a>Uwagi

Parametry *pguidCmdGroup* i *nCmdID* jednoznacznie identyfikują polecenie do wywołania. *NCmdExecOpt* parametr określa dokładną akcję do wykonania.

##  <a name="getactiveview"></a>Metody COleDocObjectItem:: GetActiveView

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać `IOleDocumentView` wskaźnik do interfejsu aktualnie aktywnego widoku.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu [IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview) aktualnie aktywnego widoku. Jeśli nie ma bieżącego widoku, zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Liczba odwołań na zwracanym `IOleDocumentView` wskaźniku nie jest zwiększana, zanim zostanie zwrócona przez tę funkcję.

##  <a name="getpagecount"></a>Metody COleDocObjectItem:: getpagecount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę stron w dokumencie.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Parametry

*pnFirstPage*<br/>
Wskaźnik do numeru pierwszej strony dokumentu. Może mieć wartość NULL, co oznacza, że obiekt wywołujący nie potrzebuje tej liczby.

*pcPages*<br/>
Wskaźnik do łącznej liczby stron w dokumencie. Może mieć wartość NULL, co oznacza, że obiekt wywołujący nie potrzebuje tej liczby.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="onprepareprinting"></a>Metody COleDocObjectItem:: OnPreparePrinting

Ta funkcja członkowska jest wywoływana przez platformę w celu przygotowania dokumentu do drukowania.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pCaller*<br/>
Wskaźnik do obiektu [CView](../../mfc/reference/cview-class.md) , który wysyła polecenie Print.

*pInfo*<br/>
Wskaźnik do obiektu [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , który opisuje zadanie do wydrukowania.

*bPrintAll*<br/>
Określa, czy cały dokument ma zostać wydrukowany.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="onprint"></a>Metody COleDocObjectItem:: OnPrint

Ta funkcja członkowska jest wywoływana przez platformę do drukowania dokumentu.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pCaller*<br/>
Wskaźnik do obiektu CView, który wysyła polecenie Print.

*pInfo*<br/>
Wskaźnik do obiektu [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , który opisuje zadanie do wydrukowania.

*bPrintAll*<br/>
Określa, czy cały dokument ma zostać wydrukowany.

##  <a name="querycommand"></a>Metody COleDocObjectItem:: QueryCommand

Wykonuje zapytania dotyczące stanu jednego lub kilku poleceń generowanych przez zdarzenia interfejsu użytkownika.

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID*<br/>
Identyfikator polecenia, dla którego jest wykonywane zapytanie.

*pdwStatus*<br/>
Wskaźnik do flag zwracanych w wyniku zapytania. Aby uzyskać listę możliwych wartości, zobacz [OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf).

*pCmdText*<br/>
Wskaźnik do struktury [OLECMDTEXT](/windows/win32/api/docobj/ns-docobj-olecmdtext) , w której mają zostać zwrócone informacje o nazwie i stanie dla jednego polecenia. Może mieć wartość NULL, aby wskazać, że obiekt wywołujący nie potrzebuje tych informacji.

*pguidCmdGroup*<br/>
Unikatowy identyfikator grupy poleceń; może mieć wartość NULL, aby określić grupę standardową.

### <a name="return-value"></a>Wartość zwracana

Aby uzyskać pełną listę zwracanych wartości, zobacz [IOleCommandTarget:: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) w Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność metody [IOleCommandTarget:: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) , zgodnie z opisem w Windows SDK.

##  <a name="release"></a>Metody COleDocObjectItem:: Release

Zwalnia połączenie z połączonym elementem OLE i zamyka je, jeśli było otwarte. Nie niszczy elementu klienta.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Parametry

*dwCloseOption*<br/>
Flaga określająca, w jaki sposób element OLE jest zapisywany po powrocie do stanu załadowanego. Aby uzyskać listę możliwych wartości, zobacz [COleClientItem:: Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Uwagi

Nie niszczy elementu klienta.

## <a name="see-also"></a>Zobacz także

[Przykład MFCBIND MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Klasa CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)
