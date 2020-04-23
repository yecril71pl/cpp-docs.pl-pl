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
ms.openlocfilehash: b72daac576411b45908d1e91bd86bbd9aeacf738
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754455"
---
# <a name="cricheditview-class"></a>Klasa CRichEditView

Z [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) i [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), zapewnia funkcjonalność formantu edycji bogatej w kontekście architektury widoku dokumentów MFC.

## <a name="syntax"></a>Składnia

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView::CRichEditView](#cricheditview)|Konstruuje `CRichEditView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView::DopasujdialogPosition](#adjustdialogposition)|Przenosi okno dialogowe, aby nie zasłaniało bieżącego zaznaczenia.|
|[CRichEditView::CanPaste](#canpaste)|Określa, czy Schowek zawiera dane, które można wkleić do widoku edycji rozszerzonej.|
|[CRichEditView::DoPaste](#dopaste)|Wkleja element OLE do tego bogatego widoku edycji.|
|[CRichEditView::FindText](#findtext)|Znajduje określony tekst, wywołując kursor oczekiwania.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Znajduje określony tekst.|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Pobiera atrybuty formatowania znaków dla bieżącego zaznaczenia.|
|[CRichEditView::GetDocument](#getdocument)|Pobiera wskaźnik do powiązanych [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md).|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Pobiera element OLE, który jest obecnie aktywny w widoku edycji rich.|
|[CRichEditView::GetMargins](#getmargins)|Pobiera marginesy dla tego zaawansowanego widoku edycji.|
|[CRichEditView::GetPageRect](#getpagerect)|Pobiera prostokąt strony dla tego bogatego widoku edycji.|
|[CRichEditView::GetPaperSize](#getpapersize)|Pobiera rozmiar papieru dla tego bogatego widoku edycji.|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Pobiera atrybuty formatowania akapitu dla bieżącego zaznaczenia.|
|[CRichEditView::GetPrintRect](#getprintrect)|Pobiera prostokąt wydruku dla tego bogatego widoku edycji.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Pobiera szerokość wydruku dla tego bogatego widoku edycji.|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Pobiera formant edycji bogatej.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Pobiera zaznaczony element z widoku edycji rich.|
|[CRichEditView::GetTextLength](#gettextlength)|Pobiera długość tekstu w widoku edycji rich.|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Pobiera liczbę znaków lub bajtów w widoku edycji rich. Rozszerzona lista flag dla metody określania długości.|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Wstawia plik jako element OLE.|
|[CRichEditView::InsertItem](#insertitem)|Wstawia nowy element jako element OLE.|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Określa, czy Schowek zawiera dane w formacie edycji sformatowania lub tekstu.|
|[CRichEditView::OnCharEffect](#onchareffect)|Przełącza formatowanie znaków dla bieżącego zaznaczenia.|
|[CRichEditView::OnParaAlign](#onparaalign)|Zmienia wyrównanie akapitów.|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Aktualizuje interfejs użytkownika polecenia dla funkcji publicznego elementu członkowskiego znaków.|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Aktualizuje interfejs użytkownika polecenia dla funkcji publicznego elementu członkowskiego akapitu.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Formatuje określony tekst w danym prostokącie.|
|[CRichEditView::PrintPage](#printpage)|Formatuje określony tekst na danej stronie.|
|[CRichEditView::SetCharFormat](#setcharformat)|Ustawia atrybuty formatowania znaków dla bieżącego zaznaczenia.|
|[CRichEditView::SetMargins](#setmargins)|Ustawia marginesy dla tego widoku edycji rozszerzonej.|
|[CRichEditView::SetPaperSize](#setpapersize)|Ustawia rozmiar papieru dla tego widoku edycji rich.|
|[CRichEditView::SetParaFormat](#setparaformat)|Ustawia atrybuty formatowania akapitu dla bieżącego zaznaczenia.|
|[CRichEditView::TextNotFound](#textnotfound)|Resetuje wewnętrzny stan wyszukiwania formantu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Pobiera obiekt Schowek dla zakresu w tym bogatym widoku edycji.|
|[CRichEditView::GetContextMenu](#getcontextmenu)|Pobiera menu kontekstowe do użycia na prawym przycisku myszy w dół.|
|[CRichEditView::IsSelected](#isselected)|Wskazuje, czy dany element OLE jest zaznaczony, czy nie.|
|[CRichEditView::OnFindNext](#onfindnext)|Znajduje następne wystąpienie podciągu.|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Odświeża widok, gdy jest on po raz pierwszy dołączony do dokumentu.|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Pobiera dane macierzyste z elementu OLE.|
|[CRichEditView::OnPrinterZmienił](#onprinterchanged)|Ustawia charakterystykę drukowania na danym urządzeniu.|
|[CRichEditView::OnReplaceAll](#onreplaceall)|Zastępuje wszystkie wystąpienia danego ciągu nowym ciągiem.|
|[CRichEditView::OnReplaceSel](#onreplacesel)|Zastępuje bieżące zaznaczenie.|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Obsługuje powiadomienie użytkownika, że żądany tekst nie został znaleziony.|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Zapytania, aby zobaczyć o `IDataObject`danych na .|
|[CRichEditView::WrapZmienił](#wrapchanged)|Dostosowuje docelowe urządzenie wyjściowe dla tego bogatego `m_nWordWrap`widoku edycji na podstawie wartości pliku .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Wskazuje ilość wcięć dla list punktorów.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Wskazuje ograniczenia zawijać wyrazu.|

## <a name="remarks"></a>Uwagi

"Formant edycji bogatej" to okno, w którym użytkownik może wprowadzać i edytować tekst. Tekst może być przypisany do formatowania znaków i akapitów i może zawierać osadzone obiekty OLE. Zaawansowane kontrolki edycji zapewniają interfejs programowania do formatowania tekstu. Jednak aplikacja musi implementować wszystkie składniki interfejsu użytkownika niezbędne do udostępnienia użytkownikowi operacji formatowania.

`CRichEditView`zachowuje charakterystykę tekstu i formatowania tekstu. `CRichEditDoc`utrzymuje listę elementów klienta OLE, które są w widoku. `CRichEditCntrItem`zapewnia dostęp po stronie kontenera do elementu klienta OLE.

Ta wspólna kontrola systemu Windows (a zatem [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i powiązane klasy) jest dostępna tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersjach 3.51 i nowszych.

Na przykład przy użyciu widoku edycji bogatej w aplikacji MFC, zobacz [wordpad](../../overview/visual-cpp-samples.md) przykładowej aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[Cctrlview](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrich.h

## <a name="cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a>CRichEditView::DopasujdialogPosition

Wywołanie tej funkcji, aby przenieść podane okno dialogowe, tak aby nie zasłaniać bieżącego zaznaczenia.

```cpp
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parametry

*pDlg (włas iem)*<br/>
Wskaźnik do `CDialog` obiektu.

## <a name="cricheditviewcanpaste"></a><a name="canpaste"></a>CRichEditView::CanPaste

Wywołanie tej funkcji, aby ustalić, czy Schowek zawiera informacje, które mogą być wklejone do tego widoku edycji rozszerzonej.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Schowek zawiera dane w formacie, który ten bogaty widok edycji może zaakceptować; w przeciwnym razie 0.

## <a name="cricheditviewcricheditview"></a><a name="cricheditview"></a>CRichEditView::CRichEditView

Wywołanie tej funkcji, aby utworzyć `CRichEditView` obiekt.

```
CRichEditView();
```

## <a name="cricheditviewdopaste"></a><a name="dopaste"></a>CRichEditView::DoPaste

Wywołanie tej funkcji, aby wkleić element OLE w *dataobj* do tego bogatego dokumentu edycji/widoku.

```cpp
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Parametry

*dataobj*<br/>
[COleDataObject](../../mfc/reference/coledataobject-class.md) zawierający dane do wklejenia.

*Por*<br/>
Żądany format Schowka.

*hMetaPict (MetalaPict)*<br/>
Metaplik reprezentujący element, który ma zostać wklejony.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję jako część domyślnej implementacji [QueryAcceptData](#queryacceptdata).

Ta funkcja określa typ wklejania na podstawie wyników programu obsługi dla Wklej specjalnie. Jeśli *cf* wynosi 0, nowy przedmiot używa aktualnej kultowej reprezentacji. Jeśli *cf* jest nonzero i *hMetaPict* nie jest NULL, nowy element używa *hMetaPict* dla jego reprezentacji.

## <a name="cricheditviewfindtext"></a><a name="findtext"></a>CRichEditView::FindText

Wywołanie tej funkcji, aby znaleźć określony tekst i ustawić go jako bieżącego zaznaczenia.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Zawiera ciąg do wyszukania.

*bKasze*<br/>
Wskazuje, czy w wyszukiwaniu jest rozróżniana wielkość liter.

*bJąka*<br/>
Wskazuje, czy wyszukiwanie powinno być zgodne tylko z całymi słowami, a nie częściami słów.

*bNastępna*<br/>
Wskazuje kierunek wyszukiwania. Jeśli true, kierunek wyszukiwania znajduje się na końcu buforu. Jeśli FAŁDa, kierunek wyszukiwania znajduje się w kierunku początku buforu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli *lpszZnajduje* tekst zostanie znaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja wyświetla kursor oczekiwania podczas operacji znajdowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

## <a name="cricheditviewfindtextsimple"></a><a name="findtextsimple"></a>CRichEditView::FindTextSimple

Wywołanie tej funkcji, aby znaleźć określony tekst i ustawić go jako bieżącego zaznaczenia.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Zawiera ciąg do wyszukania.

*bKasze*<br/>
Wskazuje, czy w wyszukiwaniu jest rozróżniana wielkość liter.

*bJąka*<br/>
Wskazuje, czy wyszukiwanie powinno być zgodne tylko z całymi słowami, a nie częściami słów.

*bNastępna*<br/>
Wskazuje kierunek wyszukiwania. Jeśli true, kierunek wyszukiwania znajduje się na końcu buforu. Jeśli FAŁDa, kierunek wyszukiwania znajduje się w kierunku początku buforu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli *lpszZnajduje* tekst zostanie znaleziony; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::FindText](#findtext).

## <a name="cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a>CRichEditView::GetCharFormatSelection

Wywołanie tej funkcji, aby uzyskać atrybuty formatowania znaków bieżącego zaznaczenia.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Wartość zwracana

Struktura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) zawierająca atrybuty formatowania znaków bieżącego zaznaczenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz komunikat [EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) i strukturę [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) w zestaw Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a>CRichEditView::GetClipboardData

Struktura wywołuje tę funkcję w ramach przetwarzania [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Parametry

*lpchrg ( lpchrg )*<br/>
Wskaźnik do struktury [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) określający zakres znaków (i elementów OLE) do skopiowania do obiektu danych określonego przez *lplpdataobj*.

*dwReco (Dwreco)*<br/>
Flaga operacji schowka. Może być jedną z tych wartości.

- RECO_COPY skopiuj do Schowka.

- RECO_CUT Wytnij do Schowka.

- RECO_DRAG Operacja przeciągania (przeciąganie i upuszczanie).

- RECO_DROP Operacja upuszczania (przeciąganie i upuszczanie).

- RECO_PASTE wklej ze Schowka.

*lpRichDataObj*<br/>
Wskaźnik do obiektu [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) zawierającego dane Schowka z formantu edycji rich ( [IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Wskaźnik do zmiennej wskaźnika, `IDataObject` która odbiera adres obiektu reprezentującego zakres określony w parametrze *lpchrg.* Wartość *lplpdataobj* jest ignorowana, jeśli zwracany jest błąd.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT raportowania sukcesu operacji. Aby uzyskać więcej informacji na temat hresult, zobacz [Struktura kodów błędów COM](/windows/win32/com/structure-of-com-error-codes) w windows SDK.

### <a name="remarks"></a>Uwagi

Jeśli zwracana wartość wskazuje `IRichEditOleCallback::GetClipboardData` na `IDataObject` powodzenie, zwraca dostęp do *lplpdataobj*; w przeciwnym razie zwraca ten, do który uzyskuje dostęp *lpRichDataObj*. Zastąp tę funkcję, aby podać własne dane Schowka. Domyślna implementacja tej funkcji zwraca E_NOTIMPL.

Jest to zaawansowane zastąpienie.

Aby uzyskać więcej informacji, zobacz [IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)i [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) w windows SDK i zobacz [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) w windows SDK.

## <a name="cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a>CRichEditView::GetContextMenu

Struktura wywołuje tę funkcję jako część przetwarzania [IRichEditOleCallback::GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu).

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parametry

*seltyp*<br/>
Typ wyboru. Wartości typu wyboru są opisane w sekcji Uwagi.

*lpoleobj ( lpoleobj )*<br/>
Wskaźnik do `OLEOBJECT` struktury określającej pierwszy wybrany obiekt OLE, jeśli zaznaczenie zawiera jeden lub więcej elementów OLE. Jeśli zaznaczenie nie zawiera żadnych elementów, *lpoleobj* ma wartość NULL. Struktura `OLEOBJECT` zawiera wskaźnik do obiektu OLE v-tabeli.

*lpchrg ( lpchrg )*<br/>
Wskaźnik do struktury [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) zawierającej bieżące zaznaczenie.

### <a name="return-value"></a>Wartość zwracana

Dojście do menu kontekstowego.

### <a name="remarks"></a>Uwagi

Ta funkcja jest typową częścią przetwarzania prawego przycisku myszy w dół.

Typ wyboru może być dowolną kombinacją następujących flag:

- SEL_EMPTY Wskazuje, że nie ma bieżącego wyboru.

- SEL_TEXT Wskazuje, że bieżące zaznaczenie zawiera tekst.

- SEL_OBJECT Wskazuje, że bieżące zaznaczenie zawiera co najmniej jeden element OLE.

- SEL_MULTICHAR Wskazuje, że bieżące zaznaczenie zawiera więcej niż jeden znak tekstu.

- SEL_MULTIOBJECT Wskazuje, że bieżące zaznaczenie zawiera więcej niż jeden obiekt OLE.

Domyślna implementacja zwraca wartość NULL. Jest to zaawansowane zastąpienie.

Aby uzyskać więcej informacji, zobacz [IRichEditOleCallback::GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) i [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) w windows SDK.

## <a name="cricheditviewgetdocument"></a><a name="getdocument"></a>CRichEditView::GetDocument

Wywołanie tej funkcji, aby `CRichEditDoc` uzyskać wskaźnik do skojarzonego z tym widokiem.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) skojarzonego z obiektem. `CRichEditView`

## <a name="cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>CRichEditView::GetInPlaceActiveItem

Wywołanie tej funkcji, aby uzyskać element OLE, który `CRichEditView` jest aktualnie aktywowany w miejscu w tym obiekcie.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pojedynczego, w miejscu aktywny [obiekt CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) w tym bogatym widoku edycji; NULL, jeśli nie ma obecnie żadnego elementu OLE w stanie aktywnym w miejscu.

## <a name="cricheditviewgetmargins"></a><a name="getmargins"></a>CRichEditView::GetMargins

Wywołanie tej funkcji, aby pobrać bieżące marginesy używane podczas drukowania.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Wartość zwracana

Marginesy używane w druku, mierzone w MM_TWIPS.

## <a name="cricheditviewgetpagerect"></a><a name="getpagerect"></a>CRichEditView::GetPageRect

Wywołanie tej funkcji, aby uzyskać wymiary strony używanej do drukowania.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Granice strony używanej do drukowania, mierzone w MM_TWIPS.

### <a name="remarks"></a>Uwagi

Ta wartość jest oparta na rozmiarze papieru.

## <a name="cricheditviewgetpapersize"></a><a name="getpapersize"></a>CRichEditView::GetPaperSize

Wywołanie tej funkcji, aby pobrać bieżący rozmiar papieru.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar papieru użytego do drukowania, mierzony w MM_TWIPS.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

## <a name="cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a>CRichEditView::GetParaFormatSelection

Wywołanie tej funkcji, aby uzyskać atrybuty formatowania akapitu bieżącego zaznaczenia.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Wartość zwracana

Struktura [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) zawierająca atrybuty formatowania akapitu bieżącego zaznaczenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) wiadomości i [strukturę PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) w programie Windows SDK.

## <a name="cricheditviewgetprintrect"></a><a name="getprintrect"></a>CRichEditView::GetPrintRect

Wywołanie tej funkcji, aby pobrać granice obszaru drukowania w prostokącie strony.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Granice obszaru obrazu używanego w druku, mierzone w MM_TWIPS.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

## <a name="cricheditviewgetprintwidth"></a><a name="getprintwidth"></a>CRichEditView::GetPrintWidth

Wywołanie tej funkcji w celu określenia szerokości obszaru drukowania.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość obszaru drukowania mierzona w MM_TWIPS.

## <a name="cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a>CRichEditView::GetRichEditCtrl

Wywołanie tej funkcji, aby pobrać [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) obiektu skojarzonego z obiektem. `CRichEditView`

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `CRichEditCtrl` dla tego widoku.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::FindText](#findtext).

## <a name="cricheditviewgetselecteditem"></a><a name="getselecteditem"></a>CRichEditView::GetSelectedItem

Wywołanie tej funkcji, aby pobrać `CRichEditCntrItem` element OLE (obiekt) aktualnie zaznaczone w tym `CRichEditView` obiekcie.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) `CRichEditView` wybranego w obiekcie; NULL, jeśli w tym widoku nie wybrano żadnego elementu.

## <a name="cricheditviewgettextlength"></a><a name="gettextlength"></a>CRichEditView::GetTextLength

Wywołanie tej funkcji, aby pobrać długość `CRichEditView` tekstu w tym obiekcie.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość tekstu w tym `CRichEditView` obiekcie.

## <a name="cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a>CRichEditView::GetTextLengthEx

Wywołanie tej funkcji elementu członkowskiego, aby `CRichEditView` obliczyć długość tekstu w tym obiekcie.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Wartość określająca metodę, która ma być używana do określania długości tekstu. Ten element członkowski może być jedną lub kilkoma wartościami wymienionymi w flagach członka [gettextlengthex](/windows/win32/api/richedit/ns-richedit-gettextlengthex) opisane w windows SDK.

*strona uCodePage*<br/>
Strona kodowa tłumaczenia (CP_ACP dla strony kodowej ANSI, 1200 dla Unicode).

### <a name="return-value"></a>Wartość zwracana

Liczba znaków lub bajtów w formancie edycji. Jeśli w *dwFlags*ustawiono niezgodne flagi, ta funkcja elementu członkowskiego zwraca E_INVALIDARG.

### <a name="remarks"></a>Uwagi

`GetTextLengthEx`zawiera dodatkowe sposoby określania długości tekstu. Obsługuje funkcję Rich Edit 2.0. Aby uzyskać więcej informacji, zobacz [Informacje o formantach edycji bogactwa](/windows/win32/Controls/about-rich-edit-controls) w sdk systemu Windows.

## <a name="cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a>CRichEditView::InsertFileAsObject

Wywołanie tej funkcji, aby wstawić określony plik (jako [obiekt CRichEditCntrItem)](../../mfc/reference/cricheditcntritem-class.md) do widoku edycji bogatej.

```cpp
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg zawierający nazwę pliku, który ma zostać wstawiony.

## <a name="cricheditviewinsertitem"></a><a name="insertitem"></a>CRichEditView::InsertItem

Wywołanie tej funkcji, aby wstawić [obiekt CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) do widoku edycji bogatej.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskaźnik do elementu, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT wskazująca powodzenie wstawiania.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat hresult, zobacz [Struktura kodów błędów COM](/windows/win32/com/structure-of-com-error-codes) w windows SDK.

## <a name="cricheditviewisricheditformat"></a><a name="isricheditformat"></a>CRichEditView::IsRichEditFormat

Wywołanie tej funkcji, aby *ustalić,* czy cf jest formatem Schowka, który jest tekst, tekst sformatowy lub tekst sformatowy z elementami OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parametry

*Por*<br/>
Format schowka zainteresowania.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli *cf* jest formatem edycji rich lub text Schowek.

## <a name="cricheditviewisselected"></a><a name="isselected"></a>CRichEditView::IsSelected

Wywołanie tej funkcji, aby ustalić, czy określony element OLE jest aktualnie zaznaczony w tym widoku.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Wskaźnik do obiektu w widoku.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt jest zaznaczony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąpić tę funkcję, jeśli klasa widoku pochodnego ma inną metodę obsługi wyboru elementów OLE.

## <a name="cricheditviewm_nbulletindent"></a><a name="m_nbulletindent"></a>CRichEditView::m_nBulletIndent

Wcięcie dla elementów punktora na liście; domyślnie 720 jednostek, czyli 1/2 cala.

```
int m_nBulletIndent;
```

## <a name="cricheditviewm_nwordwrap"></a><a name="m_nwordwrap"></a>CRichEditView::m_nWordWrap

Wskazuje typ zawijanego wyrazu dla tego bogatego widoku edycji.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Uwagi

Jedna z następujących wartości:

- `WrapNone`Wskazuje brak automatycznego zawijania wyrazów.

- `WrapToWindow`Wskazuje zawijanie wyrazów na podstawie szerokości okna.

- `WrapToTargetDevice`Wskazuje zawijanie wyrazów na podstawie charakterystyki urządzenia docelowego.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::WrapChanged](#wrapchanged).

## <a name="cricheditviewonchareffect"></a><a name="onchareffect"></a>CRichEditView::OnCharEffect

Wywołanie tej funkcji, aby przełączyć efekty formatowania znaków dla bieżącego zaznaczenia.

```cpp
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*Dwmask*<br/>
Efekty formatowania znaków do zmodyfikowania w bieżącym zaznaczeniu.

*dwEfektę*<br/>
Żądana lista efektów formatowania znaków do przełączenia.

### <a name="remarks"></a>Uwagi

Każde wywołanie tej funkcji przełącza określone efekty formatowania dla bieżącego zaznaczenia.

Aby uzyskać więcej informacji na temat parametrów *dwMask* i *dwEffect* i ich potencjalnych wartości, zobacz odpowiednie elementy członkowskie danych [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

## <a name="cricheditviewonfindnext"></a><a name="onfindnext"></a>CRichEditView::OnFindNext

Wywoływana przez platformę podczas przetwarzania poleceń z okna dialogowego Znajdowanie/zamienianie.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Ciąg do znalezienia.

*bNastępna*<br/>
Kierunek wyszukiwania: TRUE wskazuje w dół; FAŁSZ, w górę.

*bKasze*<br/>
Wskazuje, czy w wyszukiwaniu ma być rozróżniana wielkość liter.

*bJąka*<br/>
Wskazuje, czy wyszukiwanie ma być zgodne tylko z całymi słowami, czy nie.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, `CRichEditView`aby znaleźć tekst w pliku . Zastąp tę funkcję, aby zmienić właściwości wyszukiwania dla klasy widoku pochodnego.

## <a name="cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a>CRichEditView::OnInitialUpdate

Wywoływane przez ramy po widoku jest najpierw dołączony do dokumentu, ale przed widok jest początkowo wyświetlany.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje [funkcję CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) element członkowski bez informacji o wskazówkach (czyli przy użyciu wartości domyślnych 0 dla parametru *lHint* i NULL dla parametru *pHint).* Zastąd w tej funkcji należy wykonać jednorazową inicjalizację, która wymaga informacji o dokumencie. Na przykład jeśli aplikacja ma dokumenty o stałym rozmiarze, można użyć tej funkcji, aby zainicjować limity przewijania widoku na podstawie rozmiaru dokumentu. Jeśli aplikacja obsługuje dokumenty o `OnUpdate` zmiennym rozmiarze, użyj do aktualizowania limitów przewijania za każdym razem, gdy dokument się zmienia.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::m_nWordWrap](#m_nwordwrap).

## <a name="cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a>CRichEditView::OnPasteNativeObject

Ta funkcja służy do ładowania danych natywnych z elementu osadzonego.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parametry

*lpStg*<br/>
Wskaźnik do obiektu [IStorage.](/windows/win32/api/objidl/nn-objidl-istorage)

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie, 0;

### <a name="remarks"></a>Uwagi

Zazwyczaj można to zrobić, tworząc [COleStreamFile](../../mfc/reference/colestreamfile-class.md) wokół `IStorage`. Można `COleStreamFile` dołączyć do archiwum i [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) wywoływane, aby załadować dane.

Jest to zaawansowane zastąpienie.

Aby uzyskać więcej informacji, zobacz [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) w usłudze Windows SDK.

## <a name="cricheditviewonparaalign"></a><a name="onparaalign"></a>CRichEditView::OnParaAlign

Wywołanie tej funkcji w celu zmiany wyrównania akapitu dla zaznaczonych akapitów.

```cpp
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parametry

*wAlign*<br/>
Żądane wyrównanie akapitu. Jedna z następujących wartości:

- PFA_LEFT Wyrównaj akapity z lewym marginesem.

- PFA_RIGHT Wyrównaj akapity z prawym marginesem.

- PFA_CENTER Wyśrodkowaj akapity między marginesami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

## <a name="cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a>CRichEditView::OnPrinterZmienił

Zastąp tę funkcję, aby zmienić charakterystykę tego bogatego widoku edycji po zmianie drukarki.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parametry

*dcDrukarka*<br/>
Obiekt [CDC](../../mfc/reference/cdc-class.md) dla nowej drukarki.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ustawia rozmiar papieru na fizyczną wysokość i szerokość urządzenia wyjściowego (drukarki). Jeśli z *dcPrinter*nie jest skojarzony kontekst urządzenia, domyślna implementacja ustawia rozmiar papieru na 8,5 na 11 cali.

## <a name="cricheditviewonreplaceall"></a><a name="onreplaceall"></a>CRichEditView::OnReplaceAll

Wywoływana przez platformę podczas przetwarzania polecenia Zamień wszystkie z okna dialogowego Zamień.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Tekst, który ma zostać zastąpiony.

*lpszReplace (miejsce)*<br/>
Tekst zastępczy.

*bKasze*<br/>
Wskazuje, czy w wyszukiwaniu jest rozróżniana wielkość liter.

*bJąka*<br/>
Wskazuje, czy wyszukiwanie musi wybrać całe słowa, czy nie.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zastąpić wszystkie wystąpienia niektórych danego tekstu innym ciągiem. Zastąp tę funkcję, aby zmienić charakterystyki wyszukiwania dla tego widoku.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::FindText](#findtext).

## <a name="cricheditviewonreplacesel"></a><a name="onreplacesel"></a>CRichEditView::OnReplaceSel

Wywoływana przez platformę podczas przetwarzania poleceń Zamień z okna dialogowego Zamień.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Tekst, który ma zostać zastąpiony.

*bNastępna*<br/>
Wskazuje kierunek wyszukiwania: PRAWDA jest w dół; FAŁSZ, w górę.

*bKasze*<br/>
Wskazuje, czy w wyszukiwaniu jest rozróżniana wielkość liter.

*bJąka*<br/>
Wskazuje, czy wyszukiwanie musi wybrać całe słowa, czy nie.

*lpszReplace (miejsce)*<br/>
Tekst zastępczy.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zastąpić jedno wystąpienie niektórych danego tekstu innym ciągiem. Zastąp tę funkcję, aby zmienić charakterystyki wyszukiwania dla tego widoku.

## <a name="cricheditviewontextnotfound"></a><a name="ontextnotfound"></a>CRichEditView::OnTextNotFound

Wywoływane przez strukturę, gdy wyszukiwanie zakończy się niepowodzeniem.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Tekst, którego nie znaleziono.

### <a name="remarks"></a>Uwagi

Zastąpi tę funkcję, aby zmienić powiadomienie wyjściowe z [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep).

Aby uzyskać więcej informacji, zobacz [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

## <a name="cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a>CRichEditView::OnUpdateCharEffect

Struktura wywołuje tę funkcję, aby zaktualizować interfejs użytkownika polecenia dla poleceń efekt znaków.

```cpp
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do obiektu [CCmdUI.](../../mfc/reference/ccmdui-class.md)

*Dwmask*<br/>
Wskazuje maskę formatowania znaków.

*dwEfektę*<br/>
Wskazuje efekt formatowania znaków.

### <a name="remarks"></a>Uwagi

Maska *dwMask* określa, które atrybuty formatowania znaków należy sprawdzić. Flagi *dwEffect* lista atrybutów formatowania znaków, aby ustawić/wyczyścić.

Aby uzyskać więcej informacji na temat parametrów *dwMask* i *dwEffect* i ich potencjalnych wartości, zobacz odpowiednie elementy członkowskie danych [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

## <a name="cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a>CRichEditView::OnUpdateParaAlign

Struktura wywołuje tę funkcję, aby zaktualizować interfejs użytkownika polecenia dla poleceń efekt akapitu.

```cpp
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do obiektu [CCmdUI.](../../mfc/reference/ccmdui-class.md)

*wAlign*<br/>
Wyrównanie akapitu do sprawdzenia. Jedna z następujących wartości:

- PFA_LEFT Wyrównaj akapity z lewym marginesem.

- PFA_RIGHT Wyrównaj akapity z prawym marginesem.

- PFA_CENTER Wyśrodkowaj akapity między marginesami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

## <a name="cricheditviewprintinsiderect"></a><a name="printinsiderect"></a>CRichEditView::PrintInsideRect

Wywołanie tej funkcji, aby sformatować zakres tekstu w formant edycji bogatej, aby zmieścić się w *rectLayout* dla urządzenia określonego przez *pDC*.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia dla obszaru wyjściowego.

*reectLayout*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect) lub [CRect,](../../atl-mfc-shared/reference/crect-class.md) który definiuje obszar wyjściowy.

*nIndexStart (Początek)*<br/>
Indeks oparty na wartości zerowej pierwszego znaku, który ma zostać sformatowany.

*nIndexStop (Stop)*<br/>
Indeks od zera ostatniego znaku do sformatowania.

*bOutput (Nieuprzejmowanie)*<br/>
Wskazuje, czy tekst ma być renderowany. Jeśli FAŁDa, tekst jest po prostu mierzony.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatniego znaku, który mieści się w obszarze wyjściowym plus jeden.

### <a name="remarks"></a>Uwagi

Zazwyczaj po tym wywołaniu następuje wywołanie [CRichEditCtrl::DisplayBand,](../../mfc/reference/cricheditctrl-class.md#displayband) który generuje dane wyjściowe.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::GetPaperSize](#getpapersize).

## <a name="cricheditviewprintpage"></a><a name="printpage"></a>CRichEditView::PrintPage

Wywołanie tej funkcji, aby sformatować zakres tekstu w formant edycji bogatej dla urządzenia wyjściowego określonego przez *pDC*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia dla danych wyjściowych strony.

*nIndexStart (Początek)*<br/>
Indeks oparty na wartości zerowej pierwszego znaku, który ma zostać sformatowany.

*nIndexStop (Stop)*<br/>
Indeks od zera ostatniego znaku do sformatowania.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatniego znaku, który mieści się na stronie plus jeden.

### <a name="remarks"></a>Uwagi

Układ każdej strony jest kontrolowany przez [GetPageRect](#getpagerect) i [GetPrintRect](#getprintrect). Zazwyczaj po tym wywołaniu następuje wywołanie [CRichEditCtrl::DisplayBand,](../../mfc/reference/cricheditctrl-class.md#displayband) który generuje dane wyjściowe.

Należy zauważyć, że marginesy są względem strony fizycznej, a nie strony logicznej. W związku z tym marginesy zero często przycina tekst, ponieważ wiele drukarek ma obszary niedrukowalne na stronie. Aby uniknąć przycinania tekstu, należy wywołać [SetMargins](#setmargins) i ustawić rozsądne marginesy przed drukowaniem.

## <a name="cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a>CRichEditView::QueryAcceptData

Wywoływana przez strukturę do wklejenia obiektu do edycji bogatej.

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
Wskaźnik do [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) do kwerendy.

*lpcfFormat*<br/>
Wskaźnik do dopuszczalnego formatu danych.

*dwReco (Dwreco)*<br/>
Nie używany.

*bPrawdę*<br/>
Wskazuje, czy operacja wklejania powinna być kontynuowana, czy nie.

*hMetaFile*<br/>
Uchwyt do metapliku używanego do rysowania ikony elementu.

### <a name="return-value"></a>Wartość zwracana

Wartość HRESULT raportowania sukcesu operacji.

### <a name="remarks"></a>Uwagi

Zastąpij tę funkcję do obsługi różnych organizacji elementów COM w klasie dokumentu pochodnego. Jest to zaawansowane zastąpienie.

Aby uzyskać więcej informacji `IDataObject`na temat HRESULT i , zobacz [struktura kodów błędów COM](/windows/win32/com/structure-of-com-error-codes) i [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), odpowiednio, w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

## <a name="cricheditviewsetcharformat"></a><a name="setcharformat"></a>CRichEditView::SetCharFormat

Wywołanie tej funkcji, aby ustawić atrybuty `CRichEditView` formatowania znaków dla nowego tekstu w tym obiekcie.

```cpp
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parametry

*Por*<br/>
[STRUKTURA CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) zawierająca nowe domyślne atrybuty formatowania znaków.

### <a name="remarks"></a>Uwagi

Tylko atrybuty określone `dwMask` przez członka *cf* są zmieniane przez tę funkcję.

Aby uzyskać więcej informacji, zobacz [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) wiadomości i struktury [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewsetmargins"></a><a name="setmargins"></a>CRichEditView::SetMargins

Wywołanie tej funkcji w celu ustawienia marginesów drukowania dla tego widoku edycji rozszerzonej.

```cpp
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parametry

*rectMargin*<br/>
Nowe wartości marginesu dla drukowania, mierzone w MM_TWIPS.

### <a name="remarks"></a>Uwagi

Jeśli [jest](#m_nwordwrap) `WrapToTargetDevice`m_nWordWrap , należy wywołać [WrapChanged](#wrapchanged) po użyciu tej funkcji, aby dostosować charakterystykę drukowania.

Należy zauważyć, że marginesy używane przez [PrintPage](#printpage) są względem strony fizycznej, a nie strony logicznej. W związku z tym marginesy zero często przycina tekst, ponieważ wiele drukarek ma obszary niedrukowalne na stronie. Aby uniknąć obcinania tekstu, `SetMargins` należy wywołać użycie, aby ustawić rozsądne marginesy drukarki przed drukowaniem.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::GetPaperSize](#getpapersize).

## <a name="cricheditviewsetpapersize"></a><a name="setpapersize"></a>CRichEditView::SetPaperSize

Wywołanie tej funkcji powoduje ustawienie rozmiaru papieru do drukowania tego bogatego widoku edycji.

```cpp
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parametry

*rozmiarPaper*<br/>
Nowe wartości rozmiaru papieru dla drukowania, mierzone w MM_TWIPS.

### <a name="remarks"></a>Uwagi

Jeśli [jest](#m_nwordwrap) `WrapToTargetDevice`m_nWordWrap , należy wywołać [WrapChanged](#wrapchanged) po użyciu tej funkcji, aby dostosować charakterystykę drukowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

## <a name="cricheditviewsetparaformat"></a><a name="setparaformat"></a>CRichEditView::SetParaFormat

Wywołanie tej funkcji w celu ustawienia atrybutów `CRichEditView` formatowania akapitu dla bieżącego zaznaczenia w tym obiekcie.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parametry

*Pf*<br/>
[STRUKTURA PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) zawierająca nowe domyślne atrybuty formatowania akapitu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Tylko atrybuty określone `dwMask` przez element *członkowski pf* są zmieniane przez tę funkcję.

Aby uzyskać więcej informacji, zobacz [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) wiadomości i [strukturę PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) w programie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

## <a name="cricheditviewtextnotfound"></a><a name="textnotfound"></a>CRichEditView::TextNotFound

Wywołanie tej funkcji, aby zresetować wewnętrzny stan wyszukiwania [cRichEditView](../../mfc/reference/cricheditview-class.md) kontroli po nieudanej wywołaniu [FindText](#findtext).

```cpp
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Zawiera nieotworowsz ciąg tekstowy, który nie został znaleziony.

### <a name="remarks"></a>Uwagi

Zaleca się, aby ta metoda była wywoływana natychmiast po nieudanych wywołaniach [findtext,](#findtext) tak aby wewnętrzny stan wyszukiwania formantu został poprawnie zresetowany.

Parametr *lpszFind* powinien zawierać taką samą zawartość, jak ciąg dostarczony do [findtext](#findtext). Po zresetowaniu stanu wyszukiwania wewnętrznego ta metoda wywoła [Metodę OnTextNotFound](#ontextnotfound) z podanym ciągiem wyszukiwania.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::FindText](#findtext).

## <a name="cricheditviewwrapchanged"></a><a name="wrapchanged"></a>CRichEditView::WrapZmienił

Wywołanie tej funkcji po zmianie charakterystyki drukowania [(SetMargins](#setmargins) lub [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby zmodyfikować sposób, w jaki bogaty widok edycji reaguje na zmiany [w m_nWordWrap](#m_nwordwrap) lub charakterystykę drukowania ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykładowy program WORDPAD mfc](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)<br/>
[Klasa CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)
