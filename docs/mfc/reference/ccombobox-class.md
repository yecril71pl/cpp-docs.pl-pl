---
title: "Ccombobox — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
dev_langs: C++
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a8b9c9de69f9042f68cc04d435070ade9b24dd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccombobox-class"></a>Ccombobox — klasa
Udostępnia funkcjonalność pola kombi systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CComboBox : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComboBox::CComboBox](#ccombobox)|Konstruuje `CComboBox` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComboBox::AddString](#addstring)|Dodaje ciąg do końca listy w polu listy, pola kombi lub w pozycji posortowane dla pola listy z **cbs_sort —** stylu.|  
|[CComboBox::Clear](#clear)|Usuwa (czyści) bieżące zaznaczenie w formancie edycyjnym.|  
|[CComboBox::CompareItem](#compareitem)|Wywoływane przez platformę, by określić względne położenie nowy element listy w polu kombi rysowanych przez właściciela posortowane.|  
|[CComboBox::Copy](#copy)|Kopiuje bieżącego zaznaczenia, jeśli istnieje, do Schowka w **CF_TEXT** format.|  
|[CComboBox::Create](#create)|Tworzy pole kombi i dołącza go do `CComboBox` obiektu.|  
|[CComboBox::Cut](#cut)|Usuwa (części) bieżącego zaznaczenia, jeśli w edycji kontroli i kopiuje usunięty tekst do Schowka w **CF_TEXT** format.|  
|[CComboBox::DeleteItem](#deleteitem)|Wywoływane przez platformę, gdy element listy są usuwane z pola kombi rysowanych przez właściciela.|  
|[CComboBox::DeleteString](#deletestring)|Usuwa ciąg z pola listy, pola kombi.|  
|[CComboBox::Dir](#dir)|Dodaje listę nazw plików do pola listy, pola kombi.|  
|[CComboBox::DrawItem](#drawitem)|Wywoływane przez platformę, gdy visual aspekt zmiany pola kombi rysowanych przez właściciela.|  
|[CComboBox::FindString](#findstring)|Znajduje pierwszy ciąg, który zawiera określony prefiks w polu listy, pola kombi.|  
|[CComboBox::FindStringExact](#findstringexact)|Znajduje pierwszy ciąg pole listy (w polu kombi), pasującej do określonego ciągu.|  
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Pobiera informacje o `CComboBox` obiektu.|  
|[CComboBox::GetCount](#getcount)|Pobiera liczbę elementów w polu listy, pola kombi.|  
|[CComboBox::GetCueBanner](#getcuebanner)|Pobiera tekst wskaźnika, który jest wyświetlany dla kontrolki pola kombi.|  
|[CComboBox::GetCurSel](#getcursel)|Pobiera indeks aktualnie zaznaczonego elementu w polu listy, pola kombi.|  
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Pobiera współrzędne ekranu widoczne (porzuconych w dół) listy rozwijanej kombi.|  
|[CComboBox::GetDroppedState](#getdroppedstate)|Określa, czy pole listy rozwijanej kombi jest widoczny (rozwinięto).|  
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Pobiera minimalna dozwolona szerokość dla części pola listy rozwijanej pola kombi.|  
|[CComboBox::GetEditSel](#geteditsel)|Pobiera początkowy i końcowy pozycji znaku bieżące zaznaczenie w formancie edycyjnym pola kombi.|  
|[CComboBox::GetExtendedUI](#getextendedui)|Określa, czy pole kombi ma domyślny interfejs użytkownika lub interfejsu użytkownika rozszerzonej.|  
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Zwraca szerokość w pikselach, że części pola listy, pola kombi mogą być przewijane w poziomie.|  
|[CComboBox::GetItemData](#getitemdata)|Pobiera wartość 32-bitowych dostarczone przez aplikację skojarzoną z elementem pola kombi.|  
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Pobiera wskaźnik 32-bitowych dostarczone przez aplikację jest skojarzony z elementem pola kombi.|  
|[CComboBox::GetItemHeight](#getitemheight)|Pobiera wysokość elementów listy w polu kombi.|  
|[CComboBox::GetLBText](#getlbtext)|Pobiera ciąg z pola listy, pola kombi.|  
|[CComboBox::GetLBTextLen](#getlbtextlen)|Pobiera długość ciągu w polu listy, pola kombi.|  
|[CComboBox::GetLocale](#getlocale)|Pobiera identyfikator ustawień regionalnych dla pola kombi.|  
|[CComboBox::GetMinVisible](#getminvisible)|Pobiera minimalną liczbę widocznych elementów na liście rozwijanej bieżącego pola kombi.|  
|[CComboBox::GetTopIndex](#gettopindex)|Zwraca indeks pierwszego widocznego elementu w polu listy pola kombi.|  
|[CComboBox::InitStorage](#initstorage)|Preallocates bloków pamięci dla elementów i ciągi w części pola listy, pola kombi.|  
|[CComboBox::InsertString](#insertstring)|Wstawia ciąg do pola listy, pola kombi.|  
|[CComboBox::LimitText](#limittext)|Ogranicza długość tekstu, który użytkownik może wprowadzić w formancie edycyjnym pola kombi.|  
|[CComboBox::MeasureItem](#measureitem)|Wywoływane przez platformę, aby określić wymiary pole kombi po utworzeniu pola kombi rysowanych przez właściciela.|  
|[CComboBox::Paste](#paste)|Wstawia danych ze Schowka do kontrolki edycji w bieżącym położeniu kursora. Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w **CF_TEXT** format.|  
|[CComboBox::ResetContent](#resetcontent)|Usuwa wszystkie elementy na liście pole i edytować kontrolki pola kombi.|  
|[CComboBox::SelectString](#selectstring)|Wyszukuje ciąg w polu listy, pola kombi oraz, jeśli ciąg zostanie znaleziony, wybiera ciąg w polu listy i kopiuje ciąg do kontrolki edycji.|  
|[CComboBox::SetCueBanner](#setcuebanner)|Ustawia tekst wskaźnika, który jest wyświetlany dla kontrolki pola kombi.|  
|[CComboBox::SetCurSel](#setcursel)|Wybiera ciąg w polu listy, pola kombi.|  
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Ustawia minimalna dozwolona szerokość dla części pola listy rozwijanej pola kombi.|  
|[CComboBox::SetEditSel](#seteditsel)|Wybiera znaków w formancie edycyjnym pola kombi.|  
|[CComboBox::SetExtendedUI](#setextendedui)|Wybiera domyślny interfejs użytkownika lub interfejsu użytkownika rozszerzonego pola kombi, które ma **cbs_dropdown —** lub **cbs_dropdownlist —** stylu.|  
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Określa szerokość w pikselach, że części pola listy, pola kombi mogą być przewijane w poziomie.|  
|[CComboBox::SetItemData](#setitemdata)|Ustawia wartość 32-bitowych skojarzone z określonym elementem w polu kombi.|  
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Ustawia wskaźnik 32-bitowych skojarzone z określonym elementem w polu kombi.|  
|[CComboBox::SetItemHeight](#setitemheight)|Określa wysokość elementów listy w polu kombi lub wysokość kontrolki edycji (lub statycznego tekstu) część pola kombi.|  
|[CComboBox::SetLocale](#setlocale)|Określa identyfikator ustawień regionalnych dla pola kombi.|  
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Ustawia minimalną liczbę widocznych elementów na liście rozwijanej bieżącego pola kombi.|  
|[CComboBox::SetTopIndex](#settopindex)|Określa, że pole listy część pole kombi, aby wyświetlić element z określonym indeksem u góry.|  
|[CComboBox::ShowDropDown](#showdropdown)|Pokazuje lub ukrywa pole listy ma pole kombi **cbs_dropdown —** lub **cbs_dropdownlist —** stylu.|  
  
## <a name="remarks"></a>Uwagi  
 Pole kombi składa się z pola listy połączone z statyczną kontrolkę lub kontrolki edycji. Pole listy części kontrolki mogą być wyświetlane przez cały czas lub mogą tylko listy rozwijanej, gdy użytkownik wybierze strzałkę listy rozwijanej obok kontrolki.  
  
 Obecnie wybranego elementu (jeśli istnieją) w polu listy są wyświetlane w statycznych lub formantu edycyjnego. Ponadto jeśli pole kombi ma styl listy rozwijanej, użytkownik może wpisać litery jeden z elementów na liście, a pola listy, jeśli jest widoczne, wyróżnione następnego elementu z początkową znaku.  
  
 W poniższej tabeli porównano trzy pola kombi [style](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles).  
  
|Styl|Gdy jest widoczne pole listy|Formant statyczny lub edycji|  
|-----------|-------------------------------|-----------------------------|  
|Proste|Zawsze|Edytowanie|  
|Lista rozwijana|Gdy rozwinięto|Edytowanie|  
|Listy rozwijanej|Gdy rozwinięto|Static|  
  
 Można utworzyć `CComboBox` obiektu z szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach należy najpierw wywołać konstruktora `CComboBox` do skonstruowania `CComboBox` obiektu; wywoływać [Utwórz](#create) funkcji członkowskiej utworzyć formantu i dołączenie go do `CComboBox` obiektu.  
  
 Jeśli chcesz obsługiwać Windows komunikaty powiadomień wysłane przez pole kombi do elementu nadrzędnego (zazwyczaj klasą pochodną `CDialog`), Dodaj funkcji członkowskiej wpisu i program obsługi komunikatów map wiadomości do klasy nadrzędnej dla każdego komunikatu.  
  
 Każdy wpis mapy komunikatów ma następującą postać:  
  
 **ON_**powiadomień **(**`id`**,**`memberFxn`**)**  
  
 gdzie `id` Określa identyfikator okna podrzędnego kontrolki pola kombi wysyłania powiadomienia i `memberFxn` jest nazwą funkcji członkowskiej nadrzędnego zostały zapisane do obsługi powiadomień.  
  
 Prototyp funkcji elementu nadrzędnego, jak wygląda następująco:  
  
 **afx_msg** `void` `memberFxn` **();**  
  
 Kolejność, w którym będą wysyłane powiadomienia niektórych nie można przewidzieć. W szczególności **CBN_SELCHANGE** powiadomienia mogą wystąpić przed lub po **CBN_CLOSEUP** powiadomień.  
  
 Potencjalne wpisy mapy wiadomości są następujące:  
  
- **ON_CBN_CLOSEUP** (Windows 3.1 lub nowszy). Pola listy, pola kombi została zamknięta. Ten komunikat powiadomienia nie są wysyłane do pola kombi, które ma [cbs_simple —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
- **ON_CBN_DBLCLK** użytkownik kliknie dwukrotnie ciąg w polu listy, pola kombi. To powiadomienie jest wysyłane tylko pola kombi z **cbs_simple —** stylu. Pola kombi z [cbs_dropdown —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [cbs_dropdownlist —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, dwukrotne nie może wystąpić, ponieważ jednym kliknięciem powoduje ukrycie pola listy.  
  
- **ON_CBN_DROPDOWN** ma listy rozwijanej pola listy, pola kombi (były widoczne). To powiadomienie może wystąpić tylko w przypadku pola kombi z **cbs_dropdown —** lub **cbs_dropdownlist —** stylu.  
  
- **ON_CBN_EDITCHANGE** użytkownik ma podjąć akcję, która może zmienić tekst w formancie edycyjnym części pola kombi. W odróżnieniu od **CBN_EDITUPDATE** komunikat, ten komunikat jest wysyłany po ekranie aktualizacji systemu Windows. Nie są wysyłane, jeśli pole kombi ma **cbs_dropdownlist —** stylu.  
  
- **ON_CBN_EDITUPDATE** części formancie edycyjnym pola kombi ma wyświetli zmieniony tekst. To powiadomienie jest wysyłane po formantu ma sformatowanego tekstu, ale przed wyświetleniem tekst. Nie są wysyłane, jeśli pole kombi ma **cbs_dropdownlist —** stylu.  
  
- **ON_CBN_ERRSPACE** pola kombi nie może przydzielić wystarczającej ilości pamięci do spełnienia określonego żądania.  
  
- **ON_CBN_SELENDCANCEL** (Windows 3.1 lub nowszy). Wskazuje, że wybór użytkownika powinno być anulowane. Użytkownik kliknie pozycję, a następnie klika przycisk innego okna lub kontrolki, aby ukryć pola listy, pola kombi. To powiadomienie jest wysyłane przed **CBN_CLOSEUP** komunikat powiadomienia, aby wskazać, że wybór użytkownika należy ją ignorować. **CBN_SELENDCANCEL** lub **CBN_SELENDOK** powiadomienie jest wysyłane nawet wtedy, gdy **CBN_CLOSEUP** komunikatu powiadomienia nie są wysyłane (tak jak w przypadku pola kombi z **Cbs_simple —** styl).  
  
- **ON_CBN_SELENDOK** użytkownik wybiera element, a następnie naciska klawisz ENTER lub kliknie klawisz strzałki w dół, aby ukryć pola listy, pola kombi. To powiadomienie jest wysyłane przed **CBN_CLOSEUP** wiadomości, aby wskazać, że wybór użytkownika należy traktować jako prawidłowy. **CBN_SELENDCANCEL** lub **CBN_SELENDOK** powiadomienie jest wysyłane nawet wtedy, gdy **CBN_CLOSEUP** komunikatu powiadomienia nie są wysyłane (tak jak w przypadku pola kombi z **Cbs_simple —** styl).  
  
- **ON_CBN_KILLFOCUS** pola kombi jest utraci fokus wprowadzania.  
  
- **ON_CBN_SELCHANGE** zaznaczenie w polu listy, pola kombi ma zostać zmieniony po wysłaniu przez użytkownika, klikając pozycję w polu listy albo zmienić ustawienie za pomocą klawiszy strzałek. Podczas przetwarzania tego komunikatu, tekst w formancie edycyjnym pola kombi można pobrać za pomocą `GetLBText` lub innej podobnych funkcji. `GetWindowText`Nie można użyć.  
  
- **ON_CBN_SETFOCUS** pola kombi zyska fokus wprowadzania.  
  
 W przypadku utworzenia `CComboBox` obiektu w oknie dialogowym (za pośrednictwem zasób okna dialogowego), `CComboBox` obiekt zostanie zniszczony automatycznie, gdy użytkownik zamyka okno dialogowe.  
  
 Po osadzeniu `CComboBox` obiektu obiektu w innym oknie, nie trzeba go zniszcz. W przypadku utworzenia `CComboBox` obiektów na stosie, zostanie zniszczony automatycznie. W przypadku utworzenia `CComboBox` obiektów na stercie przy użyciu **nowe** funkcji, należy wywołać **usunąć** obiektu zniszczyć ją, gdy pole kombi systemu Windows zostanie zniszczony.  
  
 **Uwaga** aby obsłużyć `WM_KEYDOWN` i `WM_CHAR` wiadomości, masz do podklasy pola kombi edycji i formanty pola listy, pochodzi z klasy z `CEdit` i `CListBox`, i Dodaj programy obsługi dla tych wiadomości do pochodnej klasy. Aby uzyskać więcej informacji, zobacz [http://support.microsoft.com/default.aspxscid=kb;en-us; Q174667](http://support.microsoft.com/default.aspxscid=kb;en-us;q174667) i [CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="addstring"></a>CComboBox::AddString  
 Dodaje ciąg do pola listy, pola kombi.  
  
```  
int AddString(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszString`  
 Wskazuje ciąg zakończony zerem, który ma zostać dodany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wartość zwracana jest większa niż lub równa 0, jest liczony od zera indeks na ciąg w polu listy. Wartość zwracana jest **CB_ERR** Jeśli wystąpi błąd; wartość zwracana jest **CB_ERRSPACE** Jeśli niewystarczającej ilości miejsca jest dostępne do przechowywania nowych parametrów.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie utworzono pola listy z [cbs_sort —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl ciągu zostanie dodany na końcu listy. W przeciwnym razie wartość ciągu jest umieszczone na liście, a lista jest sortowana.  
  
> [!NOTE]
>  Ta funkcja nie jest obsługiwana przez system Windows **ComboBoxEx** formantu. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz [formanty ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) w zestawie Windows SDK.  
  
 Aby wstawić ciąg do określonej lokalizacji na liście, należy użyć [InsertString](#insertstring) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]  
  
##  <a name="ccombobox"></a>CComboBox::CComboBox  
 Konstruuje `CComboBox` obiektu.  
  
```  
CComboBox();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]  
  
##  <a name="clear"></a>CComboBox::Clear  
 Usuwa (czyści) bieżące zaznaczenie w formancie edycyjnym pola kombi.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby usunąć bieżące zaznaczenie i umieść usunięto zawartość w Schowku, użyj [Wytnij](#cut) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CComboBox::CompareItem  
 Wywoływane przez platformę, by określić względne położenie nowego elementu w polu listy pola kombi posortowane rysowania przez właściciela.  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpCompareItemStruct`  
 Długie wskaźnik do [COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa względne położenie dwa elementy opisane w `COMPAREITEMSTRUCT` struktury. Może być jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|- 1|Element 1 sortuje przed elementem 2.|  
|0|Element 1 i element 2 Sortuj takie same.|  
|1|Element 1 sortuje po elemencie 2.|  
  
 Zobacz [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) opis `COMPAREITEMSTRUCT`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta funkcja członkowska nie działa. Jeśli tworzenie rysowania przez właściciela pole kombi z **lbs_sort —** stylu, konieczne jest przesłonięcie tej funkcji członkowskiej ułatwiających platformę sortowanie nowe elementy dodane do listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]  
  
##  <a name="copy"></a>CComboBox::Copy  
 Kopiuje bieżące zaznaczenie w formancie edycyjnym pola kombi do Schowka w **CF_TEXT** format.  
  
```  
void Copy();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]  
  
##  <a name="create"></a>CComboBox::Create  
 Tworzy pole kombi i dołącza go do `CComboBox` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl pola kombi. Zastosuj dowolną kombinację [style pola kombi](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) do pola.  
  
 `rect`  
 Wskazuje położenie i rozmiar pola kombi. Może być [struktura RECT](../../mfc/reference/rect-structure1.md) lub `CRect` obiektu.  
  
 `pParentWnd`  
 Określa okno nadrzędne pola kombi (zazwyczaj `CDialog`). Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CComboBox` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać **Utwórz**, która tworzy pole kombi systemu Windows i dołącza go do `CComboBox` obiektu.  
  
 Gdy **Utwórz** wykonuje system Windows wysyła [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), i [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) wiadomości do pola kombi.  
  
 Komunikaty te są obsługiwane przez domyślnie [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), i [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funkcje Członkowskie w `CWnd` klasy podstawowej. Aby rozszerzyć domyślnej obsługi wiadomości, klasa wyprowadzona z `CComboBox`, Dodaj mapowanie komunikatów do nowej klasy i zastąpienie poprzedniego funkcje Członkowskie obsługi wiadomości. Zastąpienie `OnCreate`, na przykład, aby wykonać wymagane inicjowania dla nowej klasy.  
  
 Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki pola kombi. :  
  
- **Ws_child —** zawsze  
  
- **Ws_visible —** zwykle  
  
- **Ws_disabled —** rzadko  
  
- **Ws_vscroll —** można dodać przewijanie w pionie pola listy, pola kombi  
  
- **Ws_hscroll —** można dodać przewijania poziomego pola listy, pola kombi  
  
- **Ws_group —** na grupowanie formantów  
  
- **Ws_tabstop —** do uwzględnienia w kolejności tabulacji pola kombi  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]  
  
##  <a name="cut"></a>CComboBox::Cut  
 Usuwa (części) kontrolować bieżące zaznaczenie w polu kombi edycji i kopiuje usunięty tekst do Schowka w **CF_TEXT** format.  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby usunąć bieżące zaznaczenie bez wprowadzania usunięty tekst do Schowka, wywołaj [wyczyść](#clear) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]  
  
##  <a name="deleteitem"></a>CComboBox::DeleteItem  
 Wywoływane przez platformę, gdy użytkownik usuwa element z rysowania przez właściciela `CComboBox` obiektu lub niszczy pola kombi.  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDeleteItemStruct`  
 Długie wskaźnik do systemu Windows [DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md) struktury, który zawiera informacje o usuniętego elementu. Zobacz [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) opis tej struktury.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja nie działa. Należy przesłonić tę funkcję, aby odświeżyć pola kombi, zgodnie z potrzebami.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]  
  
##  <a name="deletestring"></a>CComboBox::DeleteString  
 Usuwa element w pozycji `nIndex` w polu kombi.  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa indeks na ciąg, który ma zostać usunięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wartość zwracana jest większa niż lub równa 0, to liczba ciągów na liście. Wartość zwracana jest **CB_ERR** Jeśli `nIndex` Określa indeks jest większy niż liczba elementów na liście.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie elementy występujące po słowie `nIndex` teraz Przenieś w dół o jedną pozycję. Na przykład jeśli pole kombi zawiera dwa elementy, usunięcie pierwszy element spowoduje, że element pozostałych się teraz na pierwszym miejscu. `nIndex`= 0 dla elementu na pierwszym miejscu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]  
  
##  <a name="dir"></a>CComboBox::Dir  
 Dodaje listę nazw plików lub stacji dysków do pola listy, pola kombi.  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>Parametry  
 `attr`  
 Może być dowolną kombinacją `enum` wartości opisanego w [CFile::GetStatus](../../mfc/reference/cfile-class.md#getstatus) lub dowolną kombinację następujących wartości:  
  
- **DDL_READWRITE** plik może być z zapisu lub odczytu.  
  
- **DDL_READONLY** pliku można odczytywać, ale nie zapisane.  
  
- **DDL_HIDDEN** plików jest ukryta i nie ma na liście zawartości katalogu.  
  
- **DDL_SYSTEM** plik jest plikiem systemu.  
  
- **DDL_DIRECTORY** nazwa określona przez `lpszWildCard` Określa katalog.  
  
- **DDL_ARCHIVE** plik został zarchiwizowany.  
  
- **DDL_DRIVES** obejmują wszystkie dyski, które odpowiada nazwie określonej przez `lpszWildCard`.  
  
- **DDL_EXCLUSIVE** flagę Exclusive. Jeśli ustawiono flagę exclusive, wyświetlane są tylko pliki o określonym typie. W przeciwnym razie pliki określonego typu są wyświetlane oprócz plików "normal".  
  
 `lpszWildCard`  
 Wskazuje ciąg specyfikacji pliku. Ten ciąg może zawierać symboli wieloznacznych (na przykład *.\*).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wartość zwracana jest większa niż lub równa 0, jest liczony od zera indeks pliku ostatniego dodany do listy. Wartość zwracana jest **CB_ERR** Jeśli wystąpi błąd; wartość zwracana jest **CB_ERRSPACE** Jeśli dostępny do przechowywania nowych ciągów jest za mało miejsca.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie jest obsługiwana przez system Windows **ComboBoxEx** formantu. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz [formanty ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]  
  
##  <a name="drawitem"></a>CComboBox::DrawItem  
 Wywoływane przez platformę, gdy visual aspekt zmiany pola kombi rysowania przez właściciela.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Wskaźnik do [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) strukturę, która zawiera informacje o typie rysunku wymagane.  
  
### <a name="remarks"></a>Uwagi  
 **ItemAction** członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane. Zobacz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) opis tej struktury.  
  
 Domyślnie ta funkcja członkowska nie działa. Przesłonić tę funkcję elementu członkowskiego, aby zaimplementować rysunku rysowania przez właściciela `CComboBox` obiektu. Przed zakończenie funkcji członkowskiej, aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interfejsu (GDI), wybrane kontekst wyświetlania dostarczane w `lpDrawItemStruct`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]  
  
##  <a name="findstring"></a>CComboBox::FindString  
 Wyszukuje, ale nie wybierzesz, pierwszy ciąg, który zawiera określony prefiks w polu listy, pola kombi.  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nStartAfter`  
 Zawiera liczony od zera indeks elementu przed pierwszym elementem do wyszukania. Podczas wyszukiwania przez nią miejsce osiągnie dolnej części pola listy, która kontynuuje od górnej krawędzi pola listy ponownie element określony przez `nStartAfter`. Jeśli wartość-1, przeszukiwany jest pole całą listę od początku.  
  
 `lpszString`  
 Wskazuje ciąg zakończony zerem, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależny, więc ten ciąg może zawierać żadnych kombinacji wielkich i małych liter.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wartość zwracana jest większa niż lub równa 0, jest liczony od zera indeks pasujący element. Jest **CB_ERR** Jeśli wyszukiwanie nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie jest obsługiwana przez system Windows **ComboBoxEx** formantu. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz [formanty ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]  
  
##  <a name="findstringexact"></a>CComboBox::FindStringExact  
 Wywołanie `FindStringExact` funkcji członkowskiej, aby znaleźć pierwszy ciąg pole listy (w polu kombi), który dopasowuje ciąg określony w `lpszFind`.  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndexStart`  
 Określa liczony od zera indeks elementu przed pierwszym elementem do wyszukania. Podczas wyszukiwania przez nią miejsce osiągnie dolnej części pola listy, która kontynuuje od górnej krawędzi pola listy ponownie element określony przez `nIndexStart`. Jeśli `nIndexStart` wynosi -1, przeszukiwany jest pole całą listę od początku.  
  
 `lpszFind`  
 Wskazuje zerem ciąg do wyszukania. Ten ciąg może zawierać pełną nazwę pliku z rozszerzeniem. Wyszukiwanie nie jest uwzględniana wielkość liter, więc ten ciąg może zawierać żadnych kombinacji wielkich i małych liter.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pasującego elementu lub **CB_ERR** Jeśli wyszukiwanie nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pola kombi została utworzona przy użyciu stylu rysowania przez właściciela, ale bez [cbs_hasstrings —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl `FindStringExact` próbuje dopasować wartość bitowego względem wartości `lpszFind`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]  
  
##  <a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo  
 Pobiera informacje o `CComboBox` obiektu.  
  
```  
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pcbi*  
 Wskaźnik do [COMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775798) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje [CB_GETCOMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775839) komunikatu, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getcount"></a>CComboBox::GetCount  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę elementów w polu listy pola kombi.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów. Zwrócona liczba jest większa niż wartość indeksu ostatniego elementu (indeks jest liczony od zera) o jeden. Jest **CB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]  
  
##  <a name="getcuebanner"></a>CComboBox::GetCueBanner  
 Pobiera tekst wskaźnika, który jest wyświetlany dla kontrolki pola kombi.  
  
```  
CString GetCueBanner() const;  
  
BOOL GetCueBanner(
    LPTSTR lpszText,   
    int cchText) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out]`lpszText`|Wskaźnik do buforu, który odbiera tekst transparentu wskaźnika.|  
|[in]`cchText`|Rozmiar buforu, który `lpszText` wskazuje parametr.|  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszym przeciążenia [cstring —](../../atl-mfc-shared/using-cstring.md) obiekt, który zawiera tekst transparentu sygnalizacji, jeśli istnieje; w przeciwnym razie `CString` obiektu, który ma zerową długość.  
  
 —lub—  
  
 W drugim przeciążenia `true` Jeśli ta metoda jest pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tekst wskaźnika jest wiersz, który jest wyświetlany w obszarze wejściowy kontrolki pola kombi. Tekst wskaźnika jest wyświetlany, dopóki użytkownik udostępnia dane wejściowe.  
  
 Ta metoda wysyła [CB_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775843) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getcursel"></a>CComboBox::GetCurSel  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, które element w polu kombi.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera Indeks aktualnie zaznaczonego elementu w polu listy, pola kombi lub **CB_ERR** , jeśli nie wybrano elementu.  
  
### <a name="remarks"></a>Uwagi  
 `GetCurSel`Zwraca indeks w liście.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]  
  
##  <a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect  
 Wywołanie `GetDroppedControlRect` funkcji członkowskiej pobrać współrzędne ekranu pola widoczne (porzucony) listy rozwijanej pola kombi z listy rozwijanej.  
  
```  
void GetDroppedControlRect(LPRECT lprect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprect —*  
 Wskazuje [struktura RECT](../../mfc/reference/rect-structure1.md) do odbierania współrzędne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]  
  
##  <a name="getdroppedstate"></a>CComboBox::GetDroppedState  
 Wywołanie `GetDroppedState` funkcji członkowskiej, aby określić, czy pole listy rozwijanej kombi jest widoczny (rozwinięto).  
  
```  
BOOL GetDroppedState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pole listy jest widoczna; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]  
  
##  <a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth  
 Wywołanie tej funkcji można pobrać minimalną szerokość dozwoloną w pikselach pola listy, pola kombi.  
  
```  
int GetDroppedWidth() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia minimalną szerokość dozwoloną w pikselach; w przeciwnym razie **CB_ERR**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja ma zastosowanie tylko do pól kombi z [cbs_dropdown —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [cbs_dropdownlist —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
 Domyślnie dozwolone minimalną szerokość pola listy rozwijanej jest 0. Można ustawić minimalną szerokość dozwoloną przez wywołanie metody [SetDroppedWidth](#setdroppedwidth). Podczas części pola listy, pola kombi jest wyświetlana, jego szerokość jest większy minimalną szerokość dozwolony lub szerokość pola kombi.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [SetDroppedWidth](#setdroppedwidth).  
  
##  <a name="geteditsel"></a>CComboBox::GetEditSel  
 Pobiera początkowy i końcowy pozycji znaku bieżące zaznaczenie w formancie edycyjnym pola kombi.  
  
```  
DWORD GetEditSel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 32-bitową wartość zawiera pozycji początkowej w programie word znaczącymi bitami i pozycja pierwszego znaku nonselected po zakończeniu wyboru w programie word znaczących. Jeśli ta funkcja jest używana w polu kombi bez formantu edycyjnego **CB_ERR** jest zwracany.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]  
  
##  <a name="getextendedui"></a>CComboBox::GetExtendedUI  
 Wywołanie `GetExtendedUI` funkcji członkowskiej, aby ustalić, czy pole kombi ma domyślny interfejs użytkownika lub interfejsu użytkownika rozszerzonej.  
  
```  
BOOL GetExtendedUI() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pole kombi ma interfejs użytkownika rozszerzonej; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs użytkownika rozszerzonej mogą zostać zidentyfikowane w następujący sposób:  
  
-   Kliknięcie przycisku kontrolki statycznej wyświetla tylko pola kombi z pola listy [cbs_dropdownlist —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
-   Naciśnięcie klawisza Strzałka w dół wyświetla pole listy (F4 jest wyłączony).  
  
 Przewijanie w kontrolce statycznych jest wyłączona, gdy element listy nie jest widoczne (strzałka klucze są wyłączone).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]  
  
##  <a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent  
 Pobiera z pola kombi szerokość w pikselach, według których część pola listy, pola kombi mogą być przewijane w poziomie.  
  
```  
UINT GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość przewijanego części pola listy, pola kombi w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ma to zastosowanie tylko wtedy, gdy część pola listy, pola kombi poziomy pasek przewijania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]  
  
##  <a name="getitemdata"></a>CComboBox::GetItemData  
 Pobiera wartość 32-bitowych dostarczone przez aplikację skojarzoną z elementem pola kombi.  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Zawiera liczony od zera indeks elementu w polu listy pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 32-bitową wartość skojarzoną z elementem, lub **CB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 32-bitową wartość można skonfigurować z `dwItemData` parametr [SetItemData](#setitemdata) wywołanie funkcji Członkowskich. Użyj `GetItemDataPtr` funkcji członkowskiej, jeśli wskaźnik jest 32-bitową wartość do pobrania ( **void\***).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]  
  
##  <a name="getitemdataptr"></a>CComboBox::GetItemDataPtr  
 Pobiera wartość 32-bitowych dostarczone przez aplikację skojarzoną z elementem pola kombi jako wskaźnik ( **void\***).  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Zawiera liczony od zera indeks elementu w polu listy pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pobiera wskaźnik lub wartość -1, jeśli wystąpi błąd.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]  
  
##  <a name="getitemheight"></a>CComboBox::GetItemHeight  
 Wywołanie `GetItemHeight` funkcji członkowskiej pobrać wysokość elementów listy w polu kombi.  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa składnik pola kombi, w których wysokość ma być pobrana. Jeśli `nIndex` parametru wynosi -1, wysokość kontrolki edycji (lub statycznego tekstu) część pola kombi są pobierane. Jeśli pole kombi ma [cbs_ownerdrawvariable —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl `nIndex` określa liczony od zera indeks elementu listy, w których wysokość ma być pobrana. W przeciwnym razie `nIndex` powinna być równa 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość w pikselach określonego elementu w polu kombi. Wartość zwracana jest **CB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]  
  
##  <a name="getlbtext"></a>CComboBox::GetLBText  
 Pobiera ciąg z pola listy, pola kombi.  
  
```  
int GetLBText(
    int nIndex,  
    LPTSTR lpszText) const;  
  
void GetLBText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Zawiera liczony od zera indeks ciągu pole listy ma zostać skopiowany.  
  
 `lpszText`  
 Wskazuje buforu, który ma otrzymać ciąg. Rozmiar buforu musi mieć wystarczającą ilość miejsca na ciąg i znak końcowy null.  
  
 `rString`  
 Odwołanie do `CString`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość (w bajtach) ciąg, z wyłączeniem znak końcowy null. Jeśli `nIndex` nie określa nieprawidłowy indeks, jest zwracana wartość **CB_ERR**.  
  
### <a name="remarks"></a>Uwagi  
 Drugi formularz tego elementu członkowskiego funkcji wypełnienia `CString` obiektu z tekstu elementu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]  
  
##  <a name="getlbtextlen"></a>CComboBox::GetLBTextLen  
 Pobiera długość ciągu w polu listy, pola kombi.  
  
```  
int GetLBTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Zawiera liczony od zera indeks ciągu pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość ciągu w bajtach, z wyłączeniem znak końcowy null. Jeśli `nIndex` nie określa nieprawidłowy indeks, jest zwracana wartość **CB_ERR**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CComboBox::GetLBText](#getlbtext).  
  
##  <a name="getlocale"></a>CComboBox::GetLocale  
 Pobiera ustawienia regionalne używane przez pola kombi.  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość identyfikatora (LCID) ustawień regionalnych dla ciągów w polu kombi.  
  
### <a name="remarks"></a>Uwagi  
 Ustawienia regionalne służy na przykład aby określić kolejność sortowania ciągów w polu kombi posortowane.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CComboBox::SetLocale](#setlocale).  
  
##  <a name="getminvisible"></a>CComboBox::GetMinVisible  
 Pobiera minimalną liczbę widocznych elementów na liście rozwijanej bieżącej kontrolki pola kombi.  
  
```  
int GetMinVisible() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Minimalna liczba widocznych elementów z bieżącej listy rozwijanej.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [CB_GETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="gettopindex"></a>CComboBox::GetTopIndex  
 Pobiera liczony od zera indeks pierwszego widocznego elementu w polu listy pola kombi.  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pierwszego widocznego elementu w polu listy pola kombi. Jeśli to się powiedzie, **CB_ERR** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Początkowo element 0 znajduje się na początku listy, ale jeśli pole listy jest przewijane, inny element może być u góry.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]  
  
##  <a name="initstorage"></a>CComboBox::InitStorage  
 Przydziela pamięć do przechowywania elementów pole listy w polu listy pola kombi.  
  
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
 Jeśli się powiedzie, maksymalna liczba elementy części pola listy, pola kombi mogą przechowywać przed pamięci jest konieczna, w przeciwnym razie **CB_ERRSPACE**, co oznacza brak wystarczającej ilości pamięci jest dostępna.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji przed dodaniem dużą liczbę elementów w polu listy części `CComboBox`.  
  
 Windows 95/98: `wParam` jest ograniczony do 16-bitowych wartości parametru. Oznacza to, że pola listy nie może zawierać więcej niż 32 767 elementów. Mimo że liczba elementów jest ograniczone, łączny rozmiar elementów w polu listy jest ograniczona tylko przez ilość dostępnej pamięci.  
  
 Ta funkcja pomaga przyspieszyć inicjowania pola listy, które ma dużą liczbę elementów (więcej niż 100). Go preallocates określoną ilością pamięci, tak że kolejne [AddString](#addstring), [InsertString](#insertstring), i [Dir](#dir) funkcje pobierać najkrótszym czasie. Szacuje można użyć parametrów. Jeśli overestimate, niektóre dodatkową pamięć jest przydzielony; Jeśli w przypadku licznik nie uwzględniać, normalne alokacji jest używana dla elementów, które przekraczają ilość przydzielony wstępnie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]  
  
##  <a name="insertstring"></a>CComboBox::InsertString  
 Wstawia ciąg do pola listy, pola kombi.  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Zawiera indeks liczony od zera pozycja w polu listy, który otrzyma ten ciąg. Jeśli ten parametr ma wartość -1, ten ciąg jest dodawany na końcu listy.  
  
 `lpszString`  
 Wskazuje ciąg zakończony zerem, który ma zostać wstawiony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pozycji, w którym została umieszczona ciąg. Wartość zwracana jest **CB_ERR** w przypadku wystąpienia błędu. Wartość zwracana jest **CB_ERRSPACE** Jeśli niewystarczającej ilości miejsca jest dostępne do przechowywania nowych parametrów.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od [AddString](#addstring) funkcji członkowskiej `InsertString` funkcji członkowskiej nie powoduje listy z [cbs_sort —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, który ma zostać posortowana.  
  
> [!NOTE]
>  Ta funkcja nie jest obsługiwana przez system Windows **ComboBoxEx** formantu. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz [formanty ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]  
  
##  <a name="limittext"></a>CComboBox::LimitText  
 Ogranicza w bajtach długość tekstu, który użytkownik może wprowadzić w formancie edycyjnym pola kombi.  
  
```  
BOOL LimitText(int nMaxChars);
```  
  
### <a name="parameters"></a>Parametry  
 `nMaxChars`  
 Określa tekst, który użytkownik może wprowadzić długość (w bajtach). Jeśli ten parametr ma wartość 0, długość tekstu wynosi 65 535 bajtów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie. Jeśli wywołana dla pola kombi przy użyciu stylu [cbs_dropdownlist —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub pola kombi bez formantu edycyjnego, jest zwracana wartość **CB_ERR**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pole kombi ma styl [cbs_autohscroll —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles), ustawiając limit tekstu będzie większy niż rozmiar kontrolki edycji nie odniesie żadnego skutku.  
  
 `LimitText`tekst, który użytkownik może wprowadzić tylko ogranicza ich. Go nie ma wpływu na dowolny tekst już w formancie edycyjnym gdy komunikat jest wysyłany, ani nie ogranicza długość tekstu skopiowane do kontrolki edycji w przypadku wybrania ciąg w polu listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]  
  
##  <a name="measureitem"></a>CComboBox::MeasureItem  
 Wywoływane przez platformę, gdy jest tworzony przy użyciu stylu rysowania przez właściciela pole kombi.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpMeasureItemStruct`  
 Długie wskaźnik do [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta funkcja członkowska nie działa. Zastąpienie tej funkcji Członkowskich i wypełnij `MEASUREITEMSTRUCT` struktury informowanie Windows wymiary listy, wpisz w polu kombi. Jeśli pole kombi jest tworzony z [cbs_ownerdrawvariable —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu, struktura wywołuje tę funkcję elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ten element członkowski zostanie wywołana tylko raz.  
  
 Przy użyciu **cbs_ownerdrawfixed —** styl rysowania przez właściciela pole kombi utworzone za pomocą [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) funkcji członkowskiej klasy `CWnd` obejmuje uwagi dodatkowe programowania. Zawiera omówienie w [14 Uwaga techniczna](../../mfc/tn014-custom-controls.md).  
  
 Zobacz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) opis `MEASUREITEMSTRUCT` struktury.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]  
  
##  <a name="paste"></a>CComboBox::Paste  
 Wstawia danych ze Schowka na formancie edycyjnym pola kombi w bieżącym położeniu kursora.  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>Uwagi  
 Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w **CF_TEXT** format.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]  
  
##  <a name="resetcontent"></a>CComboBox::ResetContent  
 Usuwa wszystkie elementy na liście pole i edytować kontrolki pola kombi.  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]  
  
##  <a name="selectstring"></a>CComboBox::SelectString  
 Wyszukuje ciąg w polu listy, pola kombi, a jeśli ciąg zostanie znaleziony, wybiera ciąg w polu listy i kopiuje go do kontrolki edycji.  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartAfter`  
 Zawiera liczony od zera indeks elementu przed pierwszym elementem do wyszukania. Podczas wyszukiwania przez nią miejsce osiągnie dolnej części pola listy, która kontynuuje od górnej krawędzi pola listy ponownie element określony przez `nStartAfter`. Jeśli wartość-1, przeszukiwany jest pole całą listę od początku.  
  
 `lpszString`  
 Wskazuje ciąg zakończony zerem, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależny, więc ten ciąg może zawierać żadnych kombinacji wielkich i małych liter.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks wybranego elementu, jeśli ciąg został znaleziony. Jeśli wyszukiwanie nie powiodło się, że zwracana wartość jest **CB_ERR** i nie ulega zmianie bieżącego zaznaczenia.  
  
### <a name="remarks"></a>Uwagi  
 Ciąg jest wybrany tylko wtedy, gdy jego znaków (od punktu początkowego) pasować do znaków w ciągu prefiksu.  
  
 Należy pamiętać, że `SelectString` i `FindString` funkcje Członkowskie zarówno znaleźć ciąg, ale `SelectString` funkcji członkowskiej zaznacza ciąg.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]  
  
##  <a name="setcuebanner"></a>CComboBox::SetCueBanner  
 Ustawia tekst wskaźnika, który jest wyświetlany dla kontrolki pola kombi.  
  
```  
BOOL SetCueBanner(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *lpszText*|Wskaźnik do buforu zerem, który zawiera tekst wskaźnika.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tekst wskaźnika jest wiersz, który jest wyświetlany w obszarze wejściowy kontrolki pola kombi. Tekst wskaźnika jest wyświetlany, dopóki użytkownik udostępnia dane wejściowe.  
  
 Ta metoda wysyła [CB_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775897) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_combobox`, która jest używana do uzyskania programowego dostępu do kontrolki pola kombi. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia transparent sygnalizacji kontrolki pola kombi.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="setcursel"></a>CComboBox::SetCurSel  
 Wybiera ciąg w polu listy, pola kombi.  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>Parametry  
 `nSelect`  
 Określa liczony od zera indeks ciąg, aby wybrać. Jeśli wartość-1, zostaną usunięte wszystkie bieżące zaznaczenie w polu listy i kontrolki edycji jest wyczyszczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks elementu wybranego w przypadku pomyślnego nawiązania wiadomości. Wartość zwracana jest **CB_ERR** Jeśli `nSelect` jest większa niż liczba elementów na liście lub, jeśli `nSelect` ma ustawioną wartość -1, co spowoduje wyczyszczenie zaznaczenia.  
  
### <a name="remarks"></a>Uwagi  
 W razie potrzeby pole listy Przewija ciąg do widoku (Jeśli pole listy jest widoczna). Tekst w formancie edycyjnym pola kombi zostanie zmieniona w celu odzwierciedlenia wyboru nowego. Wszelkie poprzednie zaznaczenie w polu listy zostanie usunięte.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]  
  
##  <a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth  
 Wywołanie tej funkcji, aby ustawić minimalną szerokość dopuszczalna, w pikselach, pola listy, pola kombi.  
  
```  
int SetDroppedWidth(UINT nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Minimalna szerokość dopuszczalny części pola listy, pola kombi w pikselach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeżeli powodzenia nową szerokość listy pole, w przeciwnym razie **CB_ERR**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja ma zastosowanie tylko do pól kombi z [cbs_dropdown —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [cbs_dropdownlist —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
 Domyślnie dozwolone minimalną szerokość pola listy rozwijanej jest 0. Podczas części pola listy, pola kombi jest wyświetlana, jego szerokość jest większy minimalną szerokość dozwolony lub szerokość pola kombi.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]  
  
##  <a name="seteditsel"></a>CComboBox::SetEditSel  
 Wybiera znaków w formancie edycyjnym pola kombi.  
  
```  
BOOL SetEditSel(
    int nStartChar,  
    int nEndChar);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartChar`  
 Określa położenie początkowe. Jeśli pozycja początkowa ma ustawioną wartość -1, zostaną usunięte wszystkie zaznaczone.  
  
 `nEndChar`  
 Określa pozycję końcową. Pozycji końcowej ma ustawioną wartość -1, a następnie cały tekst z pozycji początkowej ostatni znak w formancie edycyjnym jest zaznaczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja członkowska zakończy się pomyślnie; w przeciwnym razie 0. Jest **CB_ERR** Jeśli `CComboBox` ma [cbs_dropdownlist —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu lub nie ma pola listy.  
  
### <a name="remarks"></a>Uwagi  
 Położenie jest liczony od zera. Aby wybrać pierwszego znaku w formancie edycyjnym, należy określić pozycji początkowej 0. Pozycja końcowa jest znaku zaraz po ostatnim znakiem, aby wybrać. Na przykład aby wybrać pierwsze cztery znaki kontrolki edycji, będą używać pozycji początkowej 0 i pozycję końcową 4.  
  
> [!NOTE]
>  Ta funkcja nie jest obsługiwana przez system Windows **ComboBoxEx** formantu. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz [formanty ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CComboBox::GetEditSel](#geteditsel).  
  
##  <a name="setextendedui"></a>CComboBox::SetExtendedUI  
 Wywołanie `SetExtendedUI` funkcji członkowskiej, aby wybrać domyślny interfejs użytkownika lub interfejsu użytkownika rozszerzonego pola kombi, które ma [cbs_dropdown —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [cbs_dropdownlist —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
```  
int SetExtendedUI(BOOL bExtended = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bPrzedłużony*  
 Określa, czy pole kombi powinien używać interfejsu użytkownika rozszerzonej lub domyślny interfejs użytkownika. Wartość **TRUE** wybiera rozszerzonych interfejsu użytkownika; wartość **FALSE** wybiera standardowy interfejs użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 **CB_OKAY** Jeśli operacja zakończy się pomyślnie, lub **CB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs użytkownika rozszerzonej mogą zostać zidentyfikowane w następujący sposób:  
  
-   Kliknięcie przycisku kontrolki statycznej wyświetla tylko pola kombi z pola listy **cbs_dropdownlist —** stylu.  
  
-   Naciśnięcie klawisza Strzałka w dół wyświetla pole listy (F4 jest wyłączony).  
  
 Przewijanie w kontrolce statycznych jest wyłączona, gdy nie jest widoczny na liście elementów (klawisze strzałek są wyłączone).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CComboBox::GetExtendedUI](#getextendedui).  
  
##  <a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent  
 Określa szerokość w pikselach, według których część pola listy, pola kombi mogą być przewijane w poziomie.  
  
```  
void SetHorizontalExtent(UINT nExtent);
```  
  
### <a name="parameters"></a>Parametry  
 *nExtent*  
 Określa liczbę pikseli, za pomocą których część pola listy, pola kombi mogą być przewijane w poziomie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli szerokość pola listy jest mniejszy od tej wartości, poziomy pasek przewijania w poziomie przewinie elementy w polu listy. Jeśli szerokość pola listy jest równa lub większa niż ta wartość, poziomy pasek przewijania jest ukryty lub, jeśli pole kombi ma [cbs_disablenoscroll —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl wyłączone.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]  
  
##  <a name="setitemdata"></a>CComboBox::SetItemData  
 Ustawia wartość 32-bitowych skojarzone z określonym elementem w polu kombi.  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Zawiera liczony od zera indeks w elemencie, aby ustawić.  
  
 `dwItemData`  
 Zawiera nową wartość do skojarzenia z elementem.  
  
### <a name="return-value"></a>Wartość zwracana  
 **CB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `SetItemDataPtr` funkcji członkowskiej, jeśli element 32-bitowych ma być wskaźnikiem.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]  
  
##  <a name="setitemdataptr"></a>CComboBox::SetItemDataPtr  
 Ustawia wartość 32-bitowych skojarzony z określonym elementem w polu kombi jako wskaźnik określonego ( **void\***).  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Zawiera liczony od zera indeks w elemencie.  
  
 `pData`  
 Zawiera wskaźnik do skojarzenia z elementem.  
  
### <a name="return-value"></a>Wartość zwracana  
 **CB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 This, wskaźnik pozostaje ważność w polu kombi, mimo że względne położenie elementu w polu kombi może ulec zmianie, elementy są dodawane lub usuwane. W związku z tym można zmienić indeks elementu w polu, ale wskaźnik pozostaje wiarygodne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]  
  
##  <a name="setitemheight"></a>CComboBox::SetItemHeight  
 Wywołanie `SetItemHeight` funkcji członkowskiej, aby ustawić wysokość elementów listy w polu kombi lub wysokość kontrolki edycji (lub statycznego tekstu) część pola kombi.  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa, czy ustawiono wysokość listy elementów lub wysokość kontrolki edycji (lub statycznego tekstu) część pola kombi.  
  
 Jeśli pole kombi ma [cbs_ownerdrawvariable —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl `nIndex` liczony od zera indeks elementu listy, w których wysokość ma być ustawione; w przeciwnym razie Określa `nIndex` musi być równa 0 i wysokość listy wszystkich elementów zostanie ustawiona.  
  
 Jeśli `nIndex` jest wartość -1, wysokość formantu edycji lub statyczna tekstowym pola kombi, można ustawić.  
  
 `cyItemHeight`  
 Określa wysokość w pikselach, składnik pola kombi identyfikowany przez `nIndex`.  
  
### <a name="return-value"></a>Wartość zwracana  
 **CB_ERR** Jeśli indeks lub wysokość jest nieprawidłowy; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Wysokość kontrolki edycji (lub statycznego tekstu) część pola kombi ustawiono niezależnie od wysokości elementów listy. Stosowanie musi zapewniać wysokość części kontrolki edycji (lub statycznego tekstu) nie jest mniejsza niż wysokość elementu określonego pola listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]  
  
##  <a name="setlocale"></a>CComboBox::SetLocale  
 Określa identyfikator ustawień regionalnych dla tego pola kombi.  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>Parametry  
 `nNewLocale`  
 Nowa wartość identyfikator (LCID) ustawień regionalnych dla pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednich ustawień regionalnych (LCID) wartość identyfikatora dla tego pola kombi.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli **SetLocale** nie jest wywoływany, domyślne ustawienia regionalne są uzyskiwane z systemu. Można zmodyfikować domyślne ustawienia regionalne tego systemu za pomocą Panelu sterowania regionalne (lub międzynarodowy) aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]  
  
##  <a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems  
 Ustawia minimalną liczbę widocznych elementów na liście rozwijanej bieżącego kombi kontrolki pola.  
  
```  
BOOL SetMinVisibleItems(int iMinVisible);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iMinVisible`|Określa minimalną liczbę widocznych elementów.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [CB_SETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_combobox`, która jest używana do uzyskania programowego dostępu do kontrolki pola kombi. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu wstawia 20 elementów na liście rozwijanej kontrolki pola kombi. Następnie określa, że co najmniej 10 elementów będzie wyświetlana po naciśnięciu klawisza strzałkę listy rozwijanej.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="settopindex"></a>CComboBox::SetTopIndex  
 Zapewnia, że danego elementu jest widoczny w polu listy pola kombi.  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa liczony od zera indeks elementu pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie, lub **CB_ERR** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 System jest przewijane pole listy do element określony przez `nIndex` pojawia się na początku listy pola lub przewijania maksymalny zakres został osiągnięty.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]  
  
##  <a name="showdropdown"></a>CComboBox::ShowDropDown  
 Pokazuje lub ukrywa pole listy ma pole kombi [cbs_dropdown —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [cbs_dropdownlist —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
```  
void ShowDropDown(BOOL bShowIt = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bShowIt*  
 Określa, czy mają być pokazywane lub ukryte pole listy rozwijanej. Wartość **TRUE** zawiera pola listy. Wartość **FALSE** powoduje ukrycie pola listy.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie pole kombi tego stylu wyświetli pola listy.  
  
 Ta funkcja członkowska nie ma wpływu na pole kombi utworzone za pomocą [cbs_simple —](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CComboBox::GetDroppedState](#getdroppedstate).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Klasa CButton](../../mfc/reference/cbutton-class.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)   
 [Clistbox — klasa](../../mfc/reference/clistbox-class.md)   
 [Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [Klasa CStatic](../../mfc/reference/cstatic-class.md)   
 [Cdialog — klasa](../../mfc/reference/cdialog-class.md)
