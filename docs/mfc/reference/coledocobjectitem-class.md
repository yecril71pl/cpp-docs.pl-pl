---
title: Klasa COleDocObjectItem
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
ms.openlocfilehash: a696226185dd99b9e277e74d92cbe15c95cc900a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375054"
---
# <a name="coledocobjectitem-class"></a>Klasa COleDocObjectItem

Implementuje aktywne hermetyzacja dokumentu.

## <a name="syntax"></a>Składnia

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Konstruuje `COleDocObject` element.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Drukuje dokument aplikacji kontenera przy użyciu domyślnych ustawień drukarki.|
|[COleDocObjectItem::ExecCommand](#execcommand)|Wykonuje polecenie określone przez użytkownika.|
|[COleDocObjectItem::GetActiveView](#getactiveview)|Pobiera aktywny widok dokumentu.|
|[COleDocObjectItem::GetPageCount](#getpagecount)|Pobiera liczbę stron w dokumencie aplikacji kontenera.|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Przygotowuje dokument aplikacji kontenera do drukowania.|
|[COleDocObjectItem::OnPrint](#onprint)|Drukuje dokument aplikacji kontenera.|
|[COleDocObjectItem::QueryCommand](#querycommand)|Kwerendy o stan jednego lub więcej poleceń generowanych przez zdarzenia interfejsu użytkownika.|
|[COleDocObjectItem::Release](#release)|Zwalnia połączenie z elementem połączonym OLE i zamyka go, jeśli był otwarty. Nie niszczy elementu klienta.|

## <a name="remarks"></a>Uwagi

W MFC aktywny dokument jest obsługiwany podobnie do zwykłego osadzania w miejscu edytowalnym, z następującymi różnicami:

- Klasa `COleDocument`pochodna nadal przechowuje listę aktualnie osadzonych elementów; jednak te elementy `COleDocObjectItem`mogą być -pochodne elementów.

- Gdy aktywny dokument jest aktywny, zajmuje cały obszar klienta widoku, gdy jest aktywny w miejscu.

- Kontener dokumentu Active ma pełną kontrolę nad menu **Pomoc.**

- Menu **Pomoc** zawiera elementy menu zarówno dla kontenera dokumentu Active, jak i dla serwera.

Ponieważ kontener dokumentu Active jest właścicielem menu **Pomoc,** kontener jest odpowiedzialny za przekazywanie komunikatów menu **Pomoc** serwera do serwera. Ta integracja jest `COleDocObjectItem`obsługiwana przez .

Aby uzyskać więcej informacji na temat scalania menu i aktywacji aktywnego dokumentu, zobacz Omówienie [zamknięcia dokumentu aktywnego](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocitem](../../mfc/reference/cdocitem-class.md)

[Coleclientitem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a>COleDocObjectItem::COleDocObjectItem

Wywołanie tej funkcji elementu `COleDocObjectItem` członkowskiego, aby zainicjować obiekt.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Parametry

*pContainerDoto*<br/>
Wskaźnik do `COleDocument` obiektu działającego jako kontener aktywnego dokumentu. Ten parametr musi mieć wartość NULL, aby włączyć IMPLEMENT_SERIALIZE. Zwykle elementy OLE są konstruowane ze wskaźnikiem dokumentu nienajmowego.

## <a name="coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a>COleDocObjectItem::DoDefaultPrinting

Wywoływana przez strukturę do dokumentu przy użyciu ustawień domyślnych.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pCaller (rozmówca)*<br/>
Wskaźnik do obiektu [CView,](../../mfc/reference/cview-class.md) który wysyła polecenie drukuj.

*Pinfo*<br/>
Wskaźnik do [obiektu CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) który opisuje zadanie do wydrukowania.

## <a name="coledocobjectitemexeccommand"></a><a name="execcommand"></a>COleDocObjectItem::ExecCommand

Wywołanie tej funkcji elementu członkowskiego, aby wykonać polecenie określone przez użytkownika.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID (identyfikator nCmdID)*<br/>
Identyfikator polecenia do wykonania. Musi znajdować się w grupie identyfikowanej przez *pguidCmdGroup*.

*nCmdExecOpt*<br/>
Określa opcje wykonywania polecenia. Domyślnie ustawiono wykonanie polecenia bez monitowania użytkownika. Zobacz [OLECMDEXECOPT](/windows/win32/api/docobj/ne-docobj-olecmdexecopt) listę wartości.

*pguidCmdGroup (Grupa pguidCmd)*<br/>
Unikatowy identyfikator grupy poleceń. Domyślnie null, który określa grupę standardową. Polecenie przekazane w *nCmdID* musi należeć do grupy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli zakończy się pomyślnie; w przeciwnym razie zwraca jeden z następujących kodów błędów.

|Wartość|Opis|
|-----------|-----------------|
|E_unexpected|Wystąpił nieoczekiwany błąd.|
|E_fail|Błąd.|
|E_notimpl|Wskazuje, że MFC sam powinien próbować przetłumaczyć i wysłać polecenie.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* nie jest NULL, ale nie określa rozpoznaną grupę poleceń.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* nie jest rozpoznawany jako prawidłowe polecenie w grupie pGroup.|
|OLECMDERR_DISABLED|Polecenie zidentyfikowane przez *nCmdID* jest wyłączone i nie można go wykonać.|
|OLECMDERR_NOHELP|Dzwoniący poprosił o pomoc w komendzie zidentyfikowanej przez *nCmdID,* ale nie ma pomocy.|
|OLECMDERR_CANCELLED|Użytkownik anulował wykonanie.|

### <a name="remarks"></a>Uwagi

*PguidCmdGroup* i *parametry nCmdID* razem jednoznacznie identyfikują polecenie do wywołania. Parametr *nCmdExecOpt* określa dokładną akcję do podjęcia.

## <a name="coledocobjectitemgetactiveview"></a><a name="getactiveview"></a>COleDocObjectItem::GetActiveView

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wskaźnik do `IOleDocumentView` interfejsu aktualnie aktywnego widoku.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu [IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview) aktualnie aktywnego widoku. Jeśli nie ma bieżącego widoku, zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Liczba odwołań na `IOleDocumentView` zwrócony wskaźnik nie jest zwiększana, zanim zostanie zwrócona przez tę funkcję.

## <a name="coledocobjectitemgetpagecount"></a><a name="getpagecount"></a>COleDocObjectItem::GetPageCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę stron w dokumencie.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Parametry

*Strona pnFirstPage*<br/>
Wskaźnik do numeru pierwszej strony dokumentu. Może mieć wartość NULL, co oznacza, że wywołujący nie potrzebuje tego numeru.

*strony pcPages*<br/>
Wskaźnik do całkowitej liczby stron w dokumencie. Może mieć wartość NULL, co oznacza, że wywołujący nie potrzebuje tego numeru.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a>COleDocObjectItem::OnPreparePrinting

Ta funkcja elementu członkowskiego jest wywoływana przez platformę do przygotowania dokumentu do drukowania.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pCaller (rozmówca)*<br/>
Wskaźnik do obiektu [CView,](../../mfc/reference/cview-class.md) który wysyła polecenie drukuj.

*Pinfo*<br/>
Wskaźnik do [obiektu CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) który opisuje zadanie do wydrukowania.

*bPrintAll*<br/>
Określa, czy cały dokument ma być drukowany.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="coledocobjectitemonprint"></a><a name="onprint"></a>COleDocObjectItem::OnPrint

Ta funkcja elementu członkowskiego jest wywoływana przez strukturę do drukowania dokumentu.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pCaller (rozmówca)*<br/>
Wskaźnik do obiektu CView, który wysyła polecenie drukuj.

*Pinfo*<br/>
Wskaźnik do [obiektu CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) który opisuje zadanie do wydrukowania.

*bPrintAll*<br/>
Określa, czy cały dokument ma być drukowany.

## <a name="coledocobjectitemquerycommand"></a><a name="querycommand"></a>COleDocObjectItem::QueryCommand

Kwerendy o stan jednego lub więcej poleceń generowanych przez zdarzenia interfejsu użytkownika.

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID (identyfikator nCmdID)*<br/>
identyfikatora polecenia, o które pytamy.

*pdwStatus*<br/>
Wskaźnik do flag zwrócony w wyniku kwerendy. Aby uzyskać listę możliwych wartości, zobacz [OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf).

*pCmdText (tekst)*<br/>
Wskaźnik do struktury [OLECMDTEXT,](/windows/win32/api/docobj/ns-docobj-olecmdtext) w której można zwrócić informacje o nazwie i stanie pojedynczego polecenia. Może być null, aby wskazać, że wywołujący nie potrzebuje tych informacji.

*pguidCmdGroup (Grupa pguidCmd)*<br/>
Unikatowy identyfikator grupy poleceń; może być null, aby określić grupę standardową.

### <a name="return-value"></a>Wartość zwracana

Aby uzyskać pełną listę wartości zwracanych, zobacz [IOleCommandTarget::QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność [metody IOleCommandTarget::QueryStatus,](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) zgodnie z opisem w zestawie Windows SDK.

## <a name="coledocobjectitemrelease"></a><a name="release"></a>COleDocObjectItem::Release

Zwalnia połączenie z elementem połączonym OLE i zamyka go, jeśli był otwarty. Nie niszczy elementu klienta.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Parametry

*dwCloseOption (Kolosaopcja)*<br/>
Flaga określająca, w jakich okolicznościach element OLE jest zapisywany po powrocie do załadowanego stanu. Aby uzyskać listę możliwych wartości, zobacz [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Uwagi

Nie niszczy elementu klienta.

## <a name="see-also"></a>Zobacz też

[Próbka MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Klasa CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)
