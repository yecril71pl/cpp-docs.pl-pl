---
title: Cmenu — klasa
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
ms.openlocfilehash: 464b59f7e598ea1901cf88c47c5887cbbf308607
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375798"
---
# <a name="cmenu-class"></a>Cmenu — klasa

Hermetyzacja Windows `HMENU`.

## <a name="syntax"></a>Składnia

```
class CMenu : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMenu::CMenu](#cmenu)|Konstruuje `CMenu` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|Dołącza nowy element do końca tego menu.|
|[CMenu::Attach](#attach)|Dołącza Windows uchwyt menu, aby `CMenu` obiektu.|
|[CMenu::CheckMenuItem](#checkmenuitem)|Umieszcza pole wyboru obok pozycji lub usuwa znacznik wyboru elementu menu w menu podręcznym.|
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Umieszcza przycisk radiowy obok pozycji menu i usunięcie wszystkich innych elementów menu w grupie przycisk radiowy.|
|[CMenu::CreateMenu](#createmenu)|Tworzy puste menu i dołącza je do `CMenu` obiektu.|
|[CMenu::CreatePopupMenu](#createpopupmenu)|Tworzy puste menu podręczne i dołącza je do `CMenu` obiektu.|
|[CMenu::DeleteMenu](#deletemenu)|Usuwa określony element menu. Jeśli element menu ma skojarzone menu podręcznego, niszczy dojścia do menu podręczne i zwalnia pamięć używana przez nią.|
|[CMenu::DeleteTempMap](#deletetempmap)|Usuwa wszystkie tymczasowe `CMenu` obiekty utworzone przez `FromHandle` funkcja elementu członkowskiego.|
|[CMenu::DestroyMenu](#destroymenu)|Niszczy dołączonym do menu `CMenu` obiektu i zwalnia wszystkie pamięci, która zajęte menu.|
|[CMenu::Detach](#detach)|Odłącza Windows uchwyt menu z `CMenu` obiektu i zwraca uchwyt.|
|[CMenu::DrawItem](#drawitem)|Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt zmiany rysowanych przez właściciela menu.|
|[CMenu::EnableMenuItem](#enablemenuitem)|Włącza, wyłącza lub wygasza (szarości) elementu menu.|
|[CMenu::FromHandle](#fromhandle)|Zwraca wskaźnik do `CMenu` obiektu, biorąc pod uwagę uchwyt menu Windows.|
|[CMenu::GetDefaultItem](#getdefaultitem)|Określa domyślny element menu z menu.|
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Pobiera identyfikator kontekstu pomocy, które są skojarzone z menu.|
|[CMenu::GetMenuInfo](#getmenuinfo)|Pobiera informacje o określonym menu.|
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Określa liczbę elementów w menu podręcznym lub najwyższego poziomu.|
|[CMenu::GetMenuItemID](#getmenuitemid)|Uzyskuje identyfikator elementu menu dla elementu menu, znajduje się w określonej pozycji.|
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Pobiera informacje o elemencie menu.|
|[CMenu::GetMenuState](#getmenustate)|Zwraca stan podany element menu lub liczbę elementów w menu podręcznym.|
|[CMenu::GetMenuString](#getmenustring)|Pobiera etykietę elementu menu określony.|
|[CMenu::GetSafeHmenu](#getsafehmenu)|Zwraca `m_hMenu` owinięty przez ten `CMenu` obiektu.|
|[CMenu::GetSubMenu](#getsubmenu)|Pobiera wskaźnik do menu podręcznego.|
|[CMenu::InsertMenu](#insertmenu)|Wstawia nowy element menu na określonej pozycji przenoszenie innych elementów menu rozwijane.|
|[CMenu::InsertMenuItem](#insertmenuitem)|Wstawia nowy element menu na pozycji określonej w menu.|
|[CMenu::LoadMenu](#loadmenu)|Ładuje zasobów menu z plik wykonywalny i dołącza go do `CMenu` obiektu.|
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Ładuje menu z szablonem menu w pamięci i dołącza go do `CMenu` obiektu.|
|[CMenu::MeasureItem](#measureitem)|Metoda wywoływana przez platformę, aby określić wymiary menu, po utworzeniu rysowanych przez właściciela menu.|
|[CMenu::ModifyMenu](#modifymenu)|Zmienia istniejący element menu w określonej pozycji.|
|[CMenu::RemoveMenu](#removemenu)|Usuwa element menu za pomocą skojarzonego menu podręcznym menu określony.|
|[CMenu::SetDefaultItem](#setdefaultitem)|Ustawia domyślny element menu dla określonego menu.|
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Określa identyfikator kontekstu pomocy, który ma zostać skojarzony z menu.|
|[CMenu::SetMenuInfo](#setmenuinfo)|Ustawia informacje o określonym menu.|
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Kojarzy mapy bitowe znacznik wyboru przy użyciu elementu menu.|
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Zmienia informacje na temat elementu menu.|
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Wyświetla menu podręczne przestawne w określonej lokalizacji i śledzi zaznaczenia elementów w menu podręcznym.|
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Wyświetla menu podręczne przestawne w określonej lokalizacji i śledzi zaznaczenia elementów w menu podręcznym.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMenu::operator HMENU](#operator_hmenu)|Pobiera uchwyt obiekt menu.|
|[CMenu::operator! =](#operator_neq)|Określa, czy dwa obiekty menu nie są równe.|
|[CMenu::operator ==](#operator_eq_eq)|Określa, czy dwa obiekty menu są równe.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMenu::m_hMenu](#m_hmenu)|Określa dojścia do menu Windows dołączonych do `CMenu` obiektu.|

## <a name="remarks"></a>Uwagi

Oferuje ona funkcje Członkowskie tworzenia, śledzenie, aktualizowanie i niszczenie menu.

Tworzenie `CMenu` obiektu na ramce stosu jako lokalną, następnie wywołać `CMenu`firmy elementów członkowskich do manipulowania nowe menu, zgodnie z potrzebami. Następnie wywołaj [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) można ustawić menu do okna, następuje natychmiast po wywołaniu `CMenu` obiektu [Odłącz](#detach) funkcja elementu członkowskiego. `CWnd::SetMenu` Funkcja elementu członkowskiego ustawia menu okna w menu Nowy, powoduje, że okno zostać odświeżone w celu odzwierciedlenia zmiany menu i przekazuje własność menu do okna. Wywołanie `Detach` odłącza HMENU z `CMenu` obiektu, tak że w przypadku lokalnej `CMenu` zmienna jest przekazywana poza zakresem, `CMenu` destruktora obiektu nie jest podejmowana próba zniszczyć menu nie jest już właścicielem. Samo menu automatycznie jest niszczony, kiedy niszczony jest okna.

Możesz użyć [LoadMenuIndirect](#loadmenuindirect) funkcji elementu członkowskiego, aby utworzyć menu z szablonu w pamięci, ale menu utworzone na podstawie zasobów przez wywołanie [LoadMenu](#loadmenu) jest łatwiejsze zarządzanie i samego zasobu menu mogą być tworzone i modyfikowane przez Edytor menu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="appendmenu"></a>  CMenu::AppendMenu

Dołącza nowy element na końcu elementu menu.

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

*nFlags*<br/>
Określa informacje o stanie Nowy element menu, gdy zostanie dodany do menu. Składa się z co najmniej jedna z wartości wymienionych w sekcji uwag.

*nIDNewItem*<br/>
Określa identyfikator polecenia nowego elementu menu lub, jeśli *nFlags* jest ustawiona na MF_POPUP, uchwyt menu ( `HMENU`) z menu podręcznego. *NIDNewItem* parametr jest ignorowany (nie jest wymagany), jeśli *nFlags* jest ustawiona na MF_SEPARATOR.

*lpszNewItem*<br/>
Określa zawartość nowego elementu menu. *NFlags* parametr jest używany do interpretacji *lpszNewItem* w następujący sposób:

|nFlags|Interpretacja lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Zawiera wartość 32-bitowa aplikacja dostarczona używanego przez aplikację do obsługi dodatkowych danych skojarzone z elementem menu. Ta wartość 32-bitowych jest dostępne dla aplikacji, podczas przetwarzania WM_MEASUREITEM i WM_DRAWITEM wiadomości. Wartość jest przechowywana w `itemData` elementu członkowskiego struktury dostarczony wraz z tych komunikatów.|
|MF_STRING|Zawiera wskaźnik na ciąg zakończony znakiem null. Jest to domyślna interpretacja.|
|MF_SEPARATOR|*LpszNewItem* parametr jest ignorowany (nie jest wymagane).|

*pBmp*<br/>
Wskazuje `CBitmap` obiekt, który będzie używany jako element menu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja może określić stanu elementu menu przez ustawienie wartości w *nFlags*. Gdy *nIDNewItem* Określa menu podręczne staje się częścią menu, do którego jest dołączona. Jeśli menu jest niszczony, również zostać zniszczone dołączonym menu. Dołączonym menu powinna być odłączona od `CMenu` obiektu, aby uniknąć konfliktu. Należy pamiętać, że MF_STRING i MF_OWNERDRAW nie są prawidłowe dla wersji mapy bitowej `AppendMenu`.

Poniżej przedstawiono listę flag, które może być ustawiona w *nFlags*:

- Działa MF_CHECKED jako przełącznik z MF_UNCHECKED umieścić domyślnie sprawdź znacznik obok elementu. Jeśli aplikacja dostarcza mapy bitowe znacznik wyboru (zobacz [SetMenuItemBitmaps](#setmenuitembitmaps) składowa), mapa bitowa "znacznik wyboru na" jest wyświetlana.

- MF_UNCHECKED działa jako przełącznik z MF_CHECKED, aby usunąć znacznik wyboru obok elementu. Jeśli aplikacja dostarcza mapy bitowe znacznik wyboru (zobacz `SetMenuItemBitmaps` składowa), mapa bitowa "znacznik wyboru off" jest wyświetlana.

- MF_DISABLED wyłącza elementu menu, tak aby nie można wybrać, ale nie przyciemniaj.

- MF_ENABLED umożliwia elementu menu, który można wybrać i przywraca je ze stanu wygaszone.

- Tak, aby nie można wybrać i wygasza go MF_GRAYED powoduje wyłączenie elementu menu.

- MF_MENUBARBREAK umieszcza elementu w nowym wierszu, w menu statyczne lub w nowej kolumnie w menu podręcznym. Nowa kolumna menu podręcznego będą oddzielone od starego kolumny pionowa linia podziału.

- MF_MENUBREAK umieszcza elementu w nowym wierszu, w menu statyczne lub w nowej kolumnie w menu podręcznym. Nie linii podziału jest umieszczany między kolumnami.

- MF_OWNERDRAW Określa, że element jest elementem rysowania przez właściciela. Gdy po raz pierwszy zostanie wyświetlone menu, okna, który jest właścicielem menu odbiera komunikat WM_MEASUREITEM pobiera wysokość i szerokość elementu menu. Komunikat WM_DRAWITEM jest wysyłane po każdym właściciela, należy zaktualizować wygląd elementu menu. Ta opcja nie jest prawidłowa dla elementu menu najwyższego poziomu.

- MF_POPUP Określa, że element menu ma menu podręczne skojarzonych z nim. Parametr Identyfikatora określa dojścia do menu podręcznego, który ma być skojarzone z elementem. Służy do dodawania wyskakujących menu najwyższego poziomu lub hierarchiczny menu rozwijane do elementu menu podręcznego.

- MF_SEPARATOR rysuje poziomej linii podziału. Należy używać tylko w menu podręcznym. Ten wiersz nie wygaszone, wyłączone lub wyróżnione. Inne parametry są ignorowane.

- MF_STRING Określa, czy element menu jest ciągiem znaków.

Każdy z poniższych grup Wyświetla listę flag, które wzajemnie się wykluczają i nie mogą być używane razem:

- MF_DISABLED MF_ENABLED i MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR i wersji mapy bitowej

- MF_MENUBARBREAK i MF_MENUBREAK

- MF_CHECKED i MF_UNCHECKED

W przypadku, gdy menu, które znajdują się w oknie zostanie zmieniony (czy okno jest wyświetlane), aplikacja powinna wywołać [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::CreateMenu](#createmenu).

##  <a name="attach"></a>  CMenu::Attach

Dołącza do istniejącego menu Windows `CMenu` obiektu.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Określa dojścia do Windows menu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiodła. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja nie powinna być wywoływana, gdy menu jest już dołączony do `CMenu` obiektu. Uchwyt menu są przechowywane w `m_hMenu` element członkowski danych.

Jeśli menu, aby manipulować jest już skojarzony z oknem, możesz użyć [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) funkcję, aby uzyskać dojścia do menu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="checkmenuitem"></a>  CMenu::CheckMenuItem

Dodaje zaznaczenia lub usuwa znaczniki wyboru z elementów menu w menu podręcznym.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDCheckItem*<br/>
Określa element menu aby sprawdzić, zgodnie z ustaleniami *nSprawdź*.

*nCheck*<br/>
Określa, jak sprawdzić element menu i jak określić położenie elementu menu. *NSprawdź* parametr może być kombinacją MF_CHECKED lub MF_UNCHECKED z użyciem flag MF_BYPOSITION lub MF_BYCOMMAND. Te flagi można łączyć przy użyciu bitowego operatora OR. Mają następujące znaczenie:

- MF_BYCOMMAND Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Domyślnie włączone.

- MF_BYPOSITION Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.

- Działa MF_CHECKED jako przełącznik z MF_UNCHECKED umieścić domyślnie sprawdź znacznik obok elementu.

- MF_UNCHECKED działa jako przełącznik z MF_CHECKED, aby usunąć znacznik wyboru obok elementu.

### <a name="return-value"></a>Wartość zwracana

Poprzedni stan elementu: MF_CHECKED lub MF_UNCHECKED lub 0xFFFFFFFF, jeśli element menu nie istnieje.

### <a name="remarks"></a>Uwagi

*NIDCheckItem* parametr określa element które mają być modyfikowane.

*NIDCheckItem* parametru może zidentyfikować elementu menu podręcznego, a także elementu menu. Nie specjalne kroki są wymagane do sprawdzenia elementu menu podręcznego. Nie można sprawdzić elementy menu najwyższego poziomu. Musi być zaznaczone elementu menu podręcznego według położenia, ponieważ nie ma skojarzony z nim identyfikator elementu menu.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::GetMenuState](#getmenustate).

##  <a name="checkmenuradioitem"></a>  CMenu::CheckMenuRadioItem

Sprawdza, czy podany element menu i sprawia, że element radio.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nIDFirst*<br/>
Określa (jako identyfikator lub przesunięcie, w zależności od wartości *nFlags*) do pierwszego elementu menu, w grupie przycisków radiowych.

*nIDLast*<br/>
Określa (jako identyfikator lub przesunięcie, w zależności od wartości *nFlags*) do ostatniego elementu menu, w grupie przycisków radiowych.

*nIDItem*<br/>
Określa (jako identyfikator lub przesunięcie, w zależności od wartości *nFlags*) element w grupie, która będzie sprawdzana za pomocą przycisku radiowego.

*nFlags*<br/>
Określa interpretacji *nIDFirst*, *nIDLast*, i *nIDItem* w następujący sposób:

|nFlags|Interpretacja|
|------------|--------------------|
|MF_BYCOMMAND|Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli ustawiono MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W tym samym czasie funkcja usuwa zaznaczenie wszystkich innych elementów menu w skojarzonej grupy i czyści flagę typ radia elementu dla tych elementów. Zaznaczony element jest wyświetlany, za pomocą opcji przycisk (lub punktorów) mapy bitowej zamiast mapę bitową znacznik wyboru.

### <a name="example"></a>Przykład

  Zobacz przykład [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

##  <a name="cmenu"></a>  CMenu::CMenu

Tworzy puste menu i dołącza je do `CMenu` obiektu.

```
CMenu();
```

### <a name="remarks"></a>Uwagi

Menu nie zostanie utworzony, dopóki nie wywołać jedną z tworzenia lub załadować funkcje elementów członkowskich `CMenu:`

- [CreateMenu —](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Attach](#attach)

##  <a name="createmenu"></a>  CMenu::CreateMenu

Tworzy menu i dołącza je do `CMenu` obiektu.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli menu został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Menu jest początkowo pusta. Można dodać elementów menu za pomocą `AppendMenu` lub `InsertMenu` funkcja elementu członkowskiego.

Jeśli menu jest przypisany do okna, automatycznie jest niszczony kiedy niszczony jest okna.

Przed zakończeniem pracy, aplikacja musi zwolnić zasobów systemowych, które skojarzone z menu, jeśli menu nie jest przypisana do okna. Menu dzięki aplikacjom, wywołując [DestroyMenu](#destroymenu) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

##  <a name="createpopupmenu"></a>  CMenu::CreatePopupMenu

Tworzy menu podręczne i dołącza je do `CMenu` obiektu.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli w menu podręcznym został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Menu jest początkowo pusta. Można dodać elementów menu za pomocą `AppendMenu` lub `InsertMenu` funkcja elementu członkowskiego. Aplikację można dodać wyskakujących menu do istniejącego menu lub menu podręcznego. `TrackPopupMenu` Funkcji składowej może służyć do wyświetlania tego menu jako menu podręcznego zmiennoprzecinkowe i śledzić zaznaczeń w menu podręcznym.

Jeśli menu jest przypisany do okna, automatycznie jest niszczony kiedy niszczony jest okna. Jeśli menu jest dodawany do istniejącego menu, automatycznie jest niszczony kiedy niszczony jest menu.

Przed zakończeniem pracy, aplikacja musi zwolnić zasobów systemowych, które skojarzone z menu podręcznym Jeśli menu nie jest przypisany do okna. Menu dzięki aplikacjom, wywołując [DestroyMenu](#destroymenu) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::CreateMenu](#createmenu).

##  <a name="deletemenu"></a>  CMenu::DeleteMenu

Usuwa element z menu.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nPosition*<br/>
Określa, że element menu, który ma zostać usunięty, zgodnie z ustaleniami *nFlags*.

*nFlags*<br/>
Służy do interpretowania *Npozycji* w następujący sposób:

|nFlags|Interpretacja pozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli ustawiono MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli element menu ma skojarzone menu podręcznego `DeleteMenu` niszczy dojścia do menu podręczne i zwalnia pamięć używana przez menu podręcznego.

W przypadku, gdy menu, które znajdują się w oknie zostanie zmieniony (czy okno jest wyświetlane), aplikacja musi wywołać [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="deletetempmap"></a>  CMenu::DeleteTempMap

Wywołuje się, automatycznie przez `CWinApp` obsługi czas bezczynności (%), usuwa wszystkie tymczasowe `CMenu` obiekty utworzone przez [FromHandle](#fromhandle) funkcja elementu członkowskiego.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Uwagi

`DeleteTempMap` Odłącza obiekt menu Windows dołączona do tymczasowej `CMenu` obiekt przed usunięciem `CMenu` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

##  <a name="destroymenu"></a>  CMenu::DestroyMenu

Niszczy menu i wszystkich zasobów Windows, które były używane.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli jest niszczony, menu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Menu jest odłączony od `CMenu` obiektu, zanim został zniszczony. Windows `DestroyMenu` funkcja jest wywoływana automatycznie `CMenu` destruktora.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::CreateMenu](#createmenu).

##  <a name="detach"></a>  CMenu::Detach

Odłącza Windows menu `CMenu` obiektu i zwraca uchwyt.

```
HMENU Detach();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do typu HMENU, menu Windows, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

`m_hMenu` Element członkowski danych ma wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="drawitem"></a>  CMenu::DrawItem

Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt zmiany rysowanych przez właściciela menu.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturę, która zawiera informacje o typie rysowania wymagane.

### <a name="remarks"></a>Uwagi

`itemAction` Członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane. Zastąpienie tej funkcji elementu członkowskiego do zaimplementowania rysunku do rysowania przez właściciela `CMenu` obiektu. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interface (GDI), wybrany dla kontekstu wyświetlana podana w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

Zobacz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) opis `DRAWITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

Następujący kod pochodzi z MFC [CTRLTEST](../../overview/visual-cpp-samples.md) próbki:

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

##  <a name="enablemenuitem"></a>  CMenu::EnableMenuItem

Włącza, wyłącza lub wygasza elementu menu.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Parametry

*nIDEnableItem*<br/>
Określa, że element menu, można włączyć, zgodnie z ustaleniami *nEnable*. Ten parametr można określić elementów menu podręcznym, a także elementów menu standardowego.

*nEnable*<br/>
Określa akcję do wykonania. Może być kombinacją MF_DISABLED, MF_ENABLED lub MF_GRAYED MF_BYCOMMAND lub MF_BYPOSITION. Wartości te można łączyć przy użyciu bitowego operatora OR. Te wartości mają następujące znaczenie:

- MF_BYCOMMAND Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Domyślnie włączone.

- MF_BYPOSITION Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.

- MF_DISABLED wyłącza elementu menu, tak aby nie można wybrać, ale nie przyciemniaj.

- MF_ENABLED umożliwia elementu menu, który można wybrać i przywraca je ze stanu wygaszone.

- Tak, aby nie można wybrać i wygasza go MF_GRAYED powoduje wyłączenie elementu menu.

### <a name="return-value"></a>Wartość zwracana

Poprzedni stan (MF_DISABLED, MF_ENABLED lub MF_GRAYED) lub -1, jeśli nie jest prawidłowy.

### <a name="remarks"></a>Uwagi

[CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu), i [LoadMenuIndirect](#loadmenuindirect) funkcje Członkowskie można również ustawić stan (włączona, wyłączone lub wyszarzony) elementu menu.

Przy użyciu wartości MF_BYPOSITION wymaga od aplikacji do korzystania z prawidłowych `CMenu`. Jeśli `CMenu` menu pasek jest używany, ma to wpływ na element menu najwyższego poziomu (element na pasku menu). Aby ustawić stan elementu wyskakującego lub zagnieżdżone menu podręczne według położenia, należy określić aplikację `CMenu` z menu podręcznego.

Gdy aplikacja określa flagi MF_BYCOMMAND Windows sprawdza, czy wszystkie elementy menu podręczne, które są podrzędne w stosunku do `CMenu`; w związku z tym, o ile nie występują zduplikowane elementy przy użyciu `CMenu` menu pasek jest wystarczająca.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

##  <a name="fromhandle"></a>  CMenu::FromHandle

Zwraca wskaźnik do `CMenu` obiektu, biorąc pod uwagę jego uchwyt Windows do menu.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Windows dojścia do menu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMenu` może to być tymczasowy lub stały.

### <a name="remarks"></a>Uwagi

Jeśli `CMenu` obiekt nie jest już dołączony do obiektu Windows menu tymczasowego `CMenu` obiekt zostanie utworzony i dołączony.

Ten tymczasowy `CMenu` obiektu jest prawidłowa tylko dopóki aplikacja ma czas bezczynności w jego pętlę zdarzeń, które zostaną usunięte wszystkie obiekty tymczasowe.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::CreateMenu](#createmenu).

##  <a name="getdefaultitem"></a>  CMenu::GetDefaultItem

Określa domyślny element menu z menu.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*gmdiFlags*<br/>
Wartość określająca sposób funkcji wyszukiwania elementów menu. Ten parametr może być brak, jeden lub kombinacją następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Określa, że jeśli element domyślny jest taki, który spowoduje otwarcie podmenu, funkcja jest wyszukiwanie w odpowiedniej rekursywnie podmenu. Jeśli podmenu zawiera żadnego elementu domyślną, wartość zwracana identyfikuje element, który spowoduje otwarcie podmenu.<br /><br /> Domyślnie funkcja zwraca pierwszy element domyślny menu określonego, niezależnie od tego, czy jest elementu, który spowoduje otwarcie podmenu.|
|GMDI_USEDISABLED|Określa, że funkcja ta jest zwracać element domyślny, nawet jeśli jest ono wyłączone.<br /><br /> Domyślnie funkcja pomija elementy wyłączone lub wygaszone.|

*fByPos*<br/>
Wartość określająca, czy można pobrać identyfikatora elementu menu lub położenia. Jeśli ten parametr ma wartość FALSE, zwracana jest identyfikator. W przeciwnym wypadku zwracana pozycja.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest identyfikatora lub położenie elementu menu. Jeśli funkcja zawiedzie, wartość zwracana jest - 1.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie funkcji Win32 [GetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-getmenudefaultitem), zgodnie z opisem w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

##  <a name="getmenucontexthelpid"></a>  CMenu::GetMenuContextHelpId

Pobiera pomocy kontekstowej identyfikator skojarzony z `CMenu`.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Wartość zwracana

Pomoc kontekstowa identyfikator aktualnie skojarzone z `CMenu` Jeśli istnieje; w przeciwnym razie zero.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

##  <a name="getmenuinfo"></a>  CMenu::GetMenuInfo

Pobiera informacje o menu.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Parametry

*lpcmi*<br/>
Wskaźnik do [MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo) struktury zawierający informacje do menu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest wartość różną od zera; w przeciwnym razie wartość zwracana wynosi zero.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby pobrać informacje o menu.

##  <a name="getmenuitemcount"></a>  CMenu::GetMenuItemCount

Określa liczbę elementów w menu podręcznym lub najwyższego poziomu.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w menu, jeśli funkcja się powiedzie; w przeciwnym razie wartość-1.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="getmenuitemid"></a>  CMenu::GetMenuItemID

Uzyskuje identyfikator elementu menu dla elementu menu, znajdujący się w pozycji zdefiniowane przez *npos —*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Określa położenie (liczony od zera) elementu menu pobierania o identyfikatorze.

### <a name="return-value"></a>Wartość zwracana

Identyfikator elementu dla określonego elementu w menu podręcznym Jeśli funkcja się powiedzie. Jeśli określony element menu podręcznego (w przeciwieństwie do elementu w menu podręcznym), wartość zwracana jest wartość -1. Jeśli *npos —* odnosi się do elementu menu SEPARATOR wartość zwracana to 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

##  <a name="getmenuiteminfo"></a>  CMenu::GetMenuItemInfo

Pobiera informacje o elemencie menu.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Identyfikator lub położenie elementu menu, aby uzyskać informacje na. Znaczenie tego parametru jest zależny od wartości `ByPos`.

*lpMenuItemInfo*<br/>
Wskaźnik do [KOJARZĄCA](/windows/desktop/api/winuser/ns-winuser-tagmenuiteminfoa), zgodnie z opisem w zestawie SDK Windows, który zawiera informacje o menu.

*fByPos*<br/>
Wartość określająca znaczenie `nIDItem`. Domyślnie `ByPos` ma wartość FAŁSZ, co oznacza, że uItem jest identyfikatorem elementu menu. Jeśli `ByPos` nie jest ustawiona na wartość FALSE, oznacza to, położenie elementu menu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest wartość różną od zera. Jeśli funkcja zawiedzie, wartość zwracana wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, należy użyć funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360), zgodnie z opisem w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie funkcji Win32 [GetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-getmenuiteminfoa), zgodnie z opisem w zestawie Windows SDK. Należy pamiętać, że w implementacji MFC `GetMenuItemInfo`, nie należy używać dojścia do menu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

##  <a name="getmenustate"></a>  CMenu::GetMenuState

Zwraca stan podany element menu lub liczbę elementów w menu podręcznym.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Określa identyfikator elementu menu, zgodnie z ustaleniami *nFlags*.

*nFlags*<br/>
Określa rodzaj *nID*. Może to być jedna z następujących wartości:

- MF_BYCOMMAND Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Domyślnie włączone.

- MF_BYPOSITION Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.

### <a name="return-value"></a>Wartość zwracana

Wartość 0xFFFFFFFF, jeśli określony element nie istnieje. Jeśli *nId* menu podręczne identyfikuje znaczącym bajcie zawiera liczbę elementów w menu podręcznym, a mniej znaczący bajt flagi menu skojarzone z menu podręcznego. W przeciwnym razie zwracana jest wartość maski (wartość logiczna lub) wartości z poniższej listy (Ta maska opisuje stan menu elementu *nId* identyfikuje):

- Działa MF_CHECKED jako przełącznik z MF_UNCHECKED umieścić domyślnie sprawdź znacznik obok elementu. Jeśli aplikacja dostarcza mapy bitowe znacznik wyboru (zobacz `SetMenuItemBitmaps` składowa), mapa bitowa "znacznik wyboru na" jest wyświetlana.

- MF_DISABLED wyłącza elementu menu, tak aby nie można wybrać, ale nie przyciemniaj.

- MF_ENABLED umożliwia elementu menu, który można wybrać i przywraca je ze stanu wygaszone. Należy pamiętać, że wartość tej stałej wynosi 0; Aplikacja nie należy przetestować względem 0 w przypadku awarii, korzystając z tej wartości.

- Tak, aby nie można wybrać i wygasza go MF_GRAYED powoduje wyłączenie elementu menu.

- MF_MENUBARBREAK umieszcza elementu w nowym wierszu, w menu statyczne lub w nowej kolumnie w menu podręcznym. Nowa kolumna menu podręcznego będą oddzielone od starego kolumny pionowa linia podziału.

- MF_MENUBREAK umieszcza elementu w nowym wierszu, w menu statyczne lub w nowej kolumnie w menu podręcznym. Nie linii podziału jest umieszczany między kolumnami.

- MF_SEPARATOR rysuje poziomej linii podziału. Należy używać tylko w menu podręcznym. Ten wiersz nie wygaszone, wyłączone lub wyróżnione. Inne parametry są ignorowane.

- MF_UNCHECKED działa jako przełącznik z MF_CHECKED, aby usunąć znacznik wyboru obok elementu. Jeśli aplikacja dostarcza mapy bitowe znacznik wyboru (zobacz `SetMenuItemBitmaps` składowa), mapa bitowa "znacznik wyboru off" jest wyświetlana. Należy pamiętać, że wartość tej stałej wynosi 0; Aplikacja nie należy przetestować względem 0 w przypadku awarii, korzystając z tej wartości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

##  <a name="getmenustring"></a>  CMenu::GetMenuString

Kopiuje etykietę elementu menu określony do określonego bufora.

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

*nIDItem*<br/>
Określa identyfikator całkowitą elementu menu lub przesunięcie element menu w menu, w zależności od wartości *nFlags*.

*lpString*<br/>
Wskazuje buforu, który ma otrzymać etykietę.

*rString*<br/>
Odwołanie do `CString` obiektu, który ma otrzymać ciąg skopiowany menu.

*nMaxCount*<br/>
Określa maksymalną długość (w znakach) etykiety, która ma być skopiowany. Jeśli etykieta jest dłuższy niż maksimum określone w *nMaxCount*, dodatkowe znaki są obcinane.

*nFlags*<br/>
Określa interpretacji *nIDItem* parametru. Może to być jedna z następujących wartości:

|nFlags|Interpretacja nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli ustawiono MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

### <a name="return-value"></a>Wartość zwracana

Określa rzeczywista liczba znaków skopiowane do buforu, nie wliczając terminator o wartości null.

### <a name="remarks"></a>Uwagi

*NMaxCount* parametr powinien być jeden większa niż liczba znaków w etykiecie, aby uwzględnić znak null, który kończy ciąg.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

##  <a name="getsafehmenu"></a>  CMenu::GetSafeHmenu

Zwraca HMENU owinięty przez ten `CMenu` obiekt lub wartość NULL`CMenu` wskaźnika.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::LoadMenu](#loadmenu).

##  <a name="getsubmenu"></a>  CMenu::GetSubMenu

Pobiera `CMenu` obiekt menu podręcznego.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Określa położenie menu podręcznego znajdujących się w menu. Wartości pozycji rozpoczynają się od 0 do pierwszego elementu menu. Identyfikator menu podręcznego nie można użyć tej funkcji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CMenu` którego `m_hMenu` elementu członkowskiego zawiera dojście do menu podręcznym istnienia wyskakujących menu na pozycji; w przeciwnym razie wartość NULL. Jeśli `CMenu` obiekt nie istnieje, a następnie tymczasowy zostanie utworzony. `CMenu` Zwrócony wskaźnik nie powinien być przechowywany.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::TrackPopupMenu](#trackpopupmenu).

##  <a name="insertmenu"></a>  CMenu::InsertMenu

Wstawia nowy element menu na pozycji określonej przez *Npozycji* i inne elementy są przenoszone w dół menu.

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

*nPosition*<br/>
Określa, że element menu, przed którym ma zostać wstawiony nowy element menu. *NFlags* parametru może służyć do interpretacji *Npozycji* w następujący sposób:

|nFlags|Interpretacja pozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli ustawiono MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0. Jeśli *Npozycji* wynosi -1, nowy element menu jest dołączany na końcu elementu menu.|

*nFlags*<br/>
Określa, jak *Npozycji* interpretowany i określa informacje o stanie Nowy element menu, gdy zostanie dodany do menu. Aby uzyskać listę flag, które mogą zostać ustawione, zobacz [AppendMenu zawsze](#appendmenu) funkcja elementu członkowskiego. Aby określić więcej niż jedną wartość, należy użyć bitowy operator OR połączyć je z flagą MF_BYCOMMAND lub MF_BYPOSITION.

*nIDNewItem*<br/>
Określa identyfikator polecenia nowego elementu menu lub, jeśli *nFlags* jest ustawiona na MF_POPUP, uchwyt menu (HMENU) z menu podręcznego. *NIDNewItem* parametr jest ignorowany (nie jest wymagany), jeśli *nFlags* jest ustawiona na MF_SEPARATOR.

*lpszNewItem*<br/>
Określa zawartość nowego elementu menu. *nFlags* może służyć do interpretacji *lpszNewItem* w następujący sposób:

|nFlags|Interpretacja lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Zawiera wartość 32-bitowa aplikacja dostarczona używanego przez aplikację do obsługi dodatkowych danych skojarzone z elementem menu. Ta wartość 32-bitowych jest dostępny do aplikacji w `itemData` elementu członkowskiego struktury dostarczonych przez [WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem) i [WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem) wiadomości. Te komunikaty są wysyłane, gdy element menu są początkowo wyświetlane lub zostanie zmieniony.|
|MF_STRING|Zawiera wskaźnik długi ciąg znaków zakończony znakiem null. Jest to domyślna interpretacja.|
|MF_SEPARATOR|*LpszNewItem* parametr jest ignorowany (nie jest wymagane).|

*pBmp*<br/>
Wskazuje `CBitmap` obiekt, który będzie używany jako element menu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja może określić stanu elementu menu przez ustawienie wartości w *nFlags*.

W przypadku, gdy menu, które znajdują się w oknie zostanie zmieniony (czy okno jest wyświetlane), aplikacja powinna wywołać `CWnd::DrawMenuBar`.

Gdy *nIDNewItem* Określa menu podręczne staje się częścią menu, w którym zostanie on włożony. Jeśli menu jest niszczony, wstawiono menu również zostaną zniszczone. Wstawiono menu powinna być odłączona od `CMenu` obiektu, aby uniknąć konfliktu.

Jeśli aktywny, który jest zmaksymalizowane okna podrzędnego interfejsu (MDI) w usłudze wielu dokumentów i aplikacja wstawia menu podręczne w menu aplikacji MDI przez wywołanie tej funkcji i określić flagę MF_BYPOSITION menu jest wstawiany jedną pozycję dalej po lewej niż Oczekiwano. Dzieje się tak, ponieważ menu kontroli aktywne okno podrzędne MDI znajduje się na pierwszym miejscu paska menu okna ramki MDI. Aby prawidłowo położenie menu, aplikacja dodać 1 wartość pozycji, które będzie używane. Aplikacja może użyć komunikat WM_MDIGETACTIVE, aby ustalić, czy jest zmaksymalizowane okno podrzędne aktualnie aktywny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

##  <a name="insertmenuitem"></a>  CMenu::InsertMenuItem

Wstawia nowy element menu na pozycji określonej w menu.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Zobacz opis *uItem* w [InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema) w zestawie Windows SDK.

*lpMenuItemInfo*<br/>
Zobacz opis *lpmii* w `InsertMenuItem` w zestawie Windows SDK.

*fByPos*<br/>
Zobacz opis *fByPosition* w `InsertMenuItem` w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zawijany [InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema), które zostały opisane w zestawie Windows SDK.

##  <a name="loadmenu"></a>  CMenu::LoadMenu

Ładuje zasobów menu z pliku wykonywalnego aplikacji i dołącza go do `CMenu` obiektu.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskazuje ciąg zakończony wartością null zawierający nazwę zasobu menu, aby załadować.

*nIDResource*<br/>
Określa identyfikator menu zasób menu do załadowania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zasób menu został załadowany pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przed zakończeniem pracy, aplikacja musi zwolnić zasobów systemowych, które skojarzone z menu, jeśli menu nie jest przypisana do okna. Menu dzięki aplikacjom, wywołując [DestroyMenu](#destroymenu) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

##  <a name="loadmenuindirect"></a>  CMenu::LoadMenuIndirect

Ładuje zasobu z szablonem menu w pamięci i dołącza go do `CMenu` obiektu.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Parametry

*lpMenuTemplate*<br/>
Wskazuje na szablon menu (czyli jeden [MENUITEMTEMPLATEHEADER](/windows/desktop/api/winuser/ns-winuser-menuitemtemplateheader) struktury i kolekcji, co najmniej jednego [MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate) struktury). Aby uzyskać więcej informacji na temat tych dwóch struktur zobacz zestaw Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zasób menu został załadowany pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Szablon menu jest nagłówkiem, następuje kolekcji jednego lub więcej [MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate) struktur, z których każdy może zawierać jeden lub więcej elementów menu, jak i wyskakujących menu.

Numer wersji powinna być równa 0.

`mtOption` Flag powinny zawierać MF_END dla ostatniego elementu na liście podręczne i ostatni element na liście głównych. Zobacz `AppendMenu` funkcję członkowską inne flagi. `mtId` Elementu członkowskiego musi zostać pominięty ze struktury MENUITEMTEMPLATE, gdy MF_POPUP jest określona w `mtOption`.

Ilość miejsca przydzielonego dla struktury MENUITEMTEMPLATE musi być wystarczająco duży dla `mtString` zawierać nazwy elementu menu jako ciąg znaków zakończony znakiem null.

Przed zakończeniem pracy, aplikacja musi zwolnić zasobów systemowych, które skojarzone z menu, jeśli menu nie jest przypisana do okna. Menu dzięki aplikacjom, wywołując [DestroyMenu](#destroymenu) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

##  <a name="m_hmenu"></a>  CMenu::m_hMenu

Określa uchwyt HMENU dołączonym do menu Windows `CMenu` obiektu.

```
HMENU m_hMenu;
```

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::LoadMenu](#loadmenu).

##  <a name="measureitem"></a>  CMenu::MeasureItem

Wywoływane przez platformę, gdy zostanie utworzony przy użyciu stylu rysowania przez właściciela menu.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Wskaźnik do `MEASUREITEMSTRUCT` struktury.

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpienie tej funkcji elementu członkowskiego, a następnie wypełnij `MEASUREITEMSTRUCT` strukturę, aby poinformować Windows menu wymiarów.

Zobacz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) opis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

Następujący kod pochodzi z MFC [CTRLTEST](../../overview/visual-cpp-samples.md) próbki:

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

##  <a name="modifymenu"></a>  CMenu::ModifyMenu

Zmienia istniejący element menu na pozycji określonej przez *Npozycji*.

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

*nPosition*<br/>
Określa element menu, które mają być zmienione. *NFlags* parametru może służyć do interpretacji *Npozycji* w następujący sposób:

|nFlags|Interpretacja pozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli ustawiono MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

*nFlags*<br/>
Określa, jak *Npozycji* interpretowany i udostępnia informacje o zmianach wprowadzonych do elementu menu. Aby uzyskać listę flag, które mogą być ustawione, zobacz [AppendMenu zawsze](#appendmenu) funkcja elementu członkowskiego.

*nIDNewItem*<br/>
Określa identyfikator polecenia elementu menu zmodyfikowany lub jeśli *nFlags* jest ustawiona na MF_POPUP, uchwyt menu (HMENU) z menu podręcznego. *NIDNewItem* parametr jest ignorowany (nie jest wymagany), jeśli *nFlags* jest ustawiona na MF_SEPARATOR.

*lpszNewItem*<br/>
Określa zawartość nowego elementu menu. *NFlags* parametru może służyć do interpretacji *lpszNewItem* w następujący sposób:

|nFlags|Interpretacja lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Zawiera wartość 32-bitowa aplikacja dostarczona używanego przez aplikację do obsługi dodatkowych danych skojarzone z elementem menu. Ta wartość 32-bitowych jest dostępne dla aplikacji, podczas przetwarzania MF_MEASUREITEM i MF_DRAWITEM.|
|MF_STRING|Zawiera wskaźnik długi ciąg zakończony wartością null lub do `CString`.|
|MF_SEPARATOR|*LpszNewItem* parametr jest ignorowany (nie jest wymagane).|

*pBmp*<br/>
Wskazuje `CBitmap` obiekt, który będzie używany jako element menu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja Określa nowy stan elementu menu, ustawiając wartości w *nFlags*. Jeśli ta funkcja zastępuje menu podręcznego skojarzone z elementem menu, niszczy stare menu podręczne i zwalnia pamięć używana przez menu podręcznego.

Gdy *nIDNewItem* Określa menu podręczne staje się częścią menu, w którym zostanie on włożony. Jeśli menu jest niszczony, wstawiono menu również zostaną zniszczone. Wstawiono menu powinna być odłączona od `CMenu` obiektu, aby uniknąć konfliktu.

W przypadku, gdy menu, które znajdują się w oknie zostanie zmieniony (czy okno jest wyświetlane), aplikacja powinna wywołać `CWnd::DrawMenuBar`. Do zmiany atrybutów istniejących elementów menu, jest znacznie szybszy, aby użyć `CheckMenuItem` i `EnableMenuItem` funkcji elementów członkowskich.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

##  <a name="operator_hmenu"></a>  CMenu::operator HMENU

Użyj tego operatora, można pobrać dojście `CMenu` obiektu.

```
operator HMENU() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, uchwyt `CMenu` obiektu; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Dojście służy do wywoływania interfejsów API Windows bezpośrednio.

##  <a name="operator_neq"></a>  CMenu::operator! =

Określa, czy dwa menu logicznie nie są równe.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*Menu*<br/>
A `CMenu` obiekt do porównania.

### <a name="remarks"></a>Uwagi

Sprawdza, czy obiekt menu po lewej stronie nie jest równy obiektowi menu po prawej stronie.

##  <a name="operator_eq_eq"></a>  CMenu::operator ==

Określa, czy dwa menu są logicznie równe.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Parametry

*Menu*<br/>
A `CMenu` obiekt do porównania.

### <a name="remarks"></a>Uwagi

Sprawdza, czy obiekt menu po lewej stronie jest równe (w postaci liczby wartości HMENU) obiekt menu po prawej stronie.

##  <a name="removemenu"></a>  CMenu::RemoveMenu

Usuwa element menu za pomocą skojarzonego menu wyskakujących menu.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

*nPosition*<br/>
Określa, że element menu do usunięcia. *NFlags* parametru może służyć do interpretacji *Npozycji* w następujący sposób:

|nFlags|Interpretacja pozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli ustawiono MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

*nFlags*<br/>
Określa, jak *Npozycji* jest interpretowany.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Niszczy uchwytu menu podręczne, dzięki czemu mogą być ponownie używane menu. Przed wywołaniem tej funkcji, aplikacja może wywołać `GetSubMenu` funkcję elementu członkowskiego, aby pobrać oknie podręcznym `CMenu` obiektu do ponownego wykorzystania.

W przypadku, gdy menu, które znajdują się w oknie zostanie zmieniony (czy okno jest wyświetlane), aplikacja musi wywołać `CWnd::DrawMenuBar`.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

##  <a name="setdefaultitem"></a>  CMenu::SetDefaultItem

Ustawia domyślny element menu dla określonego menu.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Identyfikator lub pozycję nowy domyślny element menu lub - 1 dla nie element domyślny. Znaczenie tego parametru jest zależny od wartości *fByPos*.

*fByPos*<br/>
Wartość określająca znaczenie *uItem*. Jeśli ten parametr ma wartość FALSE, *uItem* jest identyfikatorem elementu menu. W przeciwnym razie jest położenie elementu menu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest wartość różną od zera. Jeśli funkcja zawiedzie, wartość zwracana wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, należy użyć funkcji Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360), zgodnie z opisem w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie funkcji Win32 [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem), zgodnie z opisem w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

##  <a name="setmenucontexthelpid"></a>  CMenu::SetMenuContextHelpId

Kojarzy identyfikator kontekstu pomocy przy użyciu `CMenu`.

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Parametry

*dwContextHelpId*<br/>
Identyfikator pomocy kontekstu do skojarzenia z `CMenu`.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wszystkie elementy menu Udostępnij ten identyfikator — nie jest możliwe, Dołącz identyfikator kontekstu pomocy do poszczególnych elementów menu.

### <a name="example"></a>Przykład

  Zobacz przykład [CMenu::InsertMenu](#insertmenu).

##  <a name="setmenuinfo"></a>  CMenu::SetMenuInfo

Ustawia informacje dotyczące menu.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Parametry

*lpcmi*<br/>
Wskaźnik do [MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo) struktury zawierający informacje do menu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest wartość różną od zera; w przeciwnym razie wartość zwracana wynosi zero.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby ustawić określone informacje na temat menu.

##  <a name="setmenuitembitmaps"></a>  CMenu::SetMenuItemBitmaps

Kojarzy określonego map bitowych przy użyciu elementu menu.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Parametry

*nPosition*<br/>
Określa element menu, które mają być zmienione. *NFlags* parametru może służyć do interpretacji *Npozycji* w następujący sposób:

|nFlags|Interpretacja pozycji|
|------------|---------------------------------|
|MF_BYCOMMAND|Określa, czy parametr zawiera identyfikator polecenia istniejącego elementu menu. Jest to wartość domyślna, jeśli ustawiono MF_BYCOMMAND ani MF_BYPOSITION.|
|MF_BYPOSITION|Określa, że parametr daje pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|

*nFlags*<br/>
Określa, jak *Npozycji* jest interpretowany.

*pBmpUnchecked*<br/>
Określa mapę bitową do użycia dla elementów menu, które nie są sprawdzane.

*pBmpChecked*<br/>
Określa mapę bitową do użycia dla elementów menu, które są sprawdzane.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Czy element menu jest zaznaczony lub niezaznaczony, Windows wyświetla odpowiednie mapy bitowej obok elementu menu.

Jeśli *pBmpUnchecked* lub *pBmpChecked* ma wartość NULL, następnie Windows wyświetla nic obok pozycji menu dla atrybutu. Jeśli oba parametry mają wartość NULL, Windows używa znacznik wyboru domyślnego, gdy element jest zaznaczone, a także usunięcie znacznika wyboru, gdy element nie jest zaznaczone.

Te mapy bitowe nie są niszczone, kiedy niszczony jest menu, Aplikacja musi zniszczyć je.

Windows `GetMenuCheckMarkDimensions` funkcja pobiera wymiary znacznik wyboru domyślne, które są używane na potrzeby elementów menu. Aplikacja używa tych wartości, aby określić odpowiedni rozmiar dla map bitowych dostarczane za pomocą tej funkcji. Pobieranie rozmiaru, utworzyć Twoje mapy bitowe, a następnie ustaw je.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

##  <a name="setmenuiteminfo"></a>  CMenu::SetMenuItemInfo

Zmienia informacje na temat elementu menu.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Parametry

*uItem*<br/>
Zobacz opis *uItem* w [SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa) w zestawie Windows SDK.

*lpMenuItemInfo*<br/>
Zobacz opis *lpmii* w `SetMenuItemInfo` w zestawie Windows SDK.

*fByPos*<br/>
Zobacz opis *fByPosition* w `SetMenuItemInfo` w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zawijany [SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa), które zostały opisane w zestawie Windows SDK.

##  <a name="trackpopupmenu"></a>  CMenu::TrackPopupMenu

Wyświetla menu podręczne przestawne w określonej lokalizacji i śledzi zaznaczenia elementów w menu podręcznym.

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>Parametry

*nFlags*<br/>
Określa flagi pozycja ekranu i położenie kursora. Zobacz [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) lista flagi dostępna.

*x*<br/>
Określa położenie menu podręczne w poziomie w współrzędne ekranu. W zależności od wartości *nFlags* parametr, menu może być wyrównany do lewej, do prawej lub do środka względem tej pozycji.

*y*<br/>
Określa położenie w pionie we współrzędnych ekranu górnej części menu na ekranie.

*pWnd*<br/>
Identyfikuje okna, który jest właścicielem menu podręcznego. Ten parametr nie może być NULL, nawet jeśli określono flagę TPM_NONOTIFY. W tym oknie odbiera wszystkie komunikaty WM_COMMAND z menu. Windows w wersji 3.1 lub nowszej, okno nie otrzymują wm_command — komunikaty do momentu `TrackPopupMenu` zwraca. 3.0 Windows okna odbiera komunikaty WM_COMMAND przed `TrackPopupMenu` zwraca.

*lpRect*<br/>
Ignorowane.

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wynik wywołania metody [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Zmiennoprzecinkowe menu podręcznego może występować w dowolnym miejscu na ekranie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

##  <a name="trackpopupmenuex"></a>  CMenu::TrackPopupMenuEx

Wyświetla menu podręczne przestawne w określonej lokalizacji i śledzi zaznaczenia elementów w menu podręcznym.

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
Określa różne funkcje dla rozszerzonych menu. Aby uzyskać listę wszystkich wartości i ich znaczenie, zobacz [TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex).

*x*<br/>
Określa położenie menu podręczne w poziomie w współrzędne ekranu.

*y*<br/>
Określa położenie w pionie we współrzędnych ekranu górnej części menu na ekranie.

*pWnd*<br/>
Wskaźnik do okna będącej właścicielem menu podręczne i odbieranie komunikatów z menu utworzony. To okno może być dowolnym oknie z bieżącej aplikacji, ale nie może mieć wartości NULL. Jeśli określisz TPM_NONOTIFY w *fuFlags* parametru funkcji nie wysyła żadnych komunikatów do *pWnd*. Funkcja musi zwracać okna wskazywany przez *pWnd* do odbierania komunikatów WM_COMMAND.

*lptpm*<br/>
Wskaźnik do [TPMPARAMS](/windows/desktop/api/winuser/ns-winuser-tagtpmparams) struktury, który określa obszar ekranu menu nie powinny się nakładać. Ten parametr może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Jeśli określisz TPM_RETURNCMD w *fuFlags* parametr, wartość zwracana jest identyfikator elementu menu elementu, który użytkownik zaznaczył. Jeśli użytkownik anuluje menu bez dokonywania wyboru lub jeśli wystąpi błąd, wartość zwracana to 0.

Jeśli nie określisz TPM_RETURNCMD w *fuFlags* parametr, wartość zwracana jest wartość różną od zera, jeśli funkcja się powiedzie, a 0 Jeśli zakończy się niepowodzeniem. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Uwagi

Zmiennoprzecinkowe menu podręcznego może występować w dowolnym miejscu na ekranie. Aby uzyskać więcej informacji na temat obsługi błędów podczas tworzenia menu podręcznego, zobacz [TrackPopupMenuEx](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Zobacz także

[Próbki MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)
