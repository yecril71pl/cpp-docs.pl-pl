---
title: Klasa CHeaderCtrl
ms.date: 11/04/2016
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
ms.openlocfilehash: 62915da703e1c938e65643ab389999b83c72d459
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78871590"
---
# <a name="cheaderctrl-class"></a>Klasa CHeaderCtrl

Oferuje funkcje formantu typowego nagłówka systemu Windows.

## <a name="syntax"></a>Składnia

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeaderCtrl:: CHeaderCtrl](#cheaderctrl)|Konstruuje obiekt `CHeaderCtrl`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeaderCtrl:: ClearAllFilters](#clearallfilters)|Czyści wszystkie filtry dla kontrolki nagłówka.|
|[CHeaderCtrl:: ClearFilter](#clearfilter)|Czyści filtr dla kontrolki nagłówka.|
|[CHeaderCtrl:: Create](#create)|Tworzy formant nagłówka i dołącza go do obiektu `CHeaderCtrl`.|
|[CHeaderCtrl:: CreateDragImage](#createdragimage)|Tworzy przezroczystą wersję obrazu elementu w formancie nagłówka.|
|[CHeaderCtrl:: CreateEx](#createex)|Tworzy formant nagłówka z określonymi stylami rozszerzonymi systemu Windows i dołącza go do obiektu `CListCtrl`.|
|[CHeaderCtrl::D eleteItem](#deleteitem)|Usuwa element z kontrolki nagłówka.|
|[CHeaderCtrl::D rawItem](#drawitem)|Rysuje określony element kontrolki nagłówka.|
|[CHeaderCtrl:: EditFilter](#editfilter)|Zaczyna edytować określony filtr kontrolki nagłówka.|
|[CHeaderCtrl:: GetBitmapMargin](#getbitmapmargin)|Pobiera szerokość marginesu mapy bitowej w kontrolce nagłówka.|
|[CHeaderCtrl:: GetFocusedItem](#getfocuseditem)|Pobiera identyfikator elementu w kontrolce bieżącego nagłówka, który ma fokus.|
|[CHeaderCtrl:: GetImageList](#getimagelist)|Pobiera uchwyt listy obrazów używany do rysowania elementów nagłówka w formancie nagłówka.|
|[CHeaderCtrl:: GetItem](#getitem)|Pobiera informacje o elemencie w kontrolce nagłówka.|
|[CHeaderCtrl:: GetItemCount](#getitemcount)|Pobiera liczbę elementów w kontrolce nagłówka.|
|[CHeaderCtrl:: GetItemDropDownRect](#getitemdropdownrect)|Pobiera informacje o prostokącie obwiedni dla określonego przycisku rozwijanego w kontrolce nagłówka.|
|[CHeaderCtrl:: GetItemRect](#getitemrect)|Pobiera prostokąt ograniczenia dla danego elementu w kontrolce nagłówka.|
|[CHeaderCtrl:: GetOrderArray](#getorderarray)|Pobiera kolejność elementów z lewej do prawej w kontrolce nagłówka.|
|[CHeaderCtrl:: GetOverflowRect](#getoverflowrect)|Pobiera prostokąt ograniczenia przycisku przepełnienia dla bieżącego formantu nagłówka.|
|[CHeaderCtrl:: HitTest](#hittest)|Określa, który element nagłówka (jeśli istnieje) znajduje się w określonym punkcie.|
|[CHeaderCtrl:: InsertItem](#insertitem)|Wstawia nowy element do kontrolki nagłówka.|
|[CHeaderCtrl:: layout](#layout)|Pobiera rozmiar i położenie kontrolki nagłówka w obrębie danego prostokąta.|
|[CHeaderCtrl:: OrderToIndex](#ordertoindex)|Pobiera wartość indeksu dla elementu na podstawie jego kolejności w formancie nagłówka.|
|[CHeaderCtrl:: SetBitmapMargin](#setbitmapmargin)|Ustawia szerokość marginesu mapy bitowej w kontrolce nagłówka.|
|[CHeaderCtrl:: SetFilterChangeTimeout](#setfilterchangetimeout)|Ustawia przedział czasu między czasem zmiany w atrybutach filtrów i księgowaniu powiadomienia `HDN_FILTERCHANGE`.|
|[CHeaderCtrl:: SetFocusedItem](#setfocuseditem)|Ustawia fokus na określony element nagłówka w bieżącym formancie nagłówka.|
|[CHeaderCtrl:: SetHotDivider](#sethotdivider)|Zmienia dzielnik między elementami nagłówka, aby wskazać ręczne przeciąganie i upuszczanie elementu nagłówka.|
|[CHeaderCtrl:: SetImageList](#setimagelist)|Przypisuje listę obrazów do kontrolki nagłówka.|
|[CHeaderCtrl:: SetItem](#setitem)|Ustawia atrybuty określonego elementu w kontrolce nagłówka.|
|[CHeaderCtrl:: SetOrderArray](#setorderarray)|Ustawia kolejność elementów w formancie nagłówka od lewej do prawej.|

## <a name="remarks"></a>Uwagi

Formant nagłówka jest oknem, które jest zwykle umieszczane powyżej zestawu kolumn tekstu lub cyfr. Zawiera tytuł dla każdej kolumny i może być podzielony na części. Użytkownik może przeciągnąć dzielniki oddzielające części, aby ustawić szerokość każdej kolumny. Ilustracja kontrolki nagłówka znajduje się w sekcji [kontrolki nagłówka](/windows/win32/Controls/header-controls).

Ta kontrolka (i w związku z tym Klasa `CHeaderCtrl`) jest dostępna tylko dla programów, które działają w systemach Windows 95/98 i Windows NT w wersji 3,51 lub nowszej.

Dodano funkcje dla systemu Windows 95/programu Internet Explorer 4,0:

- Niestandardowe porządkowanie elementu nagłówka.

- Element nagłówka — przeciąganie i upuszczanie, dla zmiany kolejności elementów nagłówka. Podczas tworzenia obiektu `CHeaderCtrl` Użyj stylu HDS_DRAGDROP.

- Tekst kolumny nagłówka jest stale wyświetlany podczas zmiany wielkości kolumny. Podczas tworzenia obiektu `CHeaderCtrl` Użyj stylu HDS_FULLDRAG.

- Śledzenie gorącą nagłówka, które podświetla element nagłówka, gdy wskaźnik myszy znajduje się nad nim. Podczas tworzenia obiektu `CHeaderCtrl` Użyj stylu HDS_HOTTRACK.

- Obsługa listy obrazów. Elementy nagłówka mogą zawierać obrazy przechowywane w obiekcie `CImageList` lub w tekście.

Aby uzyskać więcej informacji o korzystaniu z `CHeaderCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [Używanie CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="cheaderctrl"></a>CHeaderCtrl:: CHeaderCtrl

Konstruuje obiekt `CHeaderCtrl`.

```
CHeaderCtrl();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>CHeaderCtrl:: ClearAllFilters

Czyści wszystkie filtry dla kontrolki nagłówka.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje zachowanie komunikatu Win32 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter) z wartością kolumny-1, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>CHeaderCtrl:: ClearFilter

Czyści filtr dla kontrolki nagłówka.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Parametry

*nColumn*<br/>
Wartość kolumny wskazująca filtr, który ma zostać wyczyszczony.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje zachowanie [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)komunikatu Win32, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>CHeaderCtrl:: Create

Tworzy formant nagłówka i dołącza go do obiektu `CHeaderCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl kontrolki nagłówka. Aby uzyskać opis stylów kontrolki nagłówka, zobacz [Style kontrolki nagłówka](/windows/win32/Controls/header-control-styles) w Windows SDK.

*cinania*<br/>
Określa rozmiar i położenie kontrolki nagłówka. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) [lub struktura.](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki nagłówka, zazwyczaj `CDialog`. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki nagłówka.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Należy skonstruować obiekt `CHeaderCtrl` w dwóch krokach. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create`, który tworzy formant nagłówka i dołącza go do obiektu `CHeaderCtrl`.

Oprócz stylów kontrolki nagłówka, można użyć następujących standardowych stylów kontrolki, aby określić, jak pozycje i zmiany rozmiaru kontrolki nagłówka są zmieniane (zobacz [Style formantów wspólnych](/windows/win32/Controls/common-control-styles) , aby uzyskać więcej informacji):

- CCS_BOTTOM powoduje, że kontrolka w dolnej części obszaru klienckiego okna nadrzędnego jest ustawiana tak samo, jak szerokość okna nadrzędnego.

- CCS_NODIVIDER uniemożliwia narysowanie na górze formantu dwóch pikseli.

- CCS_NOMOVEY powoduje, że kontrolka zmienia rozmiar i przesunie się w poziomie, ale nie w pionie, w odpowiedzi na komunikat WM_SIZE. Jeśli styl CCS_NORESIZE jest używany, ten styl nie ma zastosowania. Kontrolki nagłówka mają domyślnie ten styl.

- CCS_NOPARENTALIGN uniemożliwia automatyczne przejście formantu do górnego lub dolnego okna nadrzędnego. Zamiast tego kontrolka zachowuje swoją pozycję w oknie nadrzędnym, pomimo zmiany rozmiaru okna nadrzędnego. Jeśli używany jest również styl CCS_TOP lub CCS_BOTTOM, wysokość jest dostosowywana do ustawienia domyślnego, ale pozycja i szerokość pozostaną bez zmian.

- CCS_NORESIZE zapobiega używaniu przez formant domyślnej szerokości i wysokości podczas ustawiania rozmiaru początkowego lub nowego rozmiaru. Zamiast tego kontrolka używa szerokości i wysokości określonej w żądaniu do utworzenia lub zmiany rozmiarów.

- CCS_TOP powoduje, że kontrolka poszerzy w górnej części obszaru klienckiego okna nadrzędnego i ustawia szerokość tak samo, jak szerokość okna nadrzędnego.

Możesz również zastosować następujące style okna do kontrolki nagłówka (zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) , aby uzyskać więcej informacji):

- WS_CHILD tworzy okno podrzędne. Nie można używać z stylem WS_POPUP.

- WS_VISIBLE tworzy okno, które jest początkowo widoczne.

- WS_DISABLED tworzy okno, które jest początkowo wyłączone.

- WS_GROUP Określa pierwszą kontrolkę grupy kontrolek, w której użytkownik może przechodzić z jednej kontrolki do następnej przy użyciu klawiszy strzałek. Wszystkie kontrolki zdefiniowane przy użyciu stylu WS_GROUP po pierwszej kontrolce należy do tej samej grupy. Następna kontrolka z stylem WS_GROUP spowoduje zakończenie grupy stylów i rozpoczęcie następnej grupy (oznacza to, że jedna grupa zostanie zakończona, gdy następny zaczyna).

- WS_TABSTOP określa jedną z dowolnych kontrolek, za pomocą których użytkownik może przechodzić przy użyciu klawisza TAB. Klawisz TAB przenosi użytkownika do następnej kontrolki określonej przez styl WS_TABSTOP.

Jeśli chcesz użyć rozszerzonych stylów systemu Windows z kontrolką, wywołaj [CreateEx](#createex) zamiast `Create`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>CHeaderCtrl:: CreateEx

Tworzy kontrolkę (okno podrzędne) i kojarzy ją z obiektem `CHeaderCtrl`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Określa rozszerzony styl formantu, który jest tworzony. Aby zapoznać się z listą rozszerzonych stylów systemu Windows, zobacz *dwExStyle* parametru [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w Windows SDK.

*dwStyle*<br/>
Styl kontrolki nagłówka. Aby uzyskać opis stylów kontrolki nagłówka, zobacz [Style kontrolki nagłówka](/windows/win32/Controls/header-control-styles) w Windows SDK. Aby uzyskać listę dodatkowych stylów, zobacz [Tworzenie](#create) .

*cinania*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator okna podrzędnego kontrolki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast `Create` do zastosowania rozszerzonych stylów systemu Windows, określonych przez **WS_EX_** wstępny stylu systemu Windows.

##  <a name="createdragimage"></a>CHeaderCtrl:: CreateDragImage

Tworzy przezroczystą wersję obrazu elementu w formancie nagłówka.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) elementu w kontrolce nagłówka. Obraz przypisany do tego elementu jest podstawą dla przezroczystego obrazu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [Korzystanie CImageList](../../mfc/reference/cimagelist-class.md) , jeśli się to powiedzie; w przeciwnym razie wartość NULL. Zwracana lista zawiera tylko jeden obraz.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)komunikatu Win32, zgodnie z opisem w Windows SDK. Jest dostarczany do obsługi przeciągania i upuszczania elementu nagłówka.

Obiekt `CImageList`, do którego punkty zwróconego wskaźnika jest obiektem tymczasowym i jest usuwany w następnym czasie bezczynności.

##  <a name="deleteitem"></a>CHeaderCtrl::D eleteItem

Usuwa element z kontrolki nagłówka.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Określa indeks (liczony od zera) elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>CHeaderCtrl::D rawItem

Wywoływane przez platformę, gdy wizualny aspekt kontrolki nagłówka rysowania przez właściciela zmienia się.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do struktury [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) opisujący element do narysowania.

### <a name="remarks"></a>Uwagi

`itemAction` element członkowski struktury `DRAWITEMSTRUCT` definiuje akcję rysowania, która ma zostać wykonana.

Domyślnie ta funkcja członkowska nic nie robi. Przesłoń tę funkcję elementu członkowskiego, aby zaimplementować rysowanie dla obiektu `CHeaderCtrl` rysowania przez właściciela.

Aplikacja powinna przywrócić wszystkie obiekty interfejsu GDI (Graphics Device Interface) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>CHeaderCtrl:: EditFilter

Rozpoczyna edytowanie określonego filtru kontrolki nagłówka.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Parametry

*nColumn*<br/>
Kolumna do edycji.

*bDiscardChanges*<br/>
Wartość, która określa, jak obsługiwać zmiany edytowane przez użytkownika, jeśli użytkownik jest w trakcie edytowania filtru podczas wysyłania komunikatu [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) .

Określ wartość TRUE, aby odrzucić zmiany wprowadzone przez użytkownika, lub wartość FAŁSZ, aby zaakceptować zmiany wprowadzone przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje zachowanie [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)komunikatu Win32, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>CHeaderCtrl:: GetBitmapMargin

Pobiera szerokość marginesu mapy bitowej w kontrolce nagłówka.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość marginesu mapy bitowej w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)komunikatu Win32, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>CHeaderCtrl:: GetFocusedItem

Pobiera indeks elementu, który ma fokus w bieżącym formancie nagłówka.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) elementu nagłówka, który ma fokus.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną `m_headerCtrl`, która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje metody `SetFocusedItem` i `GetFocusedItem`. W wcześniejszej części kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Można jednak przeciągnąć separator kolumn, aby kolumna była niewidoczna. Poniższy przykład ustawia, a następnie potwierdza ostatni nagłówek kolumny jako element fokusu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>CHeaderCtrl:: GetImageList

Pobiera uchwyt listy obrazów używany do rysowania elementów nagłówka w formancie nagłówka.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [Korzystanie CImageList](../../mfc/reference/cimagelist-class.md) .

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)komunikatu Win32, zgodnie z opisem w Windows SDK. Obiekt `CImageList`, do którego punkty zwróconego wskaźnika jest obiektem tymczasowym i jest usuwany w następnym czasie bezczynności.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>CHeaderCtrl:: GetItem

Pobiera informacje o elemencie kontrolki nagłówka.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Określa indeks (liczony od zera) elementu do pobrania.

*pHeaderItem*<br/>
Wskaźnik do struktury [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) , która otrzymuje nowy element. Ta struktura jest używana z `InsertItem` i `SetItem` funkcji Członkowskich. Wszystkie flagi ustawione w elemencie `mask` gwarantują, że wartości w odpowiednich elementach są prawidłowo wypełnione po powrocie. Jeśli element `mask` ma wartość zero, wartości w innych elementach struktury są bezużyteczne.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>CHeaderCtrl:: GetItemCount

Pobiera liczbę elementów w kontrolce nagłówka.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów kontrolnych nagłówka w przypadku powodzenia; w przeciwnym razie-1.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CHeaderCtrl::D eleteitem](#deleteitem).

##  <a name="getitemdropdownrect"></a>CHeaderCtrl:: GetItemDropDownRect

Pobiera prostokąt ograniczenia przycisku rozwijanego dla elementu nagłówka w bieżącym formancie nagłówka.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iItem*|podczas Indeks (liczony od zera) elementu nagłówka, którego styl jest HDF_SPLITBUTTON. Aby uzyskać więcej informacji, zobacz `fmt` składową struktury [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) .|
|*lpRect*|określoną Wskaźnik do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , aby otrzymać powiązane informacje o prostokącie.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta funkcja się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną `m_headerCtrl`, która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje metodę `GetItemDropDownRect`. W wcześniejszej części kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Poniższy przykład kodu rysuje prostokąt 3W wokół lokalizacji w pierwszej kolumnie zarezerwowanej dla przycisku listy rozwijanej nagłówek.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>CHeaderCtrl:: GetItemRect

Pobiera prostokąt ograniczenia dla danego elementu w kontrolce nagłówka.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) elementu formantu nagłówka.

*lpRect*<br/>
Wskaźnik do adresu struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , który odbiera powiązane informacje o prostokącie.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje zachowanie [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)komunikatu Win32, zgodnie z opisem w Windows SDK.

##  <a name="getorderarray"></a>CHeaderCtrl:: GetOrderArray

Pobiera kolejność elementów z lewej do prawej w kontrolce nagłówka.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Parametry

*piArray*<br/>
Wskaźnik do adresu bufora, który odbiera wartości indeksu elementów w formancie nagłówka, w kolejności, w jakiej są wyświetlane od lewej do prawej.

*iCount*<br/>
Liczba elementów kontrolki nagłówka. Musi być nieujemna.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)komunikatu Win32, zgodnie z opisem w Windows SDK. Jest on dostarczany z obsługą porządkowania elementów nagłówka.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>CHeaderCtrl:: GetOverflowRect

Pobiera prostokąt ograniczenia przycisku przepełnienia w bieżącym formancie nagłówka.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpRect*|określoną Wskaźnik do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , która otrzymuje powiązane informacje o prostokącie.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta funkcja się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli formant nagłówka zawiera więcej elementów niż można wyświetlić jednocześnie, kontrolka może wyświetlić przycisk przepełnienia, który jest przewijany do elementów, które nie są widoczne. Kontrolka nagłówka musi mieć style HDS_OVERFLOW i HDF_SPLITBUTTON, aby wyświetlić przycisk przepełnienie. Prostokąt ograniczający zawiera przycisk przepełnienie i istnieje tylko po wyświetleniu przycisku przepełnienia. Aby uzyskać więcej informacji, zobacz [Style kontrolki nagłówka](/windows/win32/Controls/header-control-styles).

Ta metoda wysyła komunikat [HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną `m_headerCtrl`, która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje metodę `GetOverflowRect`. W wcześniejszej części kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Można jednak przeciągnąć separator kolumn, aby kolumna była niewidoczna. Jeśli niektóre kolumny nie są widoczne, formant nagłówka rysuje przycisk przepełnienia. Poniższy przykład kodu rysuje prostokąt 3W wokół lokalizacji przycisku przepełnienia.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>CHeaderCtrl:: HitTest

Określa, który element nagłówka (jeśli istnieje) znajduje się w określonym punkcie.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*phdhti*|[in. out] Wskaźnik na strukturę [HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) , która określa punkt do testowania i odbiera wyniki testu.|

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) elementu nagłówka (jeśli istnieje) na określonej pozycji; w przeciwnym razie-1.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [HDM_HITTEST](/windows/win32/Controls/hdm-hittest) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną `m_headerCtrl`, która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje metodę `HitTest`. W poprzedniej sekcji tego przykładu kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Można jednak przeciągnąć separator kolumn, aby kolumna była niewidoczna. Ten przykład raportuje indeks kolumny, jeśli jest ona widoczna i-1, jeśli kolumna nie jest widoczna.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>CHeaderCtrl:: InsertItem

Wstawia nowy element do kontrolki nagłówka o określonym indeksie.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Indeks (liczony od zera) elementu, który ma zostać wstawiony. Jeśli wartość jest równa zero, element zostanie wstawiony na początku kontrolki nagłówka. Jeśli wartość jest większa niż wartość maksymalna, element zostanie wstawiony na końcu kontrolki nagłówek.

*phdi*<br/>
Wskaźnik na strukturę [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) , która zawiera informacje o elemencie, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Indeks nowego elementu, jeśli powodzenie; w przeciwnym razie-1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>CHeaderCtrl:: layout

Pobiera rozmiar i położenie kontrolki nagłówka w obrębie danego prostokąta.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Parametry

*pHeaderLayout*<br/>
Wskaźnik do struktury [HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-hdlayout) , która zawiera informacje używane do ustawiania rozmiaru i położenia kontrolki nagłówka.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do określania odpowiednich wymiarów dla nowej kontrolki nagłówka, która ma zajmować dany prostokąt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>CHeaderCtrl:: OrderToIndex

Pobiera wartość indeksu dla elementu na podstawie jego kolejności w formancie nagłówka.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Parametry

*nOrder*<br/>
Kolejność od zera, która jest wyświetlana w formancie nagłówka, od lewej do prawej.

### <a name="return-value"></a>Wartość zwracana

Indeks elementu na podstawie jego kolejności w formancie nagłówka. Indeks jest liczony od lewej do prawej, począwszy od 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)makr Win32, zgodnie z opisem w Windows SDK. Jest on dostarczany z obsługą porządkowania elementów nagłówka.

##  <a name="setbitmapmargin"></a>CHeaderCtrl:: SetBitmapMargin

Ustawia szerokość marginesu mapy bitowej w kontrolce nagłówka.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Szerokość (w pikselach) marginesu otaczającego mapę bitową w obrębie istniejącej kontrolki nagłówka.

### <a name="return-value"></a>Wartość zwracana

Szerokość marginesu mapy bitowej w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)komunikatu Win32, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>CHeaderCtrl:: SetFilterChangeTimeout

Ustawia przedział czasu między czasem zmiany w atrybutach filtrów i księgowaniu powiadomienia [HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange) .

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Wartość limitu czasu (w milisekundach).

### <a name="return-value"></a>Wartość zwracana

Indeks kontrolki filtru, która jest modyfikowana.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)komunikatu Win32, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>CHeaderCtrl:: SetFocusedItem

Ustawia fokus na określony element nagłówka w bieżącym formancie nagłówka.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iItem*|podczas Indeks elementu nagłówka liczony od zera.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną `m_headerCtrl`, która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje metody `SetFocusedItem` i `GetFocusedItem`. W wcześniejszej części kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Można jednak przeciągnąć separator kolumn, aby kolumna była niewidoczna. Poniższy przykład ustawia, a następnie potwierdza ostatni nagłówek kolumny jako element fokusu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>CHeaderCtrl:: SetHotDivider

Zmienia dzielnik między elementami nagłówka, aby wskazać ręczne przeciąganie i upuszczanie elementu nagłówka.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
Pozycja wskaźnika. Kontrolka nagłówka podświetla odpowiedni podział na podstawie położenia wskaźnika.

*nIndex*<br/>
Indeks wyróżnionego separatora.

### <a name="return-value"></a>Wartość zwracana

Indeks wyróżnionego separatora.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider)komunikatu Win32, zgodnie z opisem w Windows SDK. Jest dostarczany do obsługi przeciągania i upuszczania elementu nagłówka.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>CHeaderCtrl:: SetImageList

Przypisuje listę obrazów do kontrolki nagłówka.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Wskaźnik do obiektu `CImageList` zawierającego listę obrazów, która ma zostać przypisana do kontrolki nagłówka.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [Korzystanie CImageList](../../mfc/reference/cimagelist-class.md) , który został wcześniej przypisany do kontrolki nagłówka.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)komunikatu Win32, zgodnie z opisem w Windows SDK. Obiekt `CImageList`, do którego punkty zwróconego wskaźnika jest obiektem tymczasowym i jest usuwany w następnym czasie bezczynności.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CHeaderCtrl:: GetImageList](#getimagelist).

##  <a name="setitem"></a>CHeaderCtrl:: SetItem

Ustawia atrybuty określonego elementu w kontrolce nagłówka.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Indeks (liczony od zera) elementu do manipulowania.

*pHeaderItem*<br/>
Wskaźnik na strukturę [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) , która zawiera informacje o nowym elemencie.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CHeaderCtrl:: GetItem](#getitem).

##  <a name="setorderarray"></a>CHeaderCtrl:: SetOrderArray

Ustawia kolejność elementów w formancie nagłówka od lewej do prawej.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Parametry

*iCount*<br/>
Liczba elementów kontrolki nagłówka.

*piArray*<br/>
Wskaźnik do adresu bufora, który odbiera wartości indeksu elementów w formancie nagłówka, w kolejności, w jakiej są wyświetlane od lewej do prawej.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)makr Win32, zgodnie z opisem w Windows SDK. Jest on dostarczany z obsługą porządkowania elementów nagłówka.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CHeaderCtrl:: GetOrderArray](#getorderarray).

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CTabCtrl](../../mfc/reference/ctabctrl-class.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)<br/>
[Klasa CImageList](../../mfc/reference/cimagelist-class.md)
