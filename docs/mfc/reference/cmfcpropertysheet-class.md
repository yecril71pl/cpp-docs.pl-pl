---
title: Klasa CMFCPropertySheet
ms.date: 11/19/2018
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
ms.openlocfilehash: 6cdb2e966ca1878377fd26a6d4b9075090d32c3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361802"
---
# <a name="cmfcpropertysheet-class"></a>Klasa CMFCPropertySheet

Klasa `CMFCPropertySheet` obsługuje arkusz właściwości, w którym każda strona właściwości jest oznaczona przez kartę strony, przycisk paska narzędzi, węzeł sterowania drzewa lub element listy.

## <a name="syntax"></a>Składnia

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ARKUSZ CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Konstruuje `CMFCPropertySheet` obiekt.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|Dodaje stronę do arkusza właściwości.|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Dodaje nową stronę właściwości do formantu drzewa.|
|[ARKUSZ CMFCPropertySheet::AddTree](#addtreecategory)|Dodaje nowy węzeł do formantu drzewa.|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Rezerwuje miejsce u góry każdej strony, aby narysować niestandardowy nagłówek.|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Pobiera wysokość bieżącego nagłówka.|
|[CMFCPropertySheet::GetLook](#getlook)|Pobiera wartość wyliczenia, która określa wygląd bieżącego arkusza właściwości.|
|[ARKUSZ CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Ponawia ponawia szerokość paska nawigacyjnego w pikselach.|
|[ARKUSZ CMFCPropertySheet::GetTab](#gettab)|Pobiera obiekt kontroli karty wewnętrznej, który obsługuje bieżącą kontrolę arkusza właściwości.|
|`CMFCPropertySheet::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicjuje wygląd bieżącej kontroli arkusza właściwości.|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Wywoływane przez platformę, gdy strona właściwości jest włączona.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Wywoływane przez strukturę, aby narysować nagłówek strony właściwości niestandardowej.|
|`CMFCPropertySheet::OnInitDialog`|Obsługuje komunikat [WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog) (Zastępuje [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Wywoływane przez strukturę, aby usunąć stronę właściwości z formantu drzewa.|
|`CMFCPropertySheet::PreTranslateMessage`|Tłumaczy komunikaty okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. (Przesłania `CPropertySheet::PreTranslateMessage`).|
|[CMFCPropertySheet::Usuń kategorię](#removecategory)|Usuwa węzeł z formantu drzewa.|
|[CMFCPropertySheet::RemovePage](#removepage)|Usuwa stronę właściwości z arkusza właściwości.|
|[ARKUSZ CMFCPropertySheet::SetIconsList](#seticonslist)|Określa listę obrazów używanych w formancie nawigacyjnym okienka programu Outlook.|
|[CMFCPropertySheet::SetLook](#setlook)|Określa wygląd arkusza właściwości.|

## <a name="remarks"></a>Uwagi

Klasa `CMFCPropertySheet` reprezentuje arkusze właściwości, znane również jako okna dialogowe kart. Klasa `CMFCPropertySheet` może wyświetlać stronę właściwości na różne sposoby.

Wykonaj następujące kroki, `CMFCPropertySheet` aby użyć klasy w aplikacji:

1. Wyprowadzić klasę z `CMFCPropertySheet` klasy i nazwę klasy, na przykład CMyPropertySheet.

1. Konstruuj [OBIEKT CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) dla każdej strony właściwości.

1. Wywołanie [CMFCPropertySheet::SetLook](#setlook) metody w CMyPropertySheet konstruktora. Parametr tej metody określa, że strony właściwości powinny być wyświetlane jako karty w górnej lub lewej części arkusza właściwości; karty w stylu arkusza właściwości programu Microsoft OneNote; przyciski na pasku narzędzi programu Microsoft Outlook; węzły na formancie drzewa; lub jako lista elementów po lewej stronie arkusza właściwości.

1. Jeśli tworzysz arkusz właściwości w stylu paska narzędzi programu Microsoft Outlook, wywołanie [CMFCPropertySheet::SetIconsList](#seticonslist) metody skojarzyć listę obrazów wraz ze stronami właściwości.

1. Wywołanie [CMFCPropertySheet::AddPage](#addpage) metody dla każdej strony właściwości.

1. Utwórz `CMFCPropertySheet` formant `DoModal` i wywołaj jego metodę.

## <a name="illustrations"></a>Ilustracje

Na poniższej ilustracji przedstawiono arkusz właściwości, który jest w stylu osadzonego paska narzędzi programu Microsoft Outlook. Pasek narzędzi programu Outlook pojawi się po lewej stronie arkusza właściwości.

![Kontrolki kolorów arkusza CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "Kontrolki kolorów arkusza CMFCPropertySheet")

Na poniższej ilustracji przedstawiono arkusz właściwości, który zawiera [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md) obiektu. Ten obiekt jest arkuszem właściwości w stylu standardowego arkusza właściwości common controls.

![CMFCPropertySheet lista i formanty właściwości](../../mfc/reference/media/cmfcpropertysheet_list.png "CMFCPropertySheet lista i formanty właściwości")

Na poniższej ilustracji przedstawiono arkusz właściwości, który jest w stylu formantu drzewa.

![Drzewo właściwości](../../mfc/reference/media/proptree.png "Drzewo właściwości")

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cpropertysheet](../../mfc/reference/cpropertysheet-class.md)

[Cmfcpropertysheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertysheet.h

## <a name="cmfcpropertysheetaddpage"></a><a name="addpage"></a>CMFCPropertySheet::AddPage

Dodaje stronę do arkusza właściwości.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*strona pPage*<br/>
[w] Wskaźnik do obiektu strony. Ten parametr nie może być null.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje stronę określonej właściwości jako kartę po prawej stronie w arkuszu właściwości. W związku z tym użyj tej metody, aby dodać strony w kolejności od lewej do prawej.

Jeśli arkusz właściwości jest w stylu programu Microsoft Outlook, w ramach zostanie wyświetlona lista przycisków nawigacyjnych po lewej stronie arkusza właściwości. Po tej metody dodaje stronę właściwości, dodaje odpowiedni przycisk do listy. Aby wyświetlić stronę właściwości, kliknij jej odpowiedni przycisk. Aby uzyskać więcej informacji na temat stylów arkuszy właściwości, zobacz [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetaddpagetotree"></a><a name="addpagetotree"></a>CMFCPropertySheet::AddPageToTree

Dodaje nową stronę właściwości do formantu drzewa.

```
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>Parametry

*p Kategoria*<br/>
[w] Wskaźnik do węzła drzewa nadrzędnego lub NULL, aby skojarzyć określoną stronę z węzłem najwyższego poziomu. Wywołanie [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metody, aby uzyskać ten wskaźnik.

*strona pPage*<br/>
[w] Wskaźnik do obiektu strony właściwości.

*nIconNum*<br/>
[w] Indeks od zera ikony lub -1, jeśli nie jest używana żadna ikona. Ikona jest wyświetlana obok strony właściwości formantu drzewa, gdy strona nie jest zaznaczona. Wartość domyślna to -1.

*nSelIconNum (07.*<br/>
[w] Indeks od zera ikony lub -1, jeśli nie jest używana żadna ikona. Ikona jest wyświetlana obok strony właściwości formantu drzewa po wybraniu strony. Wartość domyślna to -1.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje stronę właściwości jako liść formantu drzewa. Aby dodać stronę właściwości, `CMFCPropertySheet` utwórz obiekt, należy wywołać metodę [CMFCPropertySheet::SetLook](#setlook) z parametrem *look* ustawionym na `CMFCPropertySheet::PropSheetLook_Tree`, a następnie użyj tej metody, aby dodać stronę właściwości.

## <a name="cmfcpropertysheetaddtreecategory"></a><a name="addtreecategory"></a>ARKUSZ CMFCPropertySheet::AddTree

Dodaje nowy węzeł do formantu drzewa.

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Nazwa węzła.

*nIconNum*<br/>
[w] Indeks od zera ikony lub -1, jeśli nie jest używana żadna ikona. Ikona jest wyświetlana obok strony właściwości formantu drzewa, gdy strona nie jest zaznaczona. Wartość domyślna to -1.

*nWybranekIconNum*<br/>
[w] Indeks od zera ikony lub -1, jeśli nie jest używana żadna ikona. Ikona jest wyświetlana obok strony właściwości formantu drzewa po wybraniu strony. Wartość domyślna to -1.

*p Kategoria rodziców*<br/>
[w] Wskaźnik do węzła drzewa nadrzędnego lub NULL, aby skojarzyć określoną stronę z węzłem najwyższego poziomu. Ustaw ten parametr za pomocą [cmfcpropertysheet::AddTreeCategory](#addtreecategory) metody.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego węzła w formancie drzewa.

### <a name="remarks"></a>Uwagi

Ta metoda służy do dodawania nowego węzła, który jest również określany jako kategoria, do formantu drzewa. Aby dodać węzeł, `CMFCPropertySheet` utwórz obiekt, należy wywołać metodę [CMFCPropertySheet::SetLook](#setlook) z ustawionym parametrem *look* `CMFCPropertySheet::PropSheetLook_Tree`na , a następnie użyj tej metody, aby dodać węzeł.

Użyj zwracanej wartości tej metody w kolejnych wywołaniach [do CMFCPropertySheet::AddPageToTree](#addpagetotree) i [CMFCPropertySheet::AddTreeCategory](#addtreecategory).

## <a name="cmfcpropertysheetcmfcpropertysheet"></a><a name="cmfcpropertysheet"></a>ARKUSZ CMFCPropertySheet::CMFCPropertySheet

Konstruuje `CMFCPropertySheet` obiekt.

```
CMFCPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);
```

### <a name="parameters"></a>Parametry

*pszCaption*<br/>
[w] Ciąg zawierający podpis arkusza właściwości. Nie może być null.

*nIDCaption (nIDCaption)*<br/>
[w] Identyfikator zasobu zawierający podpis arkusza właściwości.

*pParentWnd*<br/>
[w] Wskaźnik do okna nadrzędnego arkusza właściwości lub NULL, jeśli okno nadrzędne jest głównym oknem aplikacji. Wartością domyślną jest NULL.

*Strona iSelectPage*<br/>
[w] Indeks od zera strony właściwości górnej. Wartość domyślna to 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz parametry konstruktora [CPropertySheet::CPropertySheet.](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)

## <a name="cmfcpropertysheetenablepageheader"></a><a name="enablepageheader"></a>CMFCPropertySheet::EnablePageHeader

Rezerwuje miejsce u góry każdej strony, aby narysować niestandardowy nagłówek.

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Parametry

*nPozycja Dosłow*<br/>
[w] Wysokość nagłówka w pikselach.

### <a name="remarks"></a>Uwagi

Aby użyć wartości parametru *nHeaderHeight* do narysowania niestandardowego nagłówka, należy zastąpić metodę [CMFCPropertySheet::OnDrawPageHeader.](#ondrawpageheader)

## <a name="cmfcpropertysheetgetheaderheight"></a><a name="getheaderheight"></a>CMFCPropertySheet::GetHeaderHeight

Pobiera wysokość bieżącego nagłówka.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Wysokość nagłówka w pikselach.

### <a name="remarks"></a>Uwagi

Wywołanie [CMFCPropertySheet::EnablePageHeader](#enablepageheader) metody przed wywołaniem tej metody.

## <a name="cmfcpropertysheetgetlook"></a><a name="getlook"></a>CMFCPropertySheet::GetLook

Pobiera wartość wyliczenia, która określa wygląd bieżącego arkusza właściwości.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości wyliczenia, która określa wygląd arkusza właściwości. Aby uzyskać listę możliwych wartości, zobacz tabelę wyliczenia w sekcji Uwagi [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetgetnavbarwidth"></a><a name="getnavbarwidth"></a>ARKUSZ CMFCPropertySheet::GetNavBarWidth

Pobiera szerokość paska nawigacyjnego.

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość paska nawigacyjnego w pikselach.

## <a name="cmfcpropertysheetgettab"></a><a name="gettab"></a>ARKUSZ CMFCPropertySheet::GetTab

Pobiera obiekt kontroli karty wewnętrznej, który obsługuje bieżącą kontrolę arkusza właściwości.

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt kontroli karty wewnętrznej.

### <a name="remarks"></a>Uwagi

Arkusz właściwości można ustawić tak, aby był wyświetlany w różnych stylach, takich jak kontrolka drzewa, lista przycisków nawigacyjnych lub zestaw stron z kartami.

Przed wywołaniem tej metody, wywołać [CMFCPropertySheet::SetLook](#setlook) metody, aby ustawić wygląd kontroli arkusza właściwości. Następnie wywołaj [CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol) metoda inicjowania obiektu kontroli wewnętrznej karty. Ta metoda służy do pobierania obiektu kontroli karty, a następnie użyj tego obiektu do pracy z kartami w arkuszu właściwości.

Ta metoda potwierdza w trybie debugowania, jeśli formant arkusza właściwości nie jest ustawiony na wyświetlane w stylu programu Microsoft OneNote.

## <a name="cmfcpropertysheetinitnavigationcontrol"></a><a name="initnavigationcontrol"></a>CMFCPropertySheet::InitNavigationControl

Inicjuje wygląd bieżącej kontroli arkusza właściwości.

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna formantu arkusza właściwości.

### <a name="remarks"></a>Uwagi

Formant arkusza właściwości może pojawić się w kilku różnych formach, takich jak zestaw stron z kartami, kontrolka drzewa lub lista przycisków nawigacyjnych. Użyj [CMFCPropertySheet::SetLook](#setlook) metody, aby określić wygląd formantu arkusza właściwości.

## <a name="cmfcpropertysheetonactivatepage"></a><a name="onactivatepage"></a>CMFCPropertySheet::OnActivatePage

Wywoływane przez platformę, gdy strona właściwości jest włączona.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*strona pPage*<br/>
[w] Wskaźnik do obiektu strony właściwości, który reprezentuje stronę właściwości włączone.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zapewnia, że strona włączone właściwości jest przewijana do widoku. Jeśli styl bieżącego arkusza właściwości zawiera okienko programu Microsoft Outlook, ta metoda ustawia odpowiedni przycisk programu Outlook na stan zaznaczony.

## <a name="cmfcpropertysheetondrawpageheader"></a><a name="ondrawpageheader"></a>CMFCPropertySheet::OnDrawPageHeader

Wywoływane przez strukturę, aby narysować nagłówek dla strony właściwości niestandardowej.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*strona nPage*<br/>
[w] Numer strony właściwości opartej na wartości zerowej.

*reectHeader (głowica)*<br/>
[w] Prostokąt ograniczający, który określa, gdzie można narysować nagłówek.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nic nie robi. Jeśli zastąpisz tę metodę, wywołaj [metodę CMFCPropertySheet::EnablePageHeader,](#enablepageheader) zanim framework wywoła tę metodę.

## <a name="cmfcpropertysheetonremovetreepage"></a><a name="onremovetreepage"></a>CMFCPropertySheet::OnRemoveTreePage

Wywoływane przez strukturę, aby usunąć stronę właściwości z formantu drzewa.

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*strona pPage*<br/>
[w] Wskaźnik do obiektu strony właściwości, który reprezentuje stronę właściwości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

## <a name="cmfcpropertysheetremovecategory"></a><a name="removecategory"></a>CMFCPropertySheet::Usuń kategorię

Usuwa węzeł z formantu drzewa.

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Parametry

*p Kategoria*<br/>
[w] Wskaźnik do kategorii (węzła), aby usunąć.

### <a name="remarks"></a>Uwagi

Ta metoda służy do usuwania węzła, który jest również określany jako kategoria, z formantu drzewa. Użyj [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metody, aby dodać węzeł do formantu drzewa.

## <a name="cmfcpropertysheetremovepage"></a><a name="removepage"></a>CMFCPropertySheet::RemovePage

Usuwa stronę właściwości z arkusza właściwości.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*strona pPage*<br/>
[w] Wskaźnik do obiektu strony właściwości, który reprezentuje stronę właściwości do usunięcia. Nie może być null.

*strona nPage*<br/>
[w] Indeks od zera strony do usunięcia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa stronę określonej właściwości i niszczy skojarzone z nim okno. Obiekt strony właściwości, który określa parametr *pPage,* nie jest niszczony, dopóki okno [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) nie zostanie zamknięte.

## <a name="cmfcpropertysheetseticonslist"></a><a name="seticonslist"></a>ARKUSZ CMFCPropertySheet::SetIconsList

Określa listę obrazów używanych w formancie nawigacyjnym okienka programu Outlook.

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>Parametry

*uiImageListResID*<br/>
[w] Identyfikator zasobu listy obrazów.

*Cx*<br/>
[w] Szerokość ikon na liście obrazów w pikselach.

*clrPrzezroczysty*<br/>
[w] Przezroczysty kolor obrazu. Części obrazu, które są tym kolorem, będą przezroczyste. Wartością domyślną jest kolor amarantowy, RGB(255,0,255).

*hIcons*<br/>
[w] Dojście do istniejącej listy obrazów.

### <a name="return-value"></a>Wartość zwracana

W składni przeciążenia pierwszej metody, PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli arkusz właściwości jest w stylu programu Microsoft Outlook, w ramach zostanie wyświetlona lista przycisków nawigacyjnych, nazywanych kontrolką okienka programu Outlook, po lewej stronie arkusza właściwości. Ta metoda służy do ustawiania listy obrazów, która ma być używana przez kontrolkę okienka programu Outlook.

Aby uzyskać więcej informacji na temat metod, które obsługują tę metodę, zobacz [CImageList::Create](../../mfc/reference/cimagelist-class.md#create) i [CImageList::Add](../../mfc/reference/cimagelist-class.md#add). Aby uzyskać więcej informacji na temat ustawiania stylu arkusza właściwości, zobacz [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetsetlook"></a><a name="setlook"></a>CMFCPropertySheet::SetLook

Określa wygląd arkusza właściwości.

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Parametry

*Wyglądać*<br/>
[w] Jedna z wartości wyliczenia, która określa wygląd arkusza właściwości. Domyślnym stylem arkusza `CMFCPropertySheet::PropSheetLook_Tabs`właściwości jest . Aby uzyskać więcej informacji, zobacz tabelę w sekcji Uwagi tego tematu.

*nNavControlWidth*<br/>
[w] Szerokość formantu nawigacji w pikselach. Wartość domyślna to 100.

### <a name="remarks"></a>Uwagi

Aby wyświetlić arkusz właściwości w stylu innym niż domyślny, należy wywołać tę metodę przed utworzeniem okna arkusza właściwości.

W poniższej tabeli wymieniono wartości wyliczenia, które można określić w parametrze *look.*

|Wartość|Opis|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|(Domyślnie) Wyświetla kartę dla każdej strony właściwości. Karty są wyświetlane w górnej części arkusza właściwości i są ułożone, jeśli jest więcej kart niż zmieści się w jednym wierszu.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Wyświetla listę przycisków nawigacyjnych w stylu paska programu Microsoft Outlook po lewej stronie arkusza właściwości. Każdy przycisk na liście odpowiada stronie właściwości. Struktura wyświetla strzałki przewijania, jeśli istnieje więcej przycisków niż zmieści się w widocznym obszarze listy.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Wyświetla formant drzewa po lewej stronie arkusza właściwości. Każdy węzeł nadrzędny lub podrzędny formantu drzewa odpowiada stronie właściwości. Struktura wyświetla strzałki przewijania, jeśli istnieje więcej węzłów niż zmieści się w widocznym obszarze formantu drzewa.|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Wyświetla kartę w stylu programu Microsoft OneNote dla każdej strony właściwości. Struktura wyświetla karty w górnej części arkusza właściwości i strzałki przewijania, jeśli istnieje więcej kart niż zmieści się w jednym wierszu.|
|`CMFCPropertySheet::PropSheetLook_List`|Wyświetla listę po lewej stronie arkusza właściwości. Każdy element listy odpowiada stronie właściwości. Struktura wyświetla strzałki przewijania, jeśli istnieje więcej elementów listy niż zmieści się w widocznym obszarze listy.|

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
