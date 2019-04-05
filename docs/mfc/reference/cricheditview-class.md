---
title: Klasa CRichEditView
ms.date: 11/04/2016
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
ms.openlocfilehash: 60eeaa2a37dd824ae418b25e95743c21c65ae7ce
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773726"
---
# <a name="cricheditview-class"></a>Klasa CRichEditView

Za pomocą [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) i [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), zapewnia funkcję rozwiniętej kontroli edycji w kontekście architektury widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView::CRichEditView](#cricheditview)|Konstruuje `CRichEditView` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Przesuwa okno dialogowe, aby go nie może zasłaniać bieżącego zaznaczenia.|
|[CRichEditView::CanPaste](#canpaste)|Informuje, czy Schowek zawiera dane, które można wkleić do widoku bogatej edycji.|
|[CRichEditView::DoPaste](#dopaste)|Wkleja element OLE do tego widoku bogatej edycji.|
|[CRichEditView::FindText](#findtext)|Znajduje określony tekst, wywołując kursor oczekiwania.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Znajduje określony tekst.|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Pobiera znak formatowanie atrybutów dla bieżącego zaznaczenia.|
|[CRichEditView::GetDocument](#getdocument)|Pobiera wskaźnik do powiązane [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md).|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Pobiera element OLE, który jest obecnie aktywny w miejscu w widoku bogatej edycji.|
|[CRichEditView::GetMargins](#getmargins)|Pobiera marginesy dla tego widoku bogatej edycji.|
|[CRichEditView::GetPageRect](#getpagerect)|Pobiera prostokąt strony dla tego widoku bogatej edycji.|
|[CRichEditView::GetPaperSize](#getpapersize)|Pobiera rozmiar papieru dla tego widoku bogatej edycji.|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Pobiera atrybuty dla bieżącego zaznaczenia formatowania akapitu.|
|[CRichEditView::GetPrintRect](#getprintrect)|Pobiera drukowania prostokąt dla tego widoku bogatej edycji.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Pobiera szerokość wydruku dla tego widoku bogatej edycji.|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Pobiera rozwiniętej kontroli edycji.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Pobiera zaznaczony element z widoku bogatej edycji.|
|[CRichEditView::GetTextLength](#gettextlength)|Pobiera długość tekstu w widoku bogatej edycji.|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Pobiera liczbę znaków lub liczbę bajtów w widoku bogatej edycji. Lista flagi rozwiniętej metoda określania długości.|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Wstawia plik jako element OLE.|
|[CRichEditView::InsertItem](#insertitem)|Wstawia nowy element jako element OLE.|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Informuje, czy Schowek zawiera dane w formacie tekstowym lub bogatej edycji.|
|[CRichEditView::OnCharEffect](#onchareffect)|Włącza/wyłącza formatowania dla bieżącego zaznaczenia znaków.|
|[CRichEditView::OnParaAlign](#onparaalign)|Zmienia wyrównanie akapitach.|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Aktualizacje poleceń interfejsu użytkownika dla znaków publiczne funkcje Członkowskie.|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Aktualizacje poleceń interfejsu użytkownika dla funkcji składowych publicznych akapitu.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Formatuje określony tekst w obrębie danego prostokąta.|
|[CRichEditView::PrintPage](#printpage)|Formatuje tekst określony w ramach danej strony.|
|[CRichEditView::SetCharFormat](#setcharformat)|Określa formatowanie atrybutów dla bieżącego zaznaczenia znaków.|
|[CRichEditView::SetMargins](#setmargins)|Ustawia marginesy to Zaawansowane edytowanie widoku.|
|[CRichEditView::SetPaperSize](#setpapersize)|Ustawia rozmiar papieru dla tego widoku bogatej edycji.|
|[CRichEditView::SetParaFormat](#setparaformat)|Określa formatowanie atrybutów dla bieżącego zaznaczenia akapitu.|
|[CRichEditView::TextNotFound](#textnotfound)|Resetuje stan wewnętrzny wyszukiwania kontrolki.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Pobiera obiekt Schowka dla zakresu tego widoku bogatej edycji.|
|[CRichEditView::GetContextMenu](#getcontextmenu)|Pobiera menu kontekstowe na korzystanie z prawego przycisku myszy w dół.|
|[CRichEditView::IsSelected](#isselected)|Wskazuje, jeśli dany element OLE jest zaznaczone, czy nie.|
|[CRichEditView::OnFindNext](#onfindnext)|Znajduje następne wystąpienie podciągu.|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Odświeżanie widoku, gdy po raz pierwszy dołączony do dokumentu.|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Pobiera dane natywne z elementu OLE.|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Ustawia parametry wydruku dla danego urządzenia.|
|[CRichEditView::OnReplaceAll](#onreplaceall)|Zamienia wszystkie wystąpienia podanego ciągu nowy ciąg.|
|[CRichEditView::OnReplaceSel](#onreplacesel)|Zamienia bieżące zaznaczenie.|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Obsługuje powiadomienia użytkownika, którego nie można odnaleźć żądanego tekstu.|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Zapytania, aby wyświetlić dotyczące danych na `IDataObject`.|
|[CRichEditView::WrapChanged](#wrapchanged)|Dostosowuje docelowe urządzenie wyjściowe dla tej kontrolki tekstu sformatowanego widok, w oparciu o wartość `m_nWordWrap`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Wskazuje wielkość wcięcia dla listy wypunktowane.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Wskazuje ograniczenia zawijania programu word.|

## <a name="remarks"></a>Uwagi

"Kontrolki edycji wzbogaconej" to okno, w którym użytkownik może wprowadzić i edytować tekst. Tekst można przypisać znaków i formatowanie akapitów i mogą zawierać osadzonych obiektów OLE. Kontrolki edycji wzbogaconej dostarczające interfejs programowania do formatowania tekstu. Jednak aplikacja musi zaimplementować wszelkie niezbędne udostępnić użytkownikowi operacji formatowania składników interfejsu użytkownika.

`CRichEditView` przechowuje tekst i właściwości formatowania tekstu. `CRichEditDoc` przechowuje listę elementów klienta OLE, które znajdują się w widoku. `CRichEditCntrItem` udostępnia siebie kontener elementu klienta OLE.

Ten formant Windows wspólnej (i w związku z tym [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i pokrewne klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.

Aby uzyskać przykład korzystania z widoku bogatej edycji w aplikacji MFC, zobacz [WORDPAD](../../overview/visual-cpp-samples.md) przykładowej aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrich.h

##  <a name="adjustdialogposition"></a>  CRichEditView::AdjustDialogPosition

Wywołaj tę funkcję, aby przenieść okno dialogowe danego, tak, aby nie mogą zasłaniać bieżącego zaznaczenia.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parametry

*pDlg*<br/>
Wskaźnik do `CDialog` obiektu.

##  <a name="canpaste"></a>  CRichEditView::CanPaste

Wywołaj tę funkcję, aby określić, gdy Schowek zawiera dane, które można wkleić do tego widoku bogatej edycji.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli Schowek zawiera dane w formacie, który może zaakceptować tego widoku bogatej edycji; w przeciwnym razie 0.

##  <a name="cricheditview"></a>  CRichEditView::CRichEditView

Wywołaj tę funkcję, aby utworzyć `CRichEditView` obiektu.

```
CRichEditView();
```

##  <a name="dopaste"></a>  CRichEditView::DoPaste

Wywołaj tę funkcję, aby wkleić elementu OLE w *dataobj* do tego dokumentu/widoku edycji wzbogaconej.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Parametry

*dataobj*<br/>
[COleDataObject](../../mfc/reference/coledataobject-class.md) zawierający dane do wklejenia.

*cf*<br/>
Żądany format Schowka.

*hMetaPict*<br/>
Metaplik reprezentujący element do wklejenia.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję, jako część domyślna Implementacja klasy [QueryAcceptData](#queryacceptdata).

Ta funkcja określa typ Wklej na podstawie wyników procedury obsługi dla Wklej specjalne. Jeśli *cf* wynosi 0, nowy element używa bieżącej reprezentacji ikony. Jeśli *cf* jest różna od zera i *hMetaPict* nie ma wartości NULL, używa nowego elementu *hMetaPict* na jego reprezentację w postaci.

##  <a name="findtext"></a>  CRichEditView::FindText

Wywołaj tę funkcję, aby znaleźć określony tekst i ustaw ją jako bieżącego zaznaczenia.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Zawiera ciąg do wyszukania.

*bCase*<br/>
Wskazuje, jeśli w wyszukiwaniu jest uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, jeśli wyszukiwanie powinien być zgodny tylko całe wyrazy, nie części słowa.

*bDalej*<br/>
Wskazuje kierunek wyszukiwania. W przypadku opcji TRUE kierunek wyszukiwania jest pod koniec buforu. W przypadku wartości FAŁSZ kierunek wyszukiwania jest kierunku początku buforu.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera *lpszFind* tekst zostanie odnaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja ta wyświetla kursor oczekiwania podczas operacji wyszukiwania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>  CRichEditView::FindTextSimple

Wywołaj tę funkcję, aby znaleźć określony tekst i ustaw ją jako bieżącego zaznaczenia.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Zawiera ciąg do wyszukania.

*bCase*<br/>
Wskazuje, jeśli w wyszukiwaniu jest uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, jeśli wyszukiwanie powinien być zgodny tylko całe wyrazy, nie części słowa.

*bDalej*<br/>
Wskazuje kierunek wyszukiwania. W przypadku opcji TRUE kierunek wyszukiwania jest pod koniec buforu. W przypadku wartości FAŁSZ kierunek wyszukiwania jest kierunku początku buforu.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera *lpszFind* tekst zostanie odnaleziony; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::FindText](#findtext).

##  <a name="getcharformatselection"></a>  CRichEditView::GetCharFormatSelection

Wywołaj tę funkcję, aby pobrać formatowanie atrybutów bieżącego zaznaczenia znaków.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Wartość zwracana

A [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) strukturę, która zawiera znak, formatowanie atrybutów bieżącego zaznaczenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETCHARFORMAT](/windows/desktop/Controls/em-getcharformat) wiadomości i [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) struktury w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>  CRichEditView::GetClipboardData

Struktura wywołuje tę funkcję w ramach przetwarzania [IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Parametry

*lpchrg*<br/>
Wskaźnik do [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) struktury, określając zakres znaków (i elementy OLE), aby skopiować obiekt danych określonego przez *lplpdataobj*.

*dwReco*<br/>
Flaga operację Schowka. Może być jedną z następujących wartości.

- RECO_COPY kopiowania do Schowka.

- RECO_CUT wyciąć do Schowka.

- Operacja przeciągania RECO_DRAG (przeciąganie i upuszczanie).

- RECO_DROP upuszczania (przeciąganie i upuszczanie).

- RECO_PASTE wklejaniu ze Schowka.

*lpRichDataObj*<br/>
Wskaźnik do [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) formant edycji obiekt zawierający dane Schowka z zaawansowanych ( [IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Wskaźnik do zmiennej wskaźnika, który otrzymuje adres `IDataObject` obiekt reprezentujący zakresem określonym w *lpchrg* parametru. Wartość *lplpdataobj* jest ignorowana, jeśli zostanie zwrócony błąd.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT zgłaszanie powodzenia operacji. Aby uzyskać więcej informacji na temat HRESULT, zobacz [struktury COM kody błędów](/windows/desktop/com/structure-of-com-error-codes) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli zwracana wartość wskazuje Powodzenie, `IRichEditOleCallback::GetClipboardData` zwraca `IDataObject` uzyskiwał dostęp do *lplpdataobj*; w przeciwnym razie zwraca jeden uzyskują *lpRichDataObj*. Należy przesłonić tę funkcję, aby dostarczyć dane Schowka. Domyślna implementacja ta funkcja zwraca E_NOTIMPL.

Jest to zaawansowany możliwym do zastąpienia.

Aby uzyskać więcej informacji, zobacz [IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata), i [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) w zestawie Windows SDK i zobacz [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) w Windows SDK.

##  <a name="getcontextmenu"></a>  CRichEditView::GetContextMenu

Struktura wywołuje tę funkcję w ramach przetwarzania [IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu).

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parametry

*seltyp*<br/>
Typ wyboru. Wybór typu wartości są opisane w sekcji uwag.

*lpoleobj*<br/>
Wskaźnik do `OLEOBJECT` struktury, określając pierwszego wybranego obiektu OLE, jeśli zaznaczenie zawiera jeden lub więcej elementów OLE. Jeśli zaznaczenie nie zawiera żadnych elementów *lpoleobj* ma wartość NULL. `OLEOBJECT` Struktury przechowuje wskaźnik do obiektu OLE v tabeli.

*lpchrg*<br/>
Wskaźnik do [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) struktury zawierającej bieżącego zaznaczenia.

### <a name="return-value"></a>Wartość zwracana

Dojście do menu kontekstowego.

### <a name="remarks"></a>Uwagi

Ta funkcja jest typowy część prawym przyciskiem myszy w dół do przetwarzania.

Typ wyboru może być dowolną kombinacją następujących flag:

- SEL_EMPTY wskazuje, że nie ma bieżącego zaznaczenia.

- SEL_TEXT wskazuje, że bieżące zaznaczenie zawiera tekst.

- SEL_OBJECT wskazuje, że bieżące zaznaczenie zawiera co najmniej jeden element OLE.

- SEL_MULTICHAR wskazuje, że bieżące zaznaczenie zawiera więcej niż jeden znak tekstu.

- SEL_MULTIOBJECT wskazuje, że bieżące zaznaczenie zawiera więcej niż jeden obiekt OLE.

Domyślna implementacja zwraca wartość NULL. Jest to zaawansowany możliwym do zastąpienia.

Aby uzyskać więcej informacji, zobacz [IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu) i [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) w zestawie Windows SDK.

##  <a name="getdocument"></a>  CRichEditView::GetDocument

Wywołaj tę funkcję, aby uzyskać wskaźnik do `CRichEditDoc` skojarzonego z tym widokiem.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) obiekt skojarzony z Twojej `CRichEditView` obiektu.

##  <a name="getinplaceactiveitem"></a>  CRichEditView::GetInPlaceActiveItem

Wywołanie elementu tę funkcję, aby pobrać OLE, który jest aktywowany w miejscu, w tym `CRichEditView` obiektu.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywnego pojedynczy, w miejscu [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiektu tego widoku bogatej edycji; Wartość NULL, jeśli nie ma żadnego elementu OLE w stanie aktywnym w miejscu.

##  <a name="getmargins"></a>  CRichEditView::GetMargins

Wywołaj tę funkcję można pobrać bieżących marginesów używane podczas drukowania.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Wartość zwracana

Marginesy używane w drukowaniu, mierzone w MM_TWIPS.

##  <a name="getpagerect"></a>  CRichEditView::GetPageRect

Wywołaj tę funkcję można pobrać wymiary strony drukowania.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Granice strony wydruku, mierzone w MM_TWIPS.

### <a name="remarks"></a>Uwagi

Ta wartość jest oparta na rozmiar papieru.

##  <a name="getpapersize"></a>  CRichEditView::GetPaperSize

Wywołaj tę funkcję, aby pobrać bieżący rozmiar papieru.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar papieru, używany w drukowaniu, mierzone w MM_TWIPS.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>  CRichEditView::GetParaFormatSelection

Wywołaj tę funkcję, aby pobrać atrybuty bieżącego zaznaczenia formatowania akapitu.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Wartość zwracana

A [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) strukturę, która zawiera atrybuty bieżącego zaznaczenia formatowania akapitu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETPARAFORMAT](/windows/desktop/Controls/em-getparaformat) wiadomości i [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) struktury w zestawie Windows SDK.

##  <a name="getprintrect"></a>  CRichEditView::GetPrintRect

Wywołaj tę funkcję, aby pobrać granice obszar drukowania w prostokącie strony.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Granice obszaru obrazu używanego w drukowaniu, mierzone w MM_TWIPS.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>  CRichEditView::GetPrintWidth

Wywołaj tę funkcję, aby określić szerokość obszaru drukowania.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość obszaru drukowania, mierzone w MM_TWIPS.

##  <a name="getricheditctrl"></a>  CRichEditView::GetRichEditCtrl

Wywołaj tę funkcję, aby pobrać [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) obiekt skojarzony z `CRichEditView` obiektu.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

`CRichEditCtrl` Obiektu dla tego widoku.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::FindText](#findtext).

##  <a name="getselecteditem"></a>  CRichEditView::GetSelectedItem

Wywołaj tę funkcję, aby pobrać element OLE ( `CRichEditCntrItem` obiektu) aktualnie wybrane w tym `CRichEditView` obiektu.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiektu wybranego w `CRichEditView` obiektu; Wartość NULL, jeśli nie wybrano elementu w tym widoku.

##  <a name="gettextlength"></a>  CRichEditView::GetTextLength

Wywołaj tę funkcję, aby odczytać długość tekstu, w tym `CRichEditView` obiektu.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość tekstu, w tym `CRichEditView` obiektu.

##  <a name="gettextlengthex"></a>  CRichEditView::GetTextLengthEx

Wywołaj tę funkcję elementu członkowskiego, aby obliczyć długość tekstu, w tym `CRichEditView` obiektu.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parametry

*Flagidw*<br/>
Wartość określająca metoda do użycia przy określaniu długość tekstu. Ten element członkowski może być jedną lub więcej wartości wymienione w flagi członkiem [GETTEXTLENGTHEX](/windows/desktop/api/richedit/ns-richedit-_gettextlengthex) opisanego w zestawie Windows SDK.

*uCodePage*<br/>
Strona kodowa tłumaczenia (CP_ACP dla strony kodowej ANSI, 1200 dla standardu Unicode).

### <a name="return-value"></a>Wartość zwracana

Liczba znaków lub liczbę bajtów w formancie edycji. Jeśli stan został ustawiony niezgodnymi flagami *Flagidw*, ta funkcja elementu członkowskiego zwraca E_INVALIDARG.

### <a name="remarks"></a>Uwagi

`GetTextLengthEx` udostępnia dodatkowe sposoby określania długości tekstu. Obsługuje funkcje Zaawansowane edytowanie w wersji 2.0. Aby uzyskać więcej informacji, zobacz [o Zaawansowane formanty edycji](/windows/desktop/Controls/about-rich-edit-controls) w zestawie Windows SDK.

##  <a name="insertfileasobject"></a>  CRichEditView::InsertFileAsObject

Wywołaj tę funkcję, aby wstawić określonego pliku (jako [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiektu) do Zaawansowane edytowanie widoku.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg zawierający nazwę pliku, który ma zostać wstawiony.

##  <a name="insertitem"></a>  CRichEditView::InsertItem

Wywołaj tę funkcję, aby wstawić [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiekt w widoku bogatej edycji.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik do elementu, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT informujący o powodzeniu wstawiania.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat HRESULT, zobacz [struktury COM kody błędów](/windows/desktop/com/structure-of-com-error-codes) w zestawie Windows SDK.

##  <a name="isricheditformat"></a>  CRichEditView::IsRichEditFormat

Wywołaj tę funkcję, aby określić, czy *cf* jest format Schowka, czyli tekstu, tekst sformatowany lub tekstu sformatowanego przy użyciu elementów OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Format schowka zainteresowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera *cf* sformatowanego format schowka edycji lub tekstu.

##  <a name="isselected"></a>  CRichEditView::IsSelected

Wywołaj tę funkcję, aby określić, jeśli określony element OLE jest aktualnie wybrany w tym widoku.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Wskaźnik do obiektu w widoku.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt jest wybrany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, jeśli Klasa pochodna widoku ma inną metodę obsługi zaznaczenia elementów OLE.

##  <a name="m_nbulletindent"></a>  CRichEditView::m_nBulletIndent

Wcięcie punktora elementów na liście; Domyślnie 720 jednostki, która jest 1/2 cala.

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>  CRichEditView::m_nWordWrap

Wskazuje typ zawijania dla tego widoku bogatej edycji.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Uwagi

Jeden z następujących wartości:

- `WrapNone` Wskazuje nie zawijanie wyrazów automatyczne.

- `WrapToWindow` Wskazuje, zawijanie wyrazów, w oparciu o szerokości okna.

- `WrapToTargetDevice` Wskazuje, zawijanie wyrazów na podstawie właściwości urządzenia docelowego.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::WrapChanged](#wrapchanged).

##  <a name="onchareffect"></a>  CRichEditView::OnCharEffect

Wywołaj tę funkcję, aby przełączyć formatowanie efekty dla bieżącego zaznaczenia znaków.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*dwMask*<br/>
Formatowanie znaków efekty do modyfikowania w bieżącym zaznaczeniu.

*dwEffect*<br/>
Odpowiednią listę formatowanie efekty, aby przełączyć znaków.

### <a name="remarks"></a>Uwagi

Każde wywołanie tej funkcji przełącza określony efekty formatowania dla bieżącego zaznaczenia.

Aby uzyskać więcej informacji na temat *dwMask* i *dwEffect* parametrów i ich potencjalnych wartości, zobacz odpowiednie dane elementów członkowskich [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>  CRichEditView::OnFindNext

Wywoływane przez platformę podczas przetwarzania polecenia z okna dialogowego Znajdowanie i zamienianie.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Ciąg do znalezienia.

*bDalej*<br/>
Kierunek wyszukiwania: Wartość TRUE wskazuje "False" działa.

*bCase*<br/>
Wskazuje, czy wyszukiwanie ma być uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, czy wyszukiwanie ma dopasowywać całe wyrazy, tylko, czy nie.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby wyszukać tekst w obrębie `CRichEditView`. Należy przesłonić tę funkcję, aby zmienić właściwości wyszukiwania dla klasy pochodnej widoku.

##  <a name="oninitialupdate"></a>  CRichEditView::OnInitialUpdate

Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja ta funkcja wywołuje [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) funkcji składowej bez informacji o wskazówki (oznacza to, używanie domyślnych wartości 0 dla *lHint* parametr i wartość NULL w przypadku *pHint* parametru). Należy przesłonić tę funkcję, by wykonać jednorazowe inicjowanie, która wymaga informacji o dokumencie. Na przykład jeśli aplikacja zawiera dokumenty o stałym rozmiarze, umożliwia tej funkcji inicjowania widoku limity przewijania w zależności od rozmiaru dokumentu. Jeśli aplikacja obsługuje dokumenty o zmiennym rozmiarze, użyj `OnUpdate` można zaktualizować przewijania ogranicza każdym razem, gdy zmiany w dokumencie.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::m_nWordWrap](#m_nwordwrap).

##  <a name="onpastenativeobject"></a>  CRichEditView::OnPasteNativeObject

Aby załadować dane natywne z osadzonego elementu, należy użyć tej funkcji.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parametry

*lpStg*<br/>
Wskaźnik do [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zwykle będzie to zrobisz, tworząc [COleStreamFile](../../mfc/reference/colestreamfile-class.md) wokół `IStorage`. `COleStreamFile` Mogą być dołączane do archiwum i [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) wywołuje się, jak załadować dane.

Jest to zaawansowany możliwym do zastąpienia.

Aby uzyskać więcej informacji, zobacz [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) w zestawie Windows SDK.

##  <a name="onparaalign"></a>  CRichEditView::OnParaAlign

Wywołaj tę funkcję, aby zmienić wyrównanie akapitu dla wybranych akapitach.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parametry

*wAlign*<br/>
Żądane wyrównanie akapitu. Jeden z następujących wartości:

- PFA_LEFT wyrównanie akapitów z lewego marginesu.

- PFA_RIGHT wyrównanie akapitów do prawego marginesu.

- PFA_CENTER Centrum akapitów między marginesów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>  CRichEditView::OnPrinterChanged

Należy przesłonić tę funkcję, aby zmienić właściwości dla tego widoku bogatej edycji, gdy zmieni się drukarki.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parametry

*dcPrinter*<br/>
A [CDC](../../mfc/reference/cdc-class.md) obiektu dla nowej drukarki.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ustawia rozmiar papieru fizycznych wysokość i szerokość dla urządzenia wyjściowego (drukarki). W przypadku kontekstu urządzenia skojarzone z *dcPrinter*, domyślna implementacja ustawia rozmiar papieru 8,5 przez x 11 cali.

##  <a name="onreplaceall"></a>  CRichEditView::OnReplaceAll

Wywoływane przez platformę podczas przetwarzania Zastąp wszystkie polecenia z okna dialogowego Zastąp.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać zastąpione.

*lpszReplace*<br/>
Tekst zastępczy.

*bCase*<br/>
Wskazuje, jeśli w wyszukiwaniu jest uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, jeśli wyszukiwanie należy wybrać całe wyrazy, czy nie.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zastąpić wszystkie wystąpienia danego tekst z innego ciągu. Należy przesłonić tę funkcję, aby zmienić właściwości wyszukiwania dla tego widoku.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::FindText](#findtext).

##  <a name="onreplacesel"></a>  CRichEditView::OnReplaceSel

Wywoływane przez platformę podczas przetwarzania polecenia Zastąp z okna dialogowego Zastąp.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać zastąpione.

*bDalej*<br/>
Wskazuje kierunek wyszukiwania: Wartość TRUE jest wyłączony; "False" działa.

*bCase*<br/>
Wskazuje, jeśli w wyszukiwaniu jest uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, jeśli wyszukiwanie należy wybrać całe wyrazy, czy nie.

*lpszReplace*<br/>
Tekst zastępczy.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zastąpić jedno wystąpienie danego tekst z innego ciągu. Należy przesłonić tę funkcję, aby zmienić właściwości wyszukiwania dla tego widoku.

##  <a name="ontextnotfound"></a>  CRichEditView::OnTextNotFound

Wywoływane przez platformę, zawsze wtedy, gdy wyszukiwanie nie powiedzie się.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który nie został odnaleziony.

### <a name="remarks"></a>Uwagi

Przesłonić tę funkcję, aby zmienić powiadomienie dane wyjściowe z [MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep).

Aby uzyskać więcej informacji, zobacz [MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>  CRichEditView::OnUpdateCharEffect

Struktura wywołuje tę funkcję, aby zaktualizować poleceń interfejsu użytkownika dla poleceń efekt znaków.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiektu.

*dwMask*<br/>
Określa formatowanie maski znaków.

*dwEffect*<br/>
Określa formatowanie efekt znaków.

### <a name="remarks"></a>Uwagi

Maska *dwMask* Określa, który znak w atrybutach formatowania, aby sprawdzić. Flagi *dwEffect* listę atrybutów, które mają zestaw/Wyczyść formatowanie znaków.

Aby uzyskać więcej informacji na temat *dwMask* i *dwEffect* parametrów i ich potencjalnych wartości, zobacz odpowiednie dane elementów członkowskich [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>  CRichEditView::OnUpdateParaAlign

Struktura wywołuje tę funkcję, aby zaktualizować poleceń interfejsu użytkownika dla poleceń efekt akapitu.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiektu.

*wAlign*<br/>
Wyrównanie akapitu do sprawdzenia. Jeden z następujących wartości:

- PFA_LEFT wyrównanie akapitów z lewego marginesu.

- PFA_RIGHT wyrównanie akapitów do prawego marginesu.

- PFA_CENTER Centrum akapitów między marginesów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>  CRichEditView::PrintInsideRect

Wywołaj tę funkcję, aby sformatować zakres tekstu w formancie edycji wzbogaconej w celu dopasowania *rectLayout* dla urządzenia określonego przez *kontrolera pDC*.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia dla obszaru danych wyjściowych.

*rectLayout*<br/>
[Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) definiujący obszaru wyjściowego.

*nIndexStart*<br/>
Liczony od zera indeks pierwszego wystąpienia znaku do sformatowania.

*nIndexStop*<br/>
Liczony od zera indeks ostatniego znaku do sformatowania.

*bOutput*<br/>
Wskazuje, czy tekst powinien być renderowany. W przypadku wartości FAŁSZ mierzy się tylko tekst.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatni znak, który pasuje do obszaru wyjściowego plus jeden.

### <a name="remarks"></a>Uwagi

Zwykle to wywołanie następuje po wywołaniu [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) która generuje dane wyjściowe.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::GetPaperSize](#getpapersize).

##  <a name="printpage"></a>  CRichEditView::PrintPage

Wywołaj tę funkcję, aby sformatować zakres tekstu w formancie edycji wzbogaconej na urządzeniu wyjściowym określonym przez *kontrolera pDC*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia dla danych wyjściowych strony.

*nIndexStart*<br/>
Liczony od zera indeks pierwszego wystąpienia znaku do sformatowania.

*nIndexStop*<br/>
Liczony od zera indeks ostatniego znaku do sformatowania.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatni znak, który mieści się na stronie plus jeden.

### <a name="remarks"></a>Uwagi

Układ każdej strony jest kontrolowana przez [GetPageRect](#getpagerect) i [GetPrintRect](#getprintrect). Zwykle to wywołanie następuje po wywołaniu [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) która generuje dane wyjściowe.

Należy pamiętać, że marginesy są względne wobec strony fizycznej strony logicznej. W związku z tym marginesy zero będzie często obcina tekst, ponieważ wiele drukarek ma nie do drukowania obszarów na stronie. Aby uniknąć przycinanie tekstu, należy wywołać [SetMargins](#setmargins) i ustawić marginesy uzasadnione, przed rozpoczęciem drukowania.

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

Metoda wywoływana przez platformę, by wkleić obiekt do bogatej edycji.

```
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,
    CLIPFORMAT* lpcfFormat,
    DWORD dwReco,
    BOOL bReally,
    HGLOBAL hMetaFile);
```

### <a name="parameters"></a>Parametry

*lpdataobj*<br/>
Wskaźnik do [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) do wykonywania zapytań.

*lpcfFormat*<br/>
Wskaźnik do formatu utraconych danych.

*dwReco*<br/>
Nie używany.

*bReally*<br/>
Wskazuje, jeśli operacja wklejania powinno być kontynuowane, czy nie.

*hMetaFile*<br/>
Dojście do metaplik używany do rysowania ikona elementu.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT zgłaszanie powodzenia operacji.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby obsłużyć innej organizacji elementów modelu COM w klasie pochodnej dokumentu. Jest to zaawansowany możliwym do zastąpienia.

Aby uzyskać więcej informacji na temat HRESULT i `IDataObject`, zobacz [struktury COM kody błędów](/windows/desktop/com/structure-of-com-error-codes) i [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)odpowiednio w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>  CRichEditView::SetCharFormat

Wywołaj tę funkcję, aby ustawić formatowanie atrybutów dla nowego tekstu w tym znaków `CRichEditView` obiektu.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) struktury zawierającej znak nowego domyślnego formatowanie atrybutów.

### <a name="remarks"></a>Uwagi

Tylko atrybuty określone przez `dwMask` członkiem *cf* są zmieniane przez tę funkcję.

Aby uzyskać więcej informacji, zobacz [EM_SETCHARFORMAT](/windows/desktop/Controls/em-setcharformat) wiadomości i [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) struktury w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>  CRichEditView::SetMargins

Wywołaj tę funkcję, aby ustawić marginesy drukowania dla tego widoku bogatej edycji.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parametry

*rectMargin*<br/>
Nowe wartości marginesów wydruku, mierzone w MM_TWIPS.

### <a name="remarks"></a>Uwagi

Jeśli [m_nWordWrap](#m_nwordwrap) jest `WrapToTargetDevice`, należy wywołać [WrapChanged](#wrapchanged) po użyciu tę funkcję, aby dostosować ustawienia drukowania.

Należy zauważyć, że posługują się marginesy [PrintPage](#printpage) są względne wobec strony fizycznej strony logicznej. W związku z tym marginesy zero będzie często obcina tekst, ponieważ wiele drukarek ma nie do drukowania obszarów na stronie. Aby uniknąć przycinanie tekstu, należy wywołać użyj `SetMargins` można ustawić marginesy uzasadnione drukarki, przed rozpoczęciem drukowania.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::GetPaperSize](#getpapersize).

##  <a name="setpapersize"></a>  CRichEditView::SetPaperSize

Wywołaj tę funkcję, aby ustawić rozmiar papieru do drukowania tego widoku bogatej edycji.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parametry

*sizePaper*<br/>
Nowe wartości rozmiar papieru do drukowania, mierzone w MM_TWIPS.

### <a name="remarks"></a>Uwagi

Jeśli [m_nWordWrap](#m_nwordwrap) jest `WrapToTargetDevice`, należy wywołać [WrapChanged](#wrapchanged) po użyciu tę funkcję, aby dostosować ustawienia drukowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>  CRichEditView::SetParaFormat

Wywołaj tę funkcję, aby ustawić atrybuty dla bieżącego zaznaczenia w tym formatowania akapitów `CRichEditView` obiektu.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parametry

*pf*<br/>
[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) struktury zawierającej nowym domyślnym akapitu atrybuty formatowania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Tylko atrybuty określone przez `dwMask` członkiem *pf* są zmieniane przez tę funkcję.

Aby uzyskać więcej informacji, zobacz [EM_SETPARAFORMAT](/windows/desktop/Controls/em-setparaformat) wiadomości i [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) struktury w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>  CRichEditView::TextNotFound

Wywołaj tę funkcję, aby zresetować stan wewnętrzny wyszukiwania [CRichEditView](../../mfc/reference/cricheditview-class.md) kontroli po wywołaniu nie powiodło się [FindText](#findtext).

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Zawiera ciąg tekstowy, który nie został znaleziony.

### <a name="remarks"></a>Uwagi

Zalecane jest, że tej metody można wywołać natychmiast po zakończonymi niepowodzeniem wywołaniami do [FindText](#findtext) tak, aby prawidłowo zresetowaniu stan wewnętrzny wyszukiwania kontrolki.

*LpszFind* parametr powinien zawierać taką samą zawartość jako ciąg do [FindText](#findtext). Po przywróceniu stanu wewnętrznego wyszukiwania, Metoda ta będzie wywoływać [OnTextNotFound](#ontextnotfound) metody za pomocą podanego ciągu.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::FindText](#findtext).

##  <a name="wrapchanged"></a>  CRichEditView::WrapChanged

Wywołaj tę funkcję, gdy zmieniono ustawienia drukowania ( [SetMargins](#setmargins) lub [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Uwagi

Override tę funkcję, aby zmodyfikować sposób, w widoku edycji wzbogaconej reaguje na zmiany w [m_nWordWrap](#m_nwordwrap) lub drukowania cechy ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc Class](../../mfc/reference/cricheditdoc-class.md)<br/>
[Klasa CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)
