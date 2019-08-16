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
ms.openlocfilehash: f7c9d2b472a443d8bf556d0b12dfe202ea8607a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505048"
---
# <a name="cmfcpropertysheet-class"></a>Klasa CMFCPropertySheet

`CMFCPropertySheet` Klasa obsługuje arkusz właściwości, gdzie każda Strona właściwości jest oznaczona za pomocą karty strony, przycisku paska narzędzi, węzła kontrolki drzewa lub elementu listy.

## <a name="syntax"></a>Składnia

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Konstruuje `CMFCPropertySheet` obiekt.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|Dodaje stronę do arkusza właściwości.|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Dodaje nową stronę właściwości do kontrolki drzewa.|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Dodaje nowy węzeł do kontrolki drzewa.|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Rezerwuje miejsce w górnej części każdej strony, aby narysować niestandardowy nagłówek.|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Pobiera wysokość bieżącego nagłówka.|
|[CMFCPropertySheet:: getwyglądu](#getlook)|Pobiera wartość wyliczenia, która określa wygląd bieżącego arkusza właściwości.|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Ponawia próbę szerokości paska nawigacyjnego (w pikselach).|
|[CMFCPropertySheet::GetTab](#gettab)|Pobiera wewnętrzny obiekt formantu karty, który obsługuje bieżącą kontrolkę arkusza właściwości.|
|`CMFCPropertySheet::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicjuje wygląd bieżącej kontrolki arkusza właściwości.|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Wywoływane przez platformę, gdy jest włączona Strona właściwości.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Wywoływane przez platformę, by narysować niestandardowy nagłówek strony właściwości.|
|`CMFCPropertySheet::OnInitDialog`|Obsługuje komunikat [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) . (Przesłania [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Wywoływane przez platformę, aby usunąć stronę właściwości z kontrolki drzewa.|
|`CMFCPropertySheet::PreTranslateMessage`|Tłumaczy komunikaty okna przed ich wysłaniem do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Przesłania `CPropertySheet::PreTranslateMessage`).|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Usuwa węzeł z kontrolki drzewa.|
|[CMFCPropertySheet::RemovePage](#removepage)|Usuwa stronę właściwości z arkusza właściwości.|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Określa listę obrazów używanych w formancie nawigacji okienka programu Outlook.|
|[CMFCPropertySheet::SetLook](#setlook)|Określa wygląd arkusza właściwości.|

## <a name="remarks"></a>Uwagi

`CMFCPropertySheet` Klasa reprezentuje arkusze właściwości, znane również jako okna dialogowe kart. `CMFCPropertySheet` Klasa może wyświetlać stronę właściwości na różne sposoby.

Wykonaj następujące kroki, aby użyć `CMFCPropertySheet` klasy w aplikacji:

1. Utwórz klasę z `CMFCPropertySheet` klasy i nadaj jej nazwę, na przykład CMyPropertySheet.

1. Utwórz obiekt [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) dla każdej strony właściwości.

1. Wywołaj metodę [CMFCPropertySheet:: setwyglądu](#setlook) w konstruktorze CMyPropertySheet. Parametr tej metody Określa, że strony właściwości są wyświetlane jako karty w górnej lub lewej części arkusza właściwości. karty w stylu arkusza właściwości programu Microsoft OneNote; przyciski na kontrolce Microsoft Outlook Toolbar; węzły w kontrolce drzewa; lub jako lista elementów po lewej stronie arkusza właściwości.

1. Jeśli utworzysz arkusz właściwości w stylu paska narzędzi programu Microsoft Outlook, wywołaj metodę [CMFCPropertySheet:: SetIconsList](#seticonslist) , aby skojarzyć listę obrazów ze stronami właściwości.

1. Wywołaj metodę [CMFCPropertySheet:: AddPage](#addpage) dla każdej strony właściwości.

1. Utwórz kontrolkę i Wywołaj `DoModal` jej metodę. `CMFCPropertySheet`

## <a name="illustrations"></a>Ilustracje

Na poniższej ilustracji przedstawiono arkusz właściwości, który znajduje się w stylu osadzonego paska narzędzi programu Microsoft Outlook. Pasek narzędzi programu Outlook pojawia się po lewej stronie arkusza właściwości.

![Kontrolki koloru CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "Kontrolki koloru CMFCPropertySheet")

Na poniższej ilustracji przedstawiono arkusz właściwości, który zawiera obiekt [klasy CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) . Ten obiekt jest arkuszem właściwości w stylu standardowego wspólnego formantu arkusza właściwości.

![CMFCPropertySheet listy i kontrolki właściwości](../../mfc/reference/media/cmfcpropertysheet_list.png "CMFCPropertySheet listy i kontrolki właściwości")

Na poniższej ilustracji przedstawiono arkusz właściwości, który znajduje się w stylu kontrolki drzewa.

![Drzewo właściwości](../../mfc/reference/media/proptree.png "Drzewo właściwości")

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertysheet. h

##  <a name="addpage"></a>CMFCPropertySheet:: addPage

Dodaje stronę do arkusza właściwości.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
podczas Wskaźnik do obiektu strony. Ten parametr nie może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje określoną stronę właściwości jako kartę z prawej strony w arkuszu właściwości. W związku z tym Użyj tej metody, aby dodać strony w kolejności od lewej do prawej.

Jeśli arkusz właściwości jest stylem programu Microsoft Outlook, struktura wyświetla listę przycisków nawigacji po lewej stronie arkusza właściwości. Po dodaniu przez tę metodę strony właściwości zostanie dodany odpowiedni przycisk do listy. Aby wyświetlić stronę właściwości, kliknij odpowiedni przycisk. Aby uzyskać więcej informacji na temat stylów arkuszy właściwości, zobacz [CMFCPropertySheet:: setwyglądu](#setlook).

##  <a name="addpagetotree"></a>CMFCPropertySheet::AddPageToTree

Dodaje nową stronę właściwości do kontrolki drzewa.

```
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>Parametry

*pCategory*<br/>
podczas Wskaźnik na nadrzędny węzeł drzewa lub wartość NULL, aby skojarzyć określoną stronę z węzłem najwyższego poziomu. Wywołaj metodę [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) , aby uzyskać ten wskaźnik.

*pPage*<br/>
podczas Wskaźnik do obiektu strony właściwości.

*nIconNum*<br/>
podczas Indeks ikony (liczony od zera) lub-1, jeśli nie jest używana żadna ikona. Ikona jest wyświetlana obok strony właściwości kontrolki drzewa, gdy strona nie jest zaznaczona. Wartość domyślna to-1.

*nSelIconNum*<br/>
podczas Indeks ikony (liczony od zera) lub-1, jeśli nie jest używana żadna ikona. Ikona jest wyświetlana obok strony właściwości kontrolki drzewa, gdy strona jest zaznaczona. Wartość domyślna to-1.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje stronę właściwości jako liścia kontrolki drzewa. Aby dodać `CMFCPropertySheet` stronę właściwości, Utwórz obiekt, wywołaj metodę [CMFCPropertySheet:: setwyglądu](#setlook) z parametrem *wyglądu* ustawionym na `CMFCPropertySheet::PropSheetLook_Tree`, a następnie użyj tej metody, aby dodać stronę właściwości.

##  <a name="addtreecategory"></a>CMFCPropertySheet::AddTreeCategory

Dodaje nowy węzeł do kontrolki drzewa.

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
podczas Nazwa węzła.

*nIconNum*<br/>
podczas Indeks ikony (liczony od zera) lub-1, jeśli nie jest używana żadna ikona. Ikona jest wyświetlana obok strony właściwości kontrolki drzewa, gdy strona nie jest zaznaczona. Wartość domyślna to-1.

*nSelectedIconNum*<br/>
podczas Indeks ikony (liczony od zera) lub-1, jeśli nie jest używana żadna ikona. Ikona jest wyświetlana obok strony właściwości kontrolki drzewa, gdy strona jest zaznaczona. Wartość domyślna to-1.

*pParentCategory*<br/>
podczas Wskaźnik na nadrzędny węzeł drzewa lub wartość NULL, aby skojarzyć określoną stronę z węzłem najwyższego poziomu. Ustaw ten parametr za pomocą metody [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) .

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego węzła w kontrolce drzewa.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby dodać nowy węzeł, który jest również określany jako kategoria, do kontrolki drzewa. Aby `CMFCPropertySheet` dodać węzeł, Utwórz obiekt, wywołaj metodę [CMFCPropertySheet:: setwyglądu](#setlook) z parametrem *wyglądu* ustawionym na `CMFCPropertySheet::PropSheetLook_Tree`, a następnie użyj tej metody do dodania węzła.

Użyj wartości zwracanej przez tę metodę w kolejnych wywołaniach [CMFCPropertySheet:: AddPageToTree](#addpagetotree) i [CMFCPropertySheet:: AddTreeCategory](#addtreecategory).

##  <a name="cmfcpropertysheet"></a>CMFCPropertySheet::CMFCPropertySheet

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
podczas Ciąg, który zawiera podpis arkusza właściwości. Nie może mieć wartości NULL.

*nIDCaption*<br/>
podczas Identyfikator zasobu, który zawiera podpis arkusza właściwości.

*pParentWnd*<br/>
podczas Wskaźnik do okna nadrzędnego arkusza właściwości lub wartość NULL, jeśli okno nadrzędne jest głównym oknem aplikacji. Wartość domyślna to NULL.

*iSelectPage*<br/>
podczas Indeks (liczony od zera) górnej strony właściwości. Wartość domyślna to 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz parametry dla konstruktora [CPropertySheet:: CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) .

##  <a name="enablepageheader"></a>CMFCPropertySheet::EnablePageHeader

Rezerwuje miejsce w górnej części każdej strony, aby narysować niestandardowy nagłówek.

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Parametry

*nHeaderHeight*<br/>
podczas Wysokość nagłówka (w pikselach).

### <a name="remarks"></a>Uwagi

Aby użyć wartości parametru *nHeaderHeight* w celu narysowania niestandardowego nagłówka, Zastąp metodę [CMFCPropertySheet:: OnDrawPageHeader](#ondrawpageheader) .

##  <a name="getheaderheight"></a>CMFCPropertySheet::GetHeaderHeight

Pobiera wysokość bieżącego nagłówka.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Wysokość nagłówka (w pikselach).

### <a name="remarks"></a>Uwagi

Przed wywołaniem tej metody Wywołaj metodę [CMFCPropertySheet:: EnablePageHeader](#enablepageheader) .

##  <a name="getlook"></a>CMFCPropertySheet:: getwyglądu

Pobiera wartość wyliczenia, która określa wygląd bieżącego arkusza właściwości.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości wyliczenia, która określa wygląd arkusza właściwości. Listę możliwych wartości można znaleźć w tabeli Wyliczenie w sekcji uwagi [CMFCPropertySheet:: setwyglądu](#setlook).

##  <a name="getnavbarwidth"></a>CMFCPropertySheet::GetNavBarWidth

Pobiera szerokość paska nawigacyjnego.

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość paska nawigacyjnego w pikselach.

##  <a name="gettab"></a>CMFCPropertySheet::GetTab

Pobiera wewnętrzny obiekt formantu karty, który obsługuje bieżącą kontrolkę arkusza właściwości.

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt wewnętrznego formantu karty.

### <a name="remarks"></a>Uwagi

Arkusz właściwości można ustawić tak, aby był wyświetlany w różnych stylach, takich jak kontrolka drzewa, lista przycisków nawigacji lub zestaw stron z kartami.

Przed wywołaniem tej metody Wywołaj metodę [CMFCPropertySheet:: setwyglądu](#setlook) , aby ustawić wygląd kontrolki arkusza właściwości. Następnie Wywołaj metodę [CMFCPropertySheet:: InitNavigationControl](#initnavigationcontrol) , aby zainicjować obiekt wewnętrznego formantu karty. Użyj tej metody, aby pobrać obiekt formantu karty, a następnie użyć tego obiektu do pracy z kartami w arkuszu właściwości.

Ta metoda jest potwierdzona w trybie debugowania, jeśli formant arkusza właściwości nie jest ustawiony do wyświetlania w stylu programu Microsoft OneNote.

##  <a name="initnavigationcontrol"></a>CMFCPropertySheet::InitNavigationControl

Inicjuje wygląd bieżącej kontrolki arkusza właściwości.

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna kontrolki arkusza właściwości.

### <a name="remarks"></a>Uwagi

Kontrolka arkusza właściwości może być wyświetlana w kilku różnych formularzach, takich jak zestaw stron z kartami, kontrolka drzewa lub lista przycisków nawigacji. Użyj metody [CMFCPropertySheet:: Setwyglądu](#setlook) , aby określić wygląd kontrolki arkusza właściwości.

##  <a name="onactivatepage"></a>CMFCPropertySheet::OnActivatePage

Wywoływane przez platformę, gdy jest włączona Strona właściwości.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
podczas Wskaźnik do obiektu strony właściwości, który reprezentuje stronę właściwości włączony.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zapewnia, że aktywna strona właściwości jest przewijana do widoku. Jeśli styl bieżącego arkusza właściwości zawiera okienko programu Microsoft Outlook, ta metoda ustawia odpowiedni przycisk programu Outlook do stanu zaznaczenia.

##  <a name="ondrawpageheader"></a>CMFCPropertySheet::OnDrawPageHeader

Wywoływane przez platformę, by narysować nagłówek dla niestandardowej strony właściwości.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*nPage*<br/>
podczas Numer strony właściwości o wartości zero.

*rectHeader*<br/>
podczas Prostokąt ograniczający, który określa miejsce rysowania nagłówka.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nie wykonuje żadnych operacji. Jeśli zastąpisz tę metodę, wywołaj metodę [CMFCPropertySheet:: EnablePageHeader](#enablepageheader) przed wywołaniem tej metody przez platformę.

##  <a name="onremovetreepage"></a>CMFCPropertySheet::OnRemoveTreePage

Wywoływane przez platformę, aby usunąć stronę właściwości z kontrolki drzewa.

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
podczas Wskaźnik do obiektu strony właściwości, który reprezentuje stronę właściwości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

##  <a name="removecategory"></a>CMFCPropertySheet::RemoveCategory

Usuwa węzeł z kontrolki drzewa.

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Parametry

*pCategory*<br/>
podczas Wskaźnik do kategorii (węzeł) do usunięcia.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby usunąć węzeł, który jest również określany jako kategoria, z kontrolki drzewa. Użyj metody [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) , aby dodać węzeł do kontrolki drzewa.

##  <a name="removepage"></a>CMFCPropertySheet:: Wywołaj RemovePage

Usuwa stronę właściwości z arkusza właściwości.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
podczas Wskaźnik do obiektu strony właściwości, który reprezentuje stronę właściwości do usunięcia. Nie może mieć wartości NULL.

*nPage*<br/>
podczas Indeks (liczony od zera) strony do usunięcia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa określoną stronę właściwości i niszczy skojarzone z nią okno. Obiekt strony właściwości określany przez parametr *ppage* nie jest niszczony, dopóki okno [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) nie zostanie zamknięte.

##  <a name="seticonslist"></a>CMFCPropertySheet::SetIconsList

Określa listę obrazów używanych w formancie nawigacji okienka programu Outlook.

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>Parametry

*uiImageListResID*<br/>
podczas Identyfikator zasobu listy obrazów.

*cx*<br/>
podczas Szerokość ikon na liście obrazów (w pikselach).

*clrTransparent*<br/>
podczas Kolor przezroczystego obrazu. Części obrazu, które są tym kolorem, będą przezroczyste. Wartość domyślna to kolor amarantowy, RGB (255, 0255).

*hIcons*<br/>
podczas Dojście do istniejącej listy obrazów.

### <a name="return-value"></a>Wartość zwracana

W pierwszej składni przeciążenia metody wartość TRUE, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli arkusz właściwości jest stylem programu Microsoft Outlook, w strukturze zostanie wyświetlona lista przycisków nawigacji o nazwie kontrolka okienka programu Outlook znajdująca się po lewej stronie arkusza właściwości. Użyj tej metody, aby ustawić listę obrazów, która będzie używana przez formant okienka programu Outlook.

Aby uzyskać więcej informacji na temat metod, które obsługują tę metodę, zobacz [Korzystanie CImageList:: Create](../../mfc/reference/cimagelist-class.md#create) i [Korzystanie CImageList:: Add](../../mfc/reference/cimagelist-class.md#add). Aby uzyskać więcej informacji na temat sposobu ustawiania stylu arkusza właściwości, zobacz [CMFCPropertySheet:: setwyglądu](#setlook).

##  <a name="setlook"></a>CMFCPropertySheet:: setwyglądu

Określa wygląd arkusza właściwości.

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Parametry

*polu*<br/>
podczas Jedna z wartości wyliczenia, która określa wygląd arkusza właściwości. Domyślny styl arkusza właściwości to `CMFCPropertySheet::PropSheetLook_Tabs`. Więcej informacji znajduje się w tabeli w sekcji uwagi tego tematu.

*nNavControlWidth*<br/>
podczas Szerokość kontrolki nawigacji (w pikselach). Wartość domyślna to 100.

### <a name="remarks"></a>Uwagi

Aby wyświetlić arkusz właściwości w stylu innym niż domyślny, Wywołaj tę metodę przed utworzeniem okna arkusza właściwości.

Poniższa tabela zawiera listę wartości wyliczenia, które można określić w parametrze *wyglądu* .

|Wartość|Opis|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|Wartooć Wyświetla kartę dla każdej strony właściwości. Karty są wyświetlane u góry arkusza właściwości i są ułożone w stosie, jeśli istnieje więcej kart, niż mieści się w pojedynczym wierszu.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Wyświetla listę przycisków nawigacji w stylu paska programu Microsoft Outlook, po lewej stronie arkusza właściwości. Każdy przycisk na liście odpowiada stronie właściwości. W strukturze są wyświetlane strzałki przewijania, jeśli jest więcej przycisków niż mieści się w widocznym obszarze listy.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Wyświetla kontrolkę drzewa po lewej stronie arkusza właściwości. Każdy węzeł nadrzędny lub podrzędny kontrolki drzewa odpowiada stronie właściwości. Struktura wyświetla strzałki przewijania, jeśli istnieje więcej węzłów niż mieści się w widocznym obszarze formantu drzewa.|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Wyświetla kartę w stylu programu Microsoft OneNote dla każdej strony właściwości. Struktura wyświetla karty w górnej części arkusza właściwości i strzałki przewijania, jeśli istnieje więcej kart, niż mieści się w pojedynczym wierszu.|
|`CMFCPropertySheet::PropSheetLook_List`|Wyświetla listę znajdującą się po lewej stronie arkusza właściwości. Każdy element listy odpowiada stronie właściwości. Struktura wyświetla strzałki przewijania, jeśli istnieje więcej elementów listy niż mieści się w widocznym obszarze listy.|

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
