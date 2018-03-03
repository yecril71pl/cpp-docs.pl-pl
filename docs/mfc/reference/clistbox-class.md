---
title: "Clistbox — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
dev_langs:
- C++
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ecf574deed95fca6a96e8e5a5c1d1e0bebed1854
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clistbox-class"></a>Clistbox — klasa
Udostępnia funkcje systemu Windows pola listy.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CListBox : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CListBox::CListBox](#clistbox)|Konstruuje `CListBox` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CListBox::AddString](#addstring)|Dodaje ciąg do pola listy.|  
|[CListBox::CharToItem](#chartoitem)|Należy przesłonić, aby podać niestandardowy `WM_CHAR` obsługi pól listy rysowania przez właściciela, które nie zawierają ciągi.|  
|[CListBox::CompareItem](#compareitem)|Wywoływane przez platformę, by określić pozycję Nowy element w polu listy posortowane rysowania przez właściciela.|  
|[CListBox::Create](#create)|Tworzy okno listy systemu Windows i dołącza go do `CListBox` obiektu.|  
|[CListBox::DeleteItem](#deleteitem)|Wywoływane przez platformę, gdy użytkownik usuwa element z listy rysowania przez właściciela.|  
|[CListBox::DeleteString](#deletestring)|Usuwa ciąg z pola listy.|  
|[CListBox::Dir](#dir)|Dodaje nazwy plików i/lub dysków z bieżącego katalogu, do pola listy.|  
|[CListBox::DrawItem](#drawitem)|Wywoływane przez platformę, gdy visual aspekt rysowania przez właściciela zmiany z pola listy.|  
|[CListBox::FindString](#findstring)|Wyszukuje ciąg w polu listy.|  
|[CListBox::FindStringExact](#findstringexact)|Znajduje pierwszy ciąg pole listy pasującej określonego ciągu.|  
|[CListBox::GetAnchorIndex](#getanchorindex)|Pobiera liczony od zera indeks bieżącego elementu zakotwiczenia w polu listy.|  
|[CListBox::GetCaretIndex](#getcaretindex)|Określa indeks elementu, który ma prostokąt fokusu w polu listy wielokrotnego wyboru.|  
|[CListBox::GetCount](#getcount)|Zwraca liczbę ciągów w polu listy.|  
|[CListBox::GetCurSel](#getcursel)|Zwraca liczony od zera Indeks aktualnie zaznaczonego ciągu w polu listy.|  
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Zwraca szerokość w pikselach, że pole listy mogą być przewijane w poziomie.|  
|[CListBox::GetItemData](#getitemdata)|Zwraca 32-bitową wartość skojarzoną z elementem pola listy.|  
|[CListBox::GetItemDataPtr](#getitemdataptr)|Zwraca wskaźnik do elementu pola listy.|  
|[CListBox::GetItemHeight](#getitemheight)|Określa wysokość elementy w polu listy.|  
|[CListBox::GetItemRect](#getitemrect)|Zwraca prostokąt ograniczający element pola listy jest aktualnie wyświetlany.|  
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Pobiera liczbę elementów w kolumnie.|  
|[CListBox::GetLocale](#getlocale)|Pobiera identyfikator ustawień regionalnych dla pola listy.|  
|[CListBox::GetSel](#getsel)|Zwraca stan zaznaczenia elementu pola listy.|  
|[CListBox::GetSelCount](#getselcount)|Zwraca liczbę ciągów aktualnie wybrane w polu listy wielokrotnego wyboru.|  
|[CListBox::GetSelItems](#getselitems)|Zwraca indeksów ciągów aktualnie wybrane w polu listy.|  
|[CListBox::GetText](#gettext)|Kopiuje element pola listy do buforu.|  
|[CListBox::GetTextLen](#gettextlen)|Zwraca długość w bajtach elementu pola listy.|  
|[CListBox::GetTopIndex](#gettopindex)|Zwraca indeks pierwszego ciągu widoczny w polu listy.|  
|[CListBox::InitStorage](#initstorage)|Preallocates bloków pamięci dla elementów pole listy i ciągów.|  
|[CListBox::InsertString](#insertstring)|Wstawia ciąg w lokalizacji określonej w polu listy.|  
|[CListBox::ItemFromPoint](#itemfrompoint)|Zwraca indeks elementu pole listy najbliższego punktu.|  
|[CListBox::MeasureItem](#measureitem)|Wywoływane przez platformę po utworzeniu rysowania przez właściciela pole listy do określenia pola listy wymiarów.|  
|[CListBox::ResetContent](#resetcontent)|Czyści wszystkie wpisy z pola listy.|  
|[CListBox::SelectString](#selectstring)|Wyszukuje i wybiera ciąg w polu listy pojedynczego wyboru.|  
|[CListBox::SelItemRange](#selitemrange)|Wybiera lub usunięcie zaznaczenia zakresu ciągów w polu listy wielokrotnego wyboru.|  
|[CListBox::SetAnchorIndex](#setanchorindex)|Ustawia zakotwiczenia w pole listy wielokrotnego wyboru, aby rozpocząć zaznaczania rozszerzonego.|  
|[CListBox::SetCaretIndex](#setcaretindex)|Ustawia element pod określonym indeksem prostokąt fokusu w polu listy wielokrotnego wyboru.|  
|[CListBox::SetColumnWidth](#setcolumnwidth)|Ustawia szerokość kolumny wielokolumnowe pole listy.|  
|[CListBox::SetCurSel](#setcursel)|Wybiera ciąg pola listy.|  
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Określa szerokość w pikselach, że pole listy mogą być przewijane w poziomie.|  
|[CListBox::SetItemData](#setitemdata)|Ustawia 32-bitową wartość skojarzoną z elementem pola listy.|  
|[CListBox::SetItemDataPtr](#setitemdataptr)|Ustawia wskaźnik do elementu pola listy.|  
|[CListBox::SetItemHeight](#setitemheight)|Określa wysokość elementów w polu listy.|  
|[CListBox::SetLocale](#setlocale)|Określa identyfikator ustawień regionalnych dla pola listy.|  
|[CListBox::SetSel](#setsel)|Wybiera lub usunięcie zaznaczenia elementu pola listy, w polu listy wielokrotnego wyboru.|  
|[CListBox::SetTabStops](#settabstops)|Określa pozycje tabulatorów w polu listy.|  
|[CListBox::SetTopIndex](#settopindex)|Ustawia liczony od zera indeks pierwszego ciągu widoczny w polu listy.|  
|[CListBox::VKeyToItem](#vkeytoitem)|Należy przesłonić, aby podać niestandardowy `WM_KEYDOWN` obsługi dla pola listy z **lbs_wantkeyboardinput —** styl zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 Pole listy wyświetla listę elementów, takich jak nazwy plików, które użytkownik może wyświetlać i wybierać.  
  
 W polu listy z pojedynczym wyborem użytkownik może wybrać tylko jeden element. W polu listy wielokrotnego wyboru można wybrać zakres elementów. Po wybraniu elementu jest wyróżnioną pozycją i pole listy wysyła powiadomienie do okna nadrzędnego.  
  
 Można utworzyć pole listy z szablonu okna dialogowego lub bezpośrednio w kodzie. Aby utworzyć bezpośrednio, należy utworzyć `CListBox` obiekt, a następnie wywołaj [Utwórz](#create) funkcji członkowskiej Utwórz kontrolkę pola listy z systemem Windows i dołączenie go do `CListBox` obiektu. Aby użyć pola listy w szablonu okna dialogowego, zadeklarować zmiennej pole listy w klasie — okno dialogowe, a następnie użyj `DDX_Control` w klasie — okno dialogowe `DoDataExchange` funkcji, aby połączyć zmiennej członka do kontrolki. (to jest wykonywane automatycznie podczas dodawania do własnej klasy okno dialogowe Zmienna sterująca.)  
  
 Konstrukcja może być jednoetapowy proces w klasie pochodnej z `CListBox`. Zapisywanie konstruktora klasy pochodnej i wywołanie **Utwórz** z wewnątrz konstruktora.  
  
 Jeśli chcesz obsługiwać Windows komunikaty powiadomień wysłane przez pole listy do elementu nadrzędnego (zazwyczaj klasą pochodną [cdialog —](../../mfc/reference/cdialog-class.md)), Dodaj funkcji członkowskiej wpisu i program obsługi komunikatów map wiadomości do klasy nadrzędnej dla każdego komunikatu.  
  
 Każdy wpis mapy komunikatów ma następującą postać:  
  
 `ON_Notification( id, memberFxn )`  
  
 gdzie `id` Określa identyfikator okno podrzędne formantu pole listy wysyłania powiadomienia i `memberFxn` jest nazwą funkcji członkowskiej nadrzędnego zostały zapisane do obsługi powiadomień.  
  
 Prototyp funkcji elementu nadrzędnego, jak wygląda następująco:  
  
 `afx_msg void memberFxn( );`  
  
 Poniżej przedstawiono listę potencjalnych wpisów map wiadomości i opis przypadków, w których będą przesyłane do obiektu nadrzędnego:  
  
- **ON_LBN_DBLCLK** użytkownik kliknie dwukrotnie ciąg w polu listy. Tylko pole listy, które ma [lbs_notify —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl wyśle ten komunikat powiadomienia.  
  
- **ON_LBN_ERRSPACE** pola listy nie może przydzielić wystarczającej ilości pamięci do spełnienia żądania.  
  
- **ON_LBN_KILLFOCUS** pola listy jest utraci fokus wprowadzania.  
  
- **ON_LBN_SELCANCEL** bieżące zaznaczenie w polu listy zostało anulowane. Ten komunikat jest wysyłana tylko wtedy, gdy pole listy ma **lbs_notify —** stylu.  
  
- **ON_LBN_SELCHANGE** zaznaczenie w polu listy zostało zmienione. Jeśli zaznaczenie zostanie zmienione przez tego powiadomienia nie są wysyłane [CListBox::SetCurSel](#setcursel) funkcję elementu członkowskiego. To powiadomienie ma zastosowanie tylko do pola listy, który ma **lbs_notify —** stylu. **LBN_SELCHANGE** powiadomienie jest wysyłane do pola listy wielokrotnego wyboru zawsze, gdy użytkownik naciśnie klawisz strzałki, nawet wtedy, gdy nie zmienia zaznaczenia.  
  
- **ON_LBN_SETFOCUS** pola listy otrzymuje fokus wprowadzania.  
  
- **ON_WM_CHARTOITEM** rysowania przez właściciela pole listy, które ma ciągi nie odbiera `WM_CHAR` wiadomości.  
  
- **ON_WM_VKEYTOITEM** pole listy z **lbs_wantkeyboardinput —** odbiera styl `WM_KEYDOWN` wiadomości.  
  
 W przypadku utworzenia `CListBox` obiektu w oknie dialogowym (za pośrednictwem zasób okna dialogowego), `CListBox` obiekt zostanie zniszczony automatycznie, gdy użytkownik zamyka okno dialogowe.  
  
 W przypadku utworzenia `CListBox` obiektu w ramach okna, konieczne może być zniszczyć `CListBox` obiektu. W przypadku utworzenia `CListBox` obiektów na stosie, zostanie zniszczony automatycznie. W przypadku utworzenia `CListBox` obiektów na stercie przy użyciu **nowe** funkcji, należy wywołać **usunąć** obiektu zniszczyć ją, gdy użytkownik zamyka okno nadrzędne.  
  
 Jeśli Przydziel wszystkie pamięci w `CListBox` obiektów, Zastąp `CListBox` destruktora usuwania alokacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="addstring"></a>CListBox::AddString  
 Dodaje ciąg do pola listy.  
  
```  
int AddString(LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszItem`  
 Wskazuje ciąg zakończony zerem, który ma zostać dodany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks na ciąg w polu listy. Wartość zwracana jest **LB_ERR** Jeśli wystąpi błąd; wartość zwracana jest **LB_ERRSPACE** Jeśli niewystarczającej ilości miejsca jest dostępne do przechowywania nowych parametrów.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie utworzono pola listy z [lbs_sort —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl ciągu zostanie dodany na końcu listy. W przeciwnym razie wartość ciągu jest umieszczone na liście, a lista jest sortowana. Jeśli na liście utworzono za pomocą **lbs_sort —** styl, ale nie [lbs_hasstrings —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, w ramach sortuje listę przez co najmniej jednego wywołania `CompareItem` funkcji członkowskiej.  
  
 Użyj [InsertString](#insertstring) Aby wstawić ciąg do określonej lokalizacji w polu listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]  
  
##  <a name="chartoitem"></a>CListBox::CharToItem  
 Wywoływane przez platformę, gdy okno nadrzędne pola listy otrzymuje `WM_CHARTOITEM` komunikat w polu listy.  
  
```  
virtual int CharToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nKey`  
 Kod ANSI znaku wpisana przez użytkownika.  
  
 `nIndex`  
 Bieżąca pozycja karetkę pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca - 1 lub - 2, żadne dalsze działania lub nieujemna liczba, aby określić indeks elementu pola listy, na którym należy wykonać domyślną akcję dla naciśnięcia klawisza. Domyślna implementacja zwraca - 1.  
  
### <a name="remarks"></a>Uwagi  
 `WM_CHARTOITEM` Komunikat wysyłany przez pole listy po odebraniu `WM_CHAR` wiadomości, ale tylko jeśli pole listy spełnia te kryteria:  
  
-   To pole listy rysowania przez właściciela.  
  
-   Nie ma [lbs_hasstrings —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl zestawu.  
  
-   Zawiera co najmniej jeden element.  
  
 Użytkownik nigdy nie powinien wywoływać tej funkcji samodzielnie. Należy przesłonić tę funkcję, aby podać własną niestandardową obsługę komunikatów klawiatury.  
  
 W przypadku zastąpienia musi zwracać wartość platformę stwierdzić, jakie działania należy wykonać. Zwracana wartość - 1 lub - 2 wskazuje, że obsługiwane wszystkie aspekty zaznaczenie elementu i wymaga żadnych dodatkowych czynności w polu listy. Przed zwróceniem - 1 lub - 2, możesz można ustawić zaznaczenia lub Przenieś karetkę lub oba. Aby ustawić zaznaczenia, użyj [SetCurSel](#setcursel) lub [SetSel](#setsel). Aby przenieść karetki, użyj [SetCaretIndex](#setcaretindex).  
  
 Zwracane wartości 0 lub większą Określa indeks elementu w polu listy i wskazuje, że pole listy powinien wykonywać domyślną akcję dla naciśnięcia w danym elemencie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]  
  
##  <a name="clistbox"></a>CListBox::CListBox  
 Konstruuje `CListBox` obiektu.  
  
```  
CListBox();
```  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CListBox` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora **clistbox —** , a następnie wywołać **Utwórz**, która inicjuje pola listy z systemem Windows i dołącza go do `CListBox`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CListBox::CompareItem  
 Wywoływane przez platformę, by określić względne położenie nowego elementu w polu listy posortowane rysowania przez właściciela.  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpCompareItemStruct`  
 Długie wskaźnik do `COMPAREITEMSTRUCT` struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa względne położenie dwa elementy opisane w [COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md) struktury. Może być jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|-1|Element 1 sortuje przed elementem 2.|  
|0|Element 1 i element 2 Sortuj takie same.|  
|1|Element 1 sortuje po elemencie 2.|  
  
 Zobacz [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) opis `COMPAREITEMSTRUCT` struktury.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta funkcja członkowska nie działa. Jeśli tworzenie rysowania przez właściciela pole listy z **lbs_sort —** stylu, konieczne jest przesłonięcie tej funkcji członkowskiej ułatwiających platformę sortowanie nowe elementy dodane do listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]  
  
##  <a name="create"></a>CListBox::Create  
 Tworzy okno listy systemu Windows i dołącza go do `CListBox` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl pola listy. Zastosuj dowolną kombinację [style pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) do pola.  
  
 `rect`  
 Określa pole listy rozmiar i położenie. Może to być albo `CRect` obiektu lub `RECT` struktury.  
  
 `pParentWnd`  
 Określa okno nadrzędne pole listy (zazwyczaj `CDialog` obiektu). Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CListBox` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać **Utwórz**, która inicjuje pola listy z systemem Windows i dołącza go do `CListBox` obiektu.  
  
 Gdy **Utwórz** wykonuje system Windows wysyła [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), i [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) wiadomości do kontrolki pola listy.  
  
 Komunikaty te są obsługiwane przez domyślnie [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), i [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funkcje Członkowskie w `CWnd` klasy podstawowej. Aby rozszerzyć domyślnej obsługi wiadomości, klasa wyprowadzona z `CListBox`, Dodaj mapowanie komunikatów do nowej klasy i zastąpienie poprzedniego funkcje Członkowskie obsługi wiadomości. Zastąpienie `OnCreate`, na przykład, aby wykonać wymagane inicjowania dla nowej klasy.  
  
 Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do formantu pola listy.  
  
- **Ws_child —** zawsze  
  
- **Ws_visible —** zwykle  
  
- **Ws_disabled —** rzadko  
  
- **Ws_vscroll —** można dodać pionowy pasek przewijania  
  
- **Ws_hscroll —** Aby dodać poziomy pasek przewijania  
  
- **Ws_group —** na grupowanie formantów  
  
- **Ws_tabstop —** umożliwia klawisza TAB do tego formantu  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]  
  
##  <a name="deleteitem"></a>CListBox::DeleteItem  
 Wywoływane przez platformę, gdy użytkownik usuwa element z rysowania przez właściciela `CListBox` obiektu lub niszczy pola listy.  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDeleteItemStruct`  
 Długie wskaźnik do systemu Windows [DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md) struktury, który zawiera informacje o usuniętego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja nie działa. Należy przesłonić tę funkcję, aby odświeżyć rysowania przez właściciela pole listy zgodnie z potrzebami.  
  
 Zobacz [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) opis `DELETEITEMSTRUCT` struktury.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]  
  
##  <a name="deletestring"></a>CListBox::DeleteString  
 Usuwa element w pozycji `nIndex` w polu listy.  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks ciąg, który ma zostać usunięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba parametrów na liście. Wartość zwracana jest **LB_ERR** Jeśli `nIndex` Określa indeks jest większy niż liczba elementów na liście.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie elementy występujące po słowie `nIndex` teraz Przenieś w dół o jedną pozycję. Na przykład jeśli pole listy zawiera dwa elementy, usunięcie pierwszy element spowoduje, że element pozostałych się teraz na pierwszym miejscu. `nIndex`= 0 dla elementu na pierwszym miejscu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]  
  
##  <a name="dir"></a>CListBox::Dir  
 Dodaje listę nazw plików i/lub dysków do pola listy.  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>Parametry  
 `attr`  
 Może być dowolną kombinacją `enum` wartości opisanego w **CFile::GetStatu**[s](../../mfc/reference/cfile-class.md#getstatus), lub dowolną kombinację następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|0x0000|Może być zapisu lub odczytu z pliku.|  
|0X0001|Plik można odczytywać, ale nie zapisane.|  
|0X0002|Plik jest ukryta i nie ma na liście zawartości katalogu.|  
|0X0004|Plik jest plikiem systemu.|  
|0x0010|Nazwa określona przez `lpszWildCard` Określa katalog.|  
|0x0020|Plik został zarchiwizowany.|  
|0x4000|Obejmują wszystkie dyski, które odpowiada nazwie określonej przez `lpszWildCard`.|  
|0x8000|Flagę Exclusive. Jeśli ustawiono flagę exclusive, wyświetlane są tylko pliki o określonym typie. W przeciwnym razie pliki określonego typu są wyświetlane oprócz plików "normal".|  
  
 `lpszWildCard`  
 Wskazuje ciąg specyfikacji pliku. Ten ciąg może zawierać symboli wieloznacznych (na przykład *.\*).  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pliku ostatniego dodany do listy. Wartość zwracana jest **LB_ERR** Jeśli wystąpi błąd; wartość zwracana jest **LB_ERRSPACE** Jeśli dostępny do przechowywania nowych ciągów jest za mało miejsca.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]  
  
##  <a name="drawitem"></a>CListBox::DrawItem  
 Wywoływane przez platformę, gdy visual aspekt rysowania przez właściciela zmiany z pola listy.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Długie wskaźnik do [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) strukturę, która zawiera informacje o typie rysunku wymagane.  
  
### <a name="remarks"></a>Uwagi  
 **ItemAction** i **itemState** członkami `DRAWITEMSTRUCT` struktury zdefiniować rysowania akcję, która ma zostać wykonane.  
  
 Domyślnie ta funkcja członkowska nie działa. Przesłonić tę funkcję elementu członkowskiego, aby zaimplementować rysunku rysowania przez właściciela `CListBox` obiektu. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interfejsu (GDI), wybrane kontekst wyświetlania dostarczane w `lpDrawItemStruct` przed ten element członkowski kończy funkcji.  
  
 Zobacz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) opis `DRAWITEMSTRUCT` struktury.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]  
  
##  <a name="findstring"></a>CListBox::FindString  
 Znajduje pierwszy ciąg w polu listy, który zawiera określony prefiks bez zmiany zaznaczenia pola listy.  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nStartAfter`  
 Zawiera liczony od zera indeks elementu przed pierwszym elementem do wyszukania. Podczas wyszukiwania przez nią miejsce osiągnie dolnej części pola listy, która kontynuuje od górnej krawędzi pola listy ponownie element określony przez `nStartAfter`. Jeśli `nStartAfter` wynosi -1, przeszukiwany jest pole całą listę od początku.  
  
 `lpszItem`  
 Wskazuje ciąg zakończony zerem, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależny, więc ten ciąg może zawierać żadnych kombinacji wielkich i małych liter.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pasującego elementu lub **LB_ERR** Jeśli wyszukiwanie nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [SelectString](#selectstring) funkcji członkowskiej zarówno Znajdź i wybierz ciąg.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]  
  
##  <a name="findstringexact"></a>CListBox::FindStringExact  
 Znajduje pierwszy ciąg pole listy, który dopasowuje ciąg określony w `lpszFind`.  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndexStart`  
 Określa liczony od zera indeks elementu przed pierwszym elementem do wyszukania. Podczas wyszukiwania przez nią miejsce osiągnie dolnej części pola listy, która kontynuuje od górnej krawędzi pola listy ponownie element określony przez `nIndexStart`. Jeśli `nIndexStart` wynosi -1, przeszukiwany jest pole całą listę od początku.  
  
 `lpszFind`  
 Wskazuje zerem ciąg do wyszukania. Ten ciąg może zawierać pełną nazwę pliku z rozszerzeniem. Wyszukiwanie nie jest uwzględniana wielkość liter, więc ciąg może zawierać żadnych kombinacji wielkich i małych liter.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks pasującego elementu, lub **LB_ERR** Jeśli wyszukiwanie nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pole listy została utworzona przy użyciu stylu rysowania przez właściciela, ale bez [lbs_hasstrings —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl `FindStringExact` funkcji członkowskiej próbuje dopasować wartość bitowego względem wartości `lpszFind`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]  
  
##  <a name="getanchorindex"></a>CListBox::GetAnchorIndex  
 Pobiera liczony od zera indeks bieżącego elementu zakotwiczenia w polu listy.  
  
```  
int GetAnchorIndex() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks bieżącego elementu zakotwiczenia w przypadku powodzenia; w przeciwnym razie **LB_ERR**.  
  
### <a name="remarks"></a>Uwagi  
 W polu listy wielokrotnego wyboru elementu zakotwiczenia jest pierwszego lub ostatniego elementu w bloku ciągłe wybrane elementy.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CListBox::SetAnchorIndex](#setanchorindex).  
  
##  <a name="getcaretindex"></a>CListBox::GetCaretIndex  
 Określa indeks elementu, który ma prostokąt fokusu w polu listy wielokrotnego wyboru.  
  
```  
int GetCaretIndex() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks elementu, który ma prostokąt fokusu w polu listy. Jeśli pole listy ma postać pola listy z pojedynczym wyborem, zwracana wartość jest indeks elementu, który jest zaznaczone, jeśli.  
  
### <a name="remarks"></a>Uwagi  
 Element może lub nie mogą być zaznaczone.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CListBox::SetCaretIndex](#setcaretindex).  
  
##  <a name="getcount"></a>CListBox::GetCount  
 Pobiera liczbę elementów w polu listy.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w polu listy lub **LB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 Zwrócona liczba jest większa niż wartość indeksu ostatniego elementu (indeks jest liczony od zera) o jeden.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]  
  
##  <a name="getcursel"></a>CListBox::GetCurSel  
 Pobiera liczony od zera Indeks aktualnie zaznaczonego elementu w polu listy pojedynczego wyboru.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera Indeks aktualnie zaznaczonego elementu, jeśli jest pole listy z pojedynczym wyborem. Jest `LB_ERR` Jeśli wybrano żadnego elementu.  
  
 W polu listy wielokrotnego wyboru indeks elementu, który ma fokus.  
  
### <a name="remarks"></a>Uwagi  
 Nie wywołuj `GetCurSel` pola listy wielokrotnego wyboru. Użyj [CListBox::GetSelItems](#getselitems) zamiast tego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]  
  
##  <a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent  
 W polu listy pobiera szerokość w pikselach, według których on mogą być przewijane w poziomie.  
  
```  
int GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Przewijany szerokość pola listy w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ma to zastosowanie tylko wtedy, gdy pole listy ma poziomy pasek przewijania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]  
  
##  <a name="getitemdata"></a>CListBox::GetItemData  
 Pobiera wartość bitowego dostarczone przez aplikację skojarzoną z elementem pola listy.  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 32-bitową wartość skojarzoną z elementem, lub **LB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 Wartość bitowego `dwItemData` parametr [SetItemData](#setitemdata) wywołania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]  
  
##  <a name="getitemdataptr"></a>CListBox::GetItemDataPtr  
 Pobiera wartość 32-bitowych dostarczone przez aplikację skojarzoną z elementem pole listy jako wskaźnik ( **void\***).  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pobiera wskaźnik lub wartość -1, jeśli wystąpi błąd.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]  
  
##  <a name="getitemheight"></a>CListBox::GetItemHeight  
 Określa wysokość elementy w polu listy.  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu w polu listy. Ten parametr jest używany tylko wtedy, gdy pole listy ma **lbs_ownerdrawvariable —** styl; w przeciwnym razie musi mieć wartość 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość w pikselach elementów w polu listy. Jeśli pole listy ma [lbs_ownerdrawvariable —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, jest zwracana wartość wysokość element określony przez `nIndex`. Jeśli wystąpi błąd, jest zwracana wartość **LB_ERR**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]  
  
##  <a name="getitemrect"></a>CListBox::GetItemRect  
 Pobiera element granice pole listy wymiary prostokąta, gdy jest aktualnie wyświetlany w oknie pola listy.  
  
```  
int GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu.  
  
 `lpRect`  
 Określa długi wskaźnik [struktura RECT](../../mfc/reference/rect-structure1.md) odbierająca współrzędne klienta pole listy elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 **LB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]  
  
##  <a name="getlistboxinfo"></a>CListBox::GetListBoxInfo  
 Pobiera liczbę elementów w kolumnie.  
  
```  
DWORD GetListBoxInfo() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów na kolumnie `CListBox` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje [LB_GETLISTBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775208) komunikatu, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getlocale"></a>CListBox::GetLocale  
 Pobiera ustawienia regionalne używane przez pola listy.  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość identyfikatora (LCID) ustawień regionalnych dla ciągów w polu listy.  
  
### <a name="remarks"></a>Uwagi  
 Ustawienia regionalne służy na przykład aby określić kolejność sortowania ciągów w polu posortowaną listę.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CListBox::SetLocale](#setlocale).  
  
##  <a name="getsel"></a>CListBox::GetSel  
 Pobiera stan zaznaczenia elementu.  
  
```  
int GetSel(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba dodatnia, jeśli określony element jest wybrany; w przeciwnym razie jest 0. Wartość zwracana jest `LB_ERR` w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska współpracuje z obu polach listy wyboru wielu i jednego.  
  
 Aby uzyskać indeks elementu pola obecnie wybranej listy, użyj [CListBox::GetCurSel](#getcursel).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]  
  
##  <a name="getselcount"></a>CListBox::GetSelCount  
 Pobiera całkowitą liczbę wybranych elementów w polu listy wielokrotnego wyboru.  
  
```  
int GetSelCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wybranych elementów w polu listy. Jeśli pole listy ma postać pola listy z pojedynczym wyborem, jest zwracana wartość **LB_ERR**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CListBox::GetSelItems](#getselitems).  
  
##  <a name="getselitems"></a>CListBox::GetSelItems  
 Wstawia buforu tablicę liczb całkowitych, która określa element liczby wybranych elementów w polu listy wielokrotnego wyboru.  
  
```  
int GetSelItems(
    int nMaxItems,  
    LPINT rgIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nMaxItems`  
 Określa maksymalną liczbę wybranych elementów, których numery elementu zostaną umieszczone w buforze.  
  
 `rgIndex`  
 Określa wskaźnik do dużej liczby liczb całkowitych, określony przez bufor `nMaxItems`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rzeczywista liczba elementów umieszczone w buforze. Jeśli pole listy ma postać pola listy z pojedynczym wyborem, jest zwracana wartość `LB_ERR`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]  
  
##  <a name="gettext"></a>CListBox::GetText  
 Pobiera ciąg z pola listy.  
  
```  
int GetText(
    int nIndex,  
    LPTSTR lpszBuffer) const;  
  
void GetText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks ciąg do pobrania.  
  
 `lpszBuffer`  
 Wskazuje buforu, który odbiera ciąg. Rozmiar buforu musi mieć wystarczającą ilość miejsca na ciąg i znak końcowy null. Rozmiar ciągu można ustalić wcześniej, wywołując `GetTextLen` funkcję elementu członkowskiego.  
  
 `rString`  
 Odwołanie do `CString` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość (w bajtach) ciąg, z wyłączeniem znak końcowy null. Jeśli `nIndex` nie określa nieprawidłowy indeks, jest zwracana wartość **LB_ERR**.  
  
### <a name="remarks"></a>Uwagi  
 Drugi formularz tego elementu członkowskiego funkcji wypełnienia `CString` obiekt z ciągu tekstowego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]  
  
##  <a name="gettextlen"></a>CListBox::GetTextLen  
 Pobiera długość ciągu w elemencie pola listy.  
  
```  
int GetTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeksu ciągu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość ciągu znakami z wyłączeniem znak końcowy null. Jeśli `nIndex` nie określa nieprawidłowy indeks, jest zwracana wartość **LB_ERR**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CListBox::GetText](#gettext).  
  
##  <a name="gettopindex"></a>CListBox::GetTopIndex  
 Pobiera liczony od zera indeks pierwszego widocznego elementu w polu listy.  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pierwszego widocznego elementu w polu listy, jeśli to się powiedzie, **LB_ERR** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Początkowo element 0 znajduje się na początku listy, ale jeśli pole listy jest przewijane, inny element może być u góry.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]  
  
##  <a name="initstorage"></a>CListBox::InitStorage  
 Przydziela pamięć do przechowywania elementów w polu listy.  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 `nItems`  
 Określa liczbę elementów do dodania.  
  
 `nBytes`  
 Określa ilość pamięci w bajtach, można przydzielić elementu ciągów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli się powiedzie, maksymalna liczba elementy listy można przechowywać przed pamięci jest konieczna, w przeciwnym razie **LB_ERRSPACE**, co oznacza brak wystarczającej ilości pamięci jest dostępna.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji przed dodaniem dużą liczbę elementów do `CListBox`.  
  
 Ta funkcja pomaga przyspieszyć inicjowania pola listy, które ma dużą liczbę elementów (więcej niż 100). Go preallocates określoną ilością pamięci, tak że kolejne [AddString](#addstring), [InsertString](#insertstring), i [Dir](#dir) funkcje pobierać najkrótszym czasie. Szacuje można użyć parametrów. Jeśli overestimate, niektóre dodatkową pamięć jest przydzielony; Jeśli w przypadku licznik nie uwzględniać, normalne alokacji jest używana dla elementów, które przekraczają ilość przydzielony wstępnie.  
  
 Windows 95/98: `nItems` jest ograniczony do 16-bitowych wartości parametru. Oznacza to, że pola listy nie może zawierać więcej niż 32 767 elementów. Mimo że liczba elementów jest ograniczone, łączny rozmiar elementów w polu listy jest ograniczona tylko przez ilość dostępnej pamięci.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]  
  
##  <a name="insertstring"></a>CListBox::InsertString  
 Wstawia ciąg do listy.  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks pozycji, aby wstawić ciąg. Jeśli ten parametr ma wartość -1, ten ciąg jest dodawany na końcu listy.  
  
 `lpszItem`  
 Wskazuje ciąg zakończony zerem, który ma zostać wstawiony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pozycji, w którym została umieszczona ciąg. Wartość zwracana jest **LB_ERR** Jeśli wystąpi błąd; wartość zwracana jest **LB_ERRSPACE** Jeśli niewystarczającej ilości miejsca jest dostępne do przechowywania nowych parametrów.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od [AddString](#addstring) funkcji członkowskiej `InsertString` nie powoduje, że lista z [lbs_sort —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, który ma zostać posortowana.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]  
  
##  <a name="itemfrompoint"></a>CListBox::ItemFromPoint  
 Określa element pole listy najbliższy punkt określony w `pt`.  
  
```  
UINT ItemFromPoint(
    CPoint pt,  
    BOOL& bOutside) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Wskaż, dla której ma zostać znaleziony element najbliższej określony względem lewego górnego rogu obszaru klienckiego pola listy.  
  
 `bOutside`  
 Odwołanie do `BOOL` zmiennej, która zostanie ustawiona na `TRUE` Jeśli `pt` znajduje się poza obszaru klienckiego elementu najbliższej pola listy `FALSE` Jeśli `pt` znajduje się wewnątrz obszaru klienckiego elementu najbliższej pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu najbliższy punkt określony w `pt`.  
  
### <a name="remarks"></a>Uwagi  
 Można użyć tej funkcji, aby określić, który przesuwa kursor myszy nad element pola listy.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CListBox::SetAnchorIndex](#setanchorindex).  
  
##  <a name="measureitem"></a>CListBox::MeasureItem  
 Wywoływane przez platformę, gdy jest tworzony przy użyciu stylu rysowania przez właściciela pole listy.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpMeasureItemStruct`  
 Długie wskaźnik do [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta funkcja członkowska nie działa. Zastąpienie tej funkcji Członkowskich i wypełnij `MEASUREITEMSTRUCT` struktury poinformować system Windows wymiarów pola listy. Jeśli pole listy jest tworzony z [lbs_ownerdrawvariable —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, struktura wywołuje tę funkcję elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ten element członkowski zostanie wywołana tylko raz.  
  
 Aby uzyskać więcej informacji na temat używania [lbs_ownerdrawfixed —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl rysowania przez właściciela pole listy utworzone za pomocą `SubclassDlgItem` funkcji członkowskiej klasy `CWnd`, można znaleźć w omówieniu w [14 Uwaga techniczna](../../mfc/tn014-custom-controls.md).  
  
 Zobacz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) opis `MEASUREITEMSTRUCT` struktury **.**  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]  
  
##  <a name="resetcontent"></a>CListBox::ResetContent  
 Usuwa wszystkie elementy w polu listy.  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]  
  
##  <a name="selectstring"></a>CListBox::SelectString  
 Wyszukiwanie elementu pola listy, które odpowiadają określonym ciągiem znaków, a jeśli pasujący element zostanie znaleziony, jest ona wybierana elementu.  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartAfter`  
 Zawiera liczony od zera indeks elementu przed pierwszym elementem do wyszukania. Podczas wyszukiwania przez nią miejsce osiągnie dolnej części pola listy, która kontynuuje od górnej krawędzi pola listy ponownie element określony przez `nStartAfter`. Jeśli `nStartAfter` wynosi -1, przeszukiwany jest pole całą listę od początku.  
  
 `lpszItem`  
 Wskazuje ciąg zakończony zerem, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależny, więc ten ciąg może zawierać żadnych kombinacji wielkich i małych liter.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks wybranego elementu, jeśli wyszukiwanie zakończyło się pomyślnie. Jeśli wyszukiwanie nie powiodło się, że zwracana wartość jest **LB_ERR** i nie ulega zmianie bieżącego zaznaczenia.  
  
### <a name="remarks"></a>Uwagi  
 Pola listy jest przewijane, jeśli to konieczne, można wyświetlić wybranego elementu w widoku.  
  
 Ta funkcja członkowska nie można używać z pola listy, który ma [lbs_multiplesel —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu.  
  
 Element jest wybrany tylko wtedy, gdy jego znaków (od punktu początkowego) pasować do znaków w ciągu określonej przez `lpszItem`.  
  
 Użyj `FindString` funkcji członkowskiej, aby znaleźć ciąg bez zaznaczania elementu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]  
  
##  <a name="selitemrange"></a>CListBox::SelItemRange  
 Wybiera wiele kolejnych elementów w polu listy wielokrotnego wyboru.  
  
```  
int SelItemRange(
    BOOL bSelect,  
    int nFirstItem,  
    int nLastItem);
```  
  
### <a name="parameters"></a>Parametry  
 `bSelect`  
 Określa, jak ustawić zaznaczenia. Jeśli `bSelect` jest **TRUE**, ciąg jest zaznaczone i wyróżniony; Jeśli **FALSE**, zaznaczenie jest usunięte i ciąg nie jest zaznaczone.  
  
 `nFirstItem`  
 Określa liczony od zera indeks pierwszego elementu można ustawić.  
  
 `nLastItem`  
 Określa liczony od zera indeks ostatni element do ustawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 **LB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji Członkowskich tylko z polami listy wielokrotnego wyboru. Jeśli musisz wybrać tylko jeden element w polu listy wielokrotnego wyboru — oznacza to, że jeśli `nFirstItem` jest równa `nLastItem` — wywołania [SetSel](#setsel) zamiast funkcji członkowskiej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]  
  
##  <a name="setanchorindex"></a>CListBox::SetAnchorIndex  
 Ustawia zakotwiczenia w pole listy wielokrotnego wyboru, aby rozpocząć zaznaczania rozszerzonego.  
  
```  
void SetAnchorIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu pola listy, który będzie zakotwiczenia.  
  
### <a name="remarks"></a>Uwagi  
 W polu listy wielokrotnego wyboru elementu zakotwiczenia jest pierwszego lub ostatniego elementu w bloku ciągłe wybrane elementy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]  
  
##  <a name="setcaretindex"></a>CListBox::SetCaretIndex  
 Ustawia element pod określonym indeksem prostokąt fokusu w polu listy wielokrotnego wyboru.  
  
```  
int SetCaretIndex(
    int nIndex,  
    BOOL bScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu do odbierania prostokąt fokusu w polu listy.  
  
 *bScroll*  
 Jeśli ta wartość wynosi 0, element jest przewijane, dopóki nie zostanie całkowicie widoczna. Jeśli ta wartość nie jest 0, jest przewijane elementu, dopóki nie zostanie co najmniej częściowo widoczne.  
  
### <a name="return-value"></a>Wartość zwracana  
 **LB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli element nie jest widoczna, jest przewijane w widoku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]  
  
##  <a name="setcolumnwidth"></a>CListBox::SetColumnWidth  
 Ustawia szerokość w pikselach wszystkie kolumny w wielokolumnowe pole listy (utworzone za pomocą [lbs_multicolumn —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl).  
  
```  
void SetColumnWidth(int cxWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `cxWidth`  
 Określa szerokość w pikselach wszystkie kolumny.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]  
  
##  <a name="setcursel"></a>CListBox::SetCurSel  
 Wybiera ciągu i przewija do widoku, jeśli to konieczne.  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>Parametry  
 `nSelect`  
 Określa liczony od zera indeks ciąg, który można wybrać. Jeśli `nSelect` wynosi -1, pole listy ma ustawioną wartość ma Brak zaznaczenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `LB_ERR`Jeśli wystąpi błąd.  
  
### <a name="remarks"></a>Uwagi  
 Po wybraniu nowego ciągu listy Usuwa wyróżnienie z poprzednio wybranego ciągu.  
  
 Użyj tej funkcji Członkowskich tylko z polami listy z pojedynczym wyborem.  
  
 Aby ustawić lub usunąć zaznaczenie w polu listy wielokrotnego wyboru, należy użyć [CListBox::SetSel](#setsel).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]  
  
##  <a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent  
 Określa szerokość w pikselach, według których pole listy mogą być przewijane w poziomie.  
  
```  
void SetHorizontalExtent(int cxExtent);
```  
  
### <a name="parameters"></a>Parametry  
 *cxExtent*  
 Określa liczbę pikseli, za pomocą których pole listy mogą być przewijane w poziomie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli rozmiar pola listy jest mniejszy od tej wartości, poziomy pasek przewijania w poziomie przewinie elementy w polu listy. Jeśli pole listy ma tak duże lub większych niż ta wartość, poziomy pasek przewijania jest ukryty.  
  
 Aby odpowiedzieć na wywołanie `SetHorizontalExtent`, pole listy musi zdefiniowane z [ws_hscroll —](../../mfc/reference/styles-used-by-mfc.md#window-styles) stylu.  
  
 Ta funkcja członkowska nie jest przydatne w przypadku pola wielokolumnowym elemencie listy. Pola listy wielokolumnowe, można wywołać `SetColumnWidth` funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]  
  
##  <a name="setitemdata"></a>CListBox::SetItemData  
 Ustawia wartość 32-bitowych skojarzone z określonym elementem w polu listy.  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu.  
  
 `dwItemData`  
 Określa wartość, która ma zostać skojarzony z elementem.  
  
### <a name="return-value"></a>Wartość zwracana  
 **LB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]  
  
##  <a name="setitemdataptr"></a>CListBox::SetItemDataPtr  
 Ustawia wartość 32-bitowych skojarzony z określonym elementem w polu listy jako wskaźnik określony ( **void\***).  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu.  
  
 `pData`  
 Określa wskaźnik do skojarzenia z elementem.  
  
### <a name="return-value"></a>Wartość zwracana  
 **LB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 Ten wskaźnik pozostaje ważny przez cały okres istnienia pola listy, mimo że względne położenie elementu w polu listy może ulec zmianie, elementy są dodawane lub usuwane. W związku z tym można zmienić indeks elementu w polu, ale wskaźnik pozostaje wiarygodne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]  
  
##  <a name="setitemheight"></a>CListBox::SetItemHeight  
 Określa wysokość elementów w polu listy.  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu w polu listy. Ten parametr jest używany tylko wtedy, gdy pole listy ma **lbs_ownerdrawvariable —** styl; w przeciwnym razie musi mieć wartość 0.  
  
 `cyItemHeight`  
 Określa wysokość w pikselach elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 **LB_ERR** Jeśli indeks lub wysokość jest nieprawidłowa.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pole listy ma [lbs_ownerdrawvariable —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, ta funkcja Ustawia wysokość element określony przez `nIndex`. W przeciwnym razie ta funkcja Ustawia wysokość wszystkie elementy w polu listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]  
  
##  <a name="setlocale"></a>CListBox::SetLocale  
 Określa identyfikator ustawień regionalnych dla tego pola listy.  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>Parametry  
 `nNewLocale`  
 Nowa wartość identyfikator (LCID) ustawień regionalnych można ustawić pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedniej ustawień regionalnych (LCID) wartość identyfikatora dla tego pola listy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli **SetLocale** nie jest wywoływany, domyślne ustawienia regionalne są uzyskiwane z systemu. Można zmodyfikować domyślne ustawienia regionalne tego systemu za pomocą Panelu sterowania regionalne (lub międzynarodowy) aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]  
  
##  <a name="setsel"></a>CListBox::SetSel  
 Wybiera ciąg w polu listy wielokrotnego wyboru.  
  
```  
int SetSel(
    int nIndex,  
    BOOL bSelect = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Zawiera liczony od zera indeks ciąg do ustawienia. Jeśli wartość -1, zaznaczenie jest dodane lub usunięte ze wszystkich ciągów w zależności od wartości `bSelect`.  
  
 `bSelect`  
 Określa, jak ustawić zaznaczenia. Jeśli `bSelect` jest `TRUE`, ciąg jest zaznaczone i wyróżniony; Jeśli `FALSE`, zaznaczenie jest usunięte i ciąg nie jest zaznaczone. Określony ciąg jest zaznaczony, a następnie wyróżnione domyślnie.  
  
### <a name="return-value"></a>Wartość zwracana  
 `LB_ERR`Jeśli wystąpi błąd.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji Członkowskich tylko z polami listy wielokrotnego wyboru.  
  
 Aby wybrać element z pola listy z pojedynczym wyborem, użyj [CListBox::SetCurSel](#setcursel).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]  
  
##  <a name="settabstops"></a>CListBox::SetTabStops  
 Określa pozycje tabulatorów w polu listy.  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>Parametry  
 `cxEachStop`  
 Tabulatorów są ustawione na każdym `cxEachStop` jednostki okna dialogowego. Zobacz *rgTabStops* opis jednostki okna dialogowego.  
  
 `nTabStops`  
 Określa liczbę tabulatorów w polu listy.  
  
 `rgTabStops`  
 Wskazuje pierwszego elementu członkowskiego tablicy liczb całkowitych zawierającą pozycje tabulatorów w jednostkach okna dialogowego. Jednostki okna dialogowego jest odległość pozioma lub pionowa. Jednostki okna dialogowego w poziomie jest taki sam, jak jedna czwarta bieżąca jednostka podstawowa szerokość okna dialogowego i jednostki okna dialogowego pionowy jest równa 1 / 8 bieżąca jednostka podstawowa wysokość okna dialogowego. Jednostki podstawowy okna dialogowego są obliczane na podstawie wysokość i szerokość bieżącej czcionki systemowej. **GetDialogBaseUnits** systemu Windows funkcja zwraca bieżącego okna dialogowego podstawowej jednostki w pikselach. Tabulatory muszą być posortowane w rosnącej kolejności. Wstecz karty nie są dozwolone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ustawiono wszystkich kart; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ustawić tabulatorów domyślny rozmiar jednostki okna dialogowego 2, należy wywołać wersji bez parametrów funkcji członkowskiej. Tabulatorów rozmiar niż 2, wywołaj wersji z `cxEachStop` argumentu.  
  
 Aby ustawić tabulatory na tablicę rozmiary, użyj wersji z `rgTabStops` i `nTabStops` argumentów. Tabulator zostanie ustawiona dla każdej wartości w `rgTabStops`, maksymalnie liczbie określonej przez `nTabStops`.  
  
 Aby odpowiedzieć na wywołanie `SetTabStops` funkcji członkowskiej liście muszą być utworzone z [lbs_usetabstops —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]  
  
##  <a name="settopindex"></a>CListBox::SetTopIndex  
 Powoduje, że element określonego pola listy jest widoczny.  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie, lub **LB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 System jest przewijane pole listy do element określony przez `nIndex` pojawia się na początku listy pola lub przewijania maksymalny zakres został osiągnięty.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]  
  
##  <a name="vkeytoitem"></a>CListBox::VKeyToItem  
 Wywoływane przez platformę, gdy okno nadrzędne pola listy otrzymuje `WM_VKEYTOITEM` komunikat w polu listy.  
  
```  
virtual int VKeyToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nKey`  
 Kod klucza wirtualnego klucza użytkownik kliknął przycisk. Listę standardowych wirtualnego kodów klucza Zobacz Winuser.h  
  
 `nIndex`  
 Bieżąca pozycja karetkę pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca - 2 żadne dodatkowe działania, - 1 dla domyślnej akcji lub nieujemna liczba, aby określić indeks elementu do pola listy, na którym należy wykonać domyślną akcję dla naciśnięcia klawisza.  
  
### <a name="remarks"></a>Uwagi  
 `WM_VKEYTOITEM` Komunikat wysyłany przez pole listy po odebraniu `WM_KEYDOWN` wiadomości, ale tylko jeśli pole listy spełnia następujące:  
  
-   Ma [lbs_wantkeyboardinput —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl zestawu.  
  
-   Zawiera co najmniej jeden element.  
  
 Użytkownik nigdy nie powinien wywoływać tej funkcji samodzielnie. Należy przesłonić tę funkcję, aby podać własną niestandardową obsługę komunikatów klawiatury.  
  
 Musi zwracać wartość platformę stwierdzić, jaką akcję wykonać zastąpienia. Wartość zwracana - 2 wskazuje, że aplikacja obsługiwane wszystkie aspekty zaznaczenie elementu i wymaga żadnych dodatkowych czynności w polu listy. Przed zwróceniem - 2, można ustawić zaznaczenia lub Przenieś karetkę lub oba. Aby ustawić zaznaczenia, użyj [SetCurSel](#setcursel) lub [SetSel](#setsel). Aby przenieść karetki, użyj [SetCaretIndex](#setcaretindex).  
  
 Zwracana wartość - 1 wskazuje, że pole listy domyślną akcję należy wykonywać w odpowiedzi na naciśnięcie klawisza. Domyślna implementacja zwraca - 1.  
  
 Zwracane wartości 0 lub większą Określa indeks elementu w polu listy i wskazuje, że pole listy powinien wykonywać domyślną akcję dla naciśnięcia w danym elemencie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CTRLTEST](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Klasa CButton](../../mfc/reference/cbutton-class.md)   
 [Ccombobox — klasa](../../mfc/reference/ccombobox-class.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)   
 [Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [Klasa CStatic](../../mfc/reference/cstatic-class.md)
