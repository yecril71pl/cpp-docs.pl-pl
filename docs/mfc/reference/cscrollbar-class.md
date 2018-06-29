---
title: Klasa CScrollBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
dev_langs:
- C++
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86827a2f01e387eb6e7c8b2184567cb204f184e6
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079124"
---
# <a name="cscrollbar-class"></a>Klasa CScrollBar
Udostępnia funkcje systemu Windows formantu paska przewijania.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CScrollBar : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CScrollBar::CScrollBar](#cscrollbar)|Konstruuje `CScrollBar` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CScrollBar::Create](#create)|Tworzy pasek przewijania systemu Windows i dołącza go do `CScrollBar` obiektu.|  
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Włącza lub wyłącza jeden lub oba strzałek przewijania na pasku przewijania.|  
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Pobiera informacje o pasek przy użyciu przewijania `SCROLLBARINFO` struktury.|  
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Pobiera informacje o paska przewijania.|  
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Pobiera limit paska przewijania|  
|[CScrollBar::GetScrollPos](#getscrollpos)|Pobiera bieżącą pozycję pola przewijania.|  
|[CScrollBar::GetScrollRange](#getscrollrange)|Pobiera dla paska przewijania danego bieżącej pozycji minimalną i maksymalną paska przewijania.|  
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Ustawia informacje o paska przewijania.|  
|[CScrollBar::SetScrollPos](#setscrollpos)|Ustawia bieżącą pozycję pola przewijania.|  
|[CScrollBar::SetScrollRange](#setscrollrange)|Ustawia wartości minimalną i maksymalną pozycji na pasku przewijania danego.|  
|[CScrollBar::ShowScrollBar](#showscrollbar)|Pokazuje lub ukrywa pasek przewijania.|  
  
## <a name="remarks"></a>Uwagi  
 Można utworzyć formantu paska przewijania w dwóch krokach. Po pierwsze wywołanie konstruktora `CScrollBar` do skonstruowania `CScrollBar` obiekt, a następnie wywołaj [Utwórz](#create) funkcji członkowskiej Tworzenie formantu paska przewijania systemu Windows i dołączenie go do `CScrollBar` obiektu.  
  
 W przypadku utworzenia `CScrollBar` obiektu w oknie dialogowym (za pośrednictwem zasób okna dialogowego), `CScrollBar` zostanie zniszczony automatycznie, gdy użytkownik zamyka okno dialogowe.  
  
 W przypadku utworzenia `CScrollBar` obiektów w ramach okna, może być również konieczne zniszczenia.  
  
 W przypadku utworzenia `CScrollBar` obiektów na stosie, zostanie zniszczony automatycznie. W przypadku utworzenia `CScrollBar` obiektów na stercie przy użyciu **nowe** funkcji, należy wywołać **usunąć** obiektu zniszczyć ją, gdy użytkownik kończy pasek przewijania systemu Windows.  
  
 Jeśli Przydziel wszystkie pamięci w `CScrollBar` obiektów, Zastąp `CScrollBar` destruktora zlikwidować alokacje.  
  
 Powiązane informacje o używaniu `CScrollBar`, zobacz [formanty](../../mfc/controls-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="create"></a>  CScrollBar::Create  
 Tworzy pasek przewijania systemu Windows i dołącza go do `CScrollBar` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Określa przewijania styl paska. Zastosuj dowolną kombinację [Style paska przewijania](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) na pasku przewijania.  
  
 *Rect*  
 Określa rozmiar paska przewijania i pozycji. Może to być albo `RECT` struktury lub `CRect` obiektu.  
  
 *pParentWnd*  
 Określa przewijania okno nadrzędne paska, zwykle `CDialog` obiektu. Nie może być **NULL**.  
  
 *nID*  
 Identyfikator formantu paska przewijania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CScrollBar` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, który konstruuje `CScrollBar` obiektu; wywoływać `Create`, która tworzy i inicjuje skojarzone pasek przewijania systemu Windows i dołącza go do `CScrollBar` obiektu.  
  
 Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) pasek przewijania:  
  
- **Ws_child —** zawsze  
  
- **Ws_visible —** zwykle  
  
- **Ws_disabled —** rzadko  
  
- **Ws_group —** na grupowanie formantów  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]  
  
##  <a name="cscrollbar"></a>  CScrollBar::CScrollBar  
 Konstruuje `CScrollBar` obiektu.  
  
```  
CScrollBar();
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania obiektu, należy wywołać **Utwórz** funkcji członkowskiej na tworzenie i Inicjowanie paska przewijania systemu Windows.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]  
  
##  <a name="enablescrollbar"></a>  CScrollBar::EnableScrollBar  
 Włącza lub wyłącza jeden lub oba strzałek przewijania na pasku przewijania.  
  
```  
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```  
  
### <a name="parameters"></a>Parametry  
 *nArrowFlags*  
 Określa, czy włączać lub wyłączać strzałki przewijania i strzałek, które są włączone lub wyłączone. Ten parametr może mieć jedną z następujących wartości:  
  
- **ESB_ENABLE_BOTH** umożliwia zarówno strzałek przewijania na pasku przewijania.  
  
- **ESB_DISABLE_LTUP** wyłącza strzałkę poziomego paska przewijania w lewo lub strzałki w górę na pionowy pasek przewijania.  
  
- **ESB_DISABLE_RTDN** wyłącza strzałki w prawo działania poziomego paska przewijania lub strzałkę w dół pionowy pasek przewijania.  
  
- **ESB_DISABLE_BOTH** wyłącza zarówno strzałek przewijania na pasku przewijania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli strzałki są włączone lub wyłączone określone; w przeciwnym razie wartość 0, co oznacza, że strzałki są już żądany stan lub wystąpił błąd.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="getscrollbarinfo"></a>  CScrollBar::GetScrollBarInfo  
 Pobiera informacje o który **SCROLLBARINFO** struktury przechowuje o pasek przewijania.  
  
```  
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pScrollInfo*  
 Wskaźnik do [SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787535) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje [SBM_SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787545) komunikatu, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getscrollinfo"></a>  CScrollBar::GetScrollInfo  
 Pobiera informacje o który `SCROLLINFO` struktury przechowuje o pasek przewijania.  
  
```  
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    UINT nMask = SIF_ALL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpScrollInfo*  
 Wskaźnik do [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktury. Zobacz Windows SDK, aby uzyskać więcej informacji na temat tej struktury.  
  
 *nMask*  
 Określa parametry paska przewijania do pobrania. Typowy sposób, SIF_ALL, określa kombinację SIF_PAGE, SIF_POS SIF_TRACKPOS i SIF_RANGE. Zobacz `SCROLLINFO` uzyskać więcej informacji o wartości nMask.  
  
### <a name="return-value"></a>Wartość zwracana  
 Czy wiadomości pobierane wartości, jest zwracany **TRUE**. W przeciwnym razie jest **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 `GetScrollInfo` Umożliwia aplikacjom używać pozycji przewijania 32-bitowych.  
  
 [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktura zawiera informacje o paska, w tym minimalne i maksymalne przewijanie pozycji, rozmiar strony i pozycja pola przewijania (przenośny) przewijania. Zobacz `SCROLLINFO` struktury tematu w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat zmiany ustawień domyślnych struktury.  
  
 Programy obsługi, które wskazują położenie paska przewijania, wiadomości MFC Windows [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), podaj tylko 16 bitów danych pozycji. `GetScrollInfo` i `SetScrollInfo` Podaj 32 bity pasek danych położenie przewijania. W związku z tym, aplikacja może wywołać `GetScrollInfo` podczas przetwarzania albo `CWnd::OnHScroll` lub `CWnd::OnVScroll` do uzyskiwania danych pozycja paska przewijania 32-bitowych.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrolllimit"></a>  CScrollBar::GetScrollLimit  
 Pobiera maksymalną przewijanie pozycja paska przewijania.  
  
```  
int GetScrollLimit();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa maksymalną pozycja paska przewijania w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollpos"></a>  CScrollBar::GetScrollPos  
 Pobiera bieżącą pozycję pola przewijania.  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa bieżącą pozycję pola przewijania w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Bieżące położenie jest względna wartość, która jest zależna od bieżącego przewijanego zakresu. Na przykład jeśli pole przewijania jest w trakcie paska przewijania zakres wynosi od 100 do 200, bieżące położenie jest 150.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollrange"></a>  CScrollBar::GetScrollRange  
 Kopiuje bieżącego położenia minimalną i maksymalną pasek przewijania dla paska przewijania danego do lokalizacji określonej przez *lpMinPos* i *lpMaxPos*.  
  
```  
void GetScrollRange(
    LPINT lpMinPos,  
    LPINT lpMaxPos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpMinPos*  
 Wskazuje zmiennej liczba całkowita, która będzie odbierać minimalna pozycji.  
  
 *lpMaxPos*  
 Wskazuje zmiennej liczba całkowita, która będzie odbierać maksymalną pozycji.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny zakres dla formantu paska przewijania jest pusty (obie wartości to 0).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="setscrollinfo"></a>  CScrollBar::SetScrollInfo  
 Ustawia informacje, które `SCROLLINFO` struktury przechowuje o pasek przewijania.  
  
```  
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lpScrollInfo*  
 Wskaźnik do [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktury.  
  
 *bRedraw*  
 Określa, czy pasek przewijania powinien być narysowany ponownie w celu odzwierciedlenia nowych informacji. Jeśli *bRedraw* jest **TRUE**, zostanie narysowany ponownie na pasku przewijania. Jeśli jest **FALSE**, nie jest rysowane. Pasek przewijania jest odświeżana domyślnie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli pomyślnie, zwracany jest **TRUE**. W przeciwnym razie jest **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Należy podać wartości wymagane przez `SCROLLINFO` struktury parametrów, takich jak wartości flag.  
  
 `SCROLLINFO` Struktura zawiera informacje o paska, w tym minimalne i maksymalne przewijanie pozycji, rozmiar strony i pozycja pola przewijania (przenośny) przewijania. Zobacz [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktury tematu w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat zmiany ustawień domyślnych struktury.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]  
  
##  <a name="setscrollpos"></a>  CScrollBar::SetScrollPos  
 Ustawia określoną przez bieżącą pozycję pola przewijania *nPos* i, jeśli jest określony, ponownie rysuje paska przewijania w celu uwzględnienia nowej pozycji.  
  
```  
int SetScrollPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *nPos*  
 Określa nową pozycję pola przewijania. Musi ona należeć do zakresu przewijania.  
  
 *bRedraw*  
 Określa, czy pasek przewijania powinien być narysowany ponownie, aby uwzględnić nowe położenie. Jeśli *bRedraw* jest **TRUE**, zostanie narysowany ponownie na pasku przewijania. Jeśli jest **FALSE**, nie jest rysowane. Pasek przewijania jest odświeżana domyślnie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa poprzedniej pozycji suwaka w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ustaw *bRedraw* do **FALSE** po każdej zmianie narysowania paska przewijania przez kolejne wywołanie do innej funkcji uniknąć narysowany ponownie dwa razy w ciągu przez krótki czas pasek przewijania.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="setscrollrange"></a>  CScrollBar::SetScrollRange  
 Ustawia wartości minimalną i maksymalną pozycji na pasku przewijania danego.  
  
```  
void SetScrollRange(
    int nMinPos,  
    int nMaxPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *nMinPos*  
 Określa minimalny położenie przewijania.  
  
 *nMaxPos*  
 Określa maksymalny położenie przewijania.  
  
 *bRedraw*  
 Określa, czy pasek przewijania powinien być narysowany ponownie, aby odzwierciedlić zmianę. Jeśli *bRedraw* jest **TRUE**, rysowane na pasku przewijania; Jeśli **FALSE**, nie jest rysowane. Zostanie narysowany ponownie domyślnie.  
  
### <a name="remarks"></a>Uwagi  
 Ustaw *nMinPos* i *nMaxPos* na 0, aby ukryć paski przewijania standardowa.  
  
 Nie wywołuj tej funkcji, aby ukryć pasek przewijania podczas przetwarzania komunikatu powiadomienia paska przewijania.  
  
 Jeśli wywołanie `SetScrollRange` od razu następuje po wywołaniu `SetScrollPos` funkcji członkowskiej, ustaw *bRedraw* w `SetScrollPos` na 0, aby zapobiec są rysowane dwukrotnie pasek przewijania.  
  
 Różnica między wartościami określony przez *nMinPos* i *nMaxPos* nie może być większa niż 32 767 znaków. Domyślny zakres dla formantu paska przewijania jest pusty (zarówno *nMinPos* i *nMaxPos* 0).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]  
  
##  <a name="showscrollbar"></a>  CScrollBar::ShowScrollBar  
 Pokazuje lub ukrywa pasek przewijania.  
  
```  
void ShowScrollBar(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bShow*  
 Określa, czy pasek przewijania jest pokazywany lub ukryty. Jeśli ten parametr ma **TRUE**, jest wyświetlana na pasku przewijania; w przeciwnym razie jest ukryty.  
  
### <a name="remarks"></a>Uwagi  
 Aplikacja nie powinny wywoływać tej funkcji, aby ukryć pasek przewijania podczas przetwarzania komunikatu powiadomienia paska przewijania.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CScrollBar::Create](#create).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Klasa CButton](../../mfc/reference/cbutton-class.md)   
 [Ccombobox — klasa](../../mfc/reference/ccombobox-class.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)   
 [Clistbox — klasa](../../mfc/reference/clistbox-class.md)   
 [Klasa CStatic](../../mfc/reference/cstatic-class.md)   
 [Klasa CDialog](../../mfc/reference/cdialog-class.md)
