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
ms.openlocfilehash: 6b5088526ad2c1f94fdc95ec3b84ab7cf64b59e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366855"
---
# <a name="cheaderctrl-class"></a>Klasa CHeaderCtrl

Udostępnia funkcje wspólnego nagłówka systemu Windows.

## <a name="syntax"></a>Składnia

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|Konstruuje `CHeaderCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Czyści wszystkie filtry dla formantu nagłówka.|
|[CHeaderCtrl::ClearFilter](#clearfilter)|Czyści filtr dla formantu nagłówka.|
|[CHeaderCtrl::Utwórz](#create)|Tworzy formant nagłówka i `CHeaderCtrl` dołącza go do obiektu.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Tworzy przezroczystą wersję obrazu elementu w formancie nagłówka.|
|[CHeaderCtrl::CreateEx](#createex)|Tworzy formant nagłówka z określonymi stylami rozszerzonymi systemu Windows i dołącza go do `CListCtrl` obiektu.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Usuwa element z kontrolki nagłówka.|
|[CHeaderCtrl::DrawItem](#drawitem)|Rysuje określony element formantu nagłówka.|
|[CHeaderCtrl::EditFilter](#editfilter)|Rozpoczyna edycję określonego filtru formantu nagłówka.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Pobiera szerokość marginesu mapy bitowej w formancie nagłówka.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Pobiera identyfikator elementu w bieżącym formancie nagłówka, który ma fokus.|
|[CHeaderCtrl::Lista GetImage](#getimagelist)|Pobiera uchwyt listy obrazów używanej do rysowania elementów nagłówka w formancie nagłówka.|
|[CHeaderCtrl::GetItem](#getitem)|Pobiera informacje o elemencie w formancie nagłówka.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Pobiera liczbę elementów w formancie nagłówka.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Pobiera informacje prostokąta ograniczającego dla określonego przycisku rozwijanego w formancie nagłówka.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Pobiera prostokąt ograniczający dla danego elementu w formancie nagłówka.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Pobiera kolejność od lewej do prawej elementów w formancie nagłówka.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Pobiera prostokąt ograniczający przycisk przepełnienia dla bieżącego formantu nagłówka.|
|[CHeaderCtrl::HitTest](#hittest)|Określa, który element nagłówka, jeśli istnieje, znajduje się w określonym punkcie.|
|[CHeaderCtrl::InsertItem](#insertitem)|Wstawia nowy element do formantu nagłówka.|
|[CHeaderCtrl::Układ](#layout)|Pobiera rozmiar i położenie formantu nagłówka w danym prostokącie.|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Pobiera wartość indeksu dla elementu na podstawie jego kolejności w formancie nagłówka.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Ustawia szerokość marginesu mapy bitowej w formancie nagłówka.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Ustawia limit czasu między czasem zmiany ma miejsce w atrybutach `HDN_FILTERCHANGE` filtru i księgowania powiadomienia.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Ustawia fokus na określony element nagłówka w bieżącym formancie nagłówka.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Zmienia separator między elementami nagłówka, aby wskazać ręczne przeciąganie i upuszczanie elementu nagłówka.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Przypisuje listę obrazów do formantu nagłówka.|
|[CHeaderCtrl::SetItem](#setitem)|Ustawia atrybuty określonego elementu w formancie nagłówka.|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Ustawia kolejność elementów od lewej do prawej w formancie nagłówka.|

## <a name="remarks"></a>Uwagi

Formant nagłówka jest oknem, które jest zwykle umieszczone nad zestawem kolumn tekstu lub liczb. Zawiera tytuł dla każdej kolumny i można go podzielić na części. Użytkownik może przeciągnąć przegrody oddzielane części, aby ustawić szerokość każdej kolumny. Aby uzyskać ilustrację formantu nagłówka, zobacz [Formanty nagłówka](/windows/win32/Controls/header-controls).

Ten formant (i `CHeaderCtrl` dlatego klasa) jest dostępny tylko dla programów, które działają w systemach Windows 95/98 i Windows NT w wersji 3.51 lub nowszej.

Funkcje dodane dla typowych formantów systemu Windows 95/Internet Explorer 4.0 obejmują następujące elementy:

- Kolejność niestandardowa elementu nagłówka.

- Przeciąganie i upuszczanie elementu nagłówka w celu ponownego upomnienia elementów nagłówka. Podczas tworzenia `CHeaderCtrl` obiektu należy użyć stylu HDS_DRAGDROP.

- Tekst kolumny nagłówka jest stale widoczny podczas zmiany rozmiaru kolumny. Podczas tworzenia `CHeaderCtrl` obiektu należy użyć stylu HDS_FULLDRAG.

- Śledzenie na gorąco nagłówka, które wyróżnia element nagłówka, gdy wskaźnik jest nad nim najeżdżający kursor. Podczas tworzenia `CHeaderCtrl` obiektu należy użyć stylu HDS_HOTTRACK.

- Obsługa listy obrazów. Elementy nagłówka mogą zawierać `CImageList` obrazy przechowywane w obiekcie lub tekście.

Aby uzyskać więcej `CHeaderCtrl`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="cheaderctrlcheaderctrl"></a><a name="cheaderctrl"></a>CHeaderCtrl::CHeaderCtrl

Konstruuje `CHeaderCtrl` obiekt.

```
CHeaderCtrl();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

## <a name="cheaderctrlclearallfilters"></a><a name="clearallfilters"></a>CHeaderCtrl::ClearAllFilters

Czyści wszystkie filtry dla formantu nagłówka.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje zachowanie komunikatu Win32 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter) o wartości kolumny -1, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

## <a name="cheaderctrlclearfilter"></a><a name="clearfilter"></a>CHeaderCtrl::ClearFilter

Czyści filtr dla formantu nagłówka.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Parametry

*nKolumn*<br/>
Wartość kolumny wskazująca, który filtr ma być czyszczący.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje zachowanie [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

## <a name="cheaderctrlcreate"></a><a name="create"></a>CHeaderCtrl::Utwórz

Tworzy formant nagłówka i `CHeaderCtrl` dołącza go do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl formantu nagłówka. Aby uzyskać opis stylów formantu nagłówka, zobacz [Style sterowania nagłówkami](/windows/win32/Controls/header-control-styles) w panelu Windows SDK.

*Rect*<br/>
Określa rozmiar i położenie formantu nagłówka. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT.](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Określa okno nadrzędne formantu nagłówka, zwykle `CDialog`. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu nagłówka.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Konstruowanie `CHeaderCtrl` obiektu w dwóch krokach. Najpierw wywołać konstruktora, a następnie wywołać `Create`, który `CHeaderCtrl` tworzy formant nagłówka i dołącza go do obiektu.

Oprócz stylów formantu nagłówka można użyć następujących typowych stylów sterowania, aby określić, w jaki sposób położenie formantu nagłówka i jego rozmiar zmienia rozmiar (więcej informacji można znaleźć w [typowych stylach sterowania):](/windows/win32/Controls/common-control-styles)

- CCS_BOTTOM Powoduje, że formant pozycjonuje się w dolnej części obszaru klienta okna nadrzędnego i ustawia szerokość tak samo jak szerokość okna nadrzędnego.

- CCS_NODIVIDER Zapobiega rysowaniu podświetlenia dwupikselowego u góry formantu.

- CCS_NOMOVEY Powoduje, że formant, aby zmienić rozmiar i przenieść się w poziomie, ale nie w pionie, w odpowiedzi na komunikat WM_SIZE. Jeśli używany jest styl CCS_NORESIZE, ten styl nie ma zastosowania. Kontrolki nagłówka mają domyślnie ten styl.

- CCS_NOPARENTALIGN Zapobiega automatycznemu przesuwaniu formantu na górę lub u dołu okna nadrzędnego. Zamiast tego formant zachowuje swoje położenie w oknie nadrzędnym pomimo zmian w rozmiarze okna nadrzędnego. Jeśli używany jest również styl CCS_TOP lub CCS_BOTTOM, wysokość jest dopasowywana do wartości domyślnej, ale położenie i szerokość pozostają niezmienione.

- CCS_NORESIZE Zapobiega używaniu domyślnej szerokości i wysokości formantu podczas ustawiania jego początkowego rozmiaru lub nowego rozmiaru. Zamiast tego formant używa szerokości i wysokości określone w żądaniu tworzenia lub zmiany rozmiaru.

- CCS_TOP Powoduje, że formant pozycjonuje się w górnej części obszaru klienta okna nadrzędnego i ustawia szerokość tak samo jak szerokość okna nadrzędnego.

Do formantu nagłówka można również zastosować następujące style okien (więcej informacji można znaleźć w [stylach okien):](../../mfc/reference/styles-used-by-mfc.md#window-styles)

- WS_CHILD Tworzy okno podrzędne. Nie można używać ze stylem WS_POPUP.

- WS_VISIBLE Tworzy okno, które jest początkowo widoczne.

- WS_DISABLED Tworzy okno, które jest początkowo wyłączone.

- WS_GROUP Określa pierwszy formant grupy formantów, w którym użytkownik może przechodzić z jednego formantu do następnego za pomocą klawiszy strzałek. Wszystkie formanty zdefiniowane za pomocą stylu WS_GROUP po pierwszym formancie należą do tej samej grupy. Następny formant ze stylem WS_GROUP kończy grupę stylów i rozpoczyna następną grupę (oznacza to, że jedna grupa kończy się w miejscu rozpoczęcia następnego).

- WS_TABSTOP Określa jedną z wielu formantów, za pomocą których użytkownik może się poruszać za pomocą klawisza TAB. Klawisz TAB przenosi użytkownika do następnego formantu określonego przez styl WS_TABSTOP.

Jeśli chcesz używać rozszerzonych stylów okien z formantem, zadzwoń [do CreateEx](#createex) zamiast `Create`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

## <a name="cheaderctrlcreateex"></a><a name="createex"></a>CHeaderCtrl::CreateEx

Tworzy formant (okno podrzędne) i `CHeaderCtrl` skojarzyć go z obiektem.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwexstyle*<br/>
Określa rozszerzony styl tworzonego formantu. Aby uzyskać listę rozszerzonych stylów systemu Windows, zobacz parametr *dwExStyle* dla [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) w zestawie Windows SDK.

*Dwstyle*<br/>
Styl formantu nagłówka. Aby uzyskać opis stylów formantu nagłówka, zobacz [Style sterowania nagłówkami](/windows/win32/Controls/header-control-styles) w panelu Windows SDK. Zobacz [Tworzenie](#create) listy dodatkowych stylów.

*Rect*<br/>
Odwołanie do struktury [RECT](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest nadrzędnym formantu.

*Nid*<br/>
Identyfikator okna podrzędnego formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zamiast stosować rozszerzone style systemu Windows określone przez przedmową w stylu rozszerzonym systemu Windows WS_EX_ . **WS_EX_** `CreateEx` `Create`

## <a name="cheaderctrlcreatedragimage"></a><a name="createdragimage"></a>CHeaderCtrl::CreateDragImage

Tworzy przezroczystą wersję obrazu elementu w formancie nagłówka.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera elementu w formancie nagłówka. Obraz przypisany do tego elementu jest podstawą przezroczystego obrazu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CImageList,](../../mfc/reference/cimagelist-class.md) jeśli zakończy się pomyślnie; w przeciwnym razie NULL. Zwrócona lista zawiera tylko jeden obraz.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)komunikatu Win32, zgodnie z opisem w windows SDK. Jest on dostarczany do obsługi przeciągnij i upuść element nagłówka.

Obiekt, `CImageList` do którego zwracane punkty wskaźnika jest obiekt tymczasowy i jest usuwany w następnym przetwarzaniu w czasie bezczynnym.

## <a name="cheaderctrldeleteitem"></a><a name="deleteitem"></a>CHeaderCtrl::DeleteItem

Usuwa element z kontrolki nagłówka.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Określa indeks od zera elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

## <a name="cheaderctrldrawitem"></a><a name="drawitem"></a>CHeaderCtrl::DrawItem

Wywoływane przez strukturę, gdy zmienia się wizualny aspekt formantu nagłówka rysowania właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) struktury opisujące element, który ma być malowany.

### <a name="remarks"></a>Uwagi

Element `itemAction` członkowski `DRAWITEMSTRUCT` konstrukcji definiuje akcję rysowania, która ma być wykonana.

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpokaj tę funkcję elementu członkowskiego, aby zaimplementować rysunek dla obiektu rysowania `CHeaderCtrl` właściciela.

Aplikacja powinna przywrócić wszystkie obiekty interfejsu urządzenia graficznego (GDI) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

## <a name="cheaderctrleditfilter"></a><a name="editfilter"></a>CHeaderCtrl::EditFilter

Rozpoczyna edytowanie określonego filtru formantu nagłówka.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Parametry

*nKolumn*<br/>
Kolumna do edycji.

*bPrzemysłek karty*<br/>
Wartość określająca sposób obsługi zmian edycji użytkownika, jeśli użytkownik jest w trakcie edytowania filtru podczas wysyłania [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) wiadomości.

Określ wartość TRUE, aby odrzucić zmiany wprowadzone przez użytkownika, lub FALSE, aby zaakceptować zmiany wprowadzone przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje zachowanie [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

## <a name="cheaderctrlgetbitmapmargin"></a><a name="getbitmapmargin"></a>CHeaderCtrl::GetBitmapMargin

Pobiera szerokość marginesu mapy bitowej w formancie nagłówka.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość marginesu mapy bitowej w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

## <a name="cheaderctrlgetfocuseditem"></a><a name="getfocuseditem"></a>CHeaderCtrl::GetFocusedItem

Pobiera indeks elementu, który ma fokus w bieżącym formancie nagłówka.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks od zera elementu nagłówka, który ma fokus.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [HDM_GETFOCUSEDITEM,](/windows/win32/Controls/hdm-getfocuseditem) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_headerCtrl`zmienną , która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu `SetFocusedItem` pokazuje `GetFocusedItem` i metody. We wcześniejszej sekcji kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Można jednak przeciągnąć separator kolumn, aby kolumna nie była widoczna. Poniższy przykład ustawia, a następnie potwierdza nagłówek ostatniej kolumny jako element fokusu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlgetimagelist"></a><a name="getimagelist"></a>CHeaderCtrl::Lista GetImage

Pobiera uchwyt listy obrazów używanej do rysowania elementów nagłówka w formancie nagłówka.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CImageList.](../../mfc/reference/cimagelist-class.md)

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)komunikatu Win32, zgodnie z opisem w windows SDK. Obiekt, `CImageList` do którego zwracane punkty wskaźnika jest obiekt tymczasowy i jest usuwany w następnym przetwarzaniu w czasie bezczynnym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

## <a name="cheaderctrlgetitem"></a><a name="getitem"></a>CHeaderCtrl::GetItem

Pobiera informacje o elemencie formantu nagłówka.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Określa indeks od zera elementu do pobrania.

*pHeaderItem (Głowa)*<br/>
Wskaźnik do struktury [HDITEM,](/windows/win32/api/commctrl/ns-commctrl-hditemw) która odbiera nowy element. Ta struktura jest `InsertItem` używana `SetItem` z funkcjami i elementami członkowskimi. Wszystkie flagi ustawione `mask` w elemencie upewnij się, że wartości w odpowiednich elementach są prawidłowo wypełnione po powrocie. Jeśli `mask` element jest ustawiony na zero, wartości w innych elementach struktury są bez znaczenia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

## <a name="cheaderctrlgetitemcount"></a><a name="getitemcount"></a>CHeaderCtrl::GetItemCount

Pobiera liczbę elementów w formancie nagłówka.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów kontroli nagłówka w przypadku pomyślnego; w przeciwnym razie - 1.

### <a name="example"></a>Przykład

  Zobacz przykład [CHeaderCtrl::DeleteItem](#deleteitem).

## <a name="cheaderctrlgetitemdropdownrect"></a><a name="getitemdropdownrect"></a>CHeaderCtrl::GetItemDropDownRect

Pobiera prostokąt ograniczający przycisku rozwijanego dla elementu nagłówka w bieżącym formancie nagłówka.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Iitem*|[w] Indeks od zera elementu nagłówka, którego styl jest HDF_SPLITBUTTON. Aby uzyskać więcej `fmt` informacji, zobacz element struktury [HDITEM.](/windows/win32/api/commctrl/ns-commctrl-hditemw)|
|*Lprect*|[na zewnątrz] Wskaźnik do struktury [RECT,](/previous-versions/dd162897\(v=vs.85\)) aby otrzymać informacje o prostokątze ograniczającym.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta funkcja zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [HDM_GETITEMDROPDOWNRECT,](/windows/win32/Controls/hdm-getitemdropdownrect) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_headerCtrl`zmienną , która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu `GetItemDropDownRect` pokazuje metodę. We wcześniejszej sekcji kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Poniższy przykład kodu rysuje prostokąt 3D wokół lokalizacji w pierwszej kolumnie, która jest zarezerwowana dla przycisku listy rozwijanej nagłówka.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

## <a name="cheaderctrlgetitemrect"></a><a name="getitemrect"></a>CHeaderCtrl::GetItemRect

Pobiera prostokąt ograniczający dla danego elementu w formancie nagłówka.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera elementu formantu nagłówka.

*Lprect*<br/>
Wskaźnik do adresu struktury [RECT,](/previous-versions/dd162897\(v=vs.85\)) która odbiera informacje o prostokątze ograniczającym.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda implementuje zachowanie [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="cheaderctrlgetorderarray"></a><a name="getorderarray"></a>CHeaderCtrl::GetOrderArray

Pobiera kolejność od lewej do prawej elementów w formancie nagłówka.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Parametry

*PiArray (PiArray)*<br/>
Wskaźnik do adresu buforu, który odbiera wartości indeksu elementów w formancie nagłówka, w kolejności, w jakiej pojawiają się od lewej do prawej.

*Konto iCount*<br/>
Liczba elementów kontroli nagłówka. Musi być nieujemna.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)komunikatu Win32, zgodnie z opisem w windows SDK. Jest on dostarczany do obsługi zamawiania elementu nagłówka.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

## <a name="cheaderctrlgetoverflowrect"></a><a name="getoverflowrect"></a>CHeaderCtrl::GetOverflowRect

Pobiera prostokąt ograniczający przycisk przepełnienia bieżącego formantu nagłówka.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Lprect*|[na zewnątrz] Wskaźnik do struktury [RECT,](/previous-versions/dd162897\(v=vs.85\)) która odbiera informacje o prostokątze ograniczającym.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta funkcja zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli kontrolka nagłówka zawiera więcej elementów niż można jednocześnie wyświetlać, formant może wyświetlać przycisk przepełnienia, który przewija się do elementów, które nie są widoczne. Kontrolka nagłówka musi mieć style HDS_OVERFLOW i HDF_SPLITBUTTON, aby wyświetlić przycisk przepełnienia. Prostokąt ograniczający otacza przycisk przepełnienia i istnieje tylko wtedy, gdy wyświetlany jest przycisk przepełnienia. Aby uzyskać więcej informacji, zobacz [Style sterowania nagłówkiem](/windows/win32/Controls/header-control-styles).

Ta metoda wysyła komunikat [HDM_GETOVERFLOWRECT,](/windows/win32/Controls/hdm-getoverflowrect) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_headerCtrl`zmienną , która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu `GetOverflowRect` pokazuje metodę. We wcześniejszej sekcji kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Można jednak przeciągnąć separator kolumn, aby kolumna nie była widoczna. Jeśli niektóre kolumny nie są widoczne, formant nagłówka rysuje przycisk przepełnienia. Poniższy przykład kodu rysuje prostokąt 3D wokół lokalizacji przycisku przepełnienia.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

## <a name="cheaderctrlhittest"></a><a name="hittest"></a>CHeaderCtrl::HitTest

Określa, który element nagłówka, jeśli istnieje, znajduje się w określonym punkcie.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*phdhti*|[w, na zewnątrz] Wskaźnik do struktury [HDHITTESTINFO,](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) który określa punkt do testowania i odbiera wyniki testu.|

### <a name="return-value"></a>Wartość zwracana

Indeks od zera elementu nagłówka, jeśli istnieje, w określonej pozycji; w przeciwnym razie -1.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [komunikat HDM_HITTEST,](/windows/win32/Controls/hdm-hittest) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_headerCtrl`zmienną , która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu `HitTest` pokazuje metodę. We wcześniejszej sekcji tego przykładu kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Można jednak przeciągnąć separator kolumn, aby kolumna nie była widoczna. W tym przykładzie raportuje indeks kolumny, jeśli jest widoczny, i -1, jeśli kolumna nie jest widoczna.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

## <a name="cheaderctrlinsertitem"></a><a name="insertitem"></a>CHeaderCtrl::InsertItem

Wstawia nowy element do formantu nagłówka w określonym indeksie.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Indeks od zera elementu, który ma zostać wstawiony. Jeśli wartość wynosi zero, element jest wstawiany na początku formantu nagłówka. Jeśli wartość jest większa niż wartość maksymalna, element jest wstawiany na końcu formantu nagłówka.

*phdi*<br/>
Wskaźnik do struktury [HDITEM,](/windows/win32/api/commctrl/ns-commctrl-hditemw) który zawiera informacje o elemencie, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Indeks nowego elementu, jeśli zakończy się pomyślnie; w przeciwnym razie - 1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

## <a name="cheaderctrllayout"></a><a name="layout"></a>CHeaderCtrl::Układ

Pobiera rozmiar i położenie formantu nagłówka w danym prostokącie.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Parametry

*pPołowianie*<br/>
Wskaźnik do struktury [HDLAYOUT,](/windows/win32/api/commctrl/ns-commctrl-hdlayout) która zawiera informacje używane do ustawiania rozmiaru i położenia formantu nagłówka.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do określania odpowiednich wymiarów dla nowego formantu nagłówka, który ma zajmować dany prostokąt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

## <a name="cheaderctrlordertoindex"></a><a name="ordertoindex"></a>CHeaderCtrl::OrderToIndex

Pobiera wartość indeksu dla elementu na podstawie jego kolejności w formancie nagłówka.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Parametry

*nOrder*<br/>
Kolejność oparta na wartości zero, która pojawia się element w formancie nagłówka, od lewej do prawej.

### <a name="return-value"></a>Wartość zwracana

Indeks elementu, na podstawie jego kolejności w formancie nagłówka. Indeks liczy się od lewej do prawej, zaczynając od 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)makra Win32, zgodnie z opisem w windows SDK. Jest on dostarczany do obsługi zamawiania elementu nagłówka.

## <a name="cheaderctrlsetbitmapmargin"></a><a name="setbitmapmargin"></a>CHeaderCtrl::SetBitmapMargin

Ustawia szerokość marginesu mapy bitowej w formancie nagłówka.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Parametry

*nWidth (ww.*<br/>
Szerokość, określona w pikselach, marginesu otaczającego mapę bitową w istniejącym formancie nagłówka.

### <a name="return-value"></a>Wartość zwracana

Szerokość marginesu mapy bitowej w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

## <a name="cheaderctrlsetfilterchangetimeout"></a><a name="setfilterchangetimeout"></a>CHeaderCtrl::SetFilterChangeTimeout

Ustawia limit czasu między czasem zmiany ma miejsce w atrybutach filtru i księgowania [powiadomienia HDN_FILTERCHANGE.](/windows/win32/Controls/hdn-filterchange)

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Parametry

*dwTimeOut (Np.*<br/>
Wartość limitu czasu w milisekundach.

### <a name="return-value"></a>Wartość zwracana

Indeks formantu filtru jest modyfikowany.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

## <a name="cheaderctrlsetfocuseditem"></a><a name="setfocuseditem"></a>CHeaderCtrl::SetFocusedItem

Ustawia fokus na określony element nagłówka w bieżącym formancie nagłówka.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Iitem*|[w] Indeks od zera elementu nagłówka.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [HDM_SETFOCUSEDITEM,](/windows/win32/Controls/hdm-setfocuseditem) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_headerCtrl`zmienną , która jest używana do uzyskiwania dostępu do bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu `SetFocusedItem` pokazuje `GetFocusedItem` i metody. We wcześniejszej sekcji kodu utworzyliśmy kontrolkę nagłówka z pięcioma kolumnami. Można jednak przeciągnąć separator kolumn, aby kolumna nie była widoczna. Poniższy przykład ustawia, a następnie potwierdza nagłówek ostatniej kolumny jako element fokusu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlsethotdivider"></a><a name="sethotdivider"></a>CHeaderCtrl::SetHotDivider

Zmienia separator między elementami nagłówka, aby wskazać ręczne przeciąganie i upuszczanie elementu nagłówka.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Położenie wskaźnika. Formant nagłówka wyróżnia odpowiedni dzielnik na podstawie położenia wskaźnika.

*Nindex*<br/>
Indeks podświetlony dzielnik.

### <a name="return-value"></a>Wartość zwracana

Indeks podświetlony dzielnik.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider)komunikatu Win32, zgodnie z opisem w windows SDK. Jest on dostarczany do obsługi przeciągnij i upuść element nagłówka.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

## <a name="cheaderctrlsetimagelist"></a><a name="setimagelist"></a>CHeaderCtrl::SetImageList

Przypisuje listę obrazów do formantu nagłówka.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList (Lista pImage)*<br/>
Wskaźnik do `CImageList` obiektu zawierającego listę obrazów, który ma być przypisany do formantu nagłówka.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CImageList](../../mfc/reference/cimagelist-class.md) wcześniej przypisany do formantu nagłówka.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)komunikatu Win32, zgodnie z opisem w windows SDK. Obiekt, `CImageList` do którego zwracane punkty wskaźnika jest obiekt tymczasowy i jest usuwany w następnym przetwarzaniu w czasie bezczynnym.

### <a name="example"></a>Przykład

  Zobacz przykład [CHeaderCtrl::GetImageList](#getimagelist).

## <a name="cheaderctrlsetitem"></a><a name="setitem"></a>CHeaderCtrl::SetItem

Ustawia atrybuty określonego elementu w formancie nagłówka.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Indeks od zera elementu do manipulowania.

*pHeaderItem (Głowa)*<br/>
Wskaźnik do struktury [HDITEM,](/windows/win32/api/commctrl/ns-commctrl-hditemw) która zawiera informacje o nowym elemencie.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CHeaderCtrl::GetItem](#getitem).

## <a name="cheaderctrlsetorderarray"></a><a name="setorderarray"></a>CHeaderCtrl::SetOrderArray

Ustawia kolejność elementów od lewej do prawej w formancie nagłówka.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Parametry

*Konto iCount*<br/>
Liczba elementów kontroli nagłówka.

*PiArray (PiArray)*<br/>
Wskaźnik do adresu buforu, który odbiera wartości indeksu elementów w formancie nagłówka, w kolejności, w jakiej pojawiają się od lewej do prawej.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)makra Win32, zgodnie z opisem w windows SDK. Jest on dostarczany do obsługi zamawiania elementu nagłówka.

### <a name="example"></a>Przykład

  Zobacz przykład [CHeaderCtrl::GetOrderArray](#getorderarray).

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CTabCtrl](../../mfc/reference/ctabctrl-class.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)<br/>
[Klasa CImageList](../../mfc/reference/cimagelist-class.md)
