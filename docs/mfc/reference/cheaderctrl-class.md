---
title: Klasa CHeaderCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebe4b604958220a846ee3a91b1a6251f6f461de9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693470"
---
# <a name="cheaderctrl-class"></a>Klasa CHeaderCtrl
Oferuje funkcje formantu typowego nagłówka Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CHeaderCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|Konstruuje `CHeaderCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Usuwa wszystkie filtry dla formantu nagłówka.|  
|[CHeaderCtrl::ClearFilter](#clearfilter)|Usuwa filtr dla kontrolki nagłówka.|  
|[CHeaderCtrl::Create](#create)|Tworzy kontrolki nagłówka i dołącza je do `CHeaderCtrl` obiektu.|  
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Tworzy przezroczyste wersję obrazu elementu w formancie nagłówka.|  
|[CHeaderCtrl::CreateEx](#createex)|Tworzy kontrolki nagłówka przy użyciu określonego stylów rozszerzonej Windows i dołącza je do `CListCtrl` obiektu.|  
|[CHeaderCtrl::DeleteItem](#deleteitem)|Usuwa element z formantem nagłówka.|  
|[CHeaderCtrl::DrawItem](#drawitem)|Rysuje określony element kontrolki nagłówka.|  
|[CHeaderCtrl::EditFilter](#editfilter)|Uruchamia określony filtr kontrolki nagłówka do edycji.|  
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Pobiera szerokość na marginesie mapy bitowej w formancie nagłówka.|  
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Pobiera identyfikator elementu w bieżącym kontrolki nagłówka, który ma fokus.|  
|[CHeaderCtrl::GetImageList](#getimagelist)|Pobiera uchwyt listy obrazów, który jest używany do rysowania elementy nagłówka w formancie nagłówka.|  
|[CHeaderCtrl::GetItem](#getitem)|Pobiera informacje o elemencie w formancie nagłówka.|  
|[CHeaderCtrl::GetItemCount](#getitemcount)|Pobiera liczbę elementów w formancie nagłówka.|  
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Pobiera prostokąt otaczający dotycząca określonego przycisk listy rozwijanej w formancie nagłówka.|  
|[CHeaderCtrl::GetItemRect](#getitemrect)|Pobiera prostokąt otaczający dla danego elementu w formancie nagłówka.|  
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Pobiera kolejność od lewej do prawej strony elementów w formancie nagłówka.|  
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Pobiera bieżący kontrolki nagłówka prostokąt otaczający przycisku przepełnienia.|  
|[CHeaderCtrl::HitTest](#hittest)|Określa, który element nagłówka, znajduje się w określonym momencie.|  
|[CHeaderCtrl::InsertItem](#insertitem)|Wstawia nowy element do formantu nagłówka.|  
|[CHeaderCtrl::Layout](#layout)|Pobiera rozmiar i położenie formantu nagłówka w obrębie danego prostokąta.|  
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Pobiera wartość indeksu dla elementu na podstawie jego zamówienia w formancie nagłówka.|  
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Określa szerokość mapy bitowej na marginesie w formancie nagłówka.|  
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Ustawia limit czasu między czasu zmiany odbywa się w atrybutach filtrów i delegowania `HDN_FILTERCHANGE` powiadomień.|  
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Ustawia element określonego nagłówka w formancie nagłówka bieżący fokus.|  
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Zmiany, linię podziału między elementy nagłówka w celu wskazania ręcznego przeciągania i upuszczania elementu nagłówka.|  
|[CHeaderCtrl::SetImageList](#setimagelist)|Przypisuje listy obrazów kontrolki nagłówka.|  
|[CHeaderCtrl::SetItem](#setitem)|Ustawia atrybuty określonego elementu w formancie nagłówka.|  
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Ustawia kolejność od lewej do prawej strony elementów w formancie nagłówka.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrolki nagłówka o jest oknem które zazwyczaj jest umieszczana powyżej kolumny tekstu lub liczb. Zawiera on tytuł dla każdej kolumny, a można podzielić na części. Użytkownik może przeciągać separatorów, których części, aby ustawić szerokość każdej kolumny. Ilustracja kontrolki nagłówka znajduje się [kontrolki nagłówka](/windows/desktop/Controls/header-controls).  
  
 Ta kontrolka (i w związku z tym `CHeaderCtrl` klasy) jest dostępna tylko dla programów, które działają w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Funkcje dodane do wspólnych formantów Windows 95/Internet Explorer 4.0 obejmuje następujące funkcje:  
  
-   Nagłówek elementu niestandardowego porządkowania.  
  
-   Element nagłówka przeciągnij i upuść, do zmiany kolejności elementów nagłówka. Hds_dragdrop — styl są używane podczas tworzenia `CHeaderCtrl` obiektu.  
  
-   Tekst kolumny nagłówek jest stale wyświetlane podczas zmiany rozmiaru kolumn. Styl HDS_FULLDRAG są używane podczas tworzenia `CHeaderCtrl` obiektu.  
  
-   Nagłówek aktywne śledzenie, co powoduje elementu nagłówka, gdy wskaźnik myszy znajduje się nad nią. Styl HDS_HOTTRACK są używane podczas tworzenia `CHeaderCtrl` obiektu.  
  
-   Obsługa listy obrazów. Elementy nagłówka może zawierać obrazów przechowywanych w `CImageList` obiektu lub tekstu.  
  
 Aby uzyskać więcej informacji o korzystaniu z `CHeaderCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [korzystanie z CHeaderCtrl](../../mfc/using-cheaderctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHeaderCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="cheaderctrl"></a>  CHeaderCtrl::CHeaderCtrl  
 Konstruuje `CHeaderCtrl` obiektu.  
  
```  
CHeaderCtrl();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]  
  
##  <a name="clearallfilters"></a>  CHeaderCtrl::ClearAllFilters  
 Usuwa wszystkie filtry dla formantu nagłówka.  
  
```  
BOOL ClearAllFilters();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda implementuje zachowanie komunikatu Win32 [HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter) z wartością kolumny-1, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]  
  
##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter  
 Usuwa filtr dla kontrolki nagłówka.  
  
```  
BOOL ClearFilter(int nColumn);
```  
  
### <a name="parameters"></a>Parametry  
 *nColumn*  
 Wartość kolumny, wskazujące, której filtr, aby wyczyścić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda implementuje zachowanie komunikatu Win32 [HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]  
  
##  <a name="create"></a>  CHeaderCtrl::Create  
 Tworzy kontrolki nagłówka i dołącza je do `CHeaderCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Określa styl kontrolki nagłówka. Aby uzyskać opis style kontrolki nagłówka, zobacz [style kontrolki nagłówka](/windows/desktop/Controls/header-control-styles) w zestawie Windows SDK.  
  
 *Rect*  
 Określa rozmiar i położenie kontrolki nagłówka. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.  
  
 *pParentWnd*  
 Określa okno nadrzędne kontrolki nagłówka, zwykle `CDialog`. Nie może być równa NULL.  
  
 *nID*  
 Określa identyfikator kontrolki nagłówka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli inicjowanie się powiodła. w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowanie `CHeaderCtrl` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołać `Create`, który tworzy kontrolki nagłówka i dołącza go do `CHeaderCtrl` obiektu.  
  
 Oprócz style kontrolki nagłówka, można użyć następujących najczęściej używane style kontrolki do określenia pozycji i zmienia rozmiar samego formantu nagłówka (zobacz [najczęściej używane style kontrolki](/windows/desktop/Controls/common-control-styles) Aby uzyskać więcej informacji):  
  
- CCS_BOTTOM powoduje, że formant do samej pozycji w dolnej części obszaru klienckiego okna nadrzędnego i ustawia szerokość, która jest taka sama jak nadrzędnego szerokość okna.  
  
- Zapobiega CCS_NODIVIDER pikseli dwóch zaznacz z możliwością rysowania na górze kontrolki.  
  
- CCS_NOMOVEY powoduje, że formant zmienić rozmiar i Przenieś sam w poziomie, ale nie w pionie, w odpowiedzi na wiadomość WM_SIZE. Jeśli styl CCS_NORESIZE ten styl nie ma zastosowania. Kontrolki nagłówka mają ten styl domyślnie.  
  
- CCS_NOPARENTALIGN uniemożliwia jego automatyczne przejście do góry lub u dołu okna nadrzędnego. Zamiast tego formant zachowuje jego położenie w oknie nadrzędnym, niezależnie od zmian do rozmiaru okna nadrzędnego. Jeśli styl CCS_TOP lub CCS_BOTTOM jest również używany, wysokość jest dostosowana do domyślnego, ale pozycji i szerokość pozostają niezmienione.  
  
- CCS_NORESIZE zapobiega przy użyciu domyślnej szerokości i wysokości, ustawiając jego początkowy rozmiar lub nowy rozmiar kontrolki. Zamiast tego formantu używa szerokość i wysokość określony w żądaniu do tworzenia lub zmiany rozmiaru.  
  
- CCS_TOP powoduje, że formant do samej pozycji w górnej części obszaru klienckiego okna nadrzędnego i ustawia szerokość, która jest taka sama jak nadrzędnego szerokość okna.  
  
 Następujące style okna ramowego również można zastosować do formantu nagłówka (zobacz [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) Aby uzyskać więcej informacji):  
  
- WS_CHILD tworzy okno podrzędne. Nie można używać ze stylem WS_POPUP.  
  
- WS_VISIBLE tworzy okno, które jest początkowo widoczne.  
  
- WS_DISABLED tworzy okno, które jest początkowo wyłączone.  
  
- WS_GROUP Określa pierwszy formant grupy formantów, w których użytkownik może przechodzić z jednego formantu do drugiego za pomocą klawiszy strzałek. Wszystkie formanty zdefiniowane przy użyciu stylu WS_GROUP po pierwszej kontroli należą do tej samej grupy. Następny formant ze stylem WS_GROUP kończy grupy stylów i rozpoczyna następną grupę (oznacza to, że jedna grupa kończy się gdzie rozpoczyna się następna).  
  
- WS_TABSTOP określa jeden z wielu formantów, za pomocą których użytkownik może poruszać się używając klawisza TAB. Klawisz TAB przesuwa użytkownika do następnej kontrolki określonej przez styl WS_TABSTOP.  
  
 Style rozszerzone systemu windows za pomocą formantu należy wywołać [CreateEx](#createex) zamiast `Create`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]  
  
##  <a name="createex"></a>  CHeaderCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i powiąż ją z `CHeaderCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.  
  
 *dwStyle*  
 Styl kontrolki nagłówka. Aby uzyskać opis style kontrolki nagłówka, zobacz [style kontrolki nagłówka](/windows/desktop/Controls/header-control-styles) w zestawie Windows SDK. Zobacz [Utwórz](#create) listę dodatkowe style.  
  
 *Rect*  
 Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.  
  
 *pParentWnd*  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 *nID*  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast `Create` do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="createdragimage"></a>  CHeaderCtrl::CreateDragImage  
 Tworzy przezroczyste wersję obrazu elementu w formancie nagłówka.  
  
```  
CImageList* CreateDragImage(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczony od zera indeks elementu w formancie nagłówka. Obraz przypisane do tego elementu jest podstawą przezroczystego obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL. Zwracana lista zawiera tylko jeden obraz.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [HDM_CREATEDRAGIMAGE](/windows/desktop/Controls/hdm-createdragimage), zgodnie z opisem w zestawie Windows SDK. Jest ona udostępniana do obsługuje nagłówka towaru przeciągania i upuszczania.  
  
 `CImageList` Obiekt, do którego punktów zwrócony wskaźnik jest obiektem tymczasowym i zostanie usunięty z następnego przetwarzania czas bezczynności (%).  
  
##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem  
 Usuwa element z formantem nagłówka.  
  
```  
BOOL DeleteItem(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Określa liczony od zera indeks elementu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]  
  
##  <a name="drawitem"></a>  CHeaderCtrl::DrawItem  
 Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt zmian kontrolki nagłówka rysowane przez właściciela.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDrawItemStruct*  
 Wskaźnik do [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) struktura zawierająca opis elementu do narysowania.  
  
### <a name="remarks"></a>Uwagi  
 `itemAction` Członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane.  
  
 Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpienie tej funkcji elementu członkowskiego do zaimplementowania rysunku do rysowania przez właściciela `CHeaderCtrl` obiektu.  
  
 Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interface (GDI), wybrany dla kontekstu wyświetlana podana w *lpDrawItemStruct* przed ten element członkowski funkcja kończy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]  
  
##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter  
 Rozpoczyna edycję określony filtr kontrolki nagłówka.  
  
```  
BOOL EditFilter(
    int nColumn,  
    BOOL bDiscardChanges);
```  
  
### <a name="parameters"></a>Parametry  
 *nColumn*  
 Kolumna do edycji.  
  
 *bDiscardChanges*  
 Wartość, która określa sposób obsługi użytkownika przez edytowanie zmian, jeśli użytkownik jest w trakcie edycji filtru po [HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter) zostanie wysłana wiadomość.  
  
 Określ wartość TRUE, aby odrzucić zmiany wprowadzone przez użytkownika, lub FAŁSZ, aby zatwierdzić zmiany wprowadzone przez użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda implementuje zachowanie komunikatu Win32 [HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]  
  
##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin  
 Pobiera szerokość na marginesie mapy bitowej w formancie nagłówka.  
  
```  
int GetBitmapMargin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość marginesu mapy bitowej w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [HDM_GETBITMAPMARGIN](/windows/desktop/Controls/hdm-getbitmapmargin), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]  
  
##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem  
 Pobiera indeks elementu, który ma fokus w bieżącym kontrolki nagłówka.  
  
```  
int GetFocusedItem() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks elementu nagłówka, który ma fokus.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [HDM_GETFOCUSEDITEM](/windows/desktop/Controls/hdm-getfocuseditem) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_headerCtrl`, to znaczy umożliwiają dostęp do bieżącego kontrolki nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje `SetFocusedItem` i `GetFocusedItem` metody. W starszych sekcji kodu utworzyliśmy kontrolki nagłówka z pięciu kolumnach. Jednak można przeciągnąć separator kolumn, tak, aby ta kolumna nie jest widoczny. Poniższy przykład ustawia i następnie potwierdza nagłówek ostatniej kolumny jako element fokus.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList  
 Pobiera uchwyt listy obrazów, który jest używany do rysowania elementy nagłówka w formancie nagłówka.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [HDM_GETIMAGELIST](/windows/desktop/Controls/hdm-getimagelist), zgodnie z opisem w zestawie Windows SDK. `CImageList` Obiekt, do którego punktów zwrócony wskaźnik jest obiektem tymczasowym i zostanie usunięty z następnego przetwarzania czas bezczynności (%).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]  
  
##  <a name="getitem"></a>  CHeaderCtrl::GetItem  
 Pobiera informacje o elementach kontrolki nagłówka.  
  
```  
BOOL GetItem(
    int nPos,  
    HDITEM* pHeaderItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Określa liczony od zera indeks elementu do pobrania.  
  
 *pHeaderItem*  
 Wskaźnik do [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) strukturę, która otrzymuje nowy element. Ta struktura jest używana z `InsertItem` i `SetItem` funkcji elementów członkowskich. Flagi, ustaw w `mask` element upewnij się, że wartości w odpowiednich elementów są poprawnie wypełnione po powrocie. Jeśli `mask` element jest ustawiony na wartość zero, wartości w innych elementach struktury są bez znaczenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]  
  
##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount  
 Pobiera liczbę elementów w formancie nagłówka.  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementy kontrolki nagłówka, jeśli to się powiedzie; w przeciwnym razie - 1.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CHeaderCtrl::DeleteItem](#deleteitem).  
  
##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect  
 Pobiera element nagłówka w formancie nagłówka bieżący prostokąt otaczający przycisk listy rozwijanej.  
  
```  
BOOL GetItemDropDownRect(
    int iItem,   
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *towaru*|Liczony od zera indeks elementu nagłówek, którego styl jest HDF_SPLITBUTTON. Aby uzyskać więcej informacji, zobacz `fmt` członkiem [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) struktury.|  
|[out] *lprect —*|Wskaźnik do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury do uzyskiwania informacji prostokąt otaczający.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli funkcja się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [HDM_GETITEMDROPDOWNRECT](/windows/desktop/Controls/hdm-getitemdropdownrect) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_headerCtrl`, to znaczy umożliwiają dostęp do bieżącego kontrolki nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje `GetItemDropDownRect` metody. W starszych sekcji kodu utworzyliśmy kontrolki nagłówka z pięciu kolumnach. Poniższy kod rysuje prostokąt 3D wokół lokalizację, w pierwszej kolumnie FF zarezerwowanego dla nagłówka przycisk listy rozwijanej.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]  
  
##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect  
 Pobiera prostokąt otaczający dla danego elementu w formancie nagłówka.  
  
```  
BOOL GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczony od zera indeks elementu kontrolki nagłówka.  
  
 *lprect —*  
 Wskaźnik na adres [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która otrzymuje informacje prostokąt otaczający.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda implementuje zachowanie komunikatu Win32 [HDM_GETITEMRECT](/windows/desktop/Controls/hdm-getitemrect), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getorderarray"></a>  CHeaderCtrl::GetOrderArray  
 Pobiera kolejność od lewej do prawej strony elementów w formancie nagłówka.  
  
```  
BOOL GetOrderArray(
    LPINT piArray,  
    int iCount);
```  
  
### <a name="parameters"></a>Parametry  
 *piArray*  
 Wskaźnik na adres buforu, który otrzymuje wartości indeksu elementów w formancie nagłówka, w kolejności, w którym są wyświetlane od lewej do prawej.  
  
 *iCount*  
 Liczba elementów do formantu nagłówka. Musi być nieujemna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [HDM_GETORDERARRAY](/windows/desktop/Controls/hdm-getorderarray), zgodnie z opisem w zestawie Windows SDK. Jest ona udostępniana do obsługi porządkowanie elementu nagłówka.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]  
  
##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect  
 Pobiera prostokąt otaczający przycisku przepełnienia bieżącego formantu nagłówka.  
  
```  
BOOL GetOverflowRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out] *lprect —*|Wskaźnik do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która otrzymuje informacje prostokąt otaczający.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli funkcja się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli kontrolki nagłówka zawiera więcej elementów niż można wyświetlić jednocześnie, formant może wyświetlić przycisku przeciążenia, który przewija do elementów, które nie są widoczne. Kontrolki nagłówka musi mieć style HDS_OVERFLOW i HDF_SPLITBUTTON, aby wyświetlić przycisk przepełnienia. Prostokąt otaczający otacza przycisku przeciążenia i istnieje tylko wtedy, gdy jest wyświetlany przycisk przepełnienia. Aby uzyskać więcej informacji, zobacz [style kontrolki nagłówka](/windows/desktop/Controls/header-control-styles).  
  
 Ta metoda wysyła [HDM_GETOVERFLOWRECT](/windows/desktop/Controls/hdm-getoverflowrect) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_headerCtrl`, to znaczy umożliwiają dostęp do bieżącego kontrolki nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje `GetOverflowRect` metody. W starszych sekcji kodu utworzyliśmy kontrolki nagłówka z pięciu kolumnach. Jednak można przeciągnąć separator kolumn, tak, aby ta kolumna nie jest widoczny. Jeśli niektóre kolumny nie są widoczne, kontrolki nagłówka rysuje przycisku przepełnienia. Poniższy kod rysuje prostokąt 3D wokół lokalizacji przycisku przepełnienia.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]  
  
##  <a name="hittest"></a>  CHeaderCtrl::HitTest  
 Określa, który element nagłówka, znajduje się w określonym momencie.  
  
```  
int HitTest(LPHDHITTESTINFO* phdhti);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out w] *phdhti*|Wskaźnik do [HDHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_hd_hittestinfo) struktura, która określa punkt do testowania i otrzymuje wyniki testu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks elementu nagłówka, jeśli istnieje w określonej pozycji; w przeciwnym razie, wartość -1.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [HDM_HITTEST](/windows/desktop/Controls/hdm-hittest) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_headerCtrl`, to znaczy umożliwiają dostęp do bieżącego kontrolki nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje `HitTest` metody. W wcześniejszej sekcji tego przykładu kodu utworzyliśmy kontrolki nagłówka o pięciu kolumnach. Jednak można przeciągnąć separator kolumn, tak, aby ta kolumna nie jest widoczny. W tym przykładzie zgłasza indeks kolumny, jeśli nie jest widoczny, -1, jeśli kolumna nie jest widoczna.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]  
  
##  <a name="insertitem"></a>  CHeaderCtrl::InsertItem  
 Wstawia nowy element do formantu nagłówka pod określonym indeksem.  
  
```  
int InsertItem(
    int nPos,  
    HDITEM* phdi);
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Liczony od zera indeks elementu, który ma zostać wstawiony. Jeśli wartość wynosi zero, element zostanie wstawiony na początku formantu nagłówka. Jeśli wartość jest większa niż wartość maksymalna, element zostanie wstawiony na końcu kontrolki nagłówka.  
  
 *phdi*  
 Wskaźnik do [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) strukturę, która zawiera informacje na temat elementu, który ma zostać wstawiony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks nowy element, jeśli to się powiedzie; w przeciwnym razie - 1.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]  
  
##  <a name="layout"></a>  CHeaderCtrl::Layout  
 Pobiera rozmiar i położenie formantu nagłówka w obrębie danego prostokąta.  
  
```  
BOOL Layout(HDLAYOUT* pHeaderLayout);
```  
  
### <a name="parameters"></a>Parametry  
 *pHeaderLayout*  
 Wskaźnik do [HDLAYOUT](/windows/desktop/api/commctrl/ns-commctrl-_hd_layout) struktury, która zawiera informacje używane do ustawiania rozmiaru i położenia kontrolki nagłówka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana do określania odpowiednich wymiarów dla nowego formantu nagłówka, który jest zajmować danego prostokąta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]  
  
##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex  
 Pobiera wartość indeksu dla elementu na podstawie jego zamówienia w formancie nagłówka.  
  
```  
int OrderToIndex(int nOrder) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nOrder*  
 Kolejność liczony od zera element jest wyświetlany w formancie nagłówka od lewej do prawej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu, w oparciu o ich kolejność w formancie nagłówka. Indeks jest liczona od lewej do prawej, począwszy od 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie makra Win32 [HDM_ORDERTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb775355), zgodnie z opisem w zestawie Windows SDK. Jest ona udostępniana do obsługi porządkowanie elementu nagłówka.  
  
##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin  
 Określa szerokość mapy bitowej na marginesie w formancie nagłówka.  
  
```  
int SetBitmapMargin(int nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *nWidth*  
 Szerokość w pikselach marginesu, który otacza mapy bitowej w ramach istniejącej kontrolki nagłówka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość marginesu mapy bitowej w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [HDM_SETBITMAPMARGIN](/windows/desktop/Controls/hdm-setbitmapmargin), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]  
  
##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout  
 Ustawia limit czasu między czasu zmiany odbywa się w atrybutach filtrów i delegowania [HDN_FILTERCHANGE](/windows/desktop/Controls/hdn-filterchange) powiadomień.  
  
```  
int SetFilterChangeTimeout(DWORD dwTimeOut);
```  
  
### <a name="parameters"></a>Parametry  
 *dwTimeOut*  
 Wartość limitu czasu w milisekundach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks formant filtru jest modyfikowany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [HDM_SETFILTERCHANGETIMEOUT](/windows/desktop/Controls/hdm-setfilterchangetimeout), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]  
  
##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem  
 Ustawia element określonego nagłówka w formancie nagłówka bieżący fokus.  
  
```  
BOOL SetFocusedItem(int iItem);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *towaru*|Liczony od zera indeks elementu nagłówka.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [HDM_SETFOCUSEDITEM](/windows/desktop/Controls/hdm-setfocuseditem) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_headerCtrl`, to znaczy umożliwiają dostęp do bieżącego kontrolki nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje `SetFocusedItem` i `GetFocusedItem` metody. W starszych sekcji kodu utworzyliśmy kontrolki nagłówka z pięciu kolumnach. Jednak można przeciągnąć separator kolumn, tak, aby ta kolumna nie jest widoczny. Poniższy przykład ustawia i następnie potwierdza nagłówek ostatniej kolumny jako element fokus.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider  
 Zmiany, linię podziału między elementy nagłówka w celu wskazania ręcznego przeciągania i upuszczania elementu nagłówka.  
  
```  
int SetHotDivider(CPoint pt);  
int SetHotDivider(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *(czas pacyficzny)*  
 Pozycja wskaźnika. Kontrolki nagłówka wyróżnia odpowiednią linię podziału na podstawie położenia wskaźnika.  
  
 *nIndex*  
 Indeks wyróżnione podziału.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks wyróżnione podziału.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [HDM_SETHOTDIVIDER](/windows/desktop/Controls/hdm-sethotdivider), zgodnie z opisem w zestawie Windows SDK. Jest ona udostępniana do obsługuje nagłówka towaru przeciągania i upuszczania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]  
  
##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList  
 Przypisuje listy obrazów kontrolki nagłówka.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 *pImageList*  
 Wskaźnik do `CImageList` obiekt, który zawiera listy obrazów do przypisania do formantu nagłówka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu wcześniej przypisany do formantu nagłówka.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [HDM_SETIMAGELIST](/windows/desktop/Controls/hdm-setimagelist), zgodnie z opisem w zestawie Windows SDK. `CImageList` Obiekt, do którego punktów zwrócony wskaźnik jest obiektem tymczasowym i zostanie usunięty z następnego przetwarzania czas bezczynności (%).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CHeaderCtrl::GetImageList](#getimagelist).  
  
##  <a name="setitem"></a>  CHeaderCtrl::SetItem  
 Ustawia atrybuty określonego elementu w formancie nagłówka.  
  
```  
BOOL SetItem(
    int nPos,  
    HDITEM* pHeaderItem);
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Liczony od zera indeks elementu do można modyfikować.  
  
 *pHeaderItem*  
 Wskaźnik do [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) strukturę, która zawiera informacje dotyczące nowego elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CHeaderCtrl::GetItem](#getitem).  
  
##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray  
 Ustawia kolejność od lewej do prawej strony elementów w formancie nagłówka.  
  
```  
BOOL SetOrderArray(
    int iCount,  
    LPINT piArray);
```  
  
### <a name="parameters"></a>Parametry  
 *iCount*  
 Liczba elementów do formantu nagłówka.  
  
 *piArray*  
 Wskaźnik na adres buforu, który otrzymuje wartości indeksu elementów w formancie nagłówka, w kolejności, w którym są wyświetlane od lewej do prawej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie makra Win32 [HDM_SETORDERARRAY](/windows/desktop/Controls/hdm-setorderarray), zgodnie z opisem w zestawie Windows SDK. Jest ona udostępniana do obsługi porządkowanie elementu nagłówka.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CHeaderCtrl::GetOrderArray](#getorderarray).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CTabCtrl](../../mfc/reference/ctabctrl-class.md)   
 [Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)   
 [Klasa CImageList](../../mfc/reference/cimagelist-class.md)
