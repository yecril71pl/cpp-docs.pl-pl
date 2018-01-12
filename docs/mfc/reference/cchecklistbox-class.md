---
title: Klasa CCheckListBox | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
dev_langs: C++
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64e22176d0df2408db8a8c9435fde5b4c6775d21
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cchecklistbox-class"></a>Klasa CCheckListBox
Udostępnia funkcje pole listy kontrolnej systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCheckListBox : public CListBox  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Konstruuje `CCheckListBox` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCheckListBox::Create](#create)|Tworzy okno Lista kontrolna systemu Windows i dołącza go do `CCheckListBox` obiektu.|  
|[CCheckListBox::DrawItem](#drawitem)|Wywoływane przez platformę, gdy visual aspekt rysowania przez właściciela zmiany z pola listy.|  
|[CCheckListBox::Enable](#enable)|Włącza lub wyłącza element pole listy kontrolnej.|  
|[CCheckListBox::GetCheck](#getcheck)|Pobiera stan pola wyboru elementu.|  
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Pobiera styl pola wyboru formantu.|  
|[CCheckListBox::IsEnabled](#isenabled)|Określa, czy element jest włączony.|  
|[CCheckListBox::MeasureItem](#measureitem)|Wywoływane przez platformę, gdy jest tworzony przy użyciu stylu rysowania przez właściciela pole listy.|  
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Wywoływane przez platformę, by uzyskać położenie elementu pola wyboru.|  
|[CCheckListBox::SetCheck](#setcheck)|Ustawia stan pola wyboru elementu.|  
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Ustawia styl pola wyboru formantu.|  
  
## <a name="remarks"></a>Uwagi  
 "Pole listy kontrolnej" Wyświetla listę elementów, takich jak nazwy plików. Każdy element na liście ma obok niej, które użytkownik może zaznacz lub usuń zaznaczenie pola wyboru.  
  
 `CCheckListBox`jest tylko w przypadku kontrolek rysowanych przez właściciela, ponieważ lista zawiera więcej niż ciągów tekstowych. W najprostszym okno Lista kontrolna zawiera ciągi i pól wyboru, ale nie trzeba mieć tekstu. Na przykład można mieć listę małych map bitowych z polem wyboru obok każdego elementu.  
  
 Aby utworzyć własne pole listy kontrolnej, musi dziedziczyć klasy z `CCheckListBox`. Do własnych klasa wyprowadzona zapisywanie konstruktora klasy pochodnej, następnie wywołaj **Utwórz**.  
  
 Jeśli chcesz obsługiwać Windows komunikaty powiadomień wysłane przez pole listy do elementu nadrzędnego (zazwyczaj klasą pochodną [cdialog —](../../mfc/reference/cdialog-class.md)), Dodaj funkcji członkowskiej wpisu i program obsługi komunikatów map wiadomości do klasy nadrzędnej dla każdego komunikatu.  
  
 Każdy wpis mapy komunikatów ma następującą postać:  
  
 **ON_**powiadomień **(**`id`, `memberFxn` **)**  
  
 gdzie `id` Określa identyfikator okno podrzędne formantu wysyłania powiadomienia i `memberFxn` jest nazwą funkcji członkowskiej nadrzędnego zostały zapisane do obsługi powiadomień.  
  
 Prototyp funkcji elementu nadrzędnego, jak wygląda następująco:  
  
 **afx_msg** `void` `memberFxn` **();**  
  
 Istnieje tylko jeden wpis mapy komunikatów, który dotyczy w szczególności do **CCheckListBox** (Zobacz też wpisy mapy wiadomości, ale [clistbox —](../../mfc/reference/clistbox-class.md)):  
  
- **ON_CLBN_CHKCHANGE** użytkownik zmienił stan elementu checkbox.  
  
 Jeśli pole z listy kontrolnej jest pole listy kontrolnej domyślne (lista ciągów o rozmiarze domyślnym pola wyboru po lewej), użytkownik korzysta z domyślnych [CCheckListBox::DrawItem](#drawitem) do rysowania pole listy kontrolnej. W przeciwnym razie konieczne jest przesłonięcie [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) funkcji i [CCheckListBox::DrawItem](#drawitem) i [CCheckListBox::MeasureItem](#measureitem) funkcji.  
  
 Można utworzyć pole listy kontrolnej z szablonu okna dialogowego lub bezpośrednio w kodzie.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Clistbox —](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cchecklistbox"></a>CCheckListBox::CCheckListBox  
 Konstruuje `CCheckListBox` obiektu.  
  
```  
CCheckListBox();
```  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CCheckListBox` obiektu w dwóch krokach. Najpierw zdefiniować klasę pochodzącą od `CCheckListBox`, następnie wywołaj **Utwórz**, która inicjuje okno Lista kontrolna systemu Windows i dołącza go do `CCheckListBox` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]  
  
##  <a name="create"></a>CCheckListBox::Create  
 Tworzy okno Lista kontrolna systemu Windows i dołącza go do `CCheckListBox` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl pole listy kontrolnej. Styl musi być **lbs_hasstrings —** i **lbs_ownerdrawfixed —** (wszystkie elementy na liście są tego samego wysokość) lub **lbs_ownerdrawvariable —** (elementy na liście są zróżnicowanymi wysokości). Ten styl można łączyć z innymi [style pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) z wyjątkiem **lbs_usetabstops —**.  
  
 `rect`  
 Określa pole listy kontrolnej rozmiar i położenie. Może to być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](../../mfc/reference/rect-structure1.md) struktury.  
  
 `pParentWnd`  
 Określa okno nadrzędne pole listy kontrolnej (zazwyczaj `CDialog` obiektu). Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu pole listy kontrolnej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CCheckListBox` obiektu w dwóch krokach. Najpierw należy zdefiniować klasę pochodzącą od **CcheckListBox** , a następnie wywołać **Utwórz**, która inicjuje okno Lista kontrolna systemu Windows i dołącza go do `CCheckListBox`. Zobacz [CCheckListBox::CCheckListBox](#cchecklistbox) przykładowe.  
  
 Gdy **Utwórz** wykonuje system Windows wysyła [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), i [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) wiadomości do formantu pole listy kontrolnej.  
  
 Komunikaty te są obsługiwane przez domyślnie [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), i [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funkcje Członkowskie w `CWnd` klasy podstawowej. Rozszerzenie obsługi wiadomości domyślne, Dodaj mapowanie komunikatów do klasy pochodnej, a funkcje Członkowskie zastąpienie poprzedniego obsługi wiadomości. Zastąpienie `OnCreate`, na przykład, aby wykonać wymagane inicjowania dla nowej klasy.  
  
 Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do formantu pole listy kontrolnej:  
  
- **Ws_child —** zawsze  
  
- **Ws_visible —** zwykle  
  
- **Ws_disabled —** rzadko  
  
- **Ws_vscroll —** można dodać pionowy pasek przewijania  
  
- **Ws_hscroll —** Aby dodać poziomy pasek przewijania  
  
- **Ws_group —** na grupowanie formantów  
  
- **Ws_tabstop —** umożliwia klawisza TAB do tego formantu  
  
##  <a name="drawitem"></a>CCheckListBox::DrawItem  
 Wywoływane przez platformę, gdy visual aspekt zmiany pola rysowanych przez właściciela listy kontrolnej.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Długie wskaźnik do [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) strukturę, która zawiera informacje o typie rysunku wymagane.  
  
### <a name="remarks"></a>Uwagi  
 **ItemAction** i **itemState** członkami `DRAWITEMSTRUCT` struktury zdefiniować rysowania akcję, która ma zostać wykonane.  
  
 Domyślnie ta funkcja rysuje domyślnej listy wyboru, składające się z listą parametrów o rozmiarze domyślnym pole wyboru po lewej stronie. Rozmiar listy wyboru jest określona w [Utwórz](#create).  
  
 Przesłonić tę funkcję elementu członkowskiego, aby zaimplementować rysowaniem pola listy kontrolnej rysowania przez właściciela, które nie są domyślnie, takich jak lista kontrolna pola z listy, które nie są ciągami, elementy o zmiennej wysokości lub pola wyboru, które nie są po lewej stronie. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interfejsu (GDI), wybrane kontekst wyświetlania dostarczane w `lpDrawItemStruct` przed zakończeniem tej funkcji Członkowskich.  
  
 Jeśli elementy pola listy kontrolnej nie są tego samego wysokość, listę kontrolną polu Styl (określony w **Utwórz**) musi być **LBS_OWNERVARIABLE**, i konieczne jest przesłonięcie [MeasureItem](#measureitem) Funkcja.  
  
##  <a name="enable"></a>CCheckListBox::Enable  
 Wywołanie tej funkcji, aby włączyć lub wyłączyć element pole listy kontrolnej.  
  
```  
void Enable(
    int nIndex,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks elementu pole listy kontrolnej włączenia.  
  
 `bEnabled`  
 Określa, czy element jest włączony.  
  
##  <a name="getcheck"></a>CCheckListBox::GetCheck  
 Pobiera stan określonego pola wyboru.  
  
```  
int GetCheck(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks pola wyboru, która znajduje się w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan określonego pola wyboru. W poniższej tabeli przedstawiono możliwe wartości.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`BST_CHECKED`|Pole wyboru jest zaznaczone.|  
|`BST_UNCHECKED`|Nie zaznaczono pola wyboru.|  
|`BST_INDETERMINATE`|Stan pola wyboru jest nieokreślony.|  
  
##  <a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle  
 Wywołanie tej funkcji można pobrać styl pole listy kontrolnej.  
  
```  
UINT GetCheckStyle();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Styl pola wyboru formantu.  
  
### <a name="remarks"></a>Uwagi  
 Informacje dotyczące możliwych stylów znajdują się w temacie [SetCheckStyle](#setcheckstyle).  
  
##  <a name="isenabled"></a>CCheckListBox::IsEnabled  
 Wywołanie tej funkcji, aby określić, czy element jest włączony.  
  
```  
BOOL IsEnabled(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element jest włączony; w przeciwnym razie 0.  
  
##  <a name="measureitem"></a>CCheckListBox::MeasureItem  
 Wywoływane przez platformę, gdy pole listy kontrolnej, styl niestandardowy jest tworzony.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpMeasureItemStruct`  
 Długie wskaźnik do [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta funkcja członkowska nie działa. Zastąpienie tej funkcji Członkowskich i wypełnij `MEASUREITEMSTRUCT` struktury poinformować system Windows wymiarów elementów pole listy kontrolnej. Jeśli pole listy kontrolnej jest tworzony z [lbs_ownerdrawvariable —](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, struktura wywołuje tę funkcję elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ten element członkowski zostanie wywołana tylko raz.  
  
##  <a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition  
 Struktura wywołuje tę funkcję, aby uzyskać położenie i rozmiar pola wyboru w elemencie.  
  
```  
virtual CRect OnGetCheckPosition(
    CRect rectItem,  
    CRect rectCheckBox);
```  
  
### <a name="parameters"></a>Parametry  
 *rectItem*  
 Położenie i rozmiar elementu listy.  
  
 `rectCheckBox`  
 Domyślne położenie i rozmiar pola wyboru elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Położenie i rozmiar pola wyboru elementu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja zwraca tylko domyślne położenie i rozmiar pola wyboru ( `rectCheckBox`). Domyślnie pole wyboru jest wyrównywany w lewym górnym rogu elementu i rozmiar standardowe pole wyboru. Może to być przypadkach, gdy mają pola wyboru po prawej stronie lub mają większy lub mniejszy pole wyboru. W takich sytuacjach należy zastąpić `OnGetCheckPosition` można zmienić pola wyboru położenie i rozmiar w elemencie.  
  
##  <a name="setcheck"></a>CCheckListBox::SetCheck  
 Ustawia stan określonego pola wyboru.  
  
```  
void SetCheck(
    int nIndex,  
    int nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks pola wyboru, która znajduje się w polu listy.  
  
 `nCheck`  
 Stan przycisku dla określonego pola wyboru. W sekcji uwag możliwych wartości.  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono możliwe wartości `nCheck` parametru.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**BST_CHECKED**|Zaznacz pole wyboru określony.|  
|**BST_UNCHECKED**|Wyczyść pole wyboru określony.|  
|**BST_INDETERMINATE**|Ustaw stan określonego pola wyboru nieokreślony.<br /><br /> Ten stan jest dostępna, gdy stylem pole wyboru jest tylko `BS_AUTO3STATE` lub `BS_3STATE`. Aby uzyskać więcej informacji, zobacz [style przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).|  
  
##  <a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle  
 Wywołanie tej funkcji, aby ustawić styl pola wyboru w polu listy kontrolnej.  
  
```  
void SetCheckStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `nStyle`  
 Określa styl pola wyboru w polu listy kontrolnej.  
  
### <a name="remarks"></a>Uwagi  
 Nieprawidłowa style są:  
  
- **BS_CHECKBOX —**  
  
- **BS_AUTOCHECKBOX —**  
  
- **BS_AUTO3STATE —**  
  
- **BS_3STATE —**  
  
 Informacje dotyczące tych stylów znajdują się w temacie [style przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC TSTCON](../../visual-cpp-samples.md)   
 [Clistbox — klasa](../../mfc/reference/clistbox-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CListBox](../../mfc/reference/clistbox-class.md)
