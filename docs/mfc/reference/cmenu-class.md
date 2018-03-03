---
title: "Cmenu — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 104c965da403040308386e019d56684577318eee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmenu-class"></a>Cmenu — klasa
Hermetyzacja systemu Windows `HMENU`.  
  
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
|[CMenu::AppendMenu](#appendmenu)|Dołącza nowy element na końcu tego menu.|  
|[CMenu::Attach](#attach)|Dołącza dojścia menu systemu Windows do `CMenu` obiektu.|  
|[CMenu::CheckMenuItem](#checkmenuitem)|Umieszcza pole wyboru obok pozycji lub usuwa znacznik wyboru z elementu menu, w menu podręcznym.|  
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Umieszcza przycisk radiowy obok elementu menu i usuwa przycisk radiowy ze wszystkich innych elementów menu w grupie.|  
|[CMenu::CreateMenu](#createmenu)|Tworzy puste menu i dołącza go do `CMenu` obiektu.|  
|[CMenu::CreatePopupMenu](#createpopupmenu)|Tworzy pusty wyskakującym menu i dołącza go do `CMenu` obiektu.|  
|[CMenu::DeleteMenu](#deletemenu)|Usuwa określony element z menu. Jeśli element menu ma skojarzone menu podręczne, niszczy dojścia do menu podręcznego i zwalnia pamięć używana przez nią.|  
|[CMenu::DeleteTempMap](#deletetempmap)|Usuwa wszystkie tymczasowe `CMenu` obiekty utworzone przez `FromHandle` funkcję elementu członkowskiego.|  
|[CMenu::DestroyMenu](#destroymenu)|Niszczy menu dołączony do `CMenu` obiektu i zwalnia wszystkie pamięci, która zajęty menu.|  
|[CMenu::Detach](#detach)|Odłącza dojścia menu systemu Windows z `CMenu` obiektu i zwraca dojście.|  
|[CMenu::DrawItem](#drawitem)|Wywoływane przez platformę, gdy visual aspekt zmiany rysowanych przez właściciela menu.|  
|[CMenu::EnableMenuItem](#enablemenuitem)|Włącza, wyłącza lub wygasza (szarości) elementu menu.|  
|[CMenu::FromHandle](#fromhandle)|Zwraca wskaźnik do `CMenu` obiektu podane dojście menu systemu Windows.|  
|[CMenu::GetDefaultItem](#getdefaultitem)|Określa domyślny element menu z menu.|  
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Pobiera identyfikator kontekstu Pomocy skojarzone z menu.|  
|[CMenu::GetMenuInfo](#getmenuinfo)|Pobiera informacje o określonym menu.|  
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Określa liczbę elementów w menu podręczne lub najwyższego poziomu.|  
|[CMenu::GetMenuItemID](#getmenuitemid)|Uzyskuje identyfikator elementu menu dla elementu menu znajdującym się w określonej pozycji.|  
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Pobiera informacje o elemencie menu.|  
|[CMenu::GetMenuState](#getmenustate)|Zwraca informacje o stanie podany element menu lub liczba elementów w menu podręcznym.|  
|[CMenu::GetMenuString](#getmenustring)|Pobiera etykietę podany element menu.|  
|[CMenu::GetSafeHmenu](#getsafehmenu)|Zwraca `m_hMenu` opakowane przez to `CMenu` obiektu.|  
|[CMenu::GetSubMenu](#getsubmenu)|Pobiera wskaźnik do menu podręczne.|  
|[CMenu::InsertMenu](#insertmenu)|Wstawia nowy element menu na określonej pozycji, przenoszenie innych elementów menu w dół.|  
|[CMenu::InsertMenuItem](#insertmenuitem)|Wstawia nowy element menu na określonej pozycji w menu.|  
|[CMenu::LoadMenu](#loadmenu)|Ładuje menu zasobu z pliku wykonywalnego i dołącza go do `CMenu` obiektu.|  
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Ładuje menu z menu szablonu w pamięci i dołącza go do `CMenu` obiektu.|  
|[CMenu::MeasureItem](#measureitem)|Wywoływane przez platformę, aby określić wymiary menu po utworzeniu rysowanych przez właściciela menu.|  
|[CMenu::ModifyMenu](#modifymenu)|Zmienia istniejący element menu na określonej pozycji.|  
|[CMenu::RemoveMenu](#removemenu)|Usuwa element menu z menu podręcznego skojarzony z określonym menu.|  
|[CMenu::SetDefaultItem](#setdefaultitem)|Ustawia domyślny element menu dla menu określony.|  
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Określa identyfikator kontekstu pomocy ma zostać skojarzony z menu.|  
|[CMenu::SetMenuInfo](#setmenuinfo)|Ustawia informacje o określonym menu.|  
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Kojarzy map bitowych znacznik wyboru z elementu menu.|  
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Zmienia informacje o elemencie menu.|  
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Wyświetla menu podręczne przestawne w określonej lokalizacji i śledzi zaznaczenia elementów w menu podręcznym.|  
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Wyświetla menu podręczne przestawne w określonej lokalizacji i śledzi zaznaczenia elementów w menu podręcznym.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMenu::operator HMENU](#operator_hmenu)|Pobiera uchwyt obiektu menu.|  
|[CMenu::operator! =](#operator_neq)|Określa, czy dwa obiekty menu nie są takie same.|  
|[CMenu::operator ==](#operator_eq_eq)|Określa, czy dwa obiekty menu są równe.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMenu::m_hMenu](#m_hmenu)|Określa dojście do menu systemu Windows dołączona do `CMenu` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Zapewnia funkcje elementów członkowskich do tworzenia śledzenia, aktualizowanie i niszczenie menu.  
  
 Utwórz `CMenu` obiektu w ramce stosu jako lokalnej, następnie wywołaj `CMenu`w funkcji elementów członkowskich do manipulowania nowego menu, zgodnie z potrzebami. Następnie wywołaj [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) ustawioną okna, menu bezpośrednio po wywołaniu `CMenu` obiektu [Detach](#detach) funkcję elementu członkowskiego. `CWnd::SetMenu` Funkcji członkowskiej ustawienie menu okna nowego menu, powoduje, że okno, aby być narysowany ponownie, aby odzwierciedlić zmianę menu, a także przekazuje własność menu do okna. Wywołanie **Detach** odłącza `HMENU` z `CMenu` obiektu, tak że w przypadku lokalnego `CMenu` zmienna jest przekazywana poza zakresem, `CMenu` destruktor obiektu nie jest podejmowana próba zniszczyć menu go nie już jest właścicielem. Samo menu zostanie zniszczony automatycznie, gdy okno zostanie zniszczone.  
  
 Można użyć [LoadMenuIndirect](#loadmenuindirect) funkcji członkowskiej, aby utworzyć menu z szablonu w pamięci, ale menu utworzone na podstawie zasobu przez wywołanie do [LoadMenu](#loadmenu) jest łatwiejsze zarządzanie i samego zasobu menu mogą być tworzone i modyfikowane przez Edytor menu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="appendmenu"></a>CMenu::AppendMenu  
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
 `nFlags`  
 Określa informacje o stanie Nowy element menu, gdy jest ona dodawana do menu. Składa się z co najmniej jedna z wartości na liście w sekcji uwag.  
  
 `nIDNewItem`  
 Określa identyfikator polecenia nowego elementu menu lub, jeśli `nFlags` ustawiono **MF_POPUP**, dojście menu ( `HMENU`) z menu podręcznego. `nIDNewItem` Parametr jest ignorowany (nie jest to wymagane), jeśli `nFlags` ustawiono **MF_SEPARATOR**.  
  
 `lpszNewItem`  
 Określa zawartość nowego elementu menu. `nFlags` Parametr jest używany do interpretowania `lpszNewItem` w następujący sposób:  
  
|nFlags|Interpretacja lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Zawiera dostarczone przez aplikację 32-bitową wartość używaną przez aplikację do obsługi dodatkowych danych skojarzone z elementem menu. Ta wartość 32-bitowych jest dostępne dla aplikacji, podczas przetwarzania `WM_MEASUREITEM` i `WM_DRAWITEM` wiadomości. Wartość jest przechowywana w **itemData** elementu członkowskiego struktury dostarczony wraz z tych wiadomości.|  
|**MF_STRING**|Zawiera wskaźnik ciąg znaków zakończony znakiem null. Jest to domyślnej interpretacji.|  
|**MF_SEPARATOR**|`lpszNewItem` Parametr jest ignorowany (nie wymagane).|  
  
 *pBmp*  
 Wskazuje `CBitmap` obiekt, który będzie używany jako element menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aplikację można określić stanu elementu menu przez ustawienie wartości `nFlags`. Gdy `nIDNewItem` Określa menu podręczne, staje się częścią menu, do której jest dołączony. Jeśli zostanie zniszczony tego menu, menu dołączany także zostaną usunięte. Dołączany menu należy odłączyć od `CMenu` obiekt, aby uniknąć konfliktu. Należy pamiętać, że **MF_STRING** i `MF_OWNERDRAW` nie są prawidłowe dla wersji mapy bitowej `AppendMenu`.  
  
 Poniższa lista zawiera flagi, które może być ustawiona w `nFlags`:  
  
- **MF_CHECKED** działa jak przełącznik z **MF_UNCHECKED** do domyślnego pole wyboru obok elementu. Gdy aplikacja udostępnia map bitowych znacznik wyboru (zobacz [SetMenuItemBitmaps](#setmenuitembitmaps) funkcji członkowskiej), "zaznaczone na" mapy bitowej jest wyświetlany.  
  
- **MF_UNCHECKED** działa jak przełącznik z **MF_CHECKED** Aby usunąć znacznik wyboru obok elementu. Gdy aplikacja udostępnia map bitowych znacznik wyboru (zobacz `SetMenuItemBitmaps` funkcji członkowskiej), jest wyświetlany mapy bitowej "znacznik wyboru off".  
  
- **MF_DISABLED** wyłącza element menu, tak aby nie można wybrać, ale nie dim.  
  
- `MF_ENABLED`Umożliwia element menu, który można wybrać i przywracania go ze stanu na wygaszone.  
  
- **MF_GRAYED** wyłącza element menu tak, aby nie można wybrać i wygasza go.  
  
- **MF_MENUBARBREAK** element zostanie umieszczone w nowym wierszu w menu statyczne lub w nowej kolumnie w menu podręcznym. Nowa kolumna menu podręczne będą oddzielone od starego kolumny pionowych linii podziału.  
  
- **MF_MENUBREAK** element zostanie umieszczone w nowym wierszu w menu statyczne lub w nowej kolumnie w menu podręcznym. Nie linii podziału jest umieszczana między kolumnami.  
  
- `MF_OWNERDRAW`Określa, czy element jest elementem rysowania przez właściciela. Menu wyświetlanym po raz pierwszy okna, który jest właścicielem menu odbiera `WM_MEASUREITEM` wiadomości, która pobiera wysokość i szerokość elementu menu. `WM_DRAWITEM` Komunikat jest wysyłany, gdy właściciel musi zaktualizować wygląd elementu menu. Ta opcja nie jest prawidłowa dla elementu menu najwyższego poziomu.  
  
- **MF_POPUP** Określa, czy element menu ma menu podręczne skojarzonych z nim. Parametr ID określa dojścia do menu podręczne, które ma być skojarzony z elementem. Służy do dodawania najwyższego poziomu menu podręczne lub hierarchiczne menu rozwijane do elementu menu podręcznego.  
  
- **MF_SEPARATOR** rysuje linię podziału poziomą. Można używać tylko w menu podręczne. Ten wiersz nie wygaszone, wyłączone lub wyróżnione. Inne parametry są ignorowane.  
  
- **MF_STRING** Określa, że element menu jest ciąg znaków.  
  
 Flagi, które wzajemnie się wykluczają i nie można jednocześnie używać każdego z następujących grup zawiera następujące informacje:  
  
- **MF_DISABLED**, `MF_ENABLED`, i **MF_GRAYED**  
  
- **MF_STRING**, `MF_OWNERDRAW`, **MF_SEPARATOR**i wersji mapy bitowej  
  
- **MF_MENUBARBREAK** i **MF_MENUBREAK**  
  
- **MF_CHECKED** i **MF_UNCHECKED**  
  
 W przypadku, gdy menu który znajduje się w oknie zostanie zmieniona (czy okno jest wyświetlane), aplikacja powinna wywołać [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::CreateMenu](#createmenu).  
  
##  <a name="attach"></a>CMenu::Attach  
 Dołącza do istniejącego menu systemu Windows `CMenu` obiektu.  
  
```  
BOOL Attach(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 `hMenu`  
 Określa dojścia do menu systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie powinna być wywoływana, gdy menu jest już dołączony do `CMenu` obiektu. Dojście menu są przechowywane w `m_hMenu` element członkowski danych.  
  
 Jeśli chcesz manipulowanie menu jest już skojarzony z oknem, możesz użyć [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) funkcji można uzyskać dojścia do menu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="checkmenuitem"></a>CMenu::CheckMenuItem  
 Dodaje znaczniki wyboru, aby lub usuwa znaczniki wyboru z elementów menu w menu podręcznym.  
  
```  
UINT CheckMenuItem(
    UINT nIDCheckItem,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDCheckItem`  
 Określa element menu, aby sprawdzić, zgodnie z ustaleniami `nCheck`.  
  
 `nCheck`  
 Określa, jak sprawdzić element menu oraz sposobu określania położenie elementu w menu. `nCheck` Parametr może być kombinacją **MF_CHECKED** lub **MF_UNCHECKED** z **MF_BYPOSITION** lub **MF_BYCOMMAND** flagi. Te flagi można łączyć przy użyciu bitowego operatora OR. Mają następujące znaczenie:  
  
- **MF_BYCOMMAND** Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Domyślnie włączone.  
  
- **MF_BYPOSITION** Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.  
  
- **MF_CHECKED** działa jak przełącznik z **MF_UNCHECKED** do domyślnego pole wyboru obok elementu.  
  
- **MF_UNCHECKED** działa jak przełącznik z **MF_CHECKED** Aby usunąć znacznik wyboru obok elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedni stan elementu: **MF_CHECKED** lub **MF_UNCHECKED**, lub 0xFFFFFFFF, jeśli nie istnieje element menu.  
  
### <a name="remarks"></a>Uwagi  
 `nIDCheckItem` Parametr określa, że element ma być zmodyfikowana.  
  
 `nIDCheckItem` Parametr może zidentyfikować elementu menu podręcznego, a także elementu menu. Nie specjalnych czynności do sprawdzenia elementu menu podręcznego. Nie można sprawdzić elementów menu najwyższego poziomu. Element menu wyskakującego muszą zostać sprawdzone według położenia, ponieważ nie ma identyfikatora elementu menu skojarzona.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::GetMenuState](#getmenustate).  
  
##  <a name="checkmenuradioitem"></a>CMenu::CheckMenuRadioItem  
 Sprawdza podany element menu i ułatwia elementu opcji.  
  
```  
BOOL CheckMenuRadioItem(
    UINT nIDFirst,  
    UINT nIDLast,  
    UINT nIDItem,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDFirst`  
 Określa (jako identyfikator lub przesunięcie, w zależności od wartości `nFlags`) pierwszego elementu menu w grupie przycisków radiowych.  
  
 `nIDLast`  
 Określa (jako identyfikator lub przesunięcie, w zależności od wartości `nFlags`) w grupie przycisków radiowych ostatniego elementu menu.  
  
 `nIDItem`  
 Określa (jako identyfikator lub przesunięcie, w zależności od wartości `nFlags`) element w grupie, która będzie sprawdzana z przycisku radiowego.  
  
 `nFlags`  
 Określa interpretacji `nIDFirst`, `nIDLast`, i `nIDItem` w następujący sposób:  
  
|nFlags|Interpretacja|  
|------------|--------------------|  
|**MF_BYCOMMAND**|Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Jeśli nie jest to domyślny **MF_BYCOMMAND** ani **MF_BYPOSITION** jest ustawiona.|  
|**MF_BYPOSITION**|Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0  
  
### <a name="remarks"></a>Uwagi  
 W tym samym czasie funkcja usuwa zaznaczenie wszystkich innych elementów menu w skojarzonych grup i usuwa flagę typ radia elementu dla tych elementów. Zaznaczony element jest wyświetlany przy użyciu opcji przycisku (lub punktor) mapę bitową zamiast mapę bitową znacznik wyboru.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [on_command_range —](message-map-macros-mfc.md#on_command_range).  
  
##  <a name="cmenu"></a>CMenu::CMenu  
 Tworzy puste menu i dołącza go do `CMenu` obiektu.  
  
```  
CMenu();
```  
  
### <a name="remarks"></a>Uwagi  
 Menu nie zostanie utworzony, dopóki nie należy wywołać funkcji Członkowskich create lub obciążenia z **cmenu —:**  
  
- [CreateMenu](#createmenu)  
  
- [CreatePopupMenu](#createpopupmenu)  
  
- [LoadMenu](#loadmenu)  
  
- [LoadMenuIndirect](#loadmenuindirect)  
  
- [Attach](#attach)  
  
##  <a name="createmenu"></a>CMenu::CreateMenu  
 Tworzy menu i dołącza go do `CMenu` obiektu.  
  
```  
BOOL CreateMenu();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli menu został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Menu jest początkowo pusta. Elementy menu można dodać za pomocą `AppendMenu` lub `InsertMenu` funkcję elementu członkowskiego.  
  
 Jeśli menu jest przypisany do okna, automatycznie zostanie zniszczony gdy okno zostanie zniszczone.  
  
 Przed zamknięciem, aplikacja musi zwolnić zasobów systemowych, skojarzone z menu, jeśli menu nie zostanie przypisany do okna. Menu dzięki aplikacjom wywołując [DestroyMenu](#destroymenu) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]  
  
##  <a name="createpopupmenu"></a>CMenu::CreatePopupMenu  
 Tworzy menu podręcznego i dołącza go do `CMenu` obiektu.  
  
```  
BOOL CreatePopupMenu();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pomyślnie utworzono menu podręcznego; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Menu jest początkowo pusta. Elementy menu można dodać za pomocą `AppendMenu` lub `InsertMenu` funkcję elementu członkowskiego. Aplikację można dodać menu podręczne do istniejącego menu lub menu podręczne. `TrackPopupMenu` Funkcji członkowskiej może służyć do wyświetlania tego menu jako przestawne menu podręcznego i śledzić zaznaczeń w menu podręcznym.  
  
 Jeśli menu jest przypisany do okna, automatycznie zostanie zniszczony gdy okno zostanie zniszczone. Jeśli menu zostanie dodany do istniejącego menu, automatycznie zostanie zniszczony podczas tego menu zostanie zniszczony.  
  
 Przed zamknięciem, aplikacja musi zwolnić zasobów systemowych, skojarzone z menu podręcznego, jeśli menu nie zostanie przypisany do okna. Menu dzięki aplikacjom wywołując [DestroyMenu](#destroymenu) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::CreateMenu](#createmenu).  
  
##  <a name="deletemenu"></a>CMenu::DeleteMenu  
 Usuwa element z menu.  
  
```  
BOOL DeleteMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `nPosition`  
 Określa, że element menu, który ma zostać usunięty, zgodnie z ustaleniami `nFlags`.  
  
 `nFlags`  
 Służy do interpretowania `nPosition` w następujący sposób:  
  
|nFlags|Interpretacja nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Jeśli nie jest to domyślny **MF_BYCOMMAND** ani **MF_BYPOSITION** jest ustawiona.|  
|**MF_BYPOSITION**|Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli element menu ma skojarzone menu podręczne `DeleteMenu` niszczy dojścia do menu podręcznego i zwalnia pamięć używana przez menu podręczne.  
  
 W przypadku, gdy menu który znajduje się w oknie zostanie zmieniona (czy okno jest wyświetlane), aplikacja musi wywołać [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="deletetempmap"></a>CMenu::DeleteTempMap  
 Wywoływana automatycznie przez `CWinApp` obsługi czas bezczynności, usuwa wszystkie tymczasowe `CMenu` obiekty utworzone przez [FromHandle](#fromhandle) funkcję elementu członkowskiego.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Uwagi  
 `DeleteTempMap`Odłącza obiektu menu systemu Windows dołączona do tymczasowej `CMenu` obiektu przed usunięciem `CMenu` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]  
  
##  <a name="destroymenu"></a>CMenu::DestroyMenu  
 Niszczy menu i wszystkie zasoby systemu Windows, które były używane.  
  
```  
BOOL DestroyMenu();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zostanie zniszczony menu; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Menu jest odłączony od `CMenu` obiekt przed został zniszczony. Windows `DestroyMenu` automatycznie została wywołana funkcja `CMenu` destruktora.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::CreateMenu](#createmenu).  
  
##  <a name="detach"></a>CMenu::Detach  
 Odłącza menu systemu Windows z `CMenu` obiektu i zwraca dojście.  
  
```  
HMENU Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście typu `HMENU`, menu systemu Windows, w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 `m_hMenu` Ma ustawioną wartość elementu członkowskiego danych **NULL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="drawitem"></a>CMenu::DrawItem  
 Wywoływane przez platformę, gdy visual aspekt zmiany rysowanych przez właściciela menu.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Wskaźnik do [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) strukturę, która zawiera informacje o typie rysunku wymagane.  
  
### <a name="remarks"></a>Uwagi  
 `itemAction` Członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane. Przesłonić tę funkcję elementu członkowskiego, aby zaimplementować rysunku rysowania przez właściciela `CMenu` obiektu. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interfejsu (GDI), wybrane kontekst wyświetlania dostarczane w `lpDrawItemStruct` przed zakończeniem tej funkcji Członkowskich.  
  
 Zobacz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) opis `DRAWITEMSTRUCT` struktury.  
  
### <a name="example"></a>Przykład  
 Następujący kod jest z MFC [CTRLTEST](../../visual-cpp-samples.md) próbki:  
  
 [!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]  
  
##  <a name="enablemenuitem"></a>CMenu::EnableMenuItem  
 Włącza, wyłącza lub wygasza elementu menu.  
  
```  
UINT EnableMenuItem(
    UINT nIDEnableItem,  
    UINT nEnable);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDEnableItem*  
 Określa, że element menu, do włączenia, zgodnie z ustaleniami `nEnable`. Ten parametr można określić elementów menu podręczne, a także elementów menu standardowego.  
  
 `nEnable`  
 Określa akcję do wykonania. Może być kombinacją **MF_DISABLED**, `MF_ENABLED`, lub **MF_GRAYED**, z **MF_BYCOMMAND** lub **MF_BYPOSITION**. Wartości te można łączyć przy użyciu bitowego operatora OR. Te wartości mają następujące znaczenie:  
  
- **MF_BYCOMMAND** Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Domyślnie włączone.  
  
- **MF_BYPOSITION** Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.  
  
- **MF_DISABLED** wyłącza element menu, tak aby nie można wybrać, ale nie dim.  
  
- `MF_ENABLED`Umożliwia element menu, który można wybrać i przywracania go ze stanu na wygaszone.  
  
- **MF_GRAYED** wyłącza element menu tak, aby nie można wybrać i wygasza go.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedni stan ( **MF_DISABLED**, `MF_ENABLED`, lub **MF_GRAYED**) lub -1, jeśli nie jest prawidłowy.  
  
### <a name="remarks"></a>Uwagi  
 [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu), i [LoadMenuIndirect](#loadmenuindirect) funkcje Członkowskie można również ustawić stan (włączone, wyłączona albo wygaszone) elementu menu.  
  
 Przy użyciu **MF_BYPOSITION** wartość wymaga aplikacji do korzystania z prawidłowych `CMenu`. Jeśli `CMenu` menu paska jest używana, ma to wpływ na element menu najwyższego poziomu (element na pasku menu). Aby ustawić stan elementu menu podręczne lub zagnieżdżone menu podręczne według położenia, należy określić aplikację `CMenu` menu podręczne.  
  
 Gdy aplikacja Określa **MF_BYCOMMAND** flagi, system Windows sprawdza wszystkie elementy menu podręczne, które są podrzędne w stosunku do `CMenu`; w związku z tym, o ile nie występują zduplikowane elementy przy użyciu `CMenu` jest pasek menu wystarczające.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]  
  
##  <a name="fromhandle"></a>CMenu::FromHandle  
 Zwraca wskaźnik do `CMenu` obiekt na podstawie uchwytów okien do menu.  
  
```  
static CMenu* PASCAL FromHandle(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 `hMenu`  
 Dojście systemu Windows do menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CMenu` może to być tymczasowych lub trwałych.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CMenu` obiekt nie jest już dołączony do obiektu menu systemu Windows, tymczasowej `CMenu` obiekt jest tworzony i dołączyć.  
  
 To tymczasowe `CMenu` obiektu jest prawidłowa tylko po ponownym aplikacja ma czas bezczynności w jego pętli zdarzenia, w tym czasie wszystkie obiekty tymczasowe są usuwane.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::CreateMenu](#createmenu).  
  
##  <a name="getdefaultitem"></a>CMenu::GetDefaultItem  
 Określa domyślny element menu z menu.  
  
```  
UINT GetDefaultItem(
    UINT gmdiFlags,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *gmdiFlags*  
 Wartość określającą, jak funkcja wyszukiwania elementów menu. Ten parametr może być brak, jeden lub kombinację następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|**GMDI_GOINTOPOPUPS**|Określa, jeśli element domyślny to taki, który otwiera podmenu, funkcja wyszukiwania w odpowiednich rekursywnie podmenu. Jeśli podmenu nie ma żadnego elementu domyślny, zwracana wartość identyfikuje element, którego kliknięcie spowoduje otwarcie podmenu.<br /><br /> Domyślnie funkcja zwraca pierwszy element domyślny menu określony, niezależnie od tego, czy jest elementu, którego kliknięcie spowoduje otwarcie podmenu.|  
|**GMDI_USEDISABLED**|Określa, że funkcja jest do zwrócenia element domyślny, nawet jeśli została ona wyłączona.<br /><br /> Domyślnie funkcja pomija elementy wyłączone lub wygaszone.|  
  
 `fByPos`  
 Wartość określająca, czy można pobrać identyfikatora elementu menu lub położenia. Jeśli ten parametr ma **FALSE**, zwracany jest identyfikatorem. W przeciwnym razie jest zwracana pozycja.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, zwracana wartość jest identyfikatora lub położenie elementu menu. Jeśli funkcja nie powiedzie się, wartość zwracana jest - 1.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie funkcji Win32 [GetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647976), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenucontexthelpid"></a>CMenu::GetMenuContextHelpId  
 Pobiera pomocy kontekstowej identyfikator skojarzony z `CMenu`.  
  
```  
DWORD GetMenuContextHelpId() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pomoc kontekstowa identyfikator aktualnie skojarzony z `CMenu` jeśli taki istnieje; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenuinfo"></a>CMenu::GetMenuInfo  
 Pobiera informacje o menu.  
  
```  
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpcmi`  
 Wskaźnik do [MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575) struktury zawierającej informacje o menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, zwracana wartość jest różna od zera; w przeciwnym razie wartość zwracana jest wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji w celu uzyskania informacji o menu.  
  
##  <a name="getmenuitemcount"></a>CMenu::GetMenuItemCount  
 Określa liczbę elementów w menu podręczne lub najwyższego poziomu.  
  
```  
UINT GetMenuItemCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w menu, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość-1.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="getmenuitemid"></a>CMenu::GetMenuItemID  
 Uzyskuje identyfikator elementu menu dla elementu menu znajdujący się w pozycji zdefiniowane przez `nPos`.  
  
```  
UINT GetMenuItemID(int nPos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Określa położenie (liczony od zera) elementu menu pobierania o identyfikatorze.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator elementu określonego elementu w menu podręczne, jeśli funkcja zakończy się pomyślnie. Jeśli określony element menu podręcznego (w przeciwieństwie do elementu w menu podręcznym), wartość zwracana jest wartość -1. Jeśli `nPos` odpowiada **SEPARATORA** element menu, zwracana wartość jest równa 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenuiteminfo"></a>CMenu::GetMenuItemInfo  
 Pobiera informacje o elemencie menu.  
  
```  
BOOL GetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `uItem`  
 Identyfikator lub położenie elementu menu, aby uzyskać informacje. Znaczenie tego parametru zależy od wartości `ByPos`.  
  
 `lpMenuItemInfo`  
 Wskaźnik do [KOJARZĄCA](http://msdn.microsoft.com/library/windows/desktop/ms647578), zgodnie z opisem w zestawie Windows SDK, który zawiera informacje o menu.  
  
 `fByPos`  
 Wartość określającą znaczenie `nIDItem`. Domyślnie `ByPos` jest **FALSE**, co oznacza, że uItem jest identyfikatorem elementu menu. Jeśli `ByPos` nie jest ustawiony na **FALSE**, wskazuje położenie elementu menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, zwracana wartość jest różna od zera. Jeśli funkcja nie powiedzie się, zwracana wartość wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, należy użyć funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie funkcji Win32 [GetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms647980), zgodnie z opisem w zestawie Windows SDK. Należy pamiętać, że w implementacji MFC `GetMenuItemInfo`, nie należy używać dojścia do menu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]  
  
##  <a name="getmenustate"></a>CMenu::GetMenuState  
 Zwraca informacje o stanie podany element menu lub liczba elementów w menu podręcznym.  
  
```  
UINT GetMenuState(
    UINT nID,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Określa identyfikator elementu menu, zgodnie z ustaleniami `nFlags`.  
  
 `nFlags`  
 Określa rodzaj `nID`. Może być jedną z następujących wartości:  
  
- **MF_BYCOMMAND** Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Domyślnie włączone.  
  
- **MF_BYPOSITION** Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość 0xFFFFFFFF, jeśli określony element nie istnieje. Jeśli *nId* identyfikuje menu podręcznego znaczącym bajcie zawiera liczbę elementów w menu podręcznym i mniej znaczącego bajtu zawiera flagi menu skojarzone z menu podręcznego. W przeciwnym razie jest zwracana wartość maski (wartość logiczna lub) wartości z poniższej listy (Ta maska opisuje stan menu elementu *nId* identyfikuje):  
  
- **MF_CHECKED** działa jak przełącznik z **MF_UNCHECKED** do domyślnego pole wyboru obok elementu. Gdy aplikacja udostępnia map bitowych znacznik wyboru (zobacz `SetMenuItemBitmaps` funkcji członkowskiej), "zaznaczone na" mapy bitowej jest wyświetlany.  
  
- **MF_DISABLED** wyłącza element menu, tak aby nie można wybrać, ale nie dim.  
  
- `MF_ENABLED`Umożliwia element menu, który można wybrać i przywracania go ze stanu na wygaszone. Należy pamiętać, że wartość tej stałej jest 0; Aplikacja nie należy przetestować 0 w przypadku niepowodzenia użycie tej wartości.  
  
- **MF_GRAYED** wyłącza element menu tak, aby nie można wybrać i wygasza go.  
  
- **MF_MENUBARBREAK** element zostanie umieszczone w nowym wierszu w menu statyczne lub w nowej kolumnie w menu podręcznym. Nowa kolumna menu podręczne będą oddzielone od starego kolumny pionowych linii podziału.  
  
- **MF_MENUBREAK** element zostanie umieszczone w nowym wierszu w menu statyczne lub w nowej kolumnie w menu podręcznym. Nie linii podziału jest umieszczana między kolumnami.  
  
- **MF_SEPARATOR** rysuje linię podziału poziomą. Można używać tylko w menu podręczne. Ten wiersz nie wygaszone, wyłączone lub wyróżnione. Inne parametry są ignorowane.  
  
- **MF_UNCHECKED** działa jak przełącznik z **MF_CHECKED** Aby usunąć znacznik wyboru obok elementu. Gdy aplikacja udostępnia map bitowych znacznik wyboru (zobacz `SetMenuItemBitmaps` funkcji członkowskiej), jest wyświetlany mapy bitowej "znacznik wyboru off". Należy pamiętać, że wartość tej stałej jest 0; Aplikacja nie należy przetestować 0 w przypadku niepowodzenia użycie tej wartości.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]  
  
##  <a name="getmenustring"></a>CMenu::GetMenuString  
 Kopiuje etykietę elementu menu określony w buforze określona.  
  
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
 `nIDItem`  
 Określa liczbę całkowitą identyfikator elementu menu lub przesunięcie elementu menu w menu, w zależności od wartości `nFlags`.  
  
 `lpString`  
 Wskazuje buforu, który ma otrzymać etykiety.  
  
 `rString`  
 Odwołanie do `CString` obiektu, który ma otrzymać ciąg skopiowany menu.  
  
 `nMaxCount`  
 Określa maksymalną długość (w znakach) etykiety, który ma zostać skopiowany. Jeśli etykieta jest dłuższa niż maksimum określonego w `nMaxCount`, dodatkowe znaki są obcinane.  
  
 `nFlags`  
 Określa interpretacji `nIDItem` parametru. Może być jedną z następujących wartości:  
  
|nFlags|Interpretacja nIDItem|  
|------------|-------------------------------|  
|**MF_BYCOMMAND**|Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Jeśli nie jest to domyślny **MF_BYCOMMAND** ani **MF_BYPOSITION** jest ustawiona.|  
|**MF_BYPOSITION**|Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa rzeczywistą liczbę znaków kopiowania do buforu nie włącznie z terminatorem null.  
  
### <a name="remarks"></a>Uwagi  
 `nMaxCount` Parametr powinien być większy niż liczba znaków w etykiecie, aby uwzględnić znak null, który kończy się ciągiem.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getsafehmenu"></a>CMenu::GetSafeHmenu  
 Zwraca `HMENU` opakowane przez to `CMenu` obiekt, lub **NULL** `CMenu` wskaźnika.  
  
```  
HMENU GetSafeHmenu() const;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="getsubmenu"></a>CMenu::GetSubMenu  
 Pobiera `CMenu` obiekt menu podręczne.  
  
```  
CMenu* GetSubMenu(int nPos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Określa pozycję menu podręczne zawartych w menu. Wartości pozycji rozpoczynają się od 0 do pierwszego elementu menu. Nie można użyć identyfikatora menu podręcznego w tej funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CMenu` którego `m_hMenu` elementu członkowskiego zawiera dojścia do menu podręczne, jeśli istnieje menu podręczne na pozycji; w przeciwnym razie **NULL**. Jeśli `CMenu` obiekt nie istnieje, a następnie tymczasowy zostanie utworzony. `CMenu` Zwrócony wskaźnik nie powinny być przechowywane.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::TrackPopupMenu](#trackpopupmenu).  
  
##  <a name="insertmenu"></a>CMenu::InsertMenu  
 Wstawia nowy element menu na pozycji określony przez `nPosition` i inne elementy są przenoszone w dół menu.  
  
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
 `nPosition`  
 Określa, że element menu, przed którym nowy element menu jest do wstawienia. `nFlags` Parametru można zinterpretować `nPosition` w następujący sposób:  
  
|nFlags|Interpretacja nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Jeśli nie jest to domyślny **MF_BYCOMMAND** ani **MF_BYPOSITION** jest ustawiona.|  
|**MF_BYPOSITION**|Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0. Jeśli `nPosition` wynosi -1, nowy element menu jest dołączany na końcu elementu menu.|  
  
 `nFlags`  
 Określa sposób `nPosition` jest interpretowana i określa informacje o stanie Nowy element menu, gdy jest ona dodawana do menu. Lista flagi, które mogą zostać ustawione, zobacz [AppendMenu zawsze](#appendmenu) funkcję elementu członkowskiego. Aby określić więcej niż jedną wartość, należy użyć bitowy operator OR, połącz je z **MF_BYCOMMAND** lub **MF_BYPOSITION** flagi.  
  
 `nIDNewItem`  
 Określa identyfikator polecenia nowego elementu menu lub, jeśli `nFlags` ustawiono **MF_POPUP**, dojście menu ( `HMENU`) z menu podręcznego. `nIDNewItem` Parametr jest ignorowany (nie jest to wymagane), jeśli `nFlags` ustawiono **MF_SEPARATOR**.  
  
 `lpszNewItem`  
 Określa zawartość nowego elementu menu. `nFlags`może służyć do interpretowania `lpszNewItem` w następujący sposób:  
  
|nFlags|Interpretacja lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Zawiera dostarczone przez aplikację 32-bitową wartość używaną przez aplikację do obsługi dodatkowych danych skojarzone z elementem menu. Ta wartość 32-bitowych jest dostępny na potrzeby aplikacji w **itemData** elementu członkowskiego struktury dostarczonych przez [WM_MEASUREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775925) i [WM_DRAWITEM](http://msdn.microsoft.com/library/windows/desktop/bb775923) wiadomości. Komunikaty te są wysyłane, gdy element menu początkowo wyświetlana jest lub zostanie zmieniona.|  
|**MF_STRING**|Zawiera wskaźnik długi ciąg znaków zakończony znakiem null. Jest to domyślnej interpretacji.|  
|**MF_SEPARATOR**|`lpszNewItem` Parametr jest ignorowany (nie wymagane).|  
  
 *pBmp*  
 Wskazuje `CBitmap` obiekt, który będzie używany jako element menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aplikację można określić stanu elementu menu przez ustawienie wartości `nFlags`.  
  
 W przypadku, gdy menu który znajduje się w oknie zostanie zmieniona (czy okno jest wyświetlane), aplikacja powinna wywołać `CWnd::DrawMenuBar`.  
  
 Gdy `nIDNewItem` Określa menu podręczne, staje się częścią menu, w którym zostanie on włożony. Jeśli zostanie zniszczony tego menu, menu wstawionego również zostaną usunięte. Menu wstawionego należy odłączyć od `CMenu` obiekt, aby uniknąć konfliktu.  
  
 Jeśli aktywny wielu okno podrzędne interfejsu (MDI) dokumentu jest zmaksymalizowane i aplikacji wstawia menu podręcznego w menu aplikacji MDI wywołanie tej funkcji i określając **MF_BYPOSITION** dodaje się flagi, menu jedną pozycję dalej po lewej, niż oczekiwano. Dzieje się tak, ponieważ sterowanie okna podrzędnego MDI active znajduje się na pierwszym miejscu paska menu Okno ramowe MDI. Pozycja menu poprawnie, do aplikacji należy dodać 1 wartości pozycji, które w przeciwnym razie można użyć. Aplikacja może użyć **WM_MDIGETACTIVE** komunikatu, aby określić, czy okno podrzędne aktualnie aktywny jest zmaksymalizowane.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]  
  
##  <a name="insertmenuitem"></a>CMenu::InsertMenuItem  
 Wstawia nowy element menu na określonej pozycji w menu.  
  
```  
BOOL InsertMenuItem(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `uItem`  
 Zobacz opis `uItem` w [InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988) w zestawie Windows SDK.  
  
 `lpMenuItemInfo`  
 Zobacz opis `lpmii` w **InsertMenuItem** w zestawie Windows SDK.  
  
 `fByPos`  
 Zobacz opis `fByPosition` w **InsertMenuItem** w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zawijana [InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988), które zostały opisane w zestawie SDK systemu Windows.  
  
##  <a name="loadmenu"></a>CMenu::LoadMenu  
 Ładuje menu zasobu z pliku wykonywalnego aplikacji i dołącza go do `CMenu` obiektu.  
  
```  
BOOL LoadMenu(LPCTSTR lpszResourceName);  
BOOL LoadMenu(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Wskazuje zerem ciągu zawierającego nazwę zasobu menu, aby załadować.  
  
 `nIDResource`  
 Określa identyfikator menu zasobów menu do załadowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zasób menu został załadowany pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przed zamknięciem, aplikacja musi zwolnić zasobów systemowych, skojarzone z menu, jeśli menu nie zostanie przypisany do okna. Menu dzięki aplikacjom wywołując [DestroyMenu](#destroymenu) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]  
  
##  <a name="loadmenuindirect"></a>CMenu::LoadMenuIndirect  
 Ładuje zasobu z szablonu menu w pamięci i dołącza go do `CMenu` obiektu.  
  
```  
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMenuTemplate*  
 Wskazuje szablon menu (czyli pojedynczy [MENUITEMTEMPLATEHEADER](http://msdn.microsoft.com/library/windows/desktop/ms647583) struktury i kolekcji, co najmniej jednego [MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581) struktury). Aby uzyskać więcej informacji na temat tych dwóch struktur zobacz zestaw Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zasób menu został załadowany pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Szablon menu jest nagłówka zbioru co najmniej jednego [MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581) struktury, z których każdy może zawierać jeden lub więcej elementów menu i menu podręczne.  
  
 Numer wersji musi mieć wartość 0.  
  
 **MtOption** powinna zawierać flagi **MF_END** dla ostatniego elementu na liście wyskakującego i ostatniego elementu na liście głównej. Zobacz `AppendMenu` funkcji członkowskiej dla innych flag. **MtId** elementu członkowskiego musi być pominięte z **MENUITEMTEMPLATE** struktury, kiedy **MF_POPUP** została określona w **mtOption**.  
  
 Ilość miejsca przydzielonego dla **MENUITEMTEMPLATE** struktury musi być wystarczająco duży dla **mtString** zawierać nazwy elementu menu jako ciąg znaków zakończony znakiem null.  
  
 Przed zamknięciem, aplikacja musi zwolnić zasobów systemowych, skojarzone z menu, jeśli menu nie zostanie przypisany do okna. Menu dzięki aplikacjom wywołując [DestroyMenu](#destroymenu) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]  
  
##  <a name="m_hmenu"></a>CMenu::m_hMenu  
 Określa `HMENU` dojście menu systemu Windows jest dołączony do `CMenu` obiektu.  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="measureitem"></a>CMenu::MeasureItem  
 Wywoływane przez platformę, gdy jest tworzony przy użyciu stylu rysowania przez właściciela menu.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpMeasureItemStruct`  
 Wskaźnik do `MEASUREITEMSTRUCT` struktury.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta funkcja członkowska nie działa. Zastąpienie tej funkcji Członkowskich i wypełnij `MEASUREITEMSTRUCT` struktury poinformować system Windows z poziomu menu wymiarów.  
  
 Zobacz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) opis `MEASUREITEMSTRUCT` struktury.  
  
### <a name="example"></a>Przykład  
 Następujący kod jest z MFC [CTRLTEST](../../visual-cpp-samples.md) próbki:  
  
 [!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]  
  
##  <a name="modifymenu"></a>CMenu::ModifyMenu  
 Zmienia istniejący element menu na pozycji określony przez `nPosition`.  
  
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
 `nPosition`  
 Określa, że element menu zostanie zmieniony. `nFlags` Parametru można zinterpretować `nPosition` w następujący sposób:  
  
|nFlags|Interpretacja nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Jeśli nie jest to domyślny **MF_BYCOMMAND** ani **MF_BYPOSITION** jest ustawiona.|  
|**MF_BYPOSITION**|Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|  
  
 `nFlags`  
 Określa sposób `nPosition` jest interpretowana i udostępnia informacje o zmianach wprowadzonych do elementu menu. Lista flagi, które mogą zostać ustawione, zobacz [AppendMenu zawsze](#appendmenu) funkcję elementu członkowskiego.  
  
 `nIDNewItem`  
 Określa identyfikator polecenia elementu menu zmodyfikowanych lub, jeśli `nFlags` ustawiono **MF_POPUP**, dojście menu ( `HMENU`) z menu podręcznego. `nIDNewItem` Parametr jest ignorowany (nie jest to wymagane), jeśli `nFlags` ustawiono **MF_SEPARATOR**.  
  
 `lpszNewItem`  
 Określa zawartość nowego elementu menu. `nFlags` Parametru można zinterpretować `lpszNewItem` w następujący sposób:  
  
|nFlags|Interpretacja lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Zawiera dostarczone przez aplikację 32-bitową wartość używaną przez aplikację do obsługi dodatkowych danych skojarzone z elementem menu. Ta wartość 32-bitowych jest dostępne dla aplikacji, podczas przetwarzania **MF_MEASUREITEM** i **MF_DRAWITEM**.|  
|**MF_STRING**|Zawiera wskaźnik długi ciąg znaków zakończony znakiem null lub do `CString`.|  
|**MF_SEPARATOR**|`lpszNewItem` Parametr jest ignorowany (nie wymagane).|  
  
 *pBmp*  
 Wskazuje `CBitmap` obiekt, który będzie używany jako element menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aplikacja Określa nowy stan elementu menu przez ustawienie wartości `nFlags`. Jeśli ta funkcja zastępuje menu podręczne skojarzone z elementem menu, niszczy starego menu podręcznego i zwalnia pamięć używana przez menu podręczne.  
  
 Gdy `nIDNewItem` Określa menu podręczne, staje się częścią menu, w którym zostanie on włożony. Jeśli zostanie zniszczony tego menu, menu wstawionego również zostaną usunięte. Menu wstawionego należy odłączyć od `CMenu` obiekt, aby uniknąć konfliktu.  
  
 W przypadku, gdy menu który znajduje się w oknie zostanie zmieniona (czy okno jest wyświetlane), aplikacja powinna wywołać `CWnd::DrawMenuBar`. Aby zmienić atrybuty istniejących elementów menu, jest znacznie szybszy do użycia `CheckMenuItem` i `EnableMenuItem` funkcji elementów członkowskich.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="operator_hmenu"></a>CMenu::operator HMENU  
 Użyj tego operatora, aby pobrać dojście `CMenu` obiektu.  
  
```  
operator HMENU() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia dojście `CMenu` obiektu; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Dojście służy do bezpośredniego wywoływania interfejsów API systemu Windows.  
  
##  <a name="operator_neq"></a>CMenu::operator! =  
 Określa, czy dwa menu logicznie nie są takie same.  
  
```  
BOOL operator!=(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `menu`  
 A `CMenu` obiekt do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Testy, jeśli obiekt menu po lewej stronie nie jest taki sam, jak obiekt menu z prawej strony.  
  
##  <a name="operator_eq_eq"></a>CMenu::operator ==  
 Określa, czy dwa menu są logicznie równe.  
  
```  
BOOL operator==(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `menu`  
 A `CMenu` obiekt do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Sprawdza, czy obiekt menu po lewej stronie jest taki sam (w postaci liczby `HMENU` wartość) na obiekt menu z prawej strony.  
  
##  <a name="removemenu"></a>CMenu::RemoveMenu  
 Usuwa element menu z menu podręcznego skojarzone z menu.  
  
```  
BOOL RemoveMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `nPosition`  
 Określa, że element menu ma zostać usunięty. `nFlags` Parametru można zinterpretować `nPosition` w następujący sposób:  
  
|nFlags|Interpretacja nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Jeśli nie jest to domyślny **MF_BYCOMMAND** ani **MF_BYPOSITION** jest ustawiona.|  
|**MF_BYPOSITION**|Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|  
  
 `nFlags`  
 Określa sposób `nPosition` jest interpretowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Nie zniszczenia dojście do menu podręczne, więc menu mogą być ponownie używane. Przed wywołaniem tej funkcji, aplikacja może wywołać `GetSubMenu` funkcji członkowskiej pobrać oknie podręcznym `CMenu` obiektu do ponownego użycia.  
  
 W przypadku, gdy menu który znajduje się w oknie zostanie zmieniona (czy okno jest wyświetlane), aplikacja musi wywołać `CWnd::DrawMenuBar`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setdefaultitem"></a>CMenu::SetDefaultItem  
 Ustawia domyślny element menu dla menu określony.  
  
```  
BOOL SetDefaultItem(
    UINT uItem,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `uItem`  
 Identyfikator lub pozycji nowy domyślny element menu lub - 1 oznacza nie element domyślny. Znaczenie tego parametru zależy od wartości `fByPos`.  
  
 `fByPos`  
 Wartość określającą znaczenie `uItem`. Jeśli ten parametr ma **FALSE**, `uItem` jest identyfikatorem elementu menu. W przeciwnym razie jest położenie elementu menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, zwracana wartość jest różna od zera. Jeśli funkcja nie powiedzie się, zwracana wartość wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, należy użyć funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie funkcji Win32 [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setmenucontexthelpid"></a>CMenu::SetMenuContextHelpId  
 Kojarzy identyfikator kontekstu pomocy z `CMenu`.  
  
```  
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```  
  
### <a name="parameters"></a>Parametry  
 `dwContextHelpId`  
 Identyfikator pomocy kontekstu do skojarzenia z `CMenu`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie elementy w menu współdzielić ten identyfikator — nie jest możliwe do dołączenia identyfikator kontekstu pomocy do poszczególnych elementów menu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setmenuinfo"></a>CMenu::SetMenuInfo  
 Ustawia informacje dotyczące menu.  
  
```  
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```  
  
### <a name="parameters"></a>Parametry  
 `lpcmi`  
 Wskaźnik do [MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575) struktury zawierającej informacje o menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, zwracana wartość jest różna od zera; w przeciwnym razie wartość zwracana jest wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można ustawić określone informacje na temat menu.  
  
##  <a name="setmenuitembitmaps"></a>CMenu::SetMenuItemBitmaps  
 Kojarzy określonego map bitowych z elementu menu.  
  
```  
BOOL SetMenuItemBitmaps(
    UINT nPosition,  
    UINT nFlags,  
    const CBitmap* pBmpUnchecked,  
    const CBitmap* pBmpChecked);
```  
  
### <a name="parameters"></a>Parametry  
 `nPosition`  
 Określa, że element menu zostanie zmieniony. `nFlags` Parametru można zinterpretować `nPosition` w następujący sposób:  
  
|nFlags|Interpretacja nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Określa, że parametru zapewnia identyfikator polecenia istniejącego elementu menu. Jeśli nie jest to domyślny **MF_BYCOMMAND** ani **MF_BYPOSITION** jest ustawiona.|  
|**MF_BYPOSITION**|Określa, że parametru zapewnia pozycji istniejącego elementu menu. Pierwszy element znajduje się na pozycji 0.|  
  
 `nFlags`  
 Określa sposób `nPosition` jest interpretowany.  
  
 `pBmpUnchecked`  
 Określa mapy bitowej do użycia dla elementów menu, które nie są sprawdzane.  
  
 `pBmpChecked`  
 Określa mapy bitowej do użycia dla elementów menu, które są sprawdzane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Czy element menu jest zaznaczenie, system Windows wyświetli odpowiednie mapy bitowej obok elementu menu.  
  
 Jeśli dowolny `pBmpUnchecked` lub `pBmpChecked` jest **NULL**, a następnie systemu Windows nie wyświetla żadnego obrazu obok pozycji menu dla atrybutu. Jeśli oba parametry są **NULL**, system Windows używa domyślny znacznik wyboru, gdy element jest zaznaczony i usuwa znacznik wyboru, gdy element nie jest zaznaczone.  
  
 Gdy zostanie zniszczony menu, bitmapy te nie zostaną zniszczone; aplikację należy zniszczyć je.  
  
 Windows **GetMenuCheckMarkDimensions** funkcja pobiera wymiary znacznik wyboru domyślna używana dla elementów menu. Aplikacja używa tych wartości, aby określić odpowiedni rozmiar bitmap dostarczony wraz z tej funkcji. Uzyskaj informacje o rozmiarze, Utwórz użytkownika mapy bitowe, a następnie ustaw je.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]  
  
##  <a name="setmenuiteminfo"></a>CMenu::SetMenuItemInfo  
 Zmienia informacje o elemencie menu.  
  
```  
BOOL SetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `uItem`  
 Zobacz opis `uItem` w [SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001) w zestawie Windows SDK.  
  
 `lpMenuItemInfo`  
 Zobacz opis `lpmii` w **SetMenuItemInfo** w zestawie Windows SDK.  
  
 `fByPos`  
 Zobacz opis `fByPosition` w **SetMenuItemInfo** w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zawijana [SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001), które zostały opisane w zestawie SDK systemu Windows.  
  
##  <a name="trackpopupmenu"></a>CMenu::TrackPopupMenu  
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
 `nFlags`  
 Określa flagi pozycji ekranu i położenia kursora myszy. Zobacz [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) listę dostępnych flag.  
  
 *x*  
 Określa położenie we współrzędnych ekranu menu podręczne. W zależności od wartości `nFlags` parametr, menu może być wyrównany do lewej, do prawej lub do środka względem tej pozycji.  
  
 *y*  
 Określa położenie w pionie we współrzędnych ekranu górnej części menu na ekranie.  
  
 `pWnd`  
 Identyfikuje okna, który jest właścicielem menu podręczne. Ten parametr nie może być **NULL**, nawet jeśli **TPM_NONOTIFY** określono flagę. To okno odbiera wszystkie **WM_COMMAND** wiadomości z menu. W systemie Windows w wersji 3.1 lub nowszej, nie otrzyma okna **WM_COMMAND** wiadomości do momentu `TrackPopupMenu` zwraca. W środowisku Windows 3.0, otrzymuje okna **WM_COMMAND** wiadomości przed `TrackPopupMenu` zwraca.  
  
 `lpRect`  
 Ignorowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca wyniku wywołania metody [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Przestawne menu podręczne mogą występować w dowolnym miejscu na ekranie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]  
  
##  <a name="trackpopupmenuex"></a>CMenu::TrackPopupMenuEx  
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
 `fuFlags`  
 Określa różne funkcje dla rozszerzonych menu. Aby uzyskać listę wszystkich wartości i ich znaczenie, zobacz [TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003).  
  
 *x*  
 Określa położenie we współrzędnych ekranu menu podręczne.  
  
 *y*  
 Określa położenie w pionie we współrzędnych ekranu górnej części menu na ekranie.  
  
 `pWnd`  
 Wskaźnik do okna będący właścicielem menu podręcznego i odbieranie komunikatów z menu utworzony. To okno może być dowolnym oknie z bieżącej aplikacji, ale nie może być **NULL**. Jeśli określisz **TPM_NONOTIFY** w `fuFlags` parametr funkcji nie wysyła komunikaty do `pWnd`. Funkcja musi zwracać okna wskazywana przez `pWnd` do odbierania **WM_COMMAND** wiadomości.  
  
 *lptpm*  
 Wskaźnik do [TPMPARAMS](http://msdn.microsoft.com/library/windows/desktop/ms647586) struktury, który określa obszar ekranu menu nie powinny się nakładać. Ten parametr może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli określisz **TPM_RETURNCMD** w `fuFlags` parametru, zwracana wartość jest identyfikatorem elementu menu elementu, który użytkownik wybrał. Jeśli użytkownik anuluje menu bez dokonywania wyboru lub jeśli wystąpi błąd, zwracana wartość to 0.  
  
 Jeśli nie określisz **TPM_RETURNCMD** w `fuFlags` parametru, zwracana wartość jest różna od zera, jeśli funkcja zakończy się powodzeniem, a 0 w przypadku niepowodzenia. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Uwagi  
 Przestawne menu podręczne mogą występować w dowolnym miejscu na ekranie. Aby uzyskać więcej informacji dotyczących obsługi błędów podczas tworzenia menu podręczne, zobacz [TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CTRLTEST](../../visual-cpp-samples.md)   
 [Przykładowe MFC DYNAMENU](../../visual-cpp-samples.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CObject](../../mfc/reference/cobject-class.md)
