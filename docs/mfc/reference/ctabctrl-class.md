---
title: Ctabctrl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
dev_langs:
- C++
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e46a7d5720be765f2523ebde5d40655fb47b057
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378559"
---
# <a name="ctabctrl-class"></a>Ctabctrl — klasa
Udostępnia funkcje formantu karty wspólne systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CTabCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTabCtrl::CTabCtrl](#ctabctrl)|Konstruuje `CTabCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTabCtrl::AdjustRect](#adjustrect)|Oblicza obszar wyświetlania formantu karty podane prostokąt okna lub oblicza prostokąt okna, który odpowiada obszar wyświetlania danego.|  
|[CTabCtrl::Create](#create)|Tworzy kontrolkę kartę i dołącza go do wystąpienia `CTabCtrl` obiektu.|  
|[CTabCtrl::CreateEx](#createex)|Tworzy kontrolkę kartę w określonym stylu rozszerzonej systemu Windows i dołącza go do wystąpienia `CTabCtrl` obiektu.|  
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Usuwa wszystkie elementy z formantem karty.|  
|[CTabCtrl::DeleteItem](#deleteitem)|Usuwa element z formantem karty.|  
|[CTabCtrl::DeselectAll](#deselectall)|Resetuje elementów w kontrolce karty, usuwając zaznaczenie, które zostały naciśnięte.|  
|[CTabCtrl::DrawItem](#drawitem)|Pobiera określony element z formantem karty.|  
|[CTabCtrl::GetCurFocus](#getcurfocus)|Pobiera karcie z fokusie formantu karty.|  
|[CTabCtrl::GetCurSel](#getcursel)|Określa aktualnie wybrana karta formantu karty.|  
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Pobiera rozszerzone style, które są obecnie używane dla formantu karty.|  
|[CTabCtrl::GetImageList](#getimagelist)|Pobiera listy obrazów skojarzony z formantem karty.|  
|[CTabCtrl::GetItem](#getitem)|Pobiera informacje o karcie formantu karty.|  
|[CTabCtrl::GetItemCount](#getitemcount)|Pobiera numer karty w kontrolce karty.|  
|[CTabCtrl::GetItemRect](#getitemrect)|Pobiera prostokąt ograniczający karty w kontrolce karty.|  
|[CTabCtrl::GetItemState](#getitemstate)|Pobiera stan elementu kontroli wskazanych kartę.|  
|[CTabCtrl::GetRowCount](#getrowcount)|Pobiera bieżący numer wierszy kart w kontrolce karty.|  
|[CTabCtrl::GetToolTips](#gettooltips)|Pobiera dojście formantem etykietki narzędzia, które są skojarzone z formantem karty.|  
|[CTabCtrl::HighlightItem](#highlightitem)|Ustawia stan wyróżnienia element karty.|  
|[CTabCtrl::HitTest](#hittest)|Określa karty, jeśli istnieje, jest na pozycji ekranu.|  
|[CTabCtrl::InsertItem](#insertitem)|Wstawia nową kartę w kontrolce karty.|  
|[CTabCtrl::RemoveImage](#removeimage)|Usuwa obraz z listy obrazów formantu karty.|  
|[CTabCtrl::SetCurFocus](#setcurfocus)|Ustawia fokus do określonej karty w kontrolce karty.|  
|[CTabCtrl::SetCurSel](#setcursel)|Wybiera karty w kontrolce karty.|  
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Ustawia rozszerzone style dla formantu karty.|  
|[CTabCtrl::SetImageList](#setimagelist)|Przypisuje listy obrazów formantu karty.|  
|[CTabCtrl::SetItem](#setitem)|Ustawia niektóre lub wszystkie atrybuty karty.|  
|[CTabCtrl::SetItemExtra](#setitemextra)|Ustawia liczbę bajtów na karcie zarezerwowane dla danych aplikacji w kontrolce karty.|  
|[CTabCtrl::SetItemSize](#setitemsize)|Ustawia szerokość i wysokość elementu.|  
|[CTabCtrl::SetItemState](#setitemstate)|Ustawia stan element kontroli wskazanych karty.|  
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Ustawia minimalną szerokość elementów w kontrolce karty.|  
|[CTabCtrl::SetPadding](#setpadding)|Określa ilość miejsca (dopełnienie) wokół ikony i etykiety formantu karty każdej karcie.|  
|[CTabCtrl::SetToolTips](#settooltips)|Przypisuje formantem etykietki narzędzia do formantu karty.|  
  
## <a name="remarks"></a>Uwagi  
 Formant"karty" jest odpowiednikiem separatorów w notesie lub etykiet w pliku cabinet. Za pomocą formantu karty, aplikację można zdefiniować wiele stron dla tego samego obszaru okno lub okno dialogowe. Każdej strony zawiera zestaw informacji lub grupy formantów wyświetlane aplikacji, gdy użytkownik wybierze odpowiednie karty. Specjalny typ formantu karty wyświetla karty wyglądają jak przyciski. Kliknięcie przycisku należy natychmiast wykonać polecenie zamiast wyświetlania strony.  
  
 Ten formant (i w związku z tym `CTabCtrl` klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Aby uzyskać więcej informacji na temat używania `CTabCtrl`, zobacz [formanty](../../mfc/controls-mfc.md) i [przy użyciu CTabCtrl](../../mfc/using-ctabctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTabCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="adjustrect"></a>  CTabCtrl::AdjustRect  
 Oblicza obszar wyświetlania formantu karty podane prostokąt okna lub oblicza prostokąt okna, który odpowiada obszar wyświetlania danego.  
  
```  
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `bLarger`  
 Wskazuje, które operacji do wykonania. Jeśli ten parametr ma **TRUE**, `lpRect` określa prostokątny obszar wyświetlania i odbiera prostokąt odpowiednie okna. Jeśli ten parametr ma **FALSE**, `lpRect` Określa prostokąt okna i odbiera odpowiedniego prostokątny obszar wyświetlania.  
  
 `lpRect`  
 Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która określa danego prostokąt i odbiera obliczony prostokąt.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]  
  
##  <a name="create"></a>  CTabCtrl::Create  
 Tworzy kontrolkę kartę i dołącza go do wystąpienia `CTabCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl formantu karty. Zastosuj dowolną kombinację [karcie stylów formantu](http://msdn.microsoft.com/library/windows/desktop/bb760549), które zostały opisane w zestawie SDK systemu Windows. Zobacz **uwagi** listę Style okna, które można także zastosować do formantu.  
  
 `rect`  
 Określa rozmiar i położenie formantu karty. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki karty, zwykle `CDialog`. Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu karty.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli inicjowania obiektu się powiodła; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CTabCtrl` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać **Utwórz**, która tworzy formantu karty i dołącza go do `CTabCtrl` obiektu.  
  
 Oprócz karta stylów formantu należy zastosować następujące style okna do formantu karty:  
  
- **Ws_child —** tworzy okno podrzędne, które reprezentuje formantu karty. Nie można używać z `WS_POPUP` stylu.  
  
- **Ws_visible —** tworzy kontrolkę kartę, która jest widoczna od początku.  
  
- **Ws_disabled —** tworzy okno, które jest początkowo wyłączone.  
  
- **Ws_group —** Określa pierwszą kontrolkę grupy formantów, w których użytkownik może przechodzić z jednego formantu do drugiego za pomocą klawiszy strzałek. Wszystkie formanty zdefiniowane z **ws_group —** styl po pierwszą kontrolkę należą do tej samej grupy. Następnego formantu z **ws_group —** styl kończy się grupie styl i uruchamia następnej grupy (oznacza to, że jedna grupa kończy się którym rozpoczyna się następne).  
  
- **Ws_tabstop —** określa jeden z dowolną liczbę formantów za pomocą których użytkownik może przenieść za pomocą klawisza TAB. Klawisz TAB przenosi użytkownika do następnego formantu określony przez **ws_tabstop —** stylu.  
  
 Aby utworzyć formantu karty z rozszerzone Style okna, należy wywołać [CTabCtrl::CreateEx](#createex) zamiast **Utwórz**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CTabCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CTabCtrl` obiektu.  
  
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
 Określa styl formantu karty. Zastosuj dowolną kombinację [karcie stylów formantu](http://msdn.microsoft.com/library/windows/desktop/bb760549), które zostały opisane w zestawie SDK systemu Windows. Zobacz **uwagi** w [Utwórz](#create) listę Style okna, które można także zastosować do formantu.  
  
 `rect`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujące rozmiar i położenie okna, które ma zostać utworzony w współrzędne klienta `pParentWnd`.  
  
 `pParentWnd`  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 `nID`  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera w razie powodzenia 0 w inny sposób.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) dotyczyć rozszerzone style systemu Windows, określone przez wstępu rozszerzonego stylu Windows **WS_EX_**.  
  
 `CreateEx` Tworzy formantu z rozszerzone style Windows określonego przez `dwExStyle`. Rozszerzone style właściwe dla formantu przy użyciu zestawu [SetExtendedStyle](#setextendedstyle). Na przykład użyć `CreateEx` można ustawić takie style jako **ws_ex_contexthelp —**, ale użyj `SetExtendedStyle` można ustawić takie style jako **tcs_ex_flatseparators —**. Aby uzyskać więcej informacji, zobacz style opisanego w [kartę kontroli rozszerzone style](http://msdn.microsoft.com/library/windows/desktop/bb760546) w zestawie Windows SDK.  
  
##  <a name="ctabctrl"></a>  CTabCtrl::CTabCtrl  
 Konstruuje `CTabCtrl` obiektu.  
  
```  
CTabCtrl();
```  
  
##  <a name="deleteallitems"></a>  CTabCtrl::DeleteAllItems  
 Usuwa wszystkie elementy z formantem karty.  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="deleteitem"></a>  CTabCtrl::DeleteItem  
 Usuwa określony element z formantem karty.  
  
```  
BOOL DeleteItem(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Liczony od zera wartość elementu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]  
  
##  <a name="deselectall"></a>  CTabCtrl::DeselectAll  
 Resetuje elementów w kontrolce karty, usuwając zaznaczenie, które zostały naciśnięte.  
  
```  
void DeselectAll(BOOL fExcludeFocus);
```  
  
### <a name="parameters"></a>Parametry  
 *fExcludeFocus*  
 Flaga, która określa zakres deselection elementu. Jeśli ten parametr ma wartość **FALSE**, wszystkie przycisków karty zostanie zresetowany. Jeśli wartość jest ustawiona na **TRUE**, a następnie wszystkie elementy kartę, z wyjątkiem aktualnie zaznaczony spowoduje zresetowanie.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TCM_DESELECTALL](http://msdn.microsoft.com/library/windows/desktop/bb760579), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="drawitem"></a>  CTabCtrl::DrawItem  
 Wywoływane przez platformę, gdy visual aspekt rysowania przez właściciela kartę kontroli zmian.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Wskaźnik do [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) opisujące elementu, który ma zostać narysowany struktury.  
  
### <a name="remarks"></a>Uwagi  
 **ItemAction** członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane.  
  
 Domyślnie ta funkcja członkowska nie działa. Przesłonić tę funkcję elementu członkowskiego, aby zaimplementować rysunku rysowania przez właściciela `CTabCtrl` obiektu.  
  
 Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interfejsu (GDI), wybrane kontekst wyświetlania dostarczane w `lpDrawItemStruct` przed ten element członkowski kończy funkcji.  
  
##  <a name="getcurfocus"></a>  CTabCtrl::GetCurFocus  
 Pobiera indeks karcie z bieżącym fokus.  
  
```  
int GetCurFocus() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks karcie z bieżącym fokus.  
  
##  <a name="getcursel"></a>  CTabCtrl::GetCurSel  
 Pobiera aktualnie wybrana karta formantu karty.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks wybranej karty w przypadku powodzenia lub - 1, jeśli karta nie jest zaznaczone.  
  
##  <a name="getextendedstyle"></a>  CTabCtrl::GetExtendedStyle  
 Pobiera rozszerzone style, które są obecnie używane dla formantu karty.  
  
```  
DWORD GetExtendedStyle();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reprezentuje rozszerzone style obecnie w przypadku formantu karty. Ta wartość jest kombinacją [karcie kontroli rozszerzone style](http://msdn.microsoft.com/library/windows/desktop/bb760546), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TCM_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb760585), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getimagelist"></a>  CTabCtrl::GetImageList  
 Pobiera listy obrazów, który został skojarzony z formantem karty.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia operacji kontroli wskaźnik do listy obrazów karty; w przeciwnym razie **NULL**.  
  
##  <a name="getitem"></a>  CTabCtrl::GetItem  
 Pobiera informacje o karcie formantu karty.  
  
```  
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Liczony od zera indeks karty.  
  
 `pTabCtrlItem`  
 Wskaźnik do [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktury, używany do określenia informacji do pobrania. Umożliwia również odbierać informacje o karcie. Ta struktura jest używany z `InsertItem`, `GetItem`, i `SetItem` funkcji elementów członkowskich.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia; **FALSE** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Po wysłaniu wiadomości **maski** elementu członkowskiego określa atrybuty do zwrócenia. Jeśli **maski** określa element członkowski `TCIF_TEXT` wartość **pszText** elementu członkowskiego musi zawierać adres buforu, który odbiera tekst elementu i **cchTextMax** element członkowski musi być określony rozmiar buforu.  
  
 **Maska**  
 Wartość określającą, którym `TCITEM` struktury elementów członkowskich można pobrać lub ustawić. Ten element członkowski może być zero lub kombinację następujących wartości:  
  
- `TCIF_TEXT` **PszText** elementu członkowskiego jest nieprawidłowy.  
  
- `TCIF_IMAGE` `iImage` Elementu członkowskiego jest nieprawidłowy.  
  
- `TCIF_PARAM` **LParam** elementu członkowskiego jest nieprawidłowy.  
  
- `TCIF_RTLREADING` Tekst **pszText** jest wyświetlana w systemach hebrajski lub arabski przy użyciu kolejność czytania od prawej do lewej.  
  
- `TCIF_STATE` **DwState** elementu członkowskiego jest nieprawidłowy.  
  
 **pszText**  
 Wskaźnik do zerem ciąg zawierający tekst kartę, jeśli struktura zawiera informacje o karcie. Jeśli struktura otrzymuje informacje, ten element członkowski Określa adres buforu, który odbiera tekst kartę.  
  
 **cchTextMax**  
 Rozmiar buforu wskazywana przez **pszText**. Ten element członkowski jest ignorowana, jeśli struktura nie otrzymuje informacji.  
  
 `iImage`  
 Indeksuj do formantu karty listy obrazów, lub - 1, jeśli nie ma żadnego obrazu dla karty.  
  
 **lParam**  
 Dane zdefiniowane przez aplikację skojarzona z kartą. W przypadku więcej niż czterech bajtów danych aplikacji na karcie aplikacji musi definiować strukturę i użyć zamiast `TCITEM` struktury. Pierwszy element członkowski struktury zdefiniowane aplikacji musi być [TCITEMHEADER](http://msdn.microsoft.com/library/windows/desktop/bb760556)struktury. **TCITEMHEADER** struktura jest taka sama jak `TCITEM` struktury, ale bez **lParam** elementu członkowskiego. Różnica między rozmiar struktury i rozmiar **TCITEMHEADER** struktury powinna być równa liczbę dodatkowych bajtów na karcie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]  
  
##  <a name="getitemcount"></a>  CTabCtrl::GetItemCount  
 Pobiera numer karty w kontrolce karty.  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w kontrolce karty.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="getitemrect"></a>  CTabCtrl::GetItemRect  
 Pobiera prostokąt ograniczający dla określonej karty w kontrolce karty.  
  
```  
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Liczony od zera indeks elementu kartę.  
  
 `lpRect`  
 Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która odbiera prostokątem karty. Tych współrzędnych w trybie okienka ekranu bieżącego mapowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="getitemstate"></a>  CTabCtrl::GetItemState  
 Pobiera stan elementu formantu karty identyfikowane przez `nItem`.  
  
```  
DWORD GetItemState(
    int nItem,  
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Liczony od zera numer indeksu elementu, dla którego można pobrać informacji o stanie.  
  
 `dwMask`  
 Maska określający, którego stan elementu flagi do zwrócenia. Listę wartości, zobacz maski członkiem [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktury, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `DWORD` wartość odbieranie informacji o stanie. Może to być jedna z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**TCIS_BUTTONPRESSED**|Wybrano element formantu karty.|  
|**TCIS_HIGHLIGHTED**|Element formantu karty zostanie wyróżniona, a karta i tekst są rysowane przy użyciu bieżący kolor wyróżnienia. Używając koloru wyróżnienia, będzie interpolacji wartość true, nie kolor symulowany.|  
  
### <a name="remarks"></a>Uwagi  
 Stan elementu jest określona przez **dwState** członkiem `TCITEM` struktury.  
  
##  <a name="getrowcount"></a>  CTabCtrl::GetRowCount  
 Pobiera aktualna liczba wierszy w kontrolce karty.  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wierszy kart w kontrolce karty.  
  
### <a name="remarks"></a>Uwagi  
 Tylko karcie formantów, które mają **TCS_MULTILINE** styl może mieć wiele wierszy kart.  
  
##  <a name="gettooltips"></a>  CTabCtrl::GetToolTips  
 Pobiera dojście formantem etykietki narzędzia, które są skojarzone z formantem karty.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście formantem etykietki narzędzia w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Formant karty tworzy formantem etykietki narzędzia, jeśli ma ona **TCS_TOOLTIPS** stylu. Formantem etykietki narzędzia można przypisać do formantu karty, za pomocą `SetToolTips` funkcję elementu członkowskiego.  
  
##  <a name="highlightitem"></a>  CTabCtrl::HighlightItem  
 Ustawia stan wyróżnienia element karty.  
  
```  
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `idItem`  
 Liczony od zera indeks elementu kontrolki karty.  
  
 `fHighlight`  
 Wartość określającą ustawiany stan wyróżnienia. Jeśli ta wartość jest **TRUE**, wyróżniony karcie; Jeśli **FALSE**, karcie ustawiono do stanu domyślnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Funkcji członkowskiej implementuje komunikat Win32 [TCM_HIGHLIGHTITEM](http://msdn.microsoft.com/library/windows/desktop/bb760602), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="hittest"></a>  CTabCtrl::HitTest  
 Określa karty, jeśli istnieje, jest na pozycji ekranu.  
  
```  
int HitTest(TCHITTESTINFO* pHitTestInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pHitTestInfo`  
 Wskaźnik do [TCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760553) struktury, zgodnie z opisem w zestawie Windows SDK, który określa położenie ekranu do testowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczony od zera indeks karcie lub - 1, jeśli karta nie jest w określonej pozycji.  
  
##  <a name="insertitem"></a>  CTabCtrl::InsertItem  
 Wstawia nową kartę w istniejącej kontrolce karty.  
  
```  
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

 
LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

 
LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

 
LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

 
LONG InsertItem(
    UINT nMask,  
    int nItem,  
    LPCTSTR lpszItem,  
    int nImage,  
    LPARAM lParam,  
    DWORD dwState,  
    DWORD dwStateMask);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Liczony od zera indeks nowej karcie.  
  
 `pTabCtrlItem`  
 Wskaźnik do [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) strukturę, która określa atrybuty karty.  
  
 `lpszItem`  
 Adres zerem ciąg, który zawiera tekst karty.  
  
 `nImage`  
 Liczony od zera indeks obrazu do wstawienia z listy obrazów.  
  
 `nMask`  
 Określa, która `TCITEM` struktury atrybuty do ustawienia. Może być zero lub kombinację następujących wartości:  
  
- `TCIF_TEXT` **PszText** elementu członkowskiego jest nieprawidłowy.  
  
- `TCIF_IMAGE` `iImage` Elementu członkowskiego jest nieprawidłowy.  
  
- `TCIF_PARAM` **LParam** elementu członkowskiego jest nieprawidłowy.  
  
- `TCIF_RTLREADING` Tekst **pszText** jest wyświetlana w systemach hebrajski lub arabski przy użyciu kolejność czytania od prawej do lewej.  
  
- `TCIF_STATE` **DwState** elementu członkowskiego jest nieprawidłowy.  
  
 `lParam`  
 Dane zdefiniowane przez aplikację skojarzona z kartą.  
  
 `dwState`  
 Określa wartości stanów elementu. Aby uzyskać więcej informacji, zobacz [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) w zestawie Windows SDK.  
  
 *dwStateMask*  
 Określa, które stany mają być tworzone. Aby uzyskać więcej informacji, zobacz [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks nową kartę w przypadku powodzenia; w przeciwnym razie wartość - 1.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]  
  
##  <a name="removeimage"></a>  CTabCtrl::RemoveImage  
 Usuwa określony obraz z listy obrazów formantu karty.  
  
```  
void RemoveImage(int nImage);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Liczony od zera indeks obrazu do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Formantu karty aktualizuje każdy indeks obrazu, aby każdej karcie pozostają skojarzone z tego samego obrazu.  
  
##  <a name="setcurfocus"></a>  CTabCtrl::SetCurFocus  
 Ustawia fokus do określonej karty w kontrolce karty.  
  
```  
void SetCurFocus(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Określa indeks kartę, która pobiera fokus.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TCM_SETCURFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb760610), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setcursel"></a>  CTabCtrl::SetCurSel  
 Wybiera karty w kontrolce karty.  
  
```  
int SetCurSel(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Liczony od zera indeks elementu do wybrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks karcie poprzednio wybranego w przypadku powodzenia, w przeciwnym razie wartość - 1.  
  
### <a name="remarks"></a>Uwagi  
 Formant karty nie wysyła **TCN_SELCHANGING** lub **TCN_SELCHANGE** wiadomość z powiadomieniem po wybraniu karty przy użyciu tej funkcji. Te powiadomienia są wysyłane przy użyciu **WM_NOTIFY**, gdy użytkownik kliknie lub korzysta z klawiatury do zmiany karty.  
  
##  <a name="setextendedstyle"></a>  CTabCtrl::SetExtendedStyle  
 Ustawia rozszerzone style dla formantu karty.  
  
```  
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `dwNewStyle`  
 Wartość określającą kombinację kartę kontrolować rozszerzone style.  
  
 `dwExMask`  
 A `DWORD` wartość, która wskazuje style w `dwNewStyle` są, których to dotyczy. Tylko rozszerzone style w `dwExMask` zostanie zmieniona. Wszystkie inne style będzie przechowywany jest. Jeśli ten parametr ma wartość zero, a następnie wszystkie style w `dwNewStyle` będzie dotyczył.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `DWORD` wartości, która zawiera poprzedniej [karcie kontroli rozszerzone style](http://msdn.microsoft.com/library/windows/desktop/bb760546), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TCM_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb760627), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setimagelist"></a>  CTabCtrl::SetImageList  
 Przypisuje listy obrazów formantu karty.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `pImageList`  
 Wskaźnik do listy obrazów, który ma zostać przypisany do formantu karty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do poprzedniej liście obrazu lub **NULL** Jeśli nie są znane poprzedniego obrazu.  
  
##  <a name="setitem"></a>  CTabCtrl::SetItem  
 Ustawia niektóre lub wszystkie atrybuty karty.  
  
```  
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Liczony od zera indeks elementu.  
  
 `pTabCtrlItem`  
 Wskaźnik do [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktury, która zawiera nowe atrybuty elementu. **Maski** elementu członkowskiego określenie atrybutów, które można ustawić. Jeśli **maski** określa element członkowski `TCIF_TEXT` wartość **pszText** elementu członkowskiego jest adresem ciąg znaków zakończony znakiem null i **cchTextMax** elementu członkowskiego jest ignorowana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [GetItem](#getitem).  
  
##  <a name="setitemextra"></a>  CTabCtrl::SetItemExtra  
 Ustawia liczbę bajtów na karcie zarezerwowane dla danych aplikacji w kontrolce karty.  
  
```  
BOOL SetItemExtra(int nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Liczba dodatkowych bajtów do ustawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TCM_SETITEMEXTRA](http://msdn.microsoft.com/library/windows/desktop/bb760633), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setitemsize"></a>  CTabCtrl::SetItemSize  
 Ustawia szerokość i wysokość elementów formantu karty.  
  
```  
CSize SetItemSize(CSize size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Nową szerokość i wysokość w pikselach elementów formantu karty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca starego szerokości i wysokości elementów formantu karty.  
  
##  <a name="setitemstate"></a>  CTabCtrl::SetItemState  
 Ustawia stan element formantu karty identyfikowane przez `nItem`.  
  
```  
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Liczony od zera numer indeksu elementu, dla którego można ustawić informacji o stanie.  
  
 `dwMask`  
 Określanie, która stanu elementu flagi można ustawić maski. Listę wartości, zobacz maski członkiem [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktury, zgodnie z opisem w zestawie Windows SDK.  
  
 `dwState`  
 Odwołanie do `DWORD` wartość zawierającą informacje o stanie. Może to być jedna z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**TCIS_BUTTONPRESSED**|Wybrano element formantu karty.|  
|**TCIS_HIGHLIGHTED**|Element formantu karty zostanie wyróżniona, a karta i tekst są rysowane przy użyciu bieżący kolor wyróżnienia. Używając koloru wyróżnienia, będzie interpolacji wartość true, nie kolor symulowany.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="setmintabwidth"></a>  CTabCtrl::SetMinTabWidth  
 Ustawia minimalną szerokość elementów w kontrolce karty.  
  
```  
int SetMinTabWidth(int cx);
```  
  
### <a name="parameters"></a>Parametry  
 `cx`  
 Minimalna szerokość można ustawić dla elementu kontroli kartę. Jeśli ten parametr ma ustawioną wartość -1, kontrolka będzie używać domyślnej szerokości karty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednie szerokość minimalna kartę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TCM_SETMINTABWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760637), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setpadding"></a>  CTabCtrl::SetPadding  
 Określa ilość miejsca (dopełnienie) wokół ikony i etykiety formantu karty każdej karcie.  
  
```  
void SetPadding(CSize size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Określa ilość miejsca (dopełnienie) wokół ikony i etykiety formantu karty każdej karcie.  
  
##  <a name="settooltips"></a>  CTabCtrl::SetToolTips  
 Przypisuje formantem etykietki narzędzia do formantu karty.  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndTip`  
 Dojście formantem etykietki narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Możesz uzyskać formantem etykietki narzędzia, które są skojarzone z formantem karty poprzez wywołanie `GetToolTips`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cheaderctrl — klasa](../../mfc/reference/cheaderctrl-class.md)   
 [Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)
