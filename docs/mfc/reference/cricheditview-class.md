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
ms.openlocfilehash: b32578cc3c9ad4f7a89b8ee76449259c0fa0b43b
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741510"
---
# <a name="cricheditview-class"></a>Klasa CRichEditView

Funkcja [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) i [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)udostępnia funkcje kontrolki edycji wzbogaconej w kontekście architektury widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView:: CRichEditView](#cricheditview)|Konstruuje `CRichEditView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView:: AdjustDialogPosition](#adjustdialogposition)|Przenosi okno dialogowe, aby nie zasłaniał bieżącego zaznaczenia.|
|[CRichEditView:: Ostatnia próba](#canpaste)|Wskazuje, czy Schowek zawiera dane, które można wkleić do widoku zaawansowanej edycji.|
|[CRichEditView::D oPaste](#dopaste)|Wkleja element OLE do tego widoku wzbogaconej edycji.|
|[CRichEditView:: ciąg FindText](#findtext)|Znajduje określony tekst, wywołując kursor oczekiwania.|
|[CRichEditView:: FindTextSimple](#findtextsimple)|Znajduje określony tekst.|
|[CRichEditView:: GetCharFormatSelection](#getcharformatselection)|Pobiera atrybuty formatowania znaku dla bieżącego zaznaczenia.|
|[CRichEditView:: GetDocument](#getdocument)|Pobiera wskaźnik do powiązanej [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md).|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Pobiera element OLE, który jest obecnie aktywny w widoku edycji wzbogaconej.|
|[CRichEditView:: GetMargins](#getmargins)|Pobiera marginesy dla tego widoku wzbogaconej edycji.|
|[CRichEditView:: GetPageRect](#getpagerect)|Pobiera prostokąt strony dla tego widoku wzbogaconej edycji.|
|[CRichEditView:: GetPaperSize](#getpapersize)|Pobiera rozmiar papieru dla tego widoku wzbogaconej edycji.|
|[CRichEditView:: GetParaFormatSelection](#getparaformatselection)|Pobiera atrybuty formatowania akapitu dla bieżącego zaznaczenia.|
|[CRichEditView:: GetPrintRect](#getprintrect)|Pobiera prostokąt drukowania dla tego widoku wzbogaconej edycji.|
|[CRichEditView:: GetPrintWidth](#getprintwidth)|Pobiera szerokość wydruku dla tego widoku wzbogaconej edycji.|
|[CRichEditView:: GetRichEditCtrl](#getricheditctrl)|Pobiera formant edycji wzbogaconej.|
|[CRichEditView:: GetSelectedItem](#getselecteditem)|Pobiera wybrany element z widoku edycji wzbogaconej.|
|[CRichEditView:: GetTextLength](#gettextlength)|Pobiera długość tekstu w widoku edycji wzbogaconej.|
|[CRichEditView:: GetTextLengthEx](#gettextlengthex)|Pobiera liczbę znaków lub bajtów w widoku edycji wzbogaconej. Rozwinięta lista flag dla metody określania długości.|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Wstawia plik jako element OLE.|
|[CRichEditView:: InsertItem](#insertitem)|Wstawia nowy element jako element OLE.|
|[CRichEditView:: IsRichEditFormat](#isricheditformat)|Wskazuje, czy Schowek zawiera dane w formacie sformatowanym lub tekstowym.|
|[CRichEditView:: OnCharEffect](#onchareffect)|Włącza lub wyłącza formatowanie znaków dla bieżącego zaznaczenia.|
|[CRichEditView:: OnParaAlign](#onparaalign)|Zmienia wyrównanie akapitów.|
|[CRichEditView:: OnUpdateCharEffect](#onupdatechareffect)|Aktualizuje interfejs użytkownika poleceń dla funkcji publicznego elementu członkowskiego znaku.|
|[CRichEditView:: OnUpdateParaAlign](#onupdateparaalign)|Aktualizuje interfejs użytkownika poleceń dla publicznych funkcji Członkowskich akapitu.|
|[CRichEditView::P rintInsideRect](#printinsiderect)|Formatuje określony tekst w obrębie danego prostokąta.|
|[CRichEditView::P rintPage](#printpage)|Formatuje określony tekst na danej stronie.|
|[CRichEditView:: SetCharFormat](#setcharformat)|Ustawia atrybuty formatowania znaku dla bieżącego zaznaczenia.|
|[CRichEditView:: Setmargins](#setmargins)|Ustawia marginesy dla tego widoku wzbogaconej edycji.|
|[CRichEditView::SetPaperSize](#setpapersize)|Ustawia rozmiar papieru dla tego widoku wzbogaconej edycji.|
|[CRichEditView:: SetParaFormat](#setparaformat)|Ustawia atrybuty formatowania akapitu dla bieżącego zaznaczenia.|
|[CRichEditView:: TextNotFound](#textnotfound)|Resetuje stan przeszukiwania wewnętrznego formantu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView:: GetClipboardData](#getclipboarddata)|Pobiera obiekt schowka dla zakresu w tym widoku wzbogaconej edycji.|
|[CRichEditView::](#getcontextmenu)|Pobiera menu kontekstowe do użycia w prawym przyciskiem myszy w dół.|
|[CRichEditView:: IsSelected](#isselected)|Wskazuje, czy dany element OLE jest zaznaczony, czy nie.|
|[CRichEditView::OnFindNext](#onfindnext)|Znajduje następne wystąpienie podciągu.|
|[CRichEditView:: OnInitialUpdate](#oninitialupdate)|Odświeża widok, gdy jest on po raz pierwszy dołączony do dokumentu.|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Pobiera dane natywne z elementu OLE.|
|[CRichEditView:: OnPrinterChanged](#onprinterchanged)|Ustawia charakterystykę drukowania dla danego urządzenia.|
|[CRichEditView:: OnReplaceAll](#onreplaceall)|Zamienia wszystkie wystąpienia danego ciągu z nowym ciągiem.|
|[CRichEditView:: OnReplaceSel](#onreplacesel)|Zastępuje bieżące zaznaczenie.|
|[CRichEditView:: OnTextNotFound](#ontextnotfound)|Obsługuje powiadomienie użytkownika, że nie znaleziono żądanego tekstu.|
|[CRichEditView:: QueryAcceptData](#queryacceptdata)|Wykonuje zapytania, aby zobaczyć dane w `IDataObject`.|
|[CRichEditView:: WrapChanged](#wrapchanged)|Dostosowuje docelowe urządzenie wyjściowe dla tego widoku wzbogaconej edycji na podstawie wartości `m_nWordWrap`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView:: m_nBulletIndent](#m_nbulletindent)|Wskazuje liczbę wcięć dla list punktowanych.|
|[CRichEditView:: m_nWordWrap](#m_nwordwrap)|Wskazuje ograniczenia zawijania wyrazów.|

## <a name="remarks"></a>Uwagi

"Kontrolka edycji wzbogaconej" to okno, w którym użytkownik może wprowadzać i edytować tekst. Do tekstu może być przypisany znak i formatowanie akapitu, które mogą zawierać osadzone obiekty OLE. Formanty edycji wzbogaconej zapewniają interfejs programowania do formatowania tekstu. Jednak aplikacja musi zaimplementować wszelkie składniki interfejsu użytkownika niezbędne do udostępnienia użytkownikowi operacji formatowania.

`CRichEditView`Zachowuje cechę tekstu i formatowania tekstu. `CRichEditDoc`zachowuje listę elementów klienta OLE, które znajdują się w widoku. `CRichEditCntrItem`zapewnia dostęp po stronie kontenera do elementu klienta OLE.

Ten typowy formant systemu Windows (i w związku z tym [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i powiązane klasy) jest dostępny tylko dla programów uruchomionych w systemach Windows 95/98 i Windows NT w wersji 3,51 i nowszych.

Przykład korzystania z widoku edycji wzbogaconej w aplikacji MFC można znaleźć w przykładowej aplikacji programu [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrich. h

##  <a name="adjustdialogposition"></a>CRichEditView:: AdjustDialogPosition

Wywołaj tę funkcję, aby przenieść odpowiednie okno dialogowe, aby nie zasłaniać bieżącego zaznaczenia.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parametry

*pDlg*<br/>
Wskaźnik do `CDialog` obiektu.

##  <a name="canpaste"></a>CRichEditView:: Ostatnia próba

Wywołaj tę funkcję, aby określić, czy Schowek zawiera informacje, które można wkleić do widoku wzbogaconej edycji.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Schowek zawiera dane w formacie, który może akceptować ten widok wzbogaconej edycji. w przeciwnym razie 0.

##  <a name="cricheditview"></a>CRichEditView:: CRichEditView

Wywołaj tę funkcję, aby `CRichEditView` utworzyć obiekt.

```
CRichEditView();
```

##  <a name="dopaste"></a>CRichEditView::D oPaste

Wywołaj tę funkcję, aby wkleić element OLE w *dataobj* do tego zaawansowanego dokumentu/widoku edycji.

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
Żądany format schowka.

*hMetaPict*<br/>
Metaplik reprezentujący element, który ma zostać wklejony.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję jako część domyślnej implementacji [QueryAcceptData](#queryacceptdata).

Ta funkcja określa typ wklejania w oparciu o wyniki procedury obsługi dla wklejania specjalnego. Jeśli *CF* ma wartość 0, nowy element używa bieżącej reprezentacji ikon. Jeśli *CF* jest różna od zera, a *hMetaPict* nie ma wartości null, nowy element używa *hMetaPict* do reprezentowania.

##  <a name="findtext"></a>CRichEditView:: ciąg FindText

Wywołaj tę funkcję, aby znaleźć określony tekst i ustaw go jako bieżący wybór.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Zawiera ciąg, który ma zostać wyszukany.

*bCase*<br/>
Wskazuje, czy w wyszukiwaniu jest uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, czy wyszukiwanie powinno uwzględniać tylko całe wyrazy, nie części wyrazów.

*bNext*<br/>
Wskazuje kierunek wyszukiwania. W przypadku wartości TRUE kierunek wyszukiwania jest skierowany ku końcu buforu. W przypadku wartości FALSE kierunek wyszukiwania jest skierowany do początku buforu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zostanie znaleziony tekst *lpszFind* ; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja wyświetla kursor oczekiwania podczas operacji znajdowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>CRichEditView:: FindTextSimple

Wywołaj tę funkcję, aby znaleźć określony tekst i ustaw go jako bieżący wybór.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Zawiera ciąg, który ma zostać wyszukany.

*bCase*<br/>
Wskazuje, czy w wyszukiwaniu jest uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, czy wyszukiwanie powinno uwzględniać tylko całe wyrazy, nie części wyrazów.

*bNext*<br/>
Wskazuje kierunek wyszukiwania. W przypadku wartości TRUE kierunek wyszukiwania jest skierowany ku końcu buforu. W przypadku wartości FALSE kierunek wyszukiwania jest skierowany do początku buforu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zostanie znaleziony tekst *lpszFind* ; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRichEditView:: ciąg FindText](#findtext).

##  <a name="getcharformatselection"></a>CRichEditView:: GetCharFormatSelection

Wywołaj tę funkcję, aby pobrać atrybuty formatowania znaku bieżącego zaznaczenia.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Wartość zwracana

Struktura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) , która zawiera atrybuty formatowania znaku bieżącego zaznaczenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) komunikat i struktura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>CRichEditView:: GetClipboardData

Struktura wywołuje tę funkcję w ramach przetwarzania elementu [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Parametry

*lpchrg*<br/>
Wskaźnik do struktury [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) określający zakres znaków (i elementy OLE) do skopiowania do obiektu danych określonego przez *lplpdataobj*.

*dwReco*<br/>
Flaga operacji Schowka. Może być jedną z następujących wartości.

- RECO_COPY skopiuj do Schowka.

- RECO_CUT Wytnij do Schowka.

- RECO_DRAG operacji przeciągania (przeciągnij i upuść).

- RECO_DROP operacji usuwania (przeciągnij i upuść).

- RECO_PASTE Wklej ze schowka.

*lpRichDataObj*<br/>
Wskaźnik do obiektu [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) zawierającego dane ze schowka z kontrolki edycji wzbogaconej ( [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Wskaźnik do zmiennej wskaźnika, która odbiera adres `IDataObject` obiektu reprezentującego zakres określony w parametrze *lpchrg* . Wartość *lplpdataobj* jest ignorowana, Jeśli zwracany jest błąd.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT zgłasza sukces operacji. Aby uzyskać więcej informacji na temat HRESULT, zobacz [strukturę kodów błędów modelu COM](/windows/win32/com/structure-of-com-error-codes) w Windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli wartość `IRichEditOleCallback::GetClipboardData` zwracana wskazuje powodzenie, `IDataObject` zwraca dostępną przez *lplpdataobj*; w przeciwnym razie zwraca wartość dostępną przez *lpRichDataObj*. Zastąp tę funkcję, aby podać własne dane Schowka. Domyślna implementacja tej funkcji zwraca E_NOTIMPL.

Jest to zaawansowany możliwy do zaawansowania.

Aby uzyskać więcej informacji, zobacz [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)i [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) w Windows SDK i zobacz [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) w Windows SDK.

##  <a name="getcontextmenu"></a>CRichEditView::

Struktura wywołuje tę funkcję w ramach przetwarzania elementu [IRichEditOleCallback::](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)get.

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parametry

*seltyp*<br/>
Typ zaznaczenia. Wartości typu wyboru są opisane w sekcji uwagi.

*lpoleobj*<br/>
Wskaźnik do `OLEOBJECT` struktury określającej pierwszy zaznaczony obiekt OLE, jeśli zaznaczenie zawiera jeden lub więcej elementów OLE. Jeśli zaznaczenie nie zawiera żadnych elementów, *lpoleobj* ma wartość null. `OLEOBJECT` Struktura zawiera wskaźnik do tabeli obiektu OLE.

*lpchrg*<br/>
Wskaźnik do struktury [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) zawierającej bieżący wybór.

### <a name="return-value"></a>Wartość zwracana

Dojście do menu kontekstowego.

### <a name="remarks"></a>Uwagi

Ta funkcja jest typową częścią odpowiedniego przetworzenia przycisku myszy w dół.

Typ zaznaczenia może być dowolną kombinacją następujących flag:

- SEL_EMPTY wskazuje, że nie ma bieżącego wyboru.

- SEL_TEXT wskazuje, że bieżące zaznaczenie zawiera tekst.

- SEL_OBJECT wskazuje, że bieżące zaznaczenie zawiera co najmniej jeden element OLE.

- SEL_MULTICHAR wskazuje, że bieżące zaznaczenie zawiera więcej niż jeden znak tekstu.

- SEL_MULTIOBJECT wskazuje, że bieżące zaznaczenie zawiera więcej niż jeden obiekt OLE.

Domyślna implementacja zwraca wartość NULL. Jest to zaawansowany możliwy do zaawansowania.

Aby uzyskać więcej informacji, zobacz [IRichEditOleCallback::](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) geti [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) w Windows SDK.

##  <a name="getdocument"></a>CRichEditView:: GetDocument

Wywołaj tę funkcję, aby uzyskać wskaźnik do `CRichEditDoc` skojarzonego z tym widokiem.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) skojarzonego z `CRichEditView` obiektem.

##  <a name="getinplaceactiveitem"></a>CRichEditView:: GetInPlaceActiveItem

Wywołaj tę funkcję, aby pobrać element OLE, który jest aktualnie aktywowany w miejscu `CRichEditView` w tym obiekcie.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pojedynczego, w miejscu aktywnego obiektu [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) w tym widoku edycji wzbogaconej; Wartość NULL, jeśli w stanie aktywnym nie ma obecnie elementu OLE.

##  <a name="getmargins"></a>CRichEditView:: GetMargins

Wywołaj tę funkcję, aby pobrać bieżące marginesy używane podczas drukowania.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Wartość zwracana

Marginesy używane podczas drukowania, mierzone w MM_TWIPS.

##  <a name="getpagerect"></a>CRichEditView:: GetPageRect

Wywołaj tę funkcję, aby uzyskać wymiary strony używanej do drukowania.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Granice strony używanej w drukowaniu, mierzone w MM_TWIPS.

### <a name="remarks"></a>Uwagi

Ta wartość jest oparta na rozmiarze papieru.

##  <a name="getpapersize"></a>CRichEditView:: GetPaperSize

Wywołaj tę funkcję, aby pobrać bieżący rozmiar papieru.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar papieru używanego do drukowania, mierzony w MM_TWIPS.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>CRichEditView:: GetParaFormatSelection

Wywołaj tę funkcję, aby pobrać atrybuty formatowania akapitu bieżącego zaznaczenia.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Wartość zwracana

Struktura [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) , która zawiera atrybuty formatowania akapitu bieżącego zaznaczenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) Message i [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) Structure w Windows SDK.

##  <a name="getprintrect"></a>CRichEditView:: GetPrintRect

Wywołaj tę funkcję, aby pobrać granice obszaru drukowania w obrębie prostokąta strony.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Granice obszaru obrazu używane podczas drukowania, mierzone w MM_TWIPS.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>CRichEditView:: GetPrintWidth

Wywołaj tę funkcję, aby określić szerokość obszaru drukowania.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość obszaru drukowania mierzona w MM_TWIPS.

##  <a name="getricheditctrl"></a>CRichEditView:: GetRichEditCtrl

Wywołaj tę funkcję, aby pobrać obiekt [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) skojarzony z `CRichEditView` obiektem.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

`CRichEditCtrl` Obiekt dla tego widoku.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRichEditView:: ciąg FindText](#findtext).

##  <a name="getselecteditem"></a>CRichEditView:: GetSelectedItem

Wywołaj tę funkcję, aby pobrać element OLE ( `CRichEditCntrItem` obiekt), który jest aktualnie `CRichEditView` wybrany w tym obiekcie.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) zaznaczonego w `CRichEditView` obiekcie; Wartość NULL, jeśli nie wybrano żadnego elementu w tym widoku.

##  <a name="gettextlength"></a>CRichEditView:: GetTextLength

Wywołaj tę funkcję, aby pobrać długość tekstu w tym `CRichEditView` obiekcie.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość tekstu w tym `CRichEditView` obiekcie.

##  <a name="gettextlengthex"></a>CRichEditView:: GetTextLengthEx

Wywołaj tę funkcję elementu członkowskiego, aby obliczyć długość tekstu w `CRichEditView` tym obiekcie.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Wartość określająca metodę, która ma być używana podczas określania długości tekstu. Ten element członkowski może być co najmniej jedną wartością wymienioną w elemencie członkowskim flagi [GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) opisanego w Windows SDK.

*uCodePage*<br/>
Strona kodowa dla tłumaczenia (CP_ACP dla strony kodowej ANSI, 1200 dla Unicode).

### <a name="return-value"></a>Wartość zwracana

Liczba znaków lub bajtów w kontrolce edycji. W przypadku ustawienia niezgodnych flag w *flagiDW*, ta funkcja członkowska zwraca E_INVALIDARG.

### <a name="remarks"></a>Uwagi

`GetTextLengthEx`zapewnia dodatkowe sposoby określania długości tekstu. Obsługuje zaawansowane funkcje edycji 2,0. Aby uzyskać więcej informacji, zobacz [Informacje o kontrolkach edycji wzbogaconej](/windows/win32/Controls/about-rich-edit-controls) w Windows SDK.

##  <a name="insertfileasobject"></a>CRichEditView:: InsertFileAsObject

Wywołaj tę funkcję, aby wstawić określony plik (jako obiekt [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) ) do widoku wzbogaconej edycji.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg zawierający nazwę pliku, który ma zostać wstawiony.

##  <a name="insertitem"></a>CRichEditView:: InsertItem

Wywołaj tę funkcję, aby wstawić obiekt [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) do widoku wzbogaconej edycji.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik na element, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT wskazująca na powodzenie wstawiania.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat HRESULT, zobacz [strukturę kodów błędów modelu COM](/windows/win32/com/structure-of-com-error-codes) w Windows SDK.

##  <a name="isricheditformat"></a>CRichEditView:: IsRichEditFormat

Wywołaj tę funkcję, aby określić, czy *CF* jest formatem schowka, który jest tekst, tekst sformatowany lub tekst sformatowany przy użyciu elementów OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Interesujący format schowka.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli *CF* jest sformatowanym formatem tekstu lub Schowka.

##  <a name="isselected"></a>CRichEditView:: IsSelected

Wywołaj tę funkcję, aby określić, czy określony element OLE jest aktualnie wybrany w tym widoku.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Wskaźnik do obiektu w widoku.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt jest zaznaczony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, jeśli Klasa widoku pochodnego ma inną metodę obsługi wyboru elementów OLE.

##  <a name="m_nbulletindent"></a>CRichEditView:: m_nBulletIndent

Wcięcie dla elementów punktorów na liście; Domyślnie 720 jednostek, czyli 1/2 cala.

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>CRichEditView:: m_nWordWrap

Wskazuje typ zawijania wyrazów dla tego widoku wzbogaconej edycji.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Uwagi

Jedna z następujących wartości:

- `WrapNone`Nie wskazuje automatycznego zawijania wyrazów.

- `WrapToWindow`Wskazuje Zawijanie słów na podstawie szerokości okna.

- `WrapToTargetDevice`Wskazuje Zawijanie słów na podstawie charakterystyki urządzenia docelowego.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRichEditView:: WrapChanged](#wrapchanged).

##  <a name="onchareffect"></a>CRichEditView:: OnCharEffect

Wywołaj tę funkcję, aby przełączać efekty formatowania znaków dla bieżącego zaznaczenia.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*dwMask*<br/>
Formatowanie znaków w bieżącym zaznaczeniu.

*dwEffect*<br/>
Wymagana lista efektów formatowania znaków do przełączenia.

### <a name="remarks"></a>Uwagi

Każde wywołanie tej funkcji przełącza określone efekty formatowania dla bieżącego zaznaczenia.

Aby uzyskać więcej informacji o parametrach *dwMask* i *dwEffect* oraz ich potencjalnych wartościach, zobacz odpowiednie elementy członkowskie danych [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>CRichEditView:: OnFindNext

Wywoływane przez platformę podczas przetwarzania poleceń z okna dialogowego Znajdowanie/zamienianie.

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

*bNext*<br/>
Kierunek wyszukiwania: Wartość PRAWDA oznacza, że FAŁSZ, w górę.

*bCase*<br/>
Wskazuje, czy w wyszukiwaniu ma być uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, czy wyszukiwanie ma uwzględniać tylko całe wyrazy, czy nie.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby znaleźć tekst `CRichEditView`w. Zastąp tę funkcję, aby zmienić właściwości wyszukiwania dla klasy widoku pochodnego.

##  <a name="oninitialupdate"></a>CRichEditView:: OnInitialUpdate

Wywoływane przez platformę po pierwszym dołączeniu widoku do dokumentu, ale zanim widok jest początkowo wyświetlany.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje funkcję członkowską [CView:: OnUpdate](../../mfc/reference/cview-class.md#onupdate) bez informacji o wskazówce (to oznacza użycie wartości domyślnych 0 dla parametru *lHint* i wartości null dla parametru *pHint* ). Zastąp tę funkcję, aby wykonać jednorazowe inicjowanie, które wymaga informacji o dokumencie. Na przykład jeśli aplikacja ma dokumenty o stałym rozmiarze, można użyć tej funkcji do zainicjowania limitów przewijania widoku na podstawie rozmiaru dokumentu. Jeśli aplikacja obsługuje dokumenty o zmiennym rozmiarze, użyj `OnUpdate` do aktualizowania limitów przewijania za każdym razem, gdy dokument zostanie zmieniony.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRichEditView:: m_nWordWrap](#m_nwordwrap).

##  <a name="onpastenativeobject"></a>CRichEditView:: OnPasteNativeObject

Użyj tej funkcji, aby załadować dane natywne z osadzonego elementu.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parametry

*lpStg*<br/>
Wskaźnik do obiektu [Metoda IStorage](/windows/win32/api/objidl/nn-objidl-istorage) .

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0;

### <a name="remarks"></a>Uwagi

Zazwyczaj można to zrobić, tworząc [COleStreamFile](../../mfc/reference/colestreamfile-class.md) wokół `IStorage`. Można dołączyć do archiwum i [CObject:: serializować](../../mfc/reference/cobject-class.md#serialize) wywołana, aby załadować dane. `COleStreamFile`

Jest to zaawansowany możliwy do zaawansowania.

Aby uzyskać więcej informacji, zobacz [Metoda IStorage](/windows/win32/api/objidl/nn-objidl-istorage) w Windows SDK.

##  <a name="onparaalign"></a>CRichEditView:: OnParaAlign

Wywołaj tę funkcję, aby zmienić wyrównanie akapitu dla wybranych akapitów.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parametry

*wAlign*<br/>
Żądane wyrównanie akapitu. Jedna z następujących wartości:

- PFA_LEFT Dopasuj akapity do lewego marginesu.

- PFA_RIGHT Dopasuj akapity do prawego marginesu.

- PFA_CENTER Wyśrodkuj akapity między marginesami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>CRichEditView:: OnPrinterChanged

Zastąp tę funkcję, aby zmienić cechy dla tego widoku wzbogaconej edycji, gdy zmienia się drukarka.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parametry

*dcPrinter*<br/>
Obiekt [](../../mfc/reference/cdc-class.md) przerzutowania dla nowej drukarki.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ustawia rozmiar papieru na fizyczną wysokość i szerokość urządzenia wyjściowego (drukarki). Jeśli nie ma kontekstu urządzenia skojarzonego z *dcPrinter*, domyślna implementacja ustawia rozmiar papieru na 8,5 przez 11 cali.

##  <a name="onreplaceall"></a>CRichEditView:: OnReplaceAll

Wywoływane przez platformę podczas przetwarzania Zamień wszystkie polecenia z okna dialogowego Zastąp.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać zastąpiony.

*lpszReplace*<br/>
Tekst zastępczy.

*bCase*<br/>
Wskazuje, czy w wyszukiwaniu jest uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, czy w wyszukiwaniu należy wybrać całe wyrazy, czy nie.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zastąpić wszystkie wystąpienia danego tekstu innym ciągiem. Zastąp tę funkcję, aby zmienić właściwości wyszukiwania dla tego widoku.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRichEditView:: ciąg FindText](#findtext).

##  <a name="onreplacesel"></a>CRichEditView:: OnReplaceSel

Wywoływane przez platformę podczas przetwarzania zamiany poleceń z okna dialogowego Zastąp.

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
Tekst, który ma zostać zastąpiony.

*bNext*<br/>
Wskazuje kierunek wyszukiwania: PRAWDA nie działa; FAŁSZ, w górę.

*bCase*<br/>
Wskazuje, czy w wyszukiwaniu jest uwzględniana wielkość liter.

*bWord*<br/>
Wskazuje, czy w wyszukiwaniu należy wybrać całe wyrazy, czy nie.

*lpszReplace*<br/>
Tekst zastępczy.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zastąpić jedno wystąpienie danego tekstu innym ciągiem. Zastąp tę funkcję, aby zmienić właściwości wyszukiwania dla tego widoku.

##  <a name="ontextnotfound"></a>CRichEditView:: OnTextNotFound

Wywoływane przez platformę, gdy wyszukiwanie nie powiedzie się.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który nie został odnaleziony.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, aby zmienić powiadomienie wyjściowe z [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep).

Aby uzyskać więcej informacji, zobacz [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>CRichEditView:: OnUpdateCharEffect

Struktura wywołuje tę funkcję, aby zaktualizować interfejs użytkownika poleceń dla poleceń dotyczących efektów znakowych.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do obiektu [CCmdUI](../../mfc/reference/ccmdui-class.md) .

*dwMask*<br/>
Wskazuje maskę formatowania znaku.

*dwEffect*<br/>
Określa efekt formatowania znaków.

### <a name="remarks"></a>Uwagi

Maska *dwMask* określa atrybuty formatowania znaku do sprawdzenia. Flagi *dwEffect* wyświetlają atrybuty formatowania znaku, aby ustawić/wyczyścić.

Aby uzyskać więcej informacji o parametrach *dwMask* i *dwEffect* oraz ich potencjalnych wartościach, zobacz odpowiednie elementy członkowskie danych [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>CRichEditView:: OnUpdateParaAlign

Struktura wywołuje tę funkcję, aby zaktualizować interfejs użytkownika poleceń dla poleceń z efektem akapitu.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do obiektu [CCmdUI](../../mfc/reference/ccmdui-class.md) .

*wAlign*<br/>
Wyrównanie akapitu do sprawdzenia. Jedna z następujących wartości:

- PFA_LEFT Dopasuj akapity do lewego marginesu.

- PFA_RIGHT Dopasuj akapity do prawego marginesu.

- PFA_CENTER Wyśrodkuj akapity między marginesami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>CRichEditView::P rintInsideRect

Wywołaj tę funkcję, aby sformatować zakres tekstu w kontrolce edycji wzbogaconej w celu dopasowania go do *rectLayout* dla urządzenia określonego przez *PDC*.

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
Wskaźnik do kontekstu urządzenia dla obszaru wyjściowego.

*rectLayout*<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) , który definiuje obszar wyjściowy.

*nIndexStart*<br/>
Indeks (liczony od zera) pierwszego znaku do sformatowania.

*nIndexStop*<br/>
Indeks (liczony od zera) ostatniego znaku do sformatowania.

*bOutput*<br/>
Wskazuje, czy tekst powinien być renderowany. W przypadku wartości FALSE tekst jest mierzony.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatniego znaku, który mieści się w obszarze wyjściowym plus jeden.

### <a name="remarks"></a>Uwagi

Zwykle jest to wywołanie [CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) , które generuje dane wyjściowe.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRichEditView:: GetPaperSize](#getpapersize).

##  <a name="printpage"></a>CRichEditView::P rintPage

Wywołaj tę funkcję, aby sformatować zakres tekstu w kontrolce edycji wzbogaconej dla urządzenia wyjściowego określonego przez *PDC*.

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
Indeks (liczony od zera) pierwszego znaku do sformatowania.

*nIndexStop*<br/>
Indeks (liczony od zera) ostatniego znaku do sformatowania.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatniego znaku, który mieści się na stronie oraz jeden.

### <a name="remarks"></a>Uwagi

Układ każdej strony jest kontrolowany przez [GetPageRect](#getpagerect) i [GetPrintRect](#getprintrect). Zwykle jest to wywołanie [CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) , które generuje dane wyjściowe.

Należy zauważyć, że marginesy są względne względem strony fizycznej, a nie strony logicznej. W związku z tym marginesy zerowe będą często obcinać tekst, ponieważ wiele drukarek ma niedrukowalne obszary na stronie. Aby uniknąć obcinania tekstu, należy wywołać metodę [Setmargins](#setmargins) i ustawić odpowiednie marginesy przed drukowaniem.

##  <a name="queryacceptdata"></a>CRichEditView:: QueryAcceptData

Wywoływane przez platformę, aby wkleić obiekt do edycji wzbogaconej.

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
Wskaźnik do [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) do zapytania.

*lpcfFormat*<br/>
Wskaźnik na akceptowalny format danych.

*dwReco*<br/>
Nie używany.

*bReally*<br/>
Wskazuje, czy operacja wklejania powinna być kontynuowana, czy nie.

*hMetaFile*<br/>
Uchwyt do metapliku używanego do rysowania ikony elementu.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT zgłasza sukces operacji.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby obsługiwać inną organizację elementów COM w klasie dokumentu pochodnego. Jest to zaawansowany możliwy do zaawansowania.

Aby uzyskać więcej informacji na temat `IDataObject`HRESULT i, zobacz odpowiednio [strukturę kodów błędów modelu COM](/windows/win32/com/structure-of-com-error-codes) i [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>CRichEditView:: SetCharFormat

Wywołaj tę funkcję, aby ustawić atrybuty formatowania znaku dla nowego tekstu w `CRichEditView` tym obiekcie.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Struktura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) zawierająca nowe atrybuty domyślnego formatowania znaków.

### <a name="remarks"></a>Uwagi

Tylko atrybuty określone przez `dwMask` składową *CF* są zmieniane przez tę funkcję.

Aby uzyskać więcej informacji, zobacz [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) Message i [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) Structure w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>CRichEditView:: Setmargins

Wywołaj tę funkcję, aby ustawić marginesy drukowania dla tego widoku wzbogaconej edycji.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parametry

*rectMargin*<br/>
Nowe wartości marginesu do drukowania, mierzone w MM_TWIPS.

### <a name="remarks"></a>Uwagi

Jeśli [m_nWordWrap](#m_nwordwrap) jest `WrapToTargetDevice`, należy wywołać [WrapChanged](#wrapchanged) po użyciu tej funkcji, aby dostosować charakterystykę drukowania.

Należy zauważyć, że marginesy używane przez [PrintPage](#printpage) są względne względem strony fizycznej, a nie strony logicznej. W związku z tym marginesy zerowe będą często obcinać tekst, ponieważ wiele drukarek ma niedrukowalne obszary na stronie. Aby uniknąć obcinania tekstu, należy wywołać metodę USE `SetMargins` , aby ustawić odpowiednie marginesy drukarki przed drukowaniem.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRichEditView:: GetPaperSize](#getpapersize).

##  <a name="setpapersize"></a>CRichEditView:: setpapersize

Wywołaj tę funkcję, aby ustawić rozmiar papieru na potrzeby drukowania widoku wzbogaconej edycji.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parametry

*sizePaper*<br/>
Nowe wartości rozmiaru papieru do drukowania, mierzone w MM_TWIPS.

### <a name="remarks"></a>Uwagi

Jeśli [m_nWordWrap](#m_nwordwrap) jest `WrapToTargetDevice`, należy wywołać [WrapChanged](#wrapchanged) po użyciu tej funkcji, aby dostosować charakterystykę drukowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>CRichEditView:: SetParaFormat

Wywołaj tę funkcję, aby ustawić atrybuty formatowania akapitu dla bieżącego zaznaczenia w `CRichEditView` tym obiekcie.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parametry

*PF*<br/>
Struktura [PARAFORMAT2a](/windows/win32/api/richedit/ns-richedit-paraformat2) zawierająca nowe domyślne atrybuty formatowania akapitu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Tylko atrybuty określone przez `dwMask` element członkowski *PF* są zmieniane przez tę funkcję.

Aby uzyskać więcej informacji, zobacz [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) Message i [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) Structure w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>CRichEditView:: TextNotFound

Wywołaj tę funkcję, aby zresetować stan przeszukiwania wewnętrznego formantu [CRichEditView](../../mfc/reference/cricheditview-class.md) po nieudanym wywołaniu do [ciąg FindText](#findtext).

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Zawiera ciąg tekstowy, który nie został odnaleziony.

### <a name="remarks"></a>Uwagi

Zaleca się, aby ta metoda była wywoływana natychmiast po nieudanych wywołaniach do [ciąg FindText](#findtext) , tak aby wewnętrzny stan wyszukiwania kontrolki został prawidłowo zresetowany.

Parametr *lpszFind* powinien zawierać tę samą zawartość co ciąg dostarczony do [ciąg FindText](#findtext). Po zresetowaniu stanu wyszukiwania wewnętrznego ta metoda wywoła metodę [OnTextNotFound](#ontextnotfound) z podanym ciągiem wyszukiwania.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRichEditView:: ciąg FindText](#findtext).

##  <a name="wrapchanged"></a>CRichEditView:: WrapChanged

Wywołaj tę funkcję po zmianie charakterystyki drukowania ( [Setmargins](#setmargins) lub [setpapersize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby zmodyfikować sposób, w jaki widok edycji wzbogaconej reaguje na zmiany w [m_nWordWrap](#m_nwordwrap) lub charakterystyce drukowania ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykładowy program WORDPAD dla MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)<br/>
[Klasa CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)
