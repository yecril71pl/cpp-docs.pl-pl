---
title: Cheaderctrl — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 582ffffc4461edd41078f1a89844bdc260b2dd40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cheaderctrl-class"></a>Cheaderctrl — klasa
Udostępnia funkcje formantu nagłówka wspólne systemu Windows.  
  
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
|[CHeaderCtrl::ClearFilter](#clearfilter)|Czyści filtr dla kontrolki nagłówka.|  
|[CHeaderCtrl::Create](#create)|Tworzy kontrolkę nagłówka i dołącza go do `CHeaderCtrl` obiektu.|  
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Tworzy przezroczyste wersję obrazu elementu w formancie nagłówka.|  
|[CHeaderCtrl::CreateEx](#createex)|Tworzy kontrolkę nagłówka w określonym stylu rozszerzonej systemu Windows i dołącza go do `CListCtrl` obiektu.|  
|[CHeaderCtrl::DeleteItem](#deleteitem)|Usuwa element z formantem nagłówka.|  
|[CHeaderCtrl::DrawItem](#drawitem)|Pobiera określony element formantu nagłówka.|  
|[CHeaderCtrl::EditFilter](#editfilter)|Uruchamia edycji określony filtr formantu nagłówka.|  
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Pobiera szerokość marginesów mapy bitowej w formancie nagłówka.|  
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Pobiera identyfikator elementu w bieżącym formantu nagłówka, który ma fokus.|  
|[CHeaderCtrl::GetImageList](#getimagelist)|Pobiera dojście listy obrazów, który jest używany do rysowania elementy nagłówka w formancie nagłówka.|  
|[CHeaderCtrl::GetItem](#getitem)|Pobiera informacje o elemencie w formancie nagłówka.|  
|[CHeaderCtrl::GetItemCount](#getitemcount)|Pobiera liczbę elementów w formancie nagłówka.|  
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Pobiera dane prostokąt ograniczający określonego przycisku rozwijanego w formancie nagłówka.|  
|[CHeaderCtrl::GetItemRect](#getitemrect)|Pobiera prostokąt ograniczający dla danego elementu w formancie nagłówka.|  
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Pobiera kolejność elementów w formancie nagłówka od lewej do prawej.|  
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Pobiera prostokąt ograniczający przycisku przeciążenia dla bieżącego formantu nagłówka.|  
|[CHeaderCtrl::HitTest](#hittest)|Określa, który element nagłówka, znajduje się w określonym punkcie.|  
|[CHeaderCtrl::InsertItem](#insertitem)|Wstawia nowy element do formantu nagłówka.|  
|[CHeaderCtrl::Layout](#layout)|Pobiera rozmiar i położenie formantu nagłówka w obrębie danego prostokąta.|  
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Pobiera wartość indeksu dla elementu na podstawie jego kolejności w formancie nagłówka.|  
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Ustawia szerokość marginesów mapy bitowej w formancie nagłówka.|  
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Ustawia limit czasu między czasem zmiany odbywa się w atrybuty filtru i delegowania `HDN_FILTERCHANGE` powiadomień.|  
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Ustawia element określonego nagłówka w formancie nagłówka bieżącego fokus.|  
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Zmiany linię podziału między elementy nagłówka w celu wskazania ręcznego przeciągnij i upuść element nagłówka.|  
|[CHeaderCtrl::SetImageList](#setimagelist)|Przypisuje listy obrazów formantu nagłówka.|  
|[CHeaderCtrl::SetItem](#setitem)|Ustawia atrybuty określonego elementu w formancie nagłówka.|  
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Ustawia kolejność od lewej do prawej elementów w formancie nagłówka.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrolki nagłówka jest oknem, który zazwyczaj znajduje się nad zestawem kolumn tekst lub liczby. Zawiera tytuł dla każdej kolumny, a można podzielić na części. Użytkownik może przeciągać separatorów, które rozdzielić można ustawić szerokość każdej kolumny. Ilustracja formantu nagłówka, zobacz [kontrolki nagłówka](http://msdn.microsoft.com/library/windows/desktop/bb775238).  
  
 Ten formant (i w związku z tym `CHeaderCtrl` klasy) jest dostępne tylko dla programów uruchamianych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Funkcje dodane dla formantów standardowych systemu Windows 95/Internet Explorer w wersji 4.0 jest następująca:  
  
-   Nagłówek elementu niestandardowego porządkowania.  
  
-   Element nagłówka przeciągnij i upuść, do zmiany kolejności elementów nagłówka. Użyj `HDS_DRAGDROP` stylów podczas tworzenia `CHeaderCtrl` obiektu.  
  
-   Tekst kolumny nagłówka stale widoczny podczas zmiany rozmiaru kolumny. Użyj `HDS_FULLDRAG` stylów podczas tworzenia `CHeaderCtrl` obiektu.  
  
-   Nagłówek aktywne śledzenie, co powoduje elementu nagłówka, gdy wskaźnik myszy jest umieszczony nad nim. Użyj `HDS_HOTTRACK` stylów podczas tworzenia `CHeaderCtrl` obiektu.  
  
-   Obsługa listy obrazów. Elementy nagłówka może zawierać obrazy przechowywane w `CImageList` obiekt lub tekst.  
  
 Aby uzyskać więcej informacji o korzystaniu z `CHeaderCtrl`, zobacz [formanty](../../mfc/controls-mfc.md) i [przy użyciu CHeaderCtrl](../../mfc/using-cheaderctrl.md).  
  
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
 `true` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda implementuje zachowanie komunikatu Win32 [HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306) przy użyciu kolumny wartości -1, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]  
  
##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter  
 Czyści filtr dla kontrolki nagłówka.  
  
```  
BOOL ClearFilter(int nColumn);
```  
  
### <a name="parameters"></a>Parametry  
 `nColumn`  
 Wartość kolumny wskazujący, który filtr, aby wyczyścić.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda implementuje zachowanie komunikatu Win32 [HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]  
  
##  <a name="create"></a>  CHeaderCtrl::Create  
 Tworzy kontrolkę nagłówka i dołącza go do `CHeaderCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl nagłówka formantu. Opis elementu style formantu nagłówka, zobacz [stylów formantu nagłówka](http://msdn.microsoft.com/library/windows/desktop/bb775241) w zestawie Windows SDK.  
  
 `rect`  
 Określa rozmiar i położenie formantu nagłówka. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki nagłówka, zwykle `CDialog`. Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu nagłówka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CHeaderCtrl` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać **Utwórz**, która tworzy kontrolkę nagłówka i dołącza go do `CHeaderCtrl` obiektu.  
  
 Oprócz stylów formantu nagłówka, można użyć następujących najczęściej używane style kontrolki do określenia sposobu formantu nagłówka umieszcza i samodzielnie zmienia rozmiar (zobacz [najczęściej używane style formantu](http://msdn.microsoft.com/library/windows/desktop/bb775498) Aby uzyskać więcej informacji):  
  
- `CCS_BOTTOM` Powoduje, że formant umieść się w dolnej części obszaru klienckiego okna nadrzędnego i ustawia szerokość, która jest taka sama jak nadrzędnego szerokość okna.  
  
- `CCS_NODIVIDER` Wyróżnij dwa pikseli zapobiega rysowana w górnej części kontrolki.  
  
- `CCS_NOMOVEY` Powoduje, że formant Zmienianie rozmiaru i przenoszenie się w poziomie, ale nie w pionie, w odpowiedzi na `WM_SIZE` wiadomości. Jeśli `CCS_NORESIZE` styl jest używana, nie ma zastosowania tego stylu. Kontrolki nagłówka domyślnie mają ten styl.  
  
- `CCS_NOPARENTALIGN` Formant uniemożliwia automatyczne przeniesienie do góry lub u dołu okna nadrzędnego. Zamiast tego formant zachowuje jej położenie w obrębie okna nadrzędnego, niezależnie od zmian do rozmiaru okna nadrzędnego. Jeśli `CCS_TOP` lub `CCS_BOTTOM` styl jest również używana, wysokość jest dostosowywana do ustawień domyślnych, ale pozycji i szerokość pozostają niezmienione.  
  
- `CCS_NORESIZE` Zapobiega przy użyciu domyślnej szerokości i wysokości, ustawiając jego początkowy rozmiar lub nowy rozmiar formantu. Zamiast tego formantu używa szerokość i wysokość określony w żądaniu tworzenia lub zmiany rozmiaru.  
  
- `CCS_TOP` Powoduje, że formant umieść się u góry obszaru klienckiego okna nadrzędnego i ustawia szerokość, która jest taka sama jak nadrzędnego szerokość okna.  
  
 Można również zastosować następujące style okna do formantu nagłówka (zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) Aby uzyskać więcej informacji):  
  
- **Ws_child —** tworzy okno podrzędne. Nie można używać z `WS_POPUP` stylu.  
  
- **Ws_visible —** tworzy okna, które jest początkowo widoczne.  
  
- **Ws_disabled —** tworzy okno, które jest początkowo wyłączone.  
  
- **Ws_group —** Określa pierwszą kontrolkę grupy formantów, w których użytkownik może przechodzić z jednego formantu do drugiego za pomocą klawiszy strzałek. Wszystkie formanty zdefiniowane z **ws_group —** styl po pierwszą kontrolkę należą do tej samej grupy. Następnego formantu z **ws_group —** styl kończy się grupie styl i uruchamia następnej grupy (oznacza to, że jedna grupa kończy się którym rozpoczyna się następne).  
  
- **Ws_tabstop —** określa jeden z dowolną liczbę formantów za pomocą których użytkownik może przenieść za pomocą klawisza TAB. Klawisz TAB przenosi użytkownika do następnego formantu określony przez **ws_tabstop —** stylu.  
  
 Jeśli chcesz style rozszerzonej systemu windows za pomocą formantu wywołanie [CreateEx](#createex) zamiast **Utwórz**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]  
  
##  <a name="createex"></a>  CHeaderCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i skojarz ją z `CHeaderCtrl` obiektu.  
  
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
 Styl formantu nagłówka. Opis elementu style formantu nagłówka, zobacz [stylów formantu nagłówka](http://msdn.microsoft.com/library/windows/desktop/bb775241) w zestawie Windows SDK. Zobacz [Utwórz](#create) listę dodatkowych style.  
  
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
  
##  <a name="createdragimage"></a>  CHeaderCtrl::CreateDragImage  
 Tworzy przezroczyste wersję obrazu elementu w formancie nagłówka.  
  
```  
CImageList* CreateDragImage(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks elementu w formancie nagłówka. Obraz przypisany do tego elementu jest podstawą przezroczystego obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu w przypadku powodzenia; w przeciwnym razie **NULL**. Zwracana lista zawiera tylko jeden obraz.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [HDM_CREATEDRAGIMAGE](http://msdn.microsoft.com/library/windows/desktop/bb775308), zgodnie z opisem w zestawie Windows SDK. Znajduje się on do obsługi nagłówka elementu przeciągania i upuszczania.  
  
 `CImageList` Obiektu, do którego punktów zwrócony wskaźnik jest obiektem tymczasowym i zostanie usunięty z następnego przetwarzania czas bezczynności.  
  
##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem  
 Usuwa element z formantem nagłówka.  
  
```  
BOOL DeleteItem(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Określa liczony od zera indeks elementu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]  
  
##  <a name="drawitem"></a>  CHeaderCtrl::DrawItem  
 Wywoływane przez platformę, gdy visual aspekt rysowania przez właściciela nagłówka kontroli zmian.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Wskaźnik do [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) opisujące elementu, który ma zostać narysowany struktury.  
  
### <a name="remarks"></a>Uwagi  
 **ItemAction** członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane.  
  
 Domyślnie ta funkcja członkowska nie działa. Przesłonić tę funkcję elementu członkowskiego, aby zaimplementować rysunku rysowania przez właściciela `CHeaderCtrl` obiektu.  
  
 Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interfejsu (GDI), wybrane kontekst wyświetlania dostarczane w `lpDrawItemStruct` przed ten element członkowski kończy funkcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]  
  
##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter  
 Rozpoczyna edycję określony filtr formantu nagłówka.  
  
```  
BOOL EditFilter(
    int nColumn,  
    BOOL bDiscardChanges);
```  
  
### <a name="parameters"></a>Parametry  
 `nColumn`  
 Kolumny do edycji.  
  
 `bDiscardChanges`  
 Wartość, która określa sposób obsługi użytkownika do edycji zmiany, jeśli użytkownik jest w trakcie edycji filtru podczas [HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312) jest wysyłany komunikat.  
  
 Określ `true` odrzucić zmiany wprowadzone przez użytkownika, lub `false` celu zaakceptowania zmian wprowadzonych przez użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda implementuje zachowanie komunikatu Win32 [HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]  
  
##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin  
 Pobiera szerokość marginesów mapy bitowej w formancie nagłówka.  
  
```  
int GetBitmapMargin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość marginesów mapy bitowej w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [HDM_GETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775314), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]  
  
##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem  
 Pobiera indeks elementu, który ma fokus w bieżącym formantu nagłówka.  
  
```  
int GetFocusedItem() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks elementu nagłówka, który ma fokus.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [HDM_GETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775330) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_headerCtrl`, która jest używane do dostępu bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `SetFocusedItem` i `GetFocusedItem` metody. W starszej sekcji kodu utworzyliśmy kontrolki nagłówka o pięć kolumn. Jednak możesz przeciągnąć separator kolumn tak, aby ta kolumna nie jest widoczne. W poniższym przykładzie ustawia i następnie potwierdza nagłówek ostatniej kolumny jako element fokus.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList  
 Pobiera dojście listy obrazów, który jest używany do rysowania elementy nagłówka w formancie nagłówka.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [HDM_GETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775332), zgodnie z opisem w zestawie Windows SDK. `CImageList` Obiektu, do którego punktów zwrócony wskaźnik jest obiektem tymczasowym i zostanie usunięty z następnego przetwarzania czas bezczynności.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]  
  
##  <a name="getitem"></a>  CHeaderCtrl::GetItem  
 Pobiera informacje o elementach formantu nagłówka.  
  
```  
BOOL GetItem(
    int nPos,  
    HDITEM* pHeaderItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Określa liczony od zera indeks elementu do pobrania.  
  
 `pHeaderItem`  
 Wskaźnik do [HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) struktury, która odbiera nowy element. Ta struktura jest używany z `InsertItem` i `SetItem` funkcji elementów członkowskich. Ustaw flagi **maski** element upewnij się, że wartości w odpowiednie elementy są poprawnie wypełnione po powrocie. Jeśli **maski** element jest ustawiony na wartość zero, wartości w innych elementach struktury nie mają znaczenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]  
  
##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount  
 Pobiera liczbę elementów w formancie nagłówka.  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów formantu nagłówka w przypadku powodzenia; w przeciwnym razie wartość - 1.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CHeaderCtrl::DeleteItem](#deleteitem).  
  
##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect  
 Pobiera element nagłówka w formancie nagłówka bieżący prostokąt ograniczający przycisku rozwijanego.  
  
```  
BOOL GetItemDropDownRect(
    int iItem,   
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `iItem`|Liczony od zera indeks elementu nagłówka o stylu `HDF_SPLITBUTTON`. Aby uzyskać więcej informacji, zobacz `fmt` członkiem [HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) struktury.|  
|[out] `lpRect`|Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury do odbierania informacji prostokąt ograniczający.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli ta funkcja zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [HDM_GETITEMDROPDOWNRECT](http://msdn.microsoft.com/library/windows/desktop/bb775339) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_headerCtrl`, która jest używane do dostępu bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `GetItemDropDownRect` metody. W starszej sekcji kodu utworzyliśmy kontrolki nagłówka o pięć kolumn. Poniższy przykładowy kod rysuje prostokąt 3D wokół lokalizację, w pierwszej kolumnie, które jest zastrzeżone dla przycisku rozwijanego nagłówka.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]  
  
##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect  
 Pobiera prostokąt ograniczający dla danego elementu w formancie nagłówka.  
  
```  
BOOL GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks elementu kontrolki nagłówka.  
  
 `lpRect`  
 Wskaźnik do adresu [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, który odbiera dane prostokąt ograniczający.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda implementuje zachowanie komunikatu Win32 [HDM_GETITEMRECT](http://msdn.microsoft.com/library/windows/desktop/bb775341), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getorderarray"></a>  CHeaderCtrl::GetOrderArray  
 Pobiera kolejność elementów w formancie nagłówka od lewej do prawej.  
  
```  
BOOL GetOrderArray(
    LPINT piArray,  
    int iCount);
```  
  
### <a name="parameters"></a>Parametry  
 `piArray`  
 Wskaźnik do adres buforu, który odbiera wartości indeksu elementów w formancie nagłówka, w kolejności, w jakiej widnieją od lewej do prawej.  
  
 `iCount`  
 Liczba elementów do formantu nagłówka. Musi być nieujemna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [HDM_GETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775343), zgodnie z opisem w zestawie Windows SDK. Znajduje się on do obsługi kolejność elementów nagłówka.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]  
  
##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect  
 Pobiera prostokąt ograniczający bieżącego nagłówka formantu przycisku przeciążenia.  
  
```  
BOOL GetOverflowRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out] `lpRect`|Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, który odbiera dane prostokąt ograniczający.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli ta funkcja zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Formant nagłówka zawiera więcej elementów niż można wyświetlić jednocześnie, formantu wyświetlić przycisku przeciążenia, które jest przewijane elementów, które nie są widoczne. Formant nagłówka musi mieć `HDS_OVERFLOW` i `HDF_SPLITBUTTON` style, aby wyświetlić przycisku przeciążenia. Prostokąt ograniczający umieszcza przycisku przeciążenia i istnieje tylko wtedy, gdy jest wyświetlana w przycisku przeciążenia. Aby uzyskać więcej informacji, zobacz [stylów formantu nagłówka](http://msdn.microsoft.com/library/windows/desktop/bb775241).  
  
 Ta metoda wysyła [HDM_GETOVERFLOWRECT](http://msdn.microsoft.com/library/windows/desktop/bb775345) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_headerCtrl`, która jest używane do dostępu bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `GetOverflowRect` metody. W starszej sekcji kodu utworzyliśmy kontrolki nagłówka o pięć kolumn. Jednak możesz przeciągnąć separator kolumn tak, aby ta kolumna nie jest widoczne. Jeśli niektóre kolumny nie są widoczne, formantu nagłówka rysuje przycisku przeciążenia. Poniższy przykładowy kod rysuje prostokąt 3D wokół lokalizację przycisku przeciążenia.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]  
  
##  <a name="hittest"></a>  CHeaderCtrl::HitTest  
 Określa, który element nagłówka, znajduje się w określonym punkcie.  
  
```  
int HitTest(LPHDHITTESTINFO* phdhti);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[w, out] `phdhti`|Wskaźnik do [HDHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb775245) struktury, która określa punkt do testowania i odbiera wyniki testu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks elementu nagłówka, jeśli istnieje w określonej pozycji; w przeciwnym razie wartość -1.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [HDM_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb775349) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_headerCtrl`, która jest używane do dostępu bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `HitTest` metody. W sekcji wcześniej w tym przykładzie kodu utworzyliśmy kontrolki nagłówka o pięć kolumn. Jednak możesz przeciągnąć separator kolumn tak, aby ta kolumna nie jest widoczne. W tym przykładzie indeks kolumny raportów, jeśli jest on widoczny, -1, jeśli kolumna nie jest widoczna.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]  
  
##  <a name="insertitem"></a>  CHeaderCtrl::InsertItem  
 Wstawia nowy element do formantu nagłówka pod określonym indeksem.  
  
```  
int InsertItem(
    int nPos,  
    HDITEM* phdi);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Liczony od zera indeks elementu do wstawienia. Jeśli wartość wynosi zero, element są wstawiane na początku nagłówka formantu. Jeśli wartość jest większa niż wartość maksymalna, element są wstawiane na końcu formantu nagłówka.  
  
 *phdi*  
 Wskaźnik do [HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) strukturę, która zawiera informacje o elemencie do wstawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks nowego elementu w przypadku powodzenia; w przeciwnym razie wartość - 1.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]  
  
##  <a name="layout"></a>  CHeaderCtrl::Layout  
 Pobiera rozmiar i położenie formantu nagłówka w obrębie danego prostokąta.  
  
```  
BOOL Layout(HDLAYOUT* pHeaderLayout);
```  
  
### <a name="parameters"></a>Parametry  
 *pHeaderLayout*  
 Wskaźnik do [HDLAYOUT](http://msdn.microsoft.com/library/windows/desktop/bb775249) struktury, która zawiera informacje używane do definiowania rozmiar i położenie formantu nagłówka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do określania odpowiednich wymiarów dla nowego nagłówka formantu zajmować danego prostokąt.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]  
  
##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex  
 Pobiera wartość indeksu dla elementu na podstawie jego kolejności w formancie nagłówka.  
  
```  
int OrderToIndex(int nOrder) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nOrder*  
 Liczony od zera kolejność element jest wyświetlany w formancie nagłówka od lewej do prawej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu, na podstawie jego kolejności w formancie nagłówka. Indeks zlicza od lewej do prawej, począwszy od 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie makra Win32 [HDM_ORDERTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb775355), zgodnie z opisem w zestawie Windows SDK. Znajduje się on do obsługi kolejność elementów nagłówka.  
  
##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin  
 Ustawia szerokość marginesów mapy bitowej w formancie nagłówka.  
  
```  
int SetBitmapMargin(int nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Szerokość określone w pikselach margines wokół mapy bitowej w ramach istniejącego formantu nagłówka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość marginesów mapy bitowej w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [HDM_SETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775357), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]  
  
##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout  
 Ustawia limit czasu między czasem zmiany odbywa się w atrybuty filtru i delegowania [HDN_FILTERCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb775277) powiadomień.  
  
```  
int SetFilterChangeTimeout(DWORD dwTimeOut);
```  
  
### <a name="parameters"></a>Parametry  
 *dwTimeOut*  
 Wartość limitu czasu w milisekundach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks formant filtru jest modyfikowany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [HDM_SETFILTERCHANGETIMEOUT](http://msdn.microsoft.com/library/windows/desktop/bb775359), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]  
  
##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem  
 Ustawia element określonego nagłówka w formancie nagłówka bieżącego fokus.  
  
```  
BOOL SetFocusedItem(int iItem);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `iItem`|Liczony od zera indeks elementu nagłówka.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [HDM_SETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775361) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_headerCtrl`, która jest używane do dostępu bieżącego formantu nagłówka. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `SetFocusedItem` i `GetFocusedItem` metody. W starszej sekcji kodu utworzyliśmy kontrolki nagłówka o pięć kolumn. Jednak możesz przeciągnąć separator kolumn tak, aby ta kolumna nie jest widoczne. W poniższym przykładzie ustawia i następnie potwierdza nagłówek ostatniej kolumny jako element fokus.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider  
 Zmiany linię podziału między elementy nagłówka w celu wskazania ręcznego przeciągnij i upuść element nagłówka.  
  
```  
int SetHotDivider(CPoint pt);  
int SetHotDivider(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Pozycja wskaźnika. Formant nagłówka prezentuje odpowiednią linię podziału na podstawie położenia wskaźnika.  
  
 `nIndex`  
 Indeks wyróżnione podziału.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks wyróżnione podziału.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [HDM_SETHOTDIVIDER](http://msdn.microsoft.com/library/windows/desktop/bb775363), zgodnie z opisem w zestawie Windows SDK. Znajduje się on do obsługi nagłówka elementu przeciągania i upuszczania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]  
  
##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList  
 Przypisuje listy obrazów formantu nagłówka.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `pImageList`  
 Wskaźnik do `CImageList` obiekt, który zawiera listy obrazów, który ma być przypisany do formantu nagłówka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiekt wcześniej przypisany do formantu nagłówka.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [HDM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775365), zgodnie z opisem w zestawie Windows SDK. `CImageList` Obiektu, do którego punktów zwrócony wskaźnik jest obiektem tymczasowym i zostanie usunięty z następnego przetwarzania czas bezczynności.  
  
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
 `nPos`  
 Liczony od zera indeks elementu, który ma być modyfikowany w zakresie.  
  
 `pHeaderItem`  
 Wskaźnik do [HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) struktury, który zawiera informacje dotyczące nowego elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CHeaderCtrl::GetItem](#getitem).  
  
##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray  
 Ustawia kolejność od lewej do prawej elementów w formancie nagłówka.  
  
```  
BOOL SetOrderArray(
    int iCount,  
    LPINT piArray);
```  
  
### <a name="parameters"></a>Parametry  
 `iCount`  
 Liczba elementów do formantu nagłówka.  
  
 `piArray`  
 Wskaźnik do adres buforu, który odbiera wartości indeksu elementów w formancie nagłówka, w kolejności, w jakiej widnieją od lewej do prawej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie makra Win32 [HDM_SETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775369), zgodnie z opisem w zestawie Windows SDK. Znajduje się on do obsługi kolejność elementów nagłówka.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CHeaderCtrl::GetOrderArray](#getorderarray).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Ctabctrl — klasa](../../mfc/reference/ctabctrl-class.md)   
 [Clistctrl — klasa](../../mfc/reference/clistctrl-class.md)   
 [Klasa CImageList](../../mfc/reference/cimagelist-class.md)
