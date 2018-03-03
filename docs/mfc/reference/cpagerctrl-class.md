---
title: Klasa CPagerCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
dev_langs:
- C++
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c79fa877023c7a01c4814f61d75a54cb0dd64b51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cpagerctrl-class"></a>Klasa CPagerCtrl
`CPagerCtrl` Klasy opakowuje formantu modułu stronicowania systemu Windows, które mogą być przewijane w widoku zawartego okna, który nie mieści się okna nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPagerCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Konstruuje `CPagerCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPagerCtrl::Create](#create)|Tworzy kontrolkę pagera przy użyciu określonego stylów i dołącza go do bieżącej `CPagerCtrl` obiektu.|  
|[CPagerCtrl::CreateEx](#createex)|Tworzy kontrolkę pagera z określonym rozszerzone style i dołącza go do bieżącej `CPagerCtrl` obiektu.|  
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Włącza lub wyłącza przekazywanie [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) wiadomości do okna, które znajduje się w bieżącej kontrolki modułu stronicowania.|  
|[CPagerCtrl::GetBkColor](#getbkcolor)|Pobiera kolor tła bieżącego formantu modułu stronicowania.|  
|[CPagerCtrl::GetBorder](#getborder)|Pobiera rozmiar obramowania bieżącego formantu modułu stronicowania.|  
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Pobiera rozmiar przycisku bieżącego formantu modułu stronicowania.|  
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Pobiera stan określonego przycisku w bieżącym kontroli modułu stronicowania.|  
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Pobiera [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interfejs dla bieżącego formantu modułu stronicowania.|  
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Pobiera położenie przewijania bieżącego formantu modułu stronicowania.|  
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `pressed` stanu.|  
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `grayed` stanu.|  
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `hot` stanu.|  
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `invisible` stanu.|  
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Wskazuje, czy określony przycisk bieżącego formantu pagera jest w `normal` stanu.|  
|[CPagerCtrl::RecalcSize](#recalcsize)|Powoduje, że bieżący formant pagera ponownego obliczenia rozmiaru okna zawartych w niej.|  
|[CPagerCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła bieżącego formantu modułu stronicowania.|  
|[CPagerCtrl::SetBorder](#setborder)|Określa rozmiar obramowania bieżącego formantu modułu stronicowania.|  
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Ustawia rozmiar przycisku bieżącego formantu modułu stronicowania.|  
|[CPagerCtrl::SetChild](#setchild)|Ustawia zawartego okna dla bieżącego formantu modułu stronicowania.|  
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Ustawia położenie przewijania bieżącego formantu modułu stronicowania.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrolkę pagera jest oknem, które zawiera inne okno jest liniowy i większa niż okna nadrzędnego, która umożliwia przewiń zawartego okna w widoku. Formant pagera są wyświetlane dwa przyciski przewijania, które automatycznie znikają w przypadku zawartego okna jest przewijane jego zakresie najdalszych i pojawić się ponownie, w przeciwnym razie wartość. Można utworzyć kontrolkę pagera, która jest przewijane w poziomie lub pionie.  
  
 Na przykład jeśli aplikacja ma narzędzi, który nie jest dostatecznie szerokie, aby wyświetlić wszystkie elementy, pasek narzędzi można przypisać do kontrolkę pagera, a użytkownicy będą mogli do przewijania na pasku narzędzi do lewej lub prawej strony, aby uzyskać dostęp do wszystkich elementów. Microsoft Internet Explorer w wersji 4.0 (wersja commctrl.dll 4.71) wprowadzono kontrolki modułu stronicowania.  
  
 `CPagerCtrl` Jest pochodną klasy [CWnd](../../mfc/reference/cwnd-class.md) klasy. Więcej informacji oraz ilustrację kontrolkę pagera, zobacz [formantami modułu stronicowania](http://msdn.microsoft.com/library/windows/desktop/bb760855).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="cpagerctrl"></a>CPagerCtrl::CPagerCtrl  
 Konstruuje `CPagerCtrl` obiektu.  
  
```  
CPagerCtrl();
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CPagerCtrl::Create](#create) lub [CPagerCtrl::CreateEx](#createex) metody Utwórz kontrolkę pagera i dołączenie go do `CPagerCtrl` obiektu.  
  
##  <a name="create"></a>CPagerCtrl::Create  
 Tworzy kontrolkę pagera przy użyciu określonego stylów i dołącza go do bieżącej `CPagerCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`dwStyle`|Bitowe połączenie (lub) [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859) ma zostać zastosowany do formantu.|  
|[in]`rect`|Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która zawiera położenie i rozmiar formantu we współrzędnych klienta.|  
|[in]`pParentWnd`|Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki. Ten parametr nie może być `NULL`.|  
|[in]`nID`|Identyfikator formantu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Aby utworzyć kontrolkę pagera, należy zadeklarować `CPagerCtrl` zmiennej, następnie wywołaj [CPagerCtrl::Create](#create) lub [CPagerCtrl::CreateEx](#createex) metody dla tej zmiennej.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy kontrolkę pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) do kojarzenia kontrolkę przycisku bardzo dużo za pomocą formantu modułu stronicowania. W przykładzie następnie użyto [CPagerCtrl::SetButtonSize](#setbuttonsize) metodę, aby ustawić wysokość formantu pagera do 20 pikseli i [CPagerCtrl::SetBorder](#setborder) metodę, aby ustawić grubość obramowania 1 piksela.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CPagerCtrl::CreateEx  
 Tworzy kontrolkę pagera z określonym rozszerzone style i dołącza go do bieżącej `CPagerCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,   
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`dwExStyle`|Bitowe połączenie rozszerzone style, które mają być zastosowane do formantu. Aby uzyskać więcej informacji, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkcji.|  
|[in]`dwStyle`|Bitowe połączenie (lub) [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859) ma zostać zastosowany do formantu.|  
|[in]`rect`|Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która zawiera położenie i rozmiar formantu we współrzędnych klienta.|  
|[in]`pParentWnd`|Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki. Ten parametr nie może być `NULL`.|  
|[in]`nID`|Identyfikator formantu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Aby utworzyć kontrolkę pagera, należy zadeklarować `CPagerCtrl` zmiennej, następnie wywołaj [CPagerCtrl::Create](#create) lub [CPagerCtrl::CreateEx](#createex) metody dla tej zmiennej.  
  
##  <a name="forwardmouse"></a>CPagerCtrl::ForwardMouse  
 Włącza lub wyłącza przekazywanie [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) wiadomości do okna, które znajduje się w bieżącej kontrolki modułu stronicowania.  
  
```  
void ForwardMouse(BOOL bForward);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`bForward`|`true`do przesyłania dalej komunikatów myszy lub `false` nie przekazywanie komunikatów myszy.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_FORWARDMOUSE](http://msdn.microsoft.com/library/windows/desktop/bb760867) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getborder"></a>CPagerCtrl::GetBorder  
 Pobiera rozmiar obramowania bieżącego formantu modułu stronicowania.  
  
```  
int GetBorder() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący rozmiar obramowania (w pikselach).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_GETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760869) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [CPagerCtrl::GetBorder](#getborder) metoda pobierania grubość obramowania formantu modułu stronicowania.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]  
  
##  <a name="getbkcolor"></a>CPagerCtrl::GetBkColor  
 Pobiera kolor tła bieżącego formantu modułu stronicowania.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości, która zawiera bieżący kolor tła formantu modułu stronicowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760868) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [CPagerCtrl::SetBkColor](#setbkcolor) metodę, aby ustawić kolor tła formantu pagera czerwony i [CPagerCtrl::GetBkColor](#getbkcolor) metody, aby upewnić się, że zmiana została wprowadzona.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize  
 Pobiera rozmiar przycisku bieżącego formantu modułu stronicowania.  
  
```  
int GetButtonSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący rozmiar przycisku (w pikselach).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_GETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760870) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
 Jeśli kontrolkę pagera `PGS_HORZ` styl i rozmiar przycisku określa szerokość przycisków modułu stronicowania, a jeśli kontrolkę pagera `PGS_VERT` styl i rozmiar przycisku określa wysokość przycisków modułu stronicowania. Aby uzyskać więcej informacji, zobacz [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859).  
  
##  <a name="getbuttonstate"></a>CPagerCtrl::GetButtonState  
 Pobiera stan przycisku przewijania określonego w bieżącym kontroli modułu stronicowania.  
  
```  
DWORD GetButtonState(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iButton`|Wskazuje, dla której są pobierane stan przycisku. W przypadku stylu formantu pagera `PGS_HORZ`, określ `PGB_TOPORLEFT` dla przycisku po lewej stronie i `PGB_BOTTOMORRIGHT` dla prawego przycisku. W przypadku stylu formantu pagera `PGS_VERT`, określ `PGB_TOPORLEFT` do góry i `PGB_BOTTOMORRIGHT` dla przycisku dolnej. Aby uzyskać więcej informacji, zobacz [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan określonego przez naciśnięcie przycisku `iButton` parametru. Stan jest `PGF_INVISIBLE`, `PGF_NORMAL`, `PGF_GRAYED`, `PGF_DEPRESSED`, lub `PGF_HOT`. Aby uzyskać więcej informacji, zobacz sekcję zwrócić wartość [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getdroptarget"></a>CPagerCtrl::GetDropTarget  
 Pobiera [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interfejs dla bieżącego formantu modułu stronicowania.  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `IDropTarget` interfejs dla bieżącego formantu modułu stronicowania.  
  
### <a name="remarks"></a>Uwagi  
 `IDropTarget`jest jednym z interfejsów zaimplementować w celu obsługi operacji przeciągania i upuszczania w aplikacji.  
  
 Ta metoda wysyła [PGM_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb760872) komunikat, który jest opisany w zestawie SDK systemu Windows. Wywołujący ta metoda jest odpowiedzialna za wywoływania `Release` członkiem [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interfejs, gdy interfejs nie jest już potrzebne.  
  
##  <a name="getscrollpos"></a>CPagerCtrl::GetScrollPos  
 Pobiera położenie przewijania bieżącego formantu modułu stronicowania.  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżące położenie przewijania (w pikselach).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_GETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760874) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [CPagerCtrl::GetScrollPos](#getscrollpos) metoda pobierania bieżącej pozycji przewijania formantu modułu stronicowania. Jeśli formant pagera nie jest już przewijane na wartość 0, po lewej stronie pozycji w przykładzie użyto [CPagerCtrl::SetScrollPos](#setscrollpos) metodę, aby ustawić na zero jego położenie przewijania.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]  
  
##  <a name="isbuttondepressed"></a>CPagerCtrl::IsButtonDepressed  
 Wskazuje, czy przycisk przewijania określonego bieżącego formantu pagera jest w stanie naciśniętego.  
  
```  
BOOL IsButtonDepressed(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iButton`|Wskazuje, dla której są pobierane stan przycisku. W przypadku stylu formantu pagera `PGS_HORZ`, określ `PGB_TOPORLEFT` dla przycisku po lewej stronie i `PGB_BOTTOMORRIGHT` dla prawego przycisku. W przypadku stylu formantu pagera `PGS_VERT`, określ `PGB_TOPORLEFT` do góry i `PGB_BOTTOMORRIGHT` dla przycisku dolnej. Aby uzyskać więcej informacji, zobacz [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`w przypadku określonego przycisku w stan naciśnięcia; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) komunikat, który jest opisany w zestawie SDK systemu Windows. Następnie sprawdza, czy jest w stanie, który jest zwracany `PGF_DEPRESSED`. Aby uzyskać więcej informacji, zobacz sekcję zwrócić wartość [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) wiadomości.  
  
##  <a name="isbuttongrayed"></a>CPagerCtrl::IsButtonGrayed  
 Wskazuje, czy przycisk przewijania określonego bieżącego formantu pagera jest w stanie wygaszone.  
  
```  
BOOL IsButtonGrayed(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iButton`|Wskazuje, dla której są pobierane stan przycisku. W przypadku stylu formantu pagera `PGS_HORZ`, określ `PGB_TOPORLEFT` dla przycisku po lewej stronie i `PGB_BOTTOMORRIGHT` dla prawego przycisku. W przypadku stylu formantu pagera `PGS_VERT`, określ `PGB_TOPORLEFT` do góry i `PGB_BOTTOMORRIGHT` dla przycisku dolnej. Aby uzyskać więcej informacji, zobacz [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli określonego przycisku jest w stanie wygaszone; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) komunikat, który jest opisany w zestawie SDK systemu Windows. Następnie sprawdza, czy jest w stanie, który jest zwracany `PGF_GRAYED`. Aby uzyskać więcej informacji, zobacz sekcję zwrócić wartość [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) wiadomości.  
  
##  <a name="isbuttonhot"></a>CPagerCtrl::IsButtonHot  
 Wskazuje, czy przycisk przewijania określonego bieżącego formantu pagera jest w stanie dynamicznej.  
  
```  
BOOL IsButtonHot(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iButton`|Wskazuje, dla której są pobierane stan przycisku. W przypadku stylu formantu pagera `PGS_HORZ`, określ `PGB_TOPORLEFT` dla przycisku po lewej stronie i `PGB_BOTTOMORRIGHT` dla prawego przycisku. W przypadku stylu formantu pagera `PGS_VERT`, określ `PGB_TOPORLEFT` do góry i `PGB_BOTTOMORRIGHT` dla przycisku dolnej. Aby uzyskać więcej informacji, zobacz [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli określonego przycisku jest w stanie gorących; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) komunikat, który jest opisany w zestawie SDK systemu Windows. Następnie sprawdza, czy jest w stanie, który jest zwracany `PGF_HOT`. Aby uzyskać więcej informacji, zobacz sekcję zwrócić wartość [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) wiadomości.  
  
##  <a name="isbuttoninvisible"></a>CPagerCtrl::IsButtonInvisible  
 Wskazuje, czy przycisk przewijania określonego bieżącego formantu pagera jest w stanie niewidoczne.  
  
```  
BOOL IsButtonInvisible(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iButton`|Wskazuje, dla której są pobierane stan przycisku. W przypadku stylu formantu pagera `PGS_HORZ`, określ `PGB_TOPORLEFT` dla przycisku po lewej stronie i `PGB_BOTTOMORRIGHT` dla prawego przycisku. W przypadku stylu formantu pagera `PGS_VERT`, określ `PGB_TOPORLEFT` do góry i `PGB_BOTTOMORRIGHT` dla przycisku dolnej. Aby uzyskać więcej informacji, zobacz [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli określonego przycisku jest w stanie niewidoczne; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Windows sprawia, że przycisku przewijania w określonym kierunku niewidoczne podczas zawartego okna jest przewijane w jego zakresie najdalszych, ponieważ kliknięcie przycisku Dalej nie można przełączyć więcej zawartego okna w widoku.  
  
 Ta metoda wysyła [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) komunikat, który jest opisany w zestawie SDK systemu Windows. Następnie sprawdza, czy jest w stanie, który jest zwracany `PGF_INVISIBLE`. Aby uzyskać więcej informacji, zobacz sekcję zwrócić wartość [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) wiadomości.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) metodę, aby określić, czy formant pagera lewej formantu i przyciski przewijania w prawo są widoczne.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]  
  
##  <a name="isbuttonnormal"></a>CPagerCtrl::IsButtonNormal  
 Wskazuje, czy przycisk przewijania określonego bieżącego formantu pagera jest w normalnym stanie.  
  
```  
BOOL IsButtonNormal(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iButton`|Wskazuje, dla której są pobierane stan przycisku. W przypadku stylu formantu pagera `PGS_HORZ`, określ `PGB_TOPORLEFT` dla przycisku po lewej stronie i `PGB_BOTTOMORRIGHT` dla prawego przycisku. W przypadku stylu formantu pagera `PGS_VERT`, określ `PGB_TOPORLEFT` do góry i `PGB_BOTTOMORRIGHT` dla przycisku dolnej. Aby uzyskać więcej informacji, zobacz [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`w przypadku określonego przycisku w normalnym stanie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) komunikat, który jest opisany w zestawie SDK systemu Windows. Następnie sprawdza, czy jest w stanie, który jest zwracany `PGF_NORMAL`. Aby uzyskać więcej informacji, zobacz sekcję zwrócić wartość [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) wiadomości.  
  
##  <a name="recalcsize"></a>CPagerCtrl::RecalcSize  
 Powoduje, że bieżący formant pagera ponownego obliczenia rozmiaru okna zawartych w niej.  
  
```  
void RecalcSize();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_RECALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760876) komunikat, który jest opisany w zestawie SDK systemu Windows. W rezultacie wysyła kontroli pagera [PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864) powiadomienie, aby uzyskać przewijalne wymiary zawartego okna.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [CPagerCtrl::RecalcSize](#recalcsize) metody, aby zażądać bieżący formant pagera ponownego obliczenia rozmiaru.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [komunikatu odbicia](../../mfc/tn062-message-reflection-for-windows-controls.md) Aby włączyć kontrolkę pagera ponownego obliczenia rozmiaru zwalniając formantu nadrzędnego okna dialogowego, aby wykonać obliczenie. Przykład pochodzi `MyPagerCtrl` klasę z [klasy CPagerCtrl](../../mfc/reference/cpagerctrl-class.md), używa mapy komunikatów w celu skojarzenia [PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864) powiadomienie z `OnCalcsize` obsługi powiadomień. W tym przykładzie obsługi powiadomień Ustawia szerokość i wysokość formantu pagera stałej wartości.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]  
  
##  <a name="setbkcolor"></a>CPagerCtrl::SetBkColor  
 Ustawia kolor tła bieżącego formantu modułu stronicowania.  
  
```  
COLORREF SetBkColor(COLORREF clrBk);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`clrBk`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości, która zawiera na nowy kolor tła formantu modułu stronicowania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości, która zawiera poprzednie kolor tła formantu modułu stronicowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760878) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [CPagerCtrl::SetBkColor](#setbkcolor) metodę, aby ustawić kolor tła formantu pagera czerwony i [CPagerCtrl::GetBkColor](#getbkcolor) metody, aby upewnić się, że zmiana została wprowadzona.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="setborder"></a>CPagerCtrl::SetBorder  
 Określa rozmiar obramowania bieżącego formantu modułu stronicowania.  
  
```  
int SetBorder(int iBorder);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iBorder`|Nowy rozmiar obramowania (w pikselach). Jeśli `iBorder` parametru jest ujemna, rozmiar obramowania jest ustawione na zero.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedni rozmiar obramowania (w pikselach).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_SETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760880) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy kontrolkę pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) do kojarzenia kontrolkę przycisku bardzo dużo za pomocą formantu modułu stronicowania. W przykładzie następnie użyto [CPagerCtrl::SetButtonSize](#setbuttonsize) metodę, aby ustawić wysokość formantu pagera do 20 pikseli i [CPagerCtrl::SetBorder](#setborder) metodę, aby ustawić grubość obramowania 1 piksela.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize  
 Ustawia rozmiar przycisku bieżącego formantu modułu stronicowania.  
  
```  
int SetButtonSize(int iButtonSize);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iButtonSize`|Nowy rozmiar przycisku (w pikselach).|  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar przycisku poprzedniego (w pikselach).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_SETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760886) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
 Jeśli kontrolkę pagera `PGS_HORZ` styl i rozmiar przycisku określa szerokość przycisków modułu stronicowania, a jeśli kontrolkę pagera `PGS_VERT` styl i rozmiar przycisku określa wysokość przycisków modułu stronicowania. Przycisk domyślny rozmiar to trzy czwarte szerokość paska przewijania, a rozmiar minimalny przycisku to 12 pikseli. Aby uzyskać więcej informacji, zobacz [stylów formantu pagera](http://msdn.microsoft.com/library/windows/desktop/bb760859).  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy kontrolkę pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) do kojarzenia kontrolkę przycisku bardzo dużo za pomocą formantu modułu stronicowania. W przykładzie następnie użyto [CPagerCtrl::SetButtonSize](#setbuttonsize) metodę, aby ustawić wysokość formantu pagera do 20 pikseli i [CPagerCtrl::SetBorder](#setborder) metodę, aby ustawić grubość obramowania 1 piksela.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setchild"></a>CPagerCtrl::SetChild  
 Ustawia zawartego okna dla bieżącego formantu modułu stronicowania.  
  
```  
void SetChild(HWND hwndChild);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`hwndChild`|Dojście do okna, które mają być zawarte.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_SETCHILD](http://msdn.microsoft.com/library/windows/desktop/bb760884) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
 Ta metoda nie zmienić element nadrzędny zawartego okna; przypisuje tylko uchwyt okna do formantu pagera przewijania. W większości przypadków zawartego okna będzie okno podrzędne formantu modułu stronicowania.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy kontrolkę pagera, a następnie używa [CPagerCtrl::SetChild](#setchild) do kojarzenia kontrolkę przycisku bardzo dużo za pomocą formantu modułu stronicowania. W przykładzie następnie użyto [CPagerCtrl::SetButtonSize](#setbuttonsize) metodę, aby ustawić wysokość formantu pagera do 20 pikseli i [CPagerCtrl::SetBorder](#setborder) metodę, aby ustawić grubość obramowania 1 piksela.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setscrollpos"></a>CPagerCtrl::SetScrollPos  
 Ustawia położenie przewijania bieżącego formantu modułu stronicowania.  
  
```  
void SetScrollPos(int iPos);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iPos`|Nowa pozycja przewijania (w pikselach).|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [PGM_SETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760886) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Formantami modułu stronicowania](http://msdn.microsoft.com/library/windows/desktop/bb760855)



