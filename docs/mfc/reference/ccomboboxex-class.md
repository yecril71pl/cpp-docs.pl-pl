---
title: "Ccomboboxex — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
dev_langs:
- C++
helpviewer_keywords:
- CComboBoxEx [MFC], CComboBoxEx
- CComboBoxEx [MFC], Create
- CComboBoxEx [MFC], CreateEx
- CComboBoxEx [MFC], DeleteItem
- CComboBoxEx [MFC], GetComboBoxCtrl
- CComboBoxEx [MFC], GetEditCtrl
- CComboBoxEx [MFC], GetExtendedStyle
- CComboBoxEx [MFC], GetImageList
- CComboBoxEx [MFC], GetItem
- CComboBoxEx [MFC], HasEditChanged
- CComboBoxEx [MFC], InsertItem
- CComboBoxEx [MFC], SetExtendedStyle
- CComboBoxEx [MFC], SetImageList
- CComboBoxEx [MFC], SetItem
- CComboBoxEx [MFC], SetWindowTheme
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3aecbb168316b3d6416d3a41a6f6a56b04aeb990
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomboboxex-class"></a>Ccomboboxex — klasa
Rozszerza pole kombi kontrolki pola, zapewniając obsługę listy obrazów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CComboBoxEx : public CComboBox  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Konstruuje `CComboBoxEx` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComboBoxEx::Create](#create)|Tworzy pole kombi i dołącza go do `CComboBoxEx` obiektu.|  
|[CComboBoxEx::CreateEx](#createex)|Tworzy pole kombi w określonym stylu rozszerzonej systemu Windows i dołącza go do **ComboBoxEx** obiektu.|  
|[CComboBoxEx::DeleteItem](#deleteitem)|Usuwa element z **ComboBoxEx** formantu.|  
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Pobiera wskaźnik do kontrolki pola kombi podrzędnych.|  
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Pobiera dojścia do części kontrolki edycji **ComboBoxEx** formantu.|  
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Pobiera rozszerzone style, które są używane dla **ComboBoxEx** formantu.|  
|[CComboBoxEx::GetImageList](#getimagelist)|Pobiera wskaźnik do listy obrazów, przypisane do **ComboBoxEx** formantu.|  
|[CComboBoxEx::GetItem](#getitem)|Pobiera element informacje dotyczące danego **ComboBoxEx** elementu.|  
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Określa, czy użytkownik zmienił zawartość **ComboBoxEx** formantów edycji, wpisując polecenie.|  
|[CComboBoxEx::InsertItem](#insertitem)|Wstawia nowy element **ComboBoxEx** formantu.|  
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Ustawia rozszerzone style w **ComboBoxEx** formantu.|  
|[CComboBoxEx::SetImageList](#setimagelist)|Ustawia dla listy obrazów **ComboBoxEx** formantu.|  
|[CComboBoxEx::SetItem](#setitem)|Określa atrybuty elementu w **ComboBoxEx** formantu.|  
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Ustawia pole kombi rozszerzonego stylu kontrolki pola.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą `CComboBoxEx` do tworzenia kontrolki pola kombi, już nie musisz wdrożyć własny obraz kod rysowania. Zamiast tego należy użyć `CComboBoxEx` dostępu obrazów z listy obrazów.  
  
## <a name="image-list-support"></a>Obsługa listy obrazów  
 W polu kombi standardowe właściciel pola kombi jest odpowiedzialny za rysowania obrazu, tworząc pole kombi jako formant rysowania przez właściciela. Jeśli używasz `CComboBoxEx`, nie trzeba ustawić style rysowania **cbs_ownerdrawfixed —** i **cbs_hasstrings —** ponieważ są one niejawnego. W przeciwnym razie należy napisać kod, aby wykonać operacje rysowania. A `CComboBoxEx` sterowanie obsługuje maksymalnie trzy obrazy dla każdego elementu: jeden dla wybranego stanu: jeden dla stanu niezaznaczone i jeden dla obrazu nakładki.  
  
## <a name="styles"></a>Style  
 `CComboBoxEx`obsługuje style **cbs_simple —**, **cbs_dropdown —**, **cbs_dropdownlist —**, i **ws_child —**. Wszystkie inne style przekazany podczas tworzenia okna są ignorowane przez formant. Po utworzeniu okna, możesz podać inne kombi style pola wywołując `CComboBoxEx` funkcji członkowskiej [SetExtendedStyle](#setextendedstyle). Przy użyciu tych stylów możesz:  
  
-   Ustaw ciąg wyszukiwania na liście będzie uwzględniana wielkość liter.  
  
-   Tworzenie kontrolki pola kombi używającej ukośnika ("/"), ukośnika odwrotnego ("\\") i okresu (".") znaków jako ograniczników programu word. Dzięki temu użytkownicy przejść z programu word do programu word, za pomocą skrótu klawiaturowego CTRL + STRZAŁKA.  
  
-   Ustaw pole kombi kontrolki pola do wyświetlenia albo nie wyświetlania obrazu. Jeśli obraz nie jest wyświetlany, pola kombi usunąć wcięcie uwzględniający obrazu.  
  
-   Tworzenie kontrolki pola kombi wąskie, łącznie z jej zmiany rozmiaru, więc go klipy szersze pola kombi, które zawiera.  
  
 Flagi te style są opisane dalej w [przy użyciu CComboBoxEx](../../mfc/using-ccomboboxex.md).  
  
## <a name="item-retention-and-callback-item-attributes"></a>Element przechowywania i atrybuty elementu wywołania zwrotnego  
 Element informacje, takie jak indeksów elementów i obrazów, wartości wcięcia i ciągi tekstowe są przechowywane w strukturze Win32 [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746), zgodnie z opisem w zestawie Windows SDK. Struktura zawiera także elementów członkowskich, które odpowiadają flagi wywołania zwrotnego.  
  
 Omówienie szczegółowe, pojęciach, zobacz [przy użyciu CComboBoxEx](../../mfc/using-ccomboboxex.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccombobox —](../../mfc/reference/ccombobox-class.md)  
  
 `CComboBoxEx`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx  
 Wywołanie tej funkcji Członkowskich, aby utworzyć `CComboBoxEx` obiektu.  
  
```  
CComboBoxEx();
```  
  
##  <a name="create"></a>CComboBoxEx::Create  
 Tworzy pole kombi i dołącza go do `CComboBoxEx` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa kombinację style pola kombi stosowane do pola kombi. Zobacz **uwagi** poniżej Aby uzyskać więcej informacji na temat style.  
  
 `rect`  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która jest położenie i rozmiar pola kombi.  
  
 `pParentWnd`  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okna nadrzędnego pola kombi (zazwyczaj `CDialog`). Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Utwórz `CComboBoxEx` obiektu w dwóch krokach:  
  
1.  Wywołanie [CComboBoxEx](#ccomboboxex) do skonstruowania `CComboBoxEx` obiektu.  
  
2.  Wywołanie tej funkcji elementu członkowskiego, który tworzy rozszerzonego pola kombi systemu Windows i dołącza go do `CComboBoxEx` obiektu.  
  
 Podczas wywoływania **Utwórz**, MFC inicjuje wspólne kontrolki.  
  
 Podczas tworzenia pola kombi, można określić dowolne z następujących style pola kombi:  
  
- **CBS_SIMPLE —**  
  
- **CBS_DROPDOWN —**  
  
- **CBS_DROPDOWNLIST —**  
  
- **CBS_AUTOHSCROLL —**  
  
- **WS_CHILD —**  
  
 Wszystkie inne style przekazany podczas tworzenia okna są ignorowane. **ComboBoxEx** control obsługuje także rozszerzone style, które zapewniają dodatkowe funkcje. Te style są opisane w [ComboBoxEx kontrolować rozszerzone style](http://msdn.microsoft.com/library/windows/desktop/bb775742), w zestawie Windows SDK. Ustaw te style przez wywołanie metody [SetExtendedStyle](#setextendedstyle).  
  
 Jeśli chcesz style rozszerzonej systemu windows za pomocą formantu wywołanie [CreateEx](#createex) zamiast **Utwórz**.  
  
##  <a name="createex"></a>CComboBoxEx::CreateEx  
 Wywołanie tej funkcji, aby utworzyć formancie rozszerzonego pola kombi (okno podrzędne) i skojarzyć go z `CComboBoxEx` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Określa styl rozszerzony formantu tworzona. Aby uzyskać listę rozszerzone style systemu Windows, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 `dwStyle`  
 Style kontrolki pola kombi. Zobacz [Utwórz](#create) listę style.  
  
 `rect`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujące rozmiar i położenie okna, które ma zostać utworzony w współrzędne klienta `pParentWnd`.  
  
 `pParentWnd`  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 `nID`  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast **Utwórz** dotyczyć rozszerzone style systemu Windows, określone przez wstępu rozszerzonego stylu Windows **WS_EX_**.  
  
 `CreateEx`Tworzy formantu z rozszerzone style Windows określonego przez `dwExStyle`. Należy ustawić rozszerzone style określone na kombi rozszerzonego pola formantu przy użyciu [SetExtendedStyle](#setextendedstyle). Na przykład użyć `CreateEx` można ustawić takie style jako **ws_ex_contexthelp —**, ale użyj `SetExtendedStyle` można ustawić takie style jako **CBES_EX_CASESENSITIVE**. Aby uzyskać więcej informacji, zobacz opisane w temacie style [ComboBoxEx kontroli rozszerzone style](http://msdn.microsoft.com/library/windows/desktop/bb775742) w zestawie Windows SDK.  
  
##  <a name="deleteitem"></a>CComboBoxEx::DeleteItem  
 Usuwa element z **ComboBoxEx** formantu.  
  
```  
int DeleteItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `iIndex`  
 Liczony od zera indeks elementu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w formancie. Jeśli `iIndex` jest nieprawidłowa, funkcja zwraca **CB_ERR**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje funkcje wiadomości [CBEM_DELETEITEM](http://msdn.microsoft.com/library/windows/desktop/bb775768), zgodnie z opisem w zestawie Windows SDK. Podczas wywoływania DeleteItem, [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) komunikatów z **CBEN_DELETEITEM** powiadomienie zostanie wysłane do okna nadrzędnego.  
  
##  <a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl  
 Wywołanie tej funkcji Członkowskich otrzymywać wskaźnik do kontrolki pola kombi, w ramach `CComboBoxEx` obiektu.  
  
```  
CComboBox* GetComboBoxCtrl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CComboBox` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `CComboBoxEx` Kontrola składa się z okna nadrzędnego, który hermetyzuje `CComboBox`.  
  
 `CComboBox` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i zostanie zniszczony podczas następnego przetwarzania bezczynności.  
  
##  <a name="geteditctrl"></a>CComboBoxEx::GetEditCtrl  
 Wywołanie tej funkcji Członkowskich otrzymywać wskaźnik na formancie edycyjnym pola kombi.  
  
```  
CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CEdit](../../mfc/reference/cedit-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 A `CComboBoxEx` formant używa pole edycji tworzona z **cbs_dropdown —** stylu.  
  
 `CEdit` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i zostanie zniszczony podczas następnego przetwarzania bezczynności.  
  
##  <a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle  
 Wywołanie tej funkcji Członkowskich uzyskanie rozszerzone style używane dla `CComboBoxEx` formantu.  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `DWORD` Wartość, która zawiera rozszerzone style, które są używane do kontrolki pola kombi.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [ComboBoxEx kontroli rozszerzone style](http://msdn.microsoft.com/library/windows/desktop/bb775742) w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat tych stylów.  
  
##  <a name="getimagelist"></a>CComboBoxEx::GetImageList  
 Wywołanie tej funkcji Członkowskich otrzymywać wskaźnik do listy obrazów, używany przez `CComboBoxEx` formantu.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu. Jeśli nie, zwraca funkcji członkowskiej **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 `CImageList` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i zostanie zniszczony podczas następnego przetwarzania bezczynności.  
  
##  <a name="getitem"></a>CComboBoxEx::GetItem  
 Pobiera element informacje dotyczące danego **ComboBoxEx** elementu.  
  
```  
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pCBItem`  
 Wskaźnik do [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) struktury, które będą otrzymywać informacje o elementach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje funkcje wiadomości [CBEM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775779), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="haseditchanged"></a>CComboBoxEx::HasEditChanged  
 Określa, czy użytkownik zmienił zawartość **ComboBoxEx** formantów edycji, wpisując polecenie.  
  
```  
BOOL HasEditChanged();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik ma wpisane w polu edycji formantu; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje funkcje wiadomości [CBEM_HASEDITCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb775782), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="insertitem"></a>CComboBoxEx::InsertItem  
 Wstawia nowy element **ComboBoxEx** formantu.  
  
```  
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pCBItem`  
 Wskaźnik do [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) struktury, które będą otrzymywać informacje o elementach. Ta struktura zawiera wartości flag wywołanie zwrotne dla elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks, w którym dodano nowy element w przypadku powodzenia; w przeciwnym razie wartość-1.  
  
### <a name="remarks"></a>Uwagi  
 Podczas wywoływania `InsertItem`, [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) komunikatów z [CBEN_INSERTITEM](http://msdn.microsoft.com/library/windows/desktop/bb775764) powiadomienie zostanie wysłane do okna nadrzędnego.  
  
##  <a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle  
 Wywołanie tej funkcji członkowskich można ustawić rozszerzone style używany rozszerzony kontrolki pola kombi.  
  
```  
DWORD SetExtendedStyle(
    DWORD dwExMask,  
    DWORD dwExStyles);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExMask`  
 A `DWORD` wartość, która wskazuje style w `dwExStyles` są, których to dotyczy. Tylko rozszerzone style w `dwExMask` zostanie zmieniona. Wszystkie inne style będzie przechowywany jest. Jeśli ten parametr ma wartość zero, a następnie wszystkie style w `dwExStyles` będzie dotyczył.  
  
 `dwExStyles`  
 A `DWORD` wartości, która zawiera pole kombi kontrolować rozszerzone style do formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `DWORD` wartości, która zawiera rozszerzone style wcześniej używany dla formantu.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [ComboBoxEx kontroli rozszerzone style](http://msdn.microsoft.com/library/windows/desktop/bb775742) w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat tych stylów.  
  
 Aby utworzyć rozszerzony formantu o windows rozszerzone style pola kombi, użyj [CreateEx](#createex).  
  
##  <a name="setimagelist"></a>CComboBoxEx::SetImageList  
 Ustawia dla listy obrazów **ComboBoxEx** formantu.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `pImageList`  
 Wskaźnik do `CImageList` obiekt zawierający obrazy do użycia z `CComboBoxEx` formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiekt zawierający obrazy używanych wcześniej przez `CComboBoxEx` formantu. **Wartość NULL** Jeśli wcześniej została ustawiona nie listy obrazów.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje funkcje wiadomości [CBEM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775787), zgodnie z opisem w zestawie Windows SDK. Jeśli zmienisz wysokość formantu edycji domyślne wywołania funkcji Win32 [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) zmiany rozmiaru formantu po wywołaniu metody `SetImageList`, lub nie zostanie poprawnie wyświetlić.  
  
 `CImageList` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i zostanie zniszczony podczas następnego przetwarzania bezczynności.  
  
##  <a name="setitem"></a>CComboBoxEx::SetItem  
 Określa atrybuty elementu w **ComboBoxEx** formantu.  
  
```  
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pCBItem`  
 Wskaźnik do [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) struktury, które będą otrzymywać informacje o elementach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje funkcje wiadomości [CBEM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775788), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme  
 Ustawia pole kombi rozszerzonego stylu kontrolki pola.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parametry  
 `pszSubAppName`  
 Wskaźnik zawiera styl wizualny pole kombi rozszerzonej można ustawić na ciąg Unicode.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwrotna nie jest używany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje [CBEM_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb775790) komunikatu, zgodnie z opisem w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MFCIE](../../visual-cpp-samples.md)   
 [Ccombobox — klasa](../../mfc/reference/ccombobox-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CComboBox](../../mfc/reference/ccombobox-class.md)
