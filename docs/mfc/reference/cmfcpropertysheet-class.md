---
title: Klasa CMFCPropertySheet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5512f806b5abdee56b2c6eabe45f93545c8788e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442945"
---
# <a name="cmfcpropertysheet-class"></a>Klasa CMFCPropertySheet

`CMFCPropertySheet` Klasy obsługuje arkusz właściwości, gdzie każda Strona właściwości jest określona przez kartę strony, przycisk paska narzędzi, węzeł formantu drzewa lub element listy.

## <a name="syntax"></a>Składnia

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Konstruuje `CMFCPropertySheet` obiektu.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|Dodaje strony do arkusza właściwości.|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Dodaje nową stronę właściwości do kontrolki drzewa.|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Dodaje nowy węzeł w drzewie.|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Rezerwuje miejsce u góry każdej strony, aby narysować niestandardowego nagłówka.|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Pobiera wysokość bieżącego nagłówka.|
|[CMFCPropertySheet::GetLook](#getlook)|Pobiera wartość wyliczenia, który określa wygląd bieżącego arkusza właściwości.|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Ponawia próbę szerokości paska nawigacji w pikselach.|
|[CMFCPropertySheet::GetTab](#gettab)|Pobiera obiekt kontroli wewnętrznej karty, który obsługuje bieżącego formantu arkusza właściwości.|
|`CMFCPropertySheet::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicjuje wyglądu formantu bieżącego arkusza właściwości.|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Wywoływane przez platformę, gdy strona właściwości jest włączona.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Metoda wywoływana przez platformę, by narysować nagłówek strony właściwości niestandardowej.|
|`CMFCPropertySheet::OnInitDialog`|Obsługuje [/ / Złap](/windows/desktop/dlgbox/wm-initdialog) wiadomości. (Przesłania [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Metoda wywoływana przez platformę, by usunąć stronę właściwości z kontrolką drzewa.|
|`CMFCPropertySheet::PreTranslateMessage`|Wykonuje translację komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkcje Windows. (Przesłania `CPropertySheet::PreTranslateMessage`.)|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Usunięcie węzła z formantu drzewa.|
|[CMFCPropertySheet::RemovePage](#removepage)|Usuwa stronę właściwości z arkusza właściwości.|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Określa listę obrazów, które są używane w formancie nawigacji w okienku programu Outlook.|
|[CMFCPropertySheet::SetLook](#setlook)|Określa wygląd arkusza właściwości.|

## <a name="remarks"></a>Uwagi

`CMFCPropertySheet` Klasa reprezentuje arkuszy właściwości, znane również jako zakładki okna dialogowego. `CMFCPropertySheet` Klasy można wyświetlić strony właściwości w na różne sposoby.

Wykonaj poniższe kroki, aby użyć `CMFCPropertySheet` klasy w aplikacji:

1. Wyprowadzić klasę z `CMFCPropertySheet` klasy i nazwy klasy, na przykład CMyPropertySheet.

1. Konstruowania [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) obiektu dla każdej strony właściwości.

1. Wywołaj [CMFCPropertySheet::SetLook](#setlook) metody w Konstruktorze CMyPropertySheet. Parametr metody Określa, czy strony właściwości są wyświetlane jako karty wzdłuż górnej lub lewej krawędzi arkusza właściwości; karty w stylu arkusz właściwości programu Microsoft OneNote; przycisków w formancie paska narzędzi programu Microsoft Outlook; węzły w drzewie; lub jako listę elementów po lewej stronie arkusza właściwości.

1. Jeśli tworzysz arkusz właściwości w stylu narzędzi programu Microsoft Outlook, wywołaj [CMFCPropertySheet::SetIconsList](#seticonslist) do kojarzenia listy obrazów oraz na stronach właściwości.

1. Wywołaj [CMFCPropertySheet::AddPage](#addpage) metody dla każdej strony właściwości.

1. Tworzenie `CMFCPropertySheet` kontroli i wywołać jej `DoModal` metody.

## <a name="illustrations"></a>Ilustracje

Poniższa ilustracja przedstawia arkusza właściwości, który jest w stylu osadzonym pasku narzędzi programu Microsoft Outlook. Narzędzi programu Outlook pojawia się po lewej stronie arkusza właściwości.

![Formanty kolor CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet_color")

Poniższa ilustracja przedstawia arkusza właściwości, która zawiera [klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) obiektu. Ten obiekt jest w stylu standardowego wspólnego arkusza właściwości kontrolki arkusza właściwości.

![Kontrolki listy i właściwości CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet_list")

Poniższa ilustracja przedstawia w stylu formantu drzewa arkusza właściwości.

![Drzewo](../../mfc/reference/media/proptree.png "proptree")

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertysheet.h

##  <a name="addpage"></a>  CMFCPropertySheet::AddPage

Dodaje strony do arkusza właściwości.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*Strona_fizyczna*<br/>
[in] Wskaźnik do obiektu strony. Ten parametr nie może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Metoda ta umożliwia dodanie strony określonej właściwości jako kartę po prawej stronie w arkuszu właściwości. W związku z tym, ta metoda umożliwia dodawanie stron w kolejności od lewej do prawej.

W przypadku arkusza właściwości w stylu programu Microsoft Outlook, struktura Wyświetla listę przycisków nawigacji po lewej stronie arkusza właściwości. Po tej metody dodaje strony właściwości, dodaje odpowiedni przycisk do listy. Aby wyświetlić stronę właściwości, kliknij jego odpowiedni przycisk. Aby uzyskać więcej informacji o stylach arkuszy właściwości, zobacz [CMFCPropertySheet::SetLook](#setlook).

##  <a name="addpagetotree"></a>  CMFCPropertySheet::AddPageToTree

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
[in] Wskaźnik do węzła nadrzędnego w drzewie lub wartość NULL, aby skojarzyć określonej strony z węzła najwyższego poziomu. Wywołaj [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metodę, aby uzyskać ten wskaźnik.

*Strona_fizyczna*<br/>
[in] Wskaźnik do obiektu strony właściwości.

*nIconNum*<br/>
[in] Liczony od zera indeks ikony lub -1, jeśli ikona nie jest używana. Ikona jest wyświetlana obok na stronie właściwości formantu drzewa, gdy strona nie jest zaznaczona. Wartość domyślna to -1.

*nSelIconNum*<br/>
[in] Liczony od zera indeks ikony lub -1, jeśli ikona nie jest używana. Ikona jest wyświetlana obok na stronie właściwości kontrolki drzewa, po stronie jest zaznaczona. Wartość domyślna to -1.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje strony właściwości jako liścia formantu drzewa. Aby dodać stronę właściwości, Utwórz `CMFCPropertySheet` obiektu, wywołaj [CMFCPropertySheet::SetLook](#setlook) metody z *Szukaj* parametr `CMFCPropertySheet::PropSheetLook_Tree`, a następnie użyć tej metody, aby dodać stronę właściwości .

##  <a name="addtreecategory"></a>  CMFCPropertySheet::AddTreeCategory

Dodaje nowy węzeł w drzewie.

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Nazwa węzła.

*nIconNum*<br/>
[in] Liczony od zera indeks ikony lub -1, jeśli ikona nie jest używana. Ikona jest wyświetlana obok na stronie właściwości formantu drzewa, gdy strona nie jest zaznaczona. Wartość domyślna to -1.

*nSelectedIconNum*<br/>
[in] Liczony od zera indeks ikony lub -1, jeśli ikona nie jest używana. Ikona jest wyświetlana obok na stronie właściwości kontrolki drzewa, po stronie jest zaznaczona. Wartość domyślna to -1.

*pParentCategory*<br/>
[in] Wskaźnik do węzła nadrzędnego w drzewie lub wartość NULL, aby skojarzyć określonej strony z węzła najwyższego poziomu. Ustaw ten parametr z [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metody.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego węzła w drzewie.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia dodawanie nowego węzła, który jest również określany jako kategoria, do formantu drzewa. Aby dodać węzeł, Utwórz `CMFCPropertySheet` obiektu, wywołaj [CMFCPropertySheet::SetLook](#setlook) metody z *Szukaj* parametr `CMFCPropertySheet::PropSheetLook_Tree`, a następnie użyć tej metody, aby dodać węzeł.

Użyj wartości zwracanej przez tę metodę w kolejnych wywołaniach [CMFCPropertySheet::AddPageToTree](#addpagetotree) i [CMFCPropertySheet::AddTreeCategory](#addtreecategory).

##  <a name="cmfcpropertysheet"></a>  CMFCPropertySheet::CMFCPropertySheet

Konstruuje `CMFCPropertySheet` obiektu.

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
[in] Ciąg, który zawiera podpis arkusza właściwości. Nie może mieć wartości NULL.

*nIDCaption*<br/>
[in] Identyfikator zasobu, który zawiera podpis arkusza właściwości.

*pParentWnd*<br/>
[in] Wskaźnik do nadrzędnego okna arkusza właściwości, lub wartość NULL, jeśli okno nadrzędne jest głównego okna aplikacji. Wartością domyślną jest NULL.

*iSelectPage*<br/>
[in] Liczony od zera indeks strony najważniejsze właściwości. Wartość domyślna to 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz parametry [CPropertySheet::CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) konstruktora.

##  <a name="enablepageheader"></a>  CMFCPropertySheet::EnablePageHeader

Rezerwuje miejsce u góry każdej strony, aby narysować niestandardowego nagłówka.

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Parametry

*nHeaderHeight*<br/>
[in] Wysokość nagłówka, w pikselach.

### <a name="remarks"></a>Uwagi

Aby użyć wartości *nHeaderHeight* zastąpienie parametru, aby narysować niestandardowy nagłówek [CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader) metody.

##  <a name="getheaderheight"></a>  CMFCPropertySheet::GetHeaderHeight

Pobiera wysokość bieżącego nagłówka.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Wysokość nagłówka, w pikselach.

### <a name="remarks"></a>Uwagi

Wywołaj [CMFCPropertySheet::EnablePageHeader](#enablepageheader) metoda przed wywołaniem tej metody.

##  <a name="getlook"></a>  CMFCPropertySheet::GetLook

Pobiera wartość wyliczenia, który określa wygląd bieżącego arkusza właściwości.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości wyliczenia, które określa wygląd arkusza właściwości. Aby uzyskać listę możliwych wartości, zobacz tabelę wyliczenia w sekcji uwag [CMFCPropertySheet::SetLook](#setlook).

##  <a name="getnavbarwidth"></a>  CMFCPropertySheet::GetNavBarWidth

Pobiera szerokość paska nawigacyjnego.

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość paska nawigacji w pikselach.

##  <a name="gettab"></a>  CMFCPropertySheet::GetTab

Pobiera obiekt kontroli wewnętrznej karty, który obsługuje bieżącego formantu arkusza właściwości.

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt kontroli wewnętrznej karty.

### <a name="remarks"></a>Uwagi

Arkusz właściwości można ustawić tak, aby było wyświetlane w różnych stylów, takie jak formant drzewa listę przycisków nawigacji lub zestaw stron z kartami.

Przed wywołaniem tej metody należy wywołać [CMFCPropertySheet::SetLook](#setlook) metodę, aby ustawić wygląd formantu arkusza właściwości. Następnie wywołaj [CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol) metodę, aby zainicjować obiekt formantu wewnętrznej karty. Ta metoda umożliwia pobieranie obiekt formantu karty, a następnie użyj tego obiektu do pracy z kartami w arkuszu właściwości.

Ta metoda potwierdza w trybie debugowania, jeśli nie ustawiono właściwości kontrolki arkusza pojawią się w stylu programu Microsoft OneNote.

##  <a name="initnavigationcontrol"></a>  CMFCPropertySheet::InitNavigationControl

Inicjuje wyglądu formantu bieżącego arkusza właściwości.

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna formantu arkusza właściwości.

### <a name="remarks"></a>Uwagi

Formant arkusz właściwości może znajdować się w różnych formularzach, takiego jak zestaw strony z kartami, formant drzewa lub Podaj listę przycisków nawigacji. Użyj [CMFCPropertySheet::SetLook](#setlook) metodę, aby określić wygląd formantu arkusza właściwości.

##  <a name="onactivatepage"></a>  CMFCPropertySheet::OnActivatePage

Wywoływane przez platformę, gdy strona właściwości jest włączona.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*Strona_fizyczna*<br/>
[in] Wskaźnik do obiektu strony właściwości, który reprezentuje stronę dla właściwości włączone.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zapewnia, że strony dla właściwości włączone jest przewijane do widoku. Styl bieżący arkusz właściwości zawiera okienku programu Microsoft Outlook, ta metoda ustawia odpowiedni przycisk Outlook zaznaczony stan.

##  <a name="ondrawpageheader"></a>  CMFCPropertySheet::OnDrawPageHeader

Metoda wywoływana przez platformę, by narysować nagłówek dla niestandardowej strony właściwości.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*nPage*<br/>
[in] Numer strony właściwości liczony od zera.

*rectHeader*<br/>
[in] Prostokąt otaczający, który określa, gdzie można narysować nagłówka.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nie działa. Jeśli zastąpisz tę metodę należy wywołać [CMFCPropertySheet::EnablePageHeader](#enablepageheader) metoda przed struktura wywołuje tę metodę.

##  <a name="onremovetreepage"></a>  CMFCPropertySheet::OnRemoveTreePage

Metoda wywoływana przez platformę, by usunąć stronę właściwości z kontrolką drzewa.

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*Strona_fizyczna*<br/>
[in] Wskaźnik do obiektu strony właściwości, który reprezentuje stronę właściwości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="removecategory"></a>  CMFCPropertySheet::RemoveCategory

Usunięcie węzła z formantu drzewa.

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Parametry

*pCategory*<br/>
[in] Wskaźnik do kategorii (node) do usunięcia.

### <a name="remarks"></a>Uwagi

Użyj tej metody można usunąć węzła, który jest również nazywany kategorii z kontrolką drzewa. Użyj [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metodę, aby dodać węzeł do formantu drzewa.

##  <a name="removepage"></a>  CMFCPropertySheet::RemovePage

Usuwa stronę właściwości z arkusza właściwości.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*Strona_fizyczna*<br/>
[in] Wskaźnik do obiektu strony właściwości, który reprezentuje stronę właściwości do usunięcia. Nie może mieć wartości NULL.

*nPage*<br/>
[in] Liczony od zera indeks strony do usunięcia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa stronę określonej właściwości i niszczy okno skojarzone. Na stronie właściwości obiektu, który *Strona_fizyczna* parametr określa, nie jest niszczony, dopóki [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) okno zostanie zamknięte.

##  <a name="seticonslist"></a>  CMFCPropertySheet::SetIconsList

Określa listę obrazów, które są używane w formancie nawigacji w okienku programu Outlook.

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>Parametry

*uiImageListResID*<br/>
[in] Identyfikator zasobu z listy obrazów.

*CX*<br/>
[in] Szerokość w pikselach, ikony na liście obrazów.

*clrTransparent*<br/>
[in] Kolor przezroczysty obraz. Części obrazu, które są ten kolor ma być przezroczysty. Wartość domyślna to amarantowy kolorów, RGB(255,0,255).

*hIcons*<br/>
[in] Dojście do istniejącej listy obrazów.

### <a name="return-value"></a>Wartość zwracana

W przypadku pierwszej metody przeciążenia składni, wartość TRUE jeśli ta metoda się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

W przypadku arkusza właściwości w stylu programu Microsoft Outlook, struktura Wyświetla listę przycisków nawigacji, o nazwie kontrolki okienka programu Outlook, po lewej stronie arkusza właściwości. Użyj tej metody do ustawiania listy obrazów do użycia przez kontrolki okienka programu Outlook.

Aby uzyskać więcej informacji na temat metody, które obsługują tę metodę, zobacz [CImageList::Create](../../mfc/reference/cimagelist-class.md#create) i [CImageList::Add](../../mfc/reference/cimagelist-class.md#add). Aby uzyskać więcej informacji na temat ustawiania styl arkusza właściwości, zobacz [CMFCPropertySheet::SetLook](#setlook).

##  <a name="setlook"></a>  CMFCPropertySheet::SetLook

Określa wygląd arkusza właściwości.

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Parametry

*wygląd*<br/>
[in] Jedna z wartości wyliczenia, które określa wygląd arkusza właściwości. Jest to styl domyślny dla arkusza właściwości `CMFCPropertySheet::PropSheetLook_Tabs`. Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag w tym temacie.

*nNavControlWidth*<br/>
[in] Szerokość Nawigacja kontrolki, w pikselach. Wartość domyślna to 100.

### <a name="remarks"></a>Uwagi

Aby wyświetlić arkusz właściwości stylu inną niż domyślna, tę metodę należy wywołać przed utworzeniem okna arkusza właściwości.

W poniższej tabeli wymieniono wartości wyliczenia, które można określić w *Szukaj* parametru.

|Wartość|Opis|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|(Ustawienie domyślne) Wyświetla kartę dla każdej strony właściwości. Karty są wyświetlane w górnej części arkusza właściwości i są ułożone w przypadku więcej kart niż mieści się w jednym wierszu.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Wyświetla listę przycisków nawigacji w stylu na pasku programu Microsoft Outlook po lewej stronie arkusza właściwości. Każdy przycisk na liście odnosi się do strony właściwości. Struktura wyświetla strzałki przewijania, jeśli istnieje więcej przycisków, niż mieści się w obszarze widoczna lista.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Wyświetla formant drzewa po lewej stronie arkusza właściwości. Na każdym węźle nadrzędnych i podrzędnych kontrolki drzewa odnosi się do strony właściwości. Struktura wyświetla strzałki przewijania, jeśli istnieje więcej węzłów niż mieści się w obszarze widoczne kontrolki drzewa.|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Wyświetla kartę w stylu programu Microsoft OneNote dla każdej strony właściwości. Struktura wyświetla karty w górnej części arkusza właściwości i strzałki przewijania w przypadku więcej kart niż mieści się w jednym wierszu.|
|`CMFCPropertySheet::PropSheetLook_List`|Wyświetla listę po lewej stronie arkusza właściwości. Każdy element tej listy odnosi się do strony właściwości. Struktura wyświetla strzałki przewijania, jeśli istnieje więcej elementów listy, niż mieści się w obszarze widoczne listy.|

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
