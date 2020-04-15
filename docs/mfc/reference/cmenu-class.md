---
title: Klasa CMenu
ms.date: 11/04/2016
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
ms.openlocfilehash: 5ec97d8cf039034078f29b38fb6a41d6ff9a5e53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369981"
---
# <a name="cmenu-class"></a>Klasa CMenu

Hermetyzacja systemu `HMENU`Windows .

## <a name="syntax"></a>Składnia

```
class CMenu : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMenu::CMenu](#cmenu)|Konstruuje `CMenu` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMenu::Dołączmenu](#appendmenu)|Dołącza nowy element na końcu tego menu.|
|[CMenu::Dołącz](#attach)|Dołącza uchwyt menu systemu `CMenu` Windows do obiektu.|
|[CMenu::CheckMenuItem](#checkmenuitem)|Umieszcza znacznik wyboru obok lub usuwa znacznik wyboru z elementu menu w wyskakującym menu.|
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Umieszcza przycisk opcji obok elementu menu i usuwa przycisk opcji ze wszystkich pozostałych elementów menu w grupie.|
|[CMenu::CreateMenu](#createmenu)|Tworzy puste menu i dołącza `CMenu` je do obiektu.|
|[CMenu::CreatePopupMenu](#createpopupmenu)|Tworzy puste menu podręczne i dołącza `CMenu` je do obiektu.|
|[CMenu::DeleteMenu](#deletemenu)|Usuwa określony element z menu. Jeśli element menu ma skojarzone menu podręczne, niszczy uchwyt do menu podręcznego i zwalnia pamięć używaną przez niego.|
|[CMenu::DeleteTempMap](#deletetempmap)|Usuwa wszystkie `CMenu` obiekty tymczasowe `FromHandle` utworzone przez funkcję elementu członkowskiego.|
|[CMenu::DestroyMenu](#destroymenu)|Niszczy menu dołączone do `CMenu` obiektu i zwalnia każdą pamięć, którą zajmowało menu.|
|[CMenu::Detach](#detach)|Odłącza uchwyt menu systemu `CMenu` Windows od obiektu i zwraca uchwyt.|
|[CMenu::DrawItem](#drawitem)|Wywoływane przez strukturę, gdy zmienia się wizualny aspekt menu rysowanego przez właściciela.|
|[CMenu::EnableMenuItem](#enablemenuitem)|Włącza, wyłącza lub przyciemnia (szarości) element menu.|
|[CMenu::OdHandle](#fromhandle)|Zwraca wskaźnik do `CMenu` obiektu, do który ma dojść do menu systemu Windows.|
|[CMenu::GetDefaultItem](#getdefaultitem)|Określa domyślny element menu w określonym menu.|
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Pobiera identyfikator kontekstu pomocy skojarzony z menu.|
|[CMenu::GetMenuInfo](#getmenuinfo)|Pobiera informacje o określonym menu.|
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Określa liczbę elementów w menu podręcznym lub menu najwyższego poziomu.|
|[CMenu::GetMenuItemID](#getmenuitemid)|Uzyskuje identyfikator elementu menu dla elementu menu znajdującego się w określonym położeniu.|
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Pobiera informacje o elemencie menu.|
|[CMenu::GetMenuState](#getmenustate)|Zwraca stan określonego elementu menu lub liczbę elementów w menu podręcznym.|
|[CMenu::Pobierz pobierz](#getmenustring)|Pobiera etykietę określonego elementu menu.|
|[CMenu::GetSafeHmenu](#getsafehmenu)|Zwraca `m_hMenu` zawinięte `CMenu` przez ten obiekt.|
|[CMenu::GetSubMenu](#getsubmenu)|Pobiera wskaźnik do wyskakującego menu.|
|[CMenu::InsertMenu](#insertmenu)|Wstawia nowy element menu w określonym położeniu, przesuwając inne elementy w dół menu.|
|[CMenu::InsertMenuItem](#insertmenuitem)|Wstawia nowy element menu w określonym położeniu w menu.|
|[CMenu::LoadMenu](#loadmenu)|Ładuje zasób menu z pliku wykonywalnego i dołącza go do `CMenu` obiektu.|
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Ładuje menu z szablonu menu w pamięci `CMenu` i dołącza go do obiektu.|
|[CMenu::MeasureItem](#measureitem)|Wywoływana przez strukturę do określania wymiarów menu podczas tworzenia menu rysowanego przez właściciela.|
|[CMenu::ModifyMenu](#modifymenu)|Zmienia istniejący element menu w określonym położeniu.|
|[CMenu::Usuńmenu](#removemenu)|Usuwa element menu ze skojarzonym menu podręcznym z określonego menu.|
|[CMenu::SetDefaultItem](#setdefaultitem)|Ustawia domyślny element menu dla określonego menu.|
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Ustawia identyfikator kontekstu pomocy, który ma być skojarzony z menu.|
|[CMenu::SetMenuInfo](#setmenuinfo)|Ustawia informacje w określonym menu.|
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Kojarzy określone mapy bitowe znacznika wyboru z elementem menu.|
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Zmienia informacje o elemencie menu.|
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Wyświetla pływające menu podręczne w określonej lokalizacji i śledzi wybór elementów w wyskakującym menu.|
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Wyświetla pływające menu podręczne w określonej lokalizacji i śledzi wybór elementów w wyskakującym menu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMenu::operator HMENU](#operator_hmenu)|Pobiera uchwyt obiektu menu.|
|[CMenu::operator !=](#operator_neq)|Określa, czy dwa obiekty menu nie są równe.|
|[CMenu::operator ==](#operator_eq_eq)|Określa, czy dwa obiekty menu są równe.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMenu::m_hMenu](#m_hmenu)|Określa uchwyt do menu systemu Windows `CMenu` dołączonego do obiektu.|

## <a name="remarks"></a>Uwagi

Zapewnia funkcje członkowskie do tworzenia, śledzenia, aktualizowania i niszczenia menu.

Utwórz `CMenu` obiekt w ramce stosu `CMenu`jako lokalny, a następnie wywołaj funkcje członkowskie , aby w razie potrzeby manipulować nowym menu. Następnie wywołaj [CWnd::SetMenu,](../../mfc/reference/cwnd-class.md#setmenu) aby ustawić menu na okno, `CMenu` a następnie natychmiast wywołanie funkcji elementu członkowskiego [Odłączenia](#detach) obiektu. Funkcja `CWnd::SetMenu` elementu członkowskiego ustawia menu okna na nowe menu, powoduje, że okno ma zostać ponownie narysowane, aby odzwierciedlić zmianę menu, a także przekazuje własność menu do okna. Wywołanie `Detach` odłącza HMENU od `CMenu` obiektu, tak aby `CMenu` gdy zmienna lokalna przechodzi poza zakres, destruktor `CMenu` obiektu nie próbuje zniszczyć menu, które nie jest już właścicielem. Samo menu jest automatycznie niszczone po zniszczeniu okna.

Za pomocą funkcji elementu członkowskiego [LoadMenuIndirect](#loadmenuindirect) można utworzyć menu z szablonu w pamięci, ale menu utworzone z zasobu przez [wywołanie LoadMenu](#loadmenu) jest łatwiej obsługiwane, a sam zasób menu może być tworzony i modyfikowany przez edytor menu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cmenuappendmenu"></a><a name="appendmenu"></a>CMenu::Dołączmenu

Dołącza nowy element na końcu menu.

```
BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Parametry

*nPłgi*<br/>
Określa informacje o stanie nowego elementu menu po dodaniu go do menu. Składa się z jednej lub więcej wartości wymienionych w sekcji Uwagi.

*nIDNewItem*<br/>
Określa identyfikator polecenia nowego elementu menu lub, jeśli *nFlags* jest ustawiony na MF_POPUP, uchwyt `HMENU`menu ( ) wyskakującego menu. Parametr *nIDNewItem* jest ignorowany (nie jest potrzebny), jeśli *nFlags* jest ustawiony na MF_SEPARATOR.

*lpszNewItem*<br/>
Określa zawartość nowego elementu menu. Parametr *nFlags* jest używany do interpretowania *lpszNewItem* w następujący sposób:

|nPłgi|Interpretacja lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Zawiera 32-bitową wartość dostarczoną przez aplikację, której aplikacja może używać do obsługi dodatkowych danych skojarzonych z elementem menu. Ta wartość 32-bitowa jest dostępna dla aplikacji podczas przetwarzania WM_MEASUREITEM i WM_DRAWITEM komunikatów. Wartość jest przechowywana `itemData` w elementów członkowskich struktury dostarczone z tymi komunikatami.|
|MF_STRING|Zawiera wskaźnik do ciągu zakończonego wartością null. Jest to domyślna interpretacja.|
|MF_SEPARATOR|Parametr *lpszNewItem* jest ignorowany (nie jest potrzebny).|

*pBmp (wł.)*<br/>
Wskazuje `CBitmap` obiekt, który będzie używany jako element menu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja może określić stan elementu menu, ustawiając wartości w *nFlags*. Gdy *nIDNewItem* określa menu podręczne, staje się częścią menu, do którego jest dołączone. Jeśli to menu zostanie zniszczone, dołączone menu również zostanie zniszczone. Dołączone menu powinno być odłączone od obiektu, `CMenu` aby uniknąć konfliktu. Należy zauważyć, że MF_STRING i MF_OWNERDRAW nie są prawidłowe `AppendMenu`dla wersji bitmapy programu .

Na poniższej liście opisano flagi, które mogą być ustawione w *nFlags:*

- MF_CHECKED Działa jako przełącznik z MF_UNCHECKED, aby umieścić domyślny znacznik wyboru obok elementu. Gdy aplikacja dostarcza znacznika bitowego (patrz funkcja elementu członkowskiego [SetMenuItemBitmaps),](#setmenuitembitmaps) wyświetlana jest mapa bitowa "check mark on".

- MF_UNCHECKED Działa jako przełącznik z MF_CHECKED, aby usunąć znacznik wyboru obok elementu. Gdy aplikacja dostarcza mapy bitowe znacznika `SetMenuItemBitmaps` wyboru (patrz funkcja elementu członkowskiego), wyświetlana jest mapa bitowa "check mark off".

- MF_DISABLED Wyłącza element menu, tak aby nie można go było zaznaczyć, ale nie przyciemniał go.

- MF_ENABLED Włącza element menu, dzięki czemu można go wybrać i przywraca go ze stanu wygaszonego.

- MF_GRAYED Wyłącza element menu, tak aby nie można go było wybrać i przyciemniał go.

- MF_MENUBARBREAK Umieszcza element w nowym wierszu w menu statycznym lub w nowej kolumnie w menu podręcznych. Nowa kolumna menu podręcznego zostanie oddzielona od starej kolumny pionową linią podziału.

- MF_MENUBREAK Umieszcza element w nowym wierszu w menu statycznym lub w nowej kolumnie w menu podręcznych. Między kolumnami nie jest umieszczona żadna linia podziału.

- MF_OWNERDRAW Określa, że element jest elementem rysowania przez właściciela. Gdy menu jest wyświetlane po raz pierwszy, okno, które jest właścicielem menu odbiera komunikat WM_MEASUREITEM, który pobiera wysokość i szerokość elementu menu. Komunikat WM_DRAWITEM jest wysyłany za każdym razem, gdy właściciel musi zaktualizować wygląd elementu menu. Ta opcja jest nieprawidłowa dla elementu menu najwyższego poziomu.

- MF_POPUP Określa, że element menu ma skojarzone z nim menu podręczne. Parametr ID określa dojście do menu podręcznego, które ma być skojarzone z elementem. Służy do dodawania menu podręcznego najwyższego poziomu lub hierarchicznego menu podręcznego do wyskakującego elementu menu.

- MF_SEPARATOR Rysuje poziomą linię podziału. Może być używany tylko w wyskakującym menu. Nie można wygaszać, wyłączyć ani wyróżnić tej linii. Inne parametry są ignorowane.

- MF_STRING Określa, że element menu jest ciągiem znaków.

Każda z następujących grup zawiera listę flag, które wzajemnie się wykluczają i nie mogą być używane razem:

- MF_DISABLED, MF_ENABLED i MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR i wersja bitmapy

- MF_MENUBARBREAK i MF_MENUBREAK

- MF_CHECKED i MF_UNCHECKED

Za każdym razem, gdy menu, które znajduje się w oknie, zostanie zmienione (niezależnie od tego, czy jest wyświetlane okno), aplikacja powinna wywołać [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::CreateMenu](#createmenu).

## <a name="cmenuattach"></a><a name="attach"></a>CMenu::Dołącz

Dołącza do `CMenu` obiektu istniejące menu systemu Windows.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*Hmenu*<br/>
Określa dojście do menu systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja nie powinna być wywoływana, jeśli `CMenu` menu jest już dołączone do obiektu. Uchwyt menu jest przechowywany `m_hMenu` w elementów członkowskich danych.

Jeśli menu, które chcesz manipulować jest już skojarzone z oknem, można użyć [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) funkcji, aby uzyskać uchwyt do menu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenucheckmenuitem"></a><a name="checkmenuitem"></a>CMenu::CheckMenuItem

Dodaje znaczniki wyboru lub usuwa znaczniki wyboru z elementów menu w menu podręcznym.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDCheckItem*<br/>
Określa element menu, który ma być zaznaczony, zgodnie z *ustaleniami nCheck*.

*nSprawda*<br/>
Określa sposób sprawdzania elementu menu i określania pozycji elementu w menu. Parametr *nCheck* może być kombinacją MF_CHECKED lub MF_UNCHECKED z flagami MF_BYPOSITION lub MF_BYCOMMAND. Flagi te można łączyć za pomocą operatora or bitowego. Mają one następujące znaczenie:

- MF_BYCOMMAND Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Domyślnie włączone.

- MF_BYPOSITION Określa, że parametr podaje pozycję istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.

- MF_CHECKED Działa jako przełącznik z MF_UNCHECKED, aby umieścić domyślny znacznik wyboru obok elementu.

- MF_UNCHECKED Działa jako przełącznik z MF_CHECKED, aby usunąć znacznik wyboru obok elementu.

### <a name="return-value"></a>Wartość zwracana

Poprzedni stan elementu: MF_CHECKED lub MF_UNCHECKED lub 0xFFFFFFFFFF, jeśli element menu nie istnieje.

### <a name="remarks"></a>Uwagi

Parametr *nIDCheckItem* określa element, który ma zostać zmodyfikowany.

Parametr *nIDCheckItem* może identyfikować element menu podręcznego, a także element menu. Do sprawdzenia wyskakującego elementu menu nie są wymagane żadne specjalne kroki. Nie można sprawdzić elementów menu najwyższego poziomu. Wyskakującego elementu menu należy sprawdzić według pozycji, ponieważ nie ma identyfikatora elementu menu skojarzonego z nim.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::GetMenuState](#getmenustate).

## <a name="cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a>CMenu::CheckMenuRadioItem

Sprawdza określony element menu i sprawia, że element radiowy.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nIDPierwszy*<br/>
Określa (jako identyfikator lub przesunięcie, w zależności od wartości *nFlags)* pierwszy element menu w grupie przycisków opcji.

*nIDLast*<br/>
Określa (jako identyfikator lub przesunięcie, w zależności od wartości *nFlags)* ostatni element menu w grupie przycisków opcji.

*nIDItem (nIDItem)*<br/>
Określa (jako identyfikator lub przesunięcie, w zależności od wartości *nFlags)* element w grupie, który zostanie sprawdzony za pomocą przycisku opcji.

*nPłgi*<br/>
Określa interpretację *nIDFirst*, *nIDLast*i *nIDItem* w następujący sposób:

|nPłgi|Interpretacja|
|------------|--------------------|
|MF_BYCOMMAND|Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli nie ustawiono ani MF_BYCOMMAND, ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr podaje położenie istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0

### <a name="remarks"></a>Uwagi

W tym samym czasie funkcja odznacza wszystkie inne elementy menu w skojarzonej grupie i czyści flagę typu elementu radiowego dla tych elementów. Zaznaczony element jest wyświetlany przy użyciu mapy bitowej przycisku opcji (lub punktora) zamiast mapy bitowej znacznika wyboru.

### <a name="example"></a>Przykład

  Zobacz przykład [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

## <a name="cmenucmenu"></a><a name="cmenu"></a>CMenu::CMenu

Tworzy puste menu i dołącza `CMenu` je do obiektu.

```
CMenu();
```

### <a name="remarks"></a>Uwagi

Menu nie jest tworzone, dopóki nie wywołasz jednej z funkcji tworzenia lub ładowania elementu członkowskiego`CMenu:`

- [CreateMenu](#createmenu)

- [Tworzeniepopupmenu](#createpopupmenu)

- [LoadMenu ( LoadMenu )](#loadmenu)

- [LoadMenuIndirect (LoadMenuIndirect)](#loadmenuindirect)

- [Dołącz](#attach)

## <a name="cmenucreatemenu"></a><a name="createmenu"></a>CMenu::CreateMenu

Tworzy menu i dołącza je `CMenu` do obiektu.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli menu zostało utworzone pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Menu jest początkowo puste. Elementy menu można dodawać `AppendMenu` `InsertMenu` za pomocą funkcji lub elementu członkowskiego.

Jeśli menu jest przypisane do okna, jest automatycznie niszczone po zniszczeniu okna.

Przed zamknięciem aplikacji musi zwolnić zasoby systemowe skojarzone z menu, jeśli menu nie jest przypisane do okna. Aplikacja zwalnia menu, wywołując [DestroyMenu](#destroymenu) funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

## <a name="cmenucreatepopupmenu"></a><a name="createpopupmenu"></a>CMenu::CreatePopupMenu

Tworzy wyskakujące menu i `CMenu` dołącza je do obiektu.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli menu podręczne zostało pomyślnie utworzone; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Menu jest początkowo puste. Elementy menu można dodawać `AppendMenu` `InsertMenu` za pomocą funkcji lub elementu członkowskiego. Aplikacja może dodać menu podręczne do istniejącego menu lub menu podręcznego. Funkcja `TrackPopupMenu` elementu członkowskiego może służyć do wyświetlania tego menu jako pływającego menu podręcznego i śledzenia wyborów w wyskakującym menu.

Jeśli menu jest przypisane do okna, jest automatycznie niszczone po zniszczeniu okna. Jeśli menu zostanie dodane do istniejącego menu, zostanie ono automatycznie zniszczone po zniszczeniu tego menu.

Przed zamknięciem aplikacji należy zwolnić zasoby systemowe skojarzone z menu podręcznym, jeśli menu nie jest przypisane do okna. Aplikacja zwalnia menu, wywołując [DestroyMenu](#destroymenu) funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::CreateMenu](#createmenu).

## <a name="cmenudeletemenu"></a><a name="deletemenu"></a>CMenu::DeleteMenu

Usuwa element z menu.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nPozycja*<br/>
Określa element menu, który ma zostać usunięty, zgodnie z *ustaleniami nFlags*.

*nPłgi*<br/>
Służy do interpretowania *nPozycja* w następujący sposób:

|nPłgi|Interpretacja nPozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli nie ustawiono ani MF_BYCOMMAND, ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr podaje położenie istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli element menu ma skojarzone menu `DeleteMenu` podręczne, niszczy uchwyt do menu podręcznego i zwalnia pamięć używaną przez menu podręczne.

Za każdym razem, gdy menu, które znajduje się w oknie, zostanie zmienione (niezależnie od tego, czy jest wyświetlane okno, aplikacja musi wywołać [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenudeletetempmap"></a><a name="deletetempmap"></a>CMenu::DeleteTempMap

Wywoływane automatycznie `CWinApp` przez program obsługi czasu bezczynności, `CMenu` usuwa wszystkie obiekty tymczasowe utworzone przez [FromHandle](#fromhandle) funkcji elementu członkowskiego.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Uwagi

`DeleteTempMap`odłącza obiekt menu systemu Windows `CMenu` dołączony do obiektu `CMenu` tymczasowego przed usunięciem obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

## <a name="cmenudestroymenu"></a><a name="destroymenu"></a>CMenu::DestroyMenu

Niszczy menu i wszystkie zasoby systemu Windows, które zostały użyte.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli menu jest zniszczone; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Menu jest odłączony od obiektu, `CMenu` zanim zostanie zniszczony. Funkcja `DestroyMenu` systemu Windows jest automatycznie `CMenu` wywoływana w destruktorze.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::CreateMenu](#createmenu).

## <a name="cmenudetach"></a><a name="detach"></a>CMenu::Detach

Odłącza menu systemu `CMenu` Windows od obiektu i zwraca uchwyt.

```
HMENU Detach();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt, typu HMENU, do menu systemu Windows, jeśli się powiedzie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Element `m_hMenu` członkowski danych jest ustawiony na NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenudrawitem"></a><a name="drawitem"></a>CMenu::DrawItem

Wywoływane przez strukturę, gdy zmienia się wizualny aspekt menu rysowanego przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do struktury [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) który zawiera informacje o typie wymaganego rysunku.

### <a name="remarks"></a>Uwagi

Element `itemAction` członkowski `DRAWITEMSTRUCT` konstrukcji definiuje akcję rysowania, która ma być wykonana. Zastąpokaj tę funkcję elementu członkowskiego, aby zaimplementować rysunek dla obiektu rysowania `CMenu` właściciela. Aplikacja powinna przywrócić wszystkie obiekty interfejsu urządzenia graficznego (GDI) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

Zobacz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) opis `DRAWITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

Poniższy kod pochodzi z próbki MFC [CTRLTEST:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

## <a name="cmenuenablemenuitem"></a><a name="enablemenuitem"></a>CMenu::EnableMenuItem

Włącza, wyłącza lub przyciemnia element menu.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parametry

*nIDEnableItem*<br/>
Określa element menu, który ma być włączony, zgodnie z *ustaleniami nEnable*. Ten parametr może określać elementy menu podręcznego, a także standardowe elementy menu.

*nWychalny*<br/>
Określa akcję do podjęcia. Może to być połączenie MF_DISABLED, MF_ENABLED lub MF_GRAYED, z MF_BYCOMMAND lub MF_BYPOSITION. Wartości te można łączyć za pomocą operatora or bitowego. Wartości te mają następujące znaczenie:

- MF_BYCOMMAND Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Domyślnie włączone.

- MF_BYPOSITION Określa, że parametr podaje pozycję istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.

- MF_DISABLED Wyłącza element menu, tak aby nie można go było zaznaczyć, ale nie przyciemniał go.

- MF_ENABLED Włącza element menu, dzięki czemu można go wybrać i przywraca go ze stanu wygaszonego.

- MF_GRAYED Wyłącza element menu, tak aby nie można go było wybrać i przyciemniał go.

### <a name="return-value"></a>Wartość zwracana

Poprzedni stan (MF_DISABLED, MF_ENABLED lub MF_GRAYED) lub -1, jeśli nie jest prawidłowy.

### <a name="remarks"></a>Uwagi

Funkcje członkowskie [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu)i [LoadMenuIndirect](#loadmenuindirect) mogą również ustawić stan (włączony, wyłączony lub wygaszony) elementu menu.

Użycie MF_BYPOSITION wartości wymaga użycia przez aplikację `CMenu`prawidłowego . `CMenu` Jeśli używany jest pasek menu, ma to wpływ na element menu najwyższego poziomu (element na pasku menu). Aby ustawić stan elementu w wyskakującym okienku lub zagnieżdżone `CMenu` menu podręcznym według pozycji, aplikacja musi określić menu podręczne.

Gdy aplikacja określa flagę MF_BYCOMMAND, system Windows sprawdza wszystkie elementy menu podręcznego, które są podrzędne `CMenu`do ; w związku z tym, chyba że `CMenu` zduplikowane elementy menu są obecne, za pomocą paska menu jest wystarczająca.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

## <a name="cmenufromhandle"></a><a name="fromhandle"></a>CMenu::OdHandle

Zwraca wskaźnik do `CMenu` obiektu, do który doszłą dodaniem systemu Windows do menu.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*Hmenu*<br/>
Uchwyt systemu Windows do menu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMenu` a, który może być tymczasowy lub stały.

### <a name="remarks"></a>Uwagi

Jeśli `CMenu` obiekt nie jest jeszcze dołączony do obiektu `CMenu` menu systemu Windows, tworzony i dołączany jest obiekt tymczasowy.

Ten `CMenu` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynny w pętli zdarzeń, w którym to czasie wszystkie obiekty tymczasowe są usuwane.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::CreateMenu](#createmenu).

## <a name="cmenugetdefaultitem"></a><a name="getdefaultitem"></a>CMenu::GetDefaultItem

Określa domyślny element menu w określonym menu.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*gmdiFlags*<br/>
Wartość określająca sposób wyszukiwania elementów menu przez funkcję. Ten parametr może być żaden, jeden lub kombinacja następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Określa, że jeśli elementem domyślnym jest element, który otwiera podmenu, funkcja polega na ponownym wyszukiwaniu w odpowiednim podmenu. Jeśli podmenu nie ma elementu domyślnego, zwracana wartość identyfikuje element, który otwiera podmenu.<br /><br /> Domyślnie funkcja zwraca pierwszy element domyślny w określonym menu, niezależnie od tego, czy jest to element, który otwiera podmenu.|
|GMDI_USEDISABLED|Określa, że funkcja ma zwracać element domyślny, nawet jeśli jest wyłączony.<br /><br /> Domyślnie funkcja pomija wyłączone lub wyszarzone elementy.|

*fByPos*<br/>
Wartość określająca, czy element menu ma być pobierany, czy jego położenie. Jeśli ten parametr jest FALSE, zwracany jest identyfikator. W przeciwnym razie pozycja jest zwracana.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest identyfikatorem lub położeniem elementu menu. Jeśli funkcja nie powiedzie się, zwracana wartość jest - 1.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie funkcji Win32 [GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem), zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a>CMenu::GetMenuContextHelpId

Pobiera identyfikator pomocy kontekstu skojarzony z programem `CMenu`.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator pomocy kontekstu obecnie skojarzony z `CMenu` jeśli ma; zero w przeciwnym razie.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenuinfo"></a><a name="getmenuinfo"></a>CMenu::GetMenuInfo

Pobiera informacje dla menu.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parametry

*lpcmi (*<br/>
Wskaźnik do struktury [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) zawierający informacje dla menu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest niezerowa; w przeciwnym razie zwracana wartość wynosi zero.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać informacje o menu.

## <a name="cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a>CMenu::GetMenuItemCount

Określa liczbę elementów w menu podręcznym lub menu najwyższego poziomu.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w menu, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie -1.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenugetmenuitemid"></a><a name="getmenuitemid"></a>CMenu::GetMenuItemID

Uzyskuje identyfikator elementu menu dla elementu menu znajdującego się w pozycji zdefiniowanej przez *nPos*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Określa położenie (oparte na wartości zero) elementu menu, którego identyfikator jest pobierany.

### <a name="return-value"></a>Wartość zwracana

Identyfikator elementu dla określonego elementu w menu podręcznym, jeśli funkcja zakończy się pomyślnie. Jeśli określony element jest menu podręcznym (w przeciwieństwie do elementu w menu podręcznym), zwracana wartość wynosi -1. Jeśli *nPos* odpowiada pozycji menu SEPARATOR, zwracana wartość wynosi 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a>CMenu::GetMenuItemInfo

Pobiera informacje o elemencie menu.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uJ.*<br/>
Identyfikator lub położenie elementu menu, aby uzyskać informacje na temat. Znaczenie tego parametru zależy od `ByPos`wartości .

*lpMenuItemInfo*<br/>
Wskaźnik do [MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow), zgodnie z opisem w windows SDK, który zawiera informacje o menu.

*fByPos*<br/>
Wartość określająca znaczenie `nIDItem`. Domyślnie `ByPos` jest FALSE, co oznacza, że uItem jest identyfikatorem elementu menu. Jeśli `ByPos` nie jest ustawiona na FAŁSZ, wskazuje pozycję elementu menu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest niezerowa. Jeśli funkcja nie powiedzie się, zwracana wartość wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, użyj funkcji Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), zgodnie z opisem w windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie funkcji Win32 [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow), zgodnie z opisem w windows SDK. Należy zauważyć, że w `GetMenuItemInfo`implementacji MFC , nie należy używać dojścia do menu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

## <a name="cmenugetmenustate"></a><a name="getmenustate"></a>CMenu::GetMenuState

Zwraca stan określonego elementu menu lub liczbę elementów w menu podręcznym.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Określa identyfikator elementu menu określony przez *nFlags*.

*nPłgi*<br/>
Określa charakter *nID*. Może to być jedna z następujących wartości:

- MF_BYCOMMAND Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Domyślnie włączone.

- MF_BYPOSITION Określa, że parametr podaje pozycję istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.

### <a name="return-value"></a>Wartość zwracana

Wartość 0xFFFFFFFF, jeśli określony element nie istnieje. Jeśli *nId* identyfikuje menu podręczne, bajt wysokiego rzędu zawiera liczbę elementów w menu podręcznym, a bajt niskiej kolejności zawiera flagi menu skojarzone z menu podręcznym. W przeciwnym razie zwracana jest maska (Boolean OR) wartości z poniższej listy (ta maska opisuje stan elementu menu, który *nId* identyfikuje):

- MF_CHECKED Działa jako przełącznik z MF_UNCHECKED, aby umieścić domyślny znacznik wyboru obok elementu. Gdy aplikacja dostarcza mapy bitowe znacznika `SetMenuItemBitmaps` wyboru (patrz funkcja elementu członkowskiego), wyświetlana jest mapa bitowa "check mark on".

- MF_DISABLED Wyłącza element menu, tak aby nie można go było zaznaczyć, ale nie przyciemniał go.

- MF_ENABLED Włącza element menu, dzięki czemu można go wybrać i przywraca go ze stanu wygaszonego. Należy zauważyć, że wartość tej stałej wynosi 0; aplikacja nie powinna testować względem 0 dla awarii podczas korzystania z tej wartości.

- MF_GRAYED Wyłącza element menu, tak aby nie można go było wybrać i przyciemniał go.

- MF_MENUBARBREAK Umieszcza element w nowym wierszu w menu statycznym lub w nowej kolumnie w menu podręcznych. Nowa kolumna menu podręcznego zostanie oddzielona od starej kolumny pionową linią podziału.

- MF_MENUBREAK Umieszcza element w nowym wierszu w menu statycznym lub w nowej kolumnie w menu podręcznych. Między kolumnami nie jest umieszczona żadna linia podziału.

- MF_SEPARATOR Rysuje poziomą linię podziału. Może być używany tylko w wyskakującym menu. Nie można wygaszać, wyłączyć ani wyróżnić tej linii. Inne parametry są ignorowane.

- MF_UNCHECKED Działa jako przełącznik z MF_CHECKED, aby usunąć znacznik wyboru obok elementu. Gdy aplikacja dostarcza mapy bitowe znacznika `SetMenuItemBitmaps` wyboru (patrz funkcja elementu członkowskiego), wyświetlana jest mapa bitowa "check mark off". Należy zauważyć, że wartość tej stałej wynosi 0; aplikacja nie powinna testować względem 0 dla awarii podczas korzystania z tej wartości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

## <a name="cmenugetmenustring"></a><a name="getmenustring"></a>CMenu::Pobierz pobierz

Kopiuje etykietę określonego elementu menu do określonego buforu.

```
int GetMenuString(
    UINT nIDItem,
    LPTSTR lpString,
    int nMaxCount,
    UINT nFlags) const;

int GetMenuString(
    UINT nIDItem,
    CString& rString,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parametry

*nIDItem (nIDItem)*<br/>
Określa identyfikator liczby całkowitej elementu menu lub przesunięcie elementu menu w menu, w zależności od wartości *nFlags*.

*lpString (lpString)*<br/>
Wskazuje bufor, który ma odbierać etykietę.

*rString*<br/>
Odwołanie do `CString` obiektu, który ma odbierać skopiowany ciąg menu.

*nMaxCount*<br/>
Określa maksymalną długość (w znakach) etykiety, która ma zostać skopiowana. Jeśli etykieta jest dłuższa niż maksymalna określona w *nMaxCount*, dodatkowe znaki są obcinane.

*nPłgi*<br/>
Określa interpretację parametru *nIDItem.* Może to być jedna z następujących wartości:

|nPłgi|Interpretacja nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli nie ustawiono ani MF_BYCOMMAND, ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr podaje położenie istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

### <a name="return-value"></a>Wartość zwracana

Określa rzeczywistą liczbę znaków skopiowanych do buforu, z wyłączeniem zerowego terminatora.

### <a name="remarks"></a>Uwagi

Parametr *nMaxCount* powinien być większy niż liczba znaków w etykiecie, aby pomieścić znak null, który kończy ciąg.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

## <a name="cmenugetsafehmenu"></a><a name="getsafehmenu"></a>CMenu::GetSafeHmenu

Zwraca HMENU zawinięte `CMenu` przez ten`CMenu` obiekt lub wskaźnik NULL.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::LoadMenu](#loadmenu).

## <a name="cmenugetsubmenu"></a><a name="getsubmenu"></a>CMenu::GetSubMenu

Pobiera `CMenu` obiekt wyskakującego menu.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Określa położenie menu podręcznego znajdującego się w menu. Wartości pozycji zaczynają się od 0 dla pierwszego elementu menu. Identyfikatora menu podręcznego nie można użyć w tej funkcji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMenu` obiektu, `m_hMenu` którego element członkowski zawiera dojście do menu podręcznego, jeśli w danej pozycji istnieje menu podręczne; w przeciwnym razie NULL. Jeśli `CMenu` obiekt nie istnieje, tworzony jest tymczasowy. Zwrócony `CMenu` wskaźnik nie powinien być przechowywany.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::TrackPopupMenu](#trackpopupmenu).

## <a name="cmenuinsertmenu"></a><a name="insertmenu"></a>CMenu::InsertMenu

Wstawia nowy element menu w pozycji określonej przez *nPosition* i przenosi inne elementy w dół menu.

```
BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Parametry

*nPozycja*<br/>
Określa element menu, przed którym ma zostać wstawiony nowy element menu. Parametr *nFlags* może służyć do interpretacji *nPozycja* w następujący sposób:

|nPłgi|Interpretacja nPozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli nie ustawiono ani MF_BYCOMMAND, ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr podaje położenie istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0. Jeśli *nPosition* jest -1, nowy element menu jest dołączany do końca menu.|

*nPłgi*<br/>
Określa sposób interpretacji *nPosition* i określa informacje o stanie nowego elementu menu po dodaniu go do menu. Aby uzyskać listę flag, które mogą być ustawione, zobacz [AppendMenu](#appendmenu) funkcji elementu członkowskiego. Aby określić więcej niż jedną wartość, użyj operatora or bitowego, aby połączyć je z flagą MF_BYCOMMAND lub MF_BYPOSITION.

*nIDNewItem*<br/>
Określa identyfikator polecenia nowego elementu menu lub, jeśli *nFlags* jest ustawiony na MF_POPUP, uchwyt menu (HMENU) w menu podręcznym. Parametr *nIDNewItem* jest ignorowany (nie jest potrzebny), jeśli *nFlags* jest ustawiony na MF_SEPARATOR.

*lpszNewItem*<br/>
Określa zawartość nowego elementu menu. *nS.* *lpszNewItem*

|nPłgi|Interpretacja lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Zawiera 32-bitową wartość dostarczoną przez aplikację, której aplikacja może używać do obsługi dodatkowych danych skojarzonych z elementem menu. Ta wartość 32-bitowa jest dostępna `itemData` dla aplikacji w elementów członkowskich struktury dostarczonej przez [komunikaty WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) i [WM_DRAWITEM.](/windows/win32/Controls/wm-drawitem) Te wiadomości są wysyłane, gdy element menu jest początkowo wyświetlany lub jest zmieniany.|
|MF_STRING|Zawiera długi wskaźnik do ciągu zakończonego wartością null. Jest to domyślna interpretacja.|
|MF_SEPARATOR|Parametr *lpszNewItem* jest ignorowany (nie jest potrzebny).|

*pBmp (wł.)*<br/>
Wskazuje `CBitmap` obiekt, który będzie używany jako element menu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja może określić stan elementu menu, ustawiając wartości w *nFlags*.

Za każdym razem, gdy menu, które znajduje się w oknie, zostanie zmienione `CWnd::DrawMenuBar`(niezależnie od tego, czy jest wyświetlane okno, aplikacja powinna wywołać .

Gdy *nIDNewItem* określa menu podręczne, staje się częścią menu, w którym jest wstawiany. Jeśli to menu zostanie zniszczone, wstawione menu również zostanie zniszczone. Wstawione menu powinno być `CMenu` odłączone od obiektu, aby uniknąć konfliktu.

Jeśli okno podrzędne aktywnego interfejsu wielu dokumentów (MDI) jest zmaksymalizowane, a aplikacja wstawia menu podręczne do menu aplikacji MDI, wywołując tę funkcję i określając flagę MF_BYPOSITION, menu jest wstawiane o jedną pozycję dalej niż oczekiwano. Dzieje się tak, ponieważ menu Control aktywnego okna podrzędnego MDI jest wstawiany do pierwszej pozycji paska menu okna ramki MDI. Aby prawidłowo ustawić menu, aplikacja musi dodać 1 do wartości pozycji, która w przeciwnym razie zostałaby użyta. Aplikacja może użyć WM_MDIGETACTIVE komunikatu, aby ustalić, czy aktualnie aktywne okno podrzędne jest zmaksymalizowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

## <a name="cmenuinsertmenuitem"></a><a name="insertmenuitem"></a>CMenu::InsertMenuItem

Wstawia nowy element menu w określonym położeniu w menu.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uJ.*<br/>
Zobacz opis *uItem* w [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw) w windows SDK.

*lpMenuItemInfo*<br/>
Zobacz opis *lpmii* w `InsertMenuItem` windows SDK.

*fByPos*<br/>
Zobacz opis *fByPosition* w `InsertMenuItem` zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana [insertmenuitem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw), opisane w windows SDK.

## <a name="cmenuloadmenu"></a><a name="loadmenu"></a>CMenu::LoadMenu

Ładuje zasób menu z pliku wykonywalnego `CMenu` aplikacji i dołącza go do obiektu.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskazuje ciąg zakończony zerem, który zawiera nazwę zasobu menu do załadowania.

*nIDSerwród*<br/>
Określa identyfikator menu zasobu menu do załadowania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zasób menu został pomyślnie załadowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przed zamknięciem aplikacji musi zwolnić zasoby systemowe skojarzone z menu, jeśli menu nie jest przypisane do okna. Aplikacja zwalnia menu, wywołując [DestroyMenu](#destroymenu) funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

## <a name="cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a>CMenu::LoadMenuIndirect

Ładuje zasób z szablonu menu w `CMenu` pamięci i dołącza go do obiektu.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parametry

*lpMenuTemplate*<br/>
Wskazuje szablon menu (który jest pojedynczą strukturą [MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) i kolekcją jednej lub więcej struktur [MENUITEMTEMPLATE).](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) Aby uzyskać więcej informacji na temat tych dwóch struktur, zobacz Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zasób menu został pomyślnie załadowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Szablon menu to nagłówek, po którym następuje zbiór co najmniej jednej struktury [MENUITEMTEMPLATE,](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) z których każda może zawierać jeden lub więcej elementów menu i menu podręcznych.

Numer wersji powinien wynosić 0.

Flagi `mtOption` powinny zawierać MF_END dla ostatniego elementu na liście podręcznej i dla ostatniego elementu na liście głównej. Zobacz `AppendMenu` funkcję elementu członkowskiego dla innych flag. Element `mtId` członkowski musi zostać pominięty w strukturze MENUITEMTEMPLATE, `mtOption`gdy MF_POPUP jest określony w .

Miejsce przydzielone dla struktury MENUITEMTEMPLATE musi `mtString` być wystarczająco duże, aby zawierało nazwę elementu menu jako ciąg zakończony zerem.

Przed zamknięciem aplikacji musi zwolnić zasoby systemowe skojarzone z menu, jeśli menu nie jest przypisane do okna. Aplikacja zwalnia menu, wywołując [DestroyMenu](#destroymenu) funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

## <a name="cmenum_hmenu"></a><a name="m_hmenu"></a>CMenu::m_hMenu

Określa uchwyt HMENU menu systemu Windows dołączony `CMenu` do obiektu.

```
HMENU m_hMenu;
```

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::LoadMenu](#loadmenu).

## <a name="cmenumeasureitem"></a><a name="measureitem"></a>CMenu::MeasureItem

Wywoływana przez strukturę podczas tworzenia menu ze stylem rysowania właściciela.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Wskaźnik do `MEASUREITEMSTRUCT` struktury.

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpuj tę funkcję `MEASUREITEMSTRUCT` elementu członkowskiego i wypełnij strukturę, aby poinformować system Windows o wymiarach menu.

Zobacz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) opis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

Poniższy kod pochodzi z próbki MFC [CTRLTEST:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

## <a name="cmenumodifymenu"></a><a name="modifymenu"></a>CMenu::ModifyMenu

Zmienia istniejący element menu w pozycji określonej przez *nPosition*.

```
BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Parametry

*nPozycja*<br/>
Określa element menu, który ma zostać zmieniony. Parametr *nFlags* może służyć do interpretacji *nPozycja* w następujący sposób:

|nPłgi|Interpretacja nPozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli nie ustawiono ani MF_BYCOMMAND, ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr podaje położenie istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

*nPłgi*<br/>
Określa sposób interpretacji *nPosition* i zawiera informacje o zmianach, które mają zostać wprowadzone w elemencie menu. Aby uzyskać listę flag, które mogą być ustawione, zobacz [AppendMenu](#appendmenu) funkcji elementu członkowskiego.

*nIDNewItem*<br/>
Określa identyfikator polecenia zmodyfikowanego elementu menu lub, jeśli *nFlags* jest ustawiony na MF_POPUP, uchwyt menu (HMENU) wyskakującego menu. Parametr *nIDNewItem* jest ignorowany (nie jest potrzebny), jeśli *nFlags* jest ustawiony na MF_SEPARATOR.

*lpszNewItem*<br/>
Określa zawartość nowego elementu menu. Parametr *nFlags* może być używany do interpretacji *lpszNewItem* w następujący sposób:

|nPłgi|Interpretacja lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Zawiera 32-bitową wartość dostarczoną przez aplikację, której aplikacja może używać do obsługi dodatkowych danych skojarzonych z elementem menu. Ta wartość 32-bitowa jest dostępna dla aplikacji podczas przetwarzania MF_MEASUREITEM i MF_DRAWITEM.|
|MF_STRING|Zawiera długi wskaźnik do ciągu zakończonego wartością null lub do pliku `CString`.|
|MF_SEPARATOR|Parametr *lpszNewItem* jest ignorowany (nie jest potrzebny).|

*pBmp (wł.)*<br/>
Wskazuje `CBitmap` obiekt, który będzie używany jako element menu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja określa nowy stan elementu menu, ustawiając wartości w *nFlags*. Jeśli ta funkcja zastępuje menu podręczne skojarzone z elementem menu, niszczy stare menu podręczne i zwalnia pamięć używaną przez menu podręczne.

Gdy *nIDNewItem* określa menu podręczne, staje się częścią menu, w którym jest wstawiany. Jeśli to menu zostanie zniszczone, wstawione menu również zostanie zniszczone. Wstawione menu powinno być `CMenu` odłączone od obiektu, aby uniknąć konfliktu.

Za każdym razem, gdy menu, które znajduje się w oknie, zostanie zmienione `CWnd::DrawMenuBar`(niezależnie od tego, czy jest wyświetlane okno, aplikacja powinna wywołać . Aby zmienić atrybuty istniejących elementów menu, `CheckMenuItem` jest `EnableMenuItem` znacznie szybciej korzystać z funkcji i element członkowski.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

## <a name="cmenuoperator-hmenu"></a><a name="operator_hmenu"></a>CMenu::operator HMENU

Ten operator służy do pobierania `CMenu` dojścia obiektu.

```
operator HMENU() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, `CMenu` uchwyt obiektu; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Dojścia można używać do bezpośredniego wywoływania interfejsów API systemu Windows.

## <a name="cmenuoperator-"></a><a name="operator_neq"></a>CMenu::operator !=

Określa, czy dwa menu nie są logicznie równe.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*Menu*<br/>
Obiekt `CMenu` do porównania.

### <a name="remarks"></a>Uwagi

Sprawdza, czy obiekt menu po lewej stronie nie jest równy obiektowi menu po prawej stronie.

## <a name="cmenuoperator-"></a><a name="operator_eq_eq"></a>CMenu::operator ==

Określa, czy dwa menu są logicznie równe.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*Menu*<br/>
Obiekt `CMenu` do porównania.

### <a name="remarks"></a>Uwagi

Sprawdza, czy obiekt menu po lewej stronie jest równy (pod względem wartości HMENU) do obiektu menu po prawej stronie.

## <a name="cmenuremovemenu"></a><a name="removemenu"></a>CMenu::Usuńmenu

Usuwa element menu ze skojarzonym menu podręcznym z menu.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nPozycja*<br/>
Określa element menu, który ma zostać usunięty. Parametr *nFlags* może służyć do interpretacji *nPozycja* w następujący sposób:

|nPłgi|Interpretacja nPozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli nie ustawiono ani MF_BYCOMMAND, ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr podaje położenie istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

*nPłgi*<br/>
Określa sposób interpretacji *nPosition.*

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nie niszczy uchwyt menu podręcznego, więc menu może być ponownie. Przed wywołaniem tej funkcji aplikacja `GetSubMenu` może wywołać funkcję elementu `CMenu` członkowskiego, aby pobrać obiekt wyskakujących do ponownego użycia.

Za każdym razem, gdy menu, które znajduje się w oknie, zostanie zmienione `CWnd::DrawMenuBar`(niezależnie od tego, czy jest wyświetlane okno, aplikacja musi wywołać .

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetdefaultitem"></a><a name="setdefaultitem"></a>CMenu::SetDefaultItem

Ustawia domyślny element menu dla określonego menu.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uJ.*<br/>
Identyfikator lub położenie nowego domyślnego elementu menu lub - 1 dla braku elementu domyślnego. Znaczenie tego parametru zależy od wartości *fByPos*.

*fByPos*<br/>
Wartość określająca znaczenie *uItem*. Jeśli ten parametr jest FALSE, *uItem* jest identyfikatorem elementu menu. W przeciwnym razie jest to pozycja elementu menu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest niezerowa. Jeśli funkcja nie powiedzie się, zwracana wartość wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, użyj funkcji Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), zgodnie z opisem w windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie funkcji Win32 [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem), zgodnie z opisem w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a>CMenu::SetMenuContextHelpId

Kojarzy identyfikator pomocy kontekstu z . `CMenu`

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parametry

*dwContextHelpId*<br/>
Identyfikator pomocy kontekstu `CMenu`do skojarzenia z .

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0

### <a name="remarks"></a>Uwagi

Wszystkie elementy w menu współużytkują ten identyfikator — nie można dołączyć identyfikatora kontekstu pomocy do poszczególnych elementów menu.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

## <a name="cmenusetmenuinfo"></a><a name="setmenuinfo"></a>CMenu::SetMenuInfo

Ustawia informacje dla menu.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parametry

*lpcmi (*<br/>
Wskaźnik do struktury [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) zawierający informacje dla menu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest niezerowa; w przeciwnym razie zwracana wartość wynosi zero.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby ustawić konkretne informacje o menu.

## <a name="cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a>CMenu::SetMenuItemBitmaps

Kojarzy określone mapy bitowe z elementem menu.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parametry

*nPozycja*<br/>
Określa element menu, który ma zostać zmieniony. Parametr *nFlags* może służyć do interpretacji *nPozycja* w następujący sposób:

|nPłgi|Interpretacja nPozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, że parametr podaje identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli nie ustawiono ani MF_BYCOMMAND, ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr podaje położenie istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

*nPłgi*<br/>
Określa sposób interpretacji *nPosition.*

*pBmpNiesprawdzone*<br/>
Określa mapę bitową, która ma być używana dla elementów menu, które nie są zaznaczone.

*pBmpSprawki*<br/>
Określa mapę bitową, która ma być używana dla elementów menu, które są zaznaczone.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Niezależnie od tego, czy element menu jest zaznaczony, czy nie jest zaznaczony, system Windows wyświetla odpowiednią mapę bitową obok elementu menu.

Jeśli albo *pBmpUnchecked* lub *pBmpChecked* jest NULL, a następnie system Windows wyświetla nic obok elementu menu dla odpowiedniego atrybutu. Jeśli oba parametry mają wartość NULL, system Windows używa domyślnego znacznika wyboru, gdy element jest zaznaczony i usuwa znacznik wyboru, gdy element jest niezaznaczony.

Gdy menu zostanie zniszczone, te mapy bitowe nie są niszczone; aplikacja musi je zniszczyć.

Funkcja `GetMenuCheckMarkDimensions` Systemu Windows pobiera wymiary domyślnego znacznika wyboru używanego dla elementów menu. Aplikacja używa tych wartości do określenia odpowiedniego rozmiaru dla map bitowych dostarczonych z tą funkcją. Uzyskaj rozmiar, utwórz mapy bitowe, a następnie ustaw je.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

## <a name="cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a>CMenu::SetMenuItemInfo

Zmienia informacje o elemencie menu.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uJ.*<br/>
Zobacz opis *uItem* w [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow) w zestawie Windows SDK.

*lpMenuItemInfo*<br/>
Zobacz opis *lpmii* w `SetMenuItemInfo` windows SDK.

*fByPos*<br/>
Zobacz opis *fByPosition* w `SetMenuItemInfo` zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja jest [zawija SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow), opisane w zestawie Windows SDK.

## <a name="cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a>CMenu::TrackPopupMenu

Wyświetla pływające menu podręczne w określonej lokalizacji i śledzi wybór elementów w wyskakującym menu.

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>Parametry

*nPłgi*<br/>
Określa flagi położenia ekranu i położenia myszy. Zobacz [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) listę dostępnych flag.

*X*<br/>
Określa położenie poziome we współrzędnych ekranu w menu podręcznym. W zależności od wartości parametru *nFlags* menu może być wyrównane do lewej, wyrównane do prawej lub wyśrodkowane względem tej pozycji.

*Y*<br/>
Określa położenie w pionie we współrzędnych ekranu górnej części menu na ekranie.

*Pwnd*<br/>
Identyfikuje okno, które jest właścicielem menu podręcznego. Ten parametr nie może być null, nawet jeśli TPM_NONOTIFY flaga jest określona. To okno odbiera wszystkie komunikaty WM_COMMAND z menu. W systemie Windows w wersji 3.1 lub nowszej `TrackPopupMenu` okno nie odbiera WM_COMMAND wiadomości, dopóki nie zostanie wróconych. W systemie Windows 3.0 okno odbiera WM_COMMAND `TrackPopupMenu` wiadomości przed powrotem.

*Lprect*<br/>
Ignorowane.

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wynik wywołania [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Zmienne menu podręczne może pojawić się w dowolnym miejscu na ekranie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

## <a name="cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a>CMenu::TrackPopupMenuEx

Wyświetla pływające menu podręczne w określonej lokalizacji i śledzi wybór elementów w wyskakującym menu.

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>Parametry

*fuFlags*<br/>
Określa różne funkcje rozszerzonego menu. Aby uzyskać listę wszystkich wartości i ich znaczenia, zobacz [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

*X*<br/>
Określa położenie poziome we współrzędnych ekranu w menu podręcznym.

*Y*<br/>
Określa położenie w pionie we współrzędnych ekranu górnej części menu na ekranie.

*Pwnd*<br/>
Wskaźnik do okna, w tym menu podręcznym i odbierania wiadomości z utworzonego menu. To okno może być dowolnym oknem z bieżącej aplikacji, ale nie może być null. Jeśli określisz TPM_NONOTIFY w parametrze *fuFlags,* funkcja nie wysyła żadnych wiadomości do *pWnd*. Funkcja musi zwracać dla okna wskazywał przez *pWnd,* aby otrzymać komunikat WM_COMMAND.

*lptpm*<br/>
Wskaźnik do struktury [TPMPARAMS,](/windows/win32/api/winuser/ns-winuser-tpmparams) która określa obszar ekranu menu nie powinny nakładać się. Ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Jeśli określisz TPM_RETURNCMD w parametrze *fuFlags,* zwracana wartość jest identyfikatorem elementu menu elementu wybranego przez użytkownika. Jeśli użytkownik anuluje menu bez dokonywania wyboru lub jeśli wystąpi błąd, zwracana wartość wynosi 0.

Jeśli nie określisz TPM_RETURNCMD w *parametrze fuFlags,* zwracana wartość jest niezerowa, jeśli funkcja powiedzie się, a 0, jeśli nie powiedzie się. Aby uzyskać rozszerzone informacje o błędzie, zadzwoń [do GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Uwagi

Zmienne menu podręczne może pojawić się w dowolnym miejscu na ekranie. Aby uzyskać więcej informacji na temat obsługi błędów podczas tworzenia menu podręcznego, zobacz [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Zobacz też

[Próbka MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)
