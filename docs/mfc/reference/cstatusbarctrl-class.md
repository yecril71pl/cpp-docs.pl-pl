---
title: "Cstatusbarctrl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
dev_langs: C++
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4131e6ab9d73a5e55b478dfff8e68e0eca0dc614
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cstatusbarctrl-class"></a>Cstatusbarctrl — klasa
Udostępnia funkcje formantu paska stanu wspólne systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Konstruuje `CStatusBarCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](#create)|Tworzy kontrolkę paska stanu i dołącza go do `CStatusBarCtrl` obiektu.|  
|[CStatusBarCtrl::CreateEx](#createex)|Tworzy kontrolkę paska stanu w określonym stylu rozszerzonej systemu Windows i dołącza go do `CStatusBarCtrl` obiektu.|  
|[CStatusBarCtrl::DrawItem](#drawitem)|Wywoływane, gdy visual aspekt zmiany formantu paska stanu rysowania przez właściciela.|  
|[CStatusBarCtrl::GetBorders](#getborders)|Pobiera bieżący szerokości obramowania poziomie i w pionie formantu paska stanu.|  
|[CStatusBarCtrl::GetIcon](#geticon)|Pobiera ikonę części (okienko) w bieżącym formantu paska stanu.|  
|[CStatusBarCtrl::GetParts](#getparts)|Pobiera liczbę elementów w formancie paska stanu.|  
|[CStatusBarCtrl::GetRect](#getrect)|Pobiera prostokąt ograniczający części w formancie paska stanu.|  
|[CStatusBarCtrl::GetText](#gettext)|Pobiera tekst z danej części formantu paska stanu.|  
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Pobiera długość w znakach tekstu z danym część formantu paska stanu.|  
|[CStatusBarCtrl::GetTipText](#gettiptext)|Pobiera tekst etykietki narzędzia dla okienka na pasku stanu.|  
|[CStatusBarCtrl::IsSimple](#issimple)|Sprawdza stan formantu okna do określenia, czy jest w trybie proste.|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła na pasku stanu.|  
|[CStatusBarCtrl::SetIcon](#seticon)|Ustawia okienko ikonę na pasku stanu.|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Ustawia minimalną wysokość stanu paska obszar rysowania formantu.|  
|[CStatusBarCtrl::SetParts](#setparts)|Ustawia numer części stan formantu i Współrzędna prawej krawędzi każdej części paska.|  
|[CStatusBarCtrl::SetSimple](#setsimple)|Określa, czy formantu paska stanu wyświetla prosty tekst lub wyświetla wszystkie części kontroli przez poprzednie wywołanie `SetParts`.|  
|[CStatusBarCtrl::SetText](#settext)|Ustawia tekst w danej części formantu paska stanu.|  
|[CStatusBarCtrl::SetTipText](#settiptext)|Ustawia tekst etykietki narzędzia dla okienko na pasku stanu.|  
  
## <a name="remarks"></a>Uwagi  
 "Formantu paska stanu" jest oknem poziomy, zwykle wyświetlane w dolnej części okna nadrzędnego, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie. Formantu paska stanu, można podzielić na części, aby wyświetlić więcej niż jeden typ danych.  
  
 Ten formant (i w związku z tym `CStatusBarCtrl` klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Aby uzyskać więcej informacji na temat używania `CStatusBarCtrl`, zobacz [formanty](../../mfc/controls-mfc.md) i [za pomocą formantu CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="create"></a>CStatusBarCtrl::Create  
 Tworzy kontrolkę paska stanu i dołącza go do `CStatusBarCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl formantu paska stanu. Zastosuj dowolną kombinację pasek stylów formantu na liście stanu [najczęściej używane style formantu](http://msdn.microsoft.com/library/windows/desktop/bb775498) w zestawie Windows SDK. Ten parametr musi zawierać **ws_child —** stylu. Należy uwzględnić również **ws_visible —** stylu.  
  
 `rect`  
 Określa rozmiar i położenie formantu paska stanu. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.  
  
 `pParentWnd`  
 Określa stan paska okno nadrzędne kontrolki, zwykle `CDialog`. Nie może być **wartości NULL.**  
  
 `nID`  
 Określa identyfikator formantu paska stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CStatusBarCtrl` w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać **Utwórz**, która tworzy kontrolkę paska stanu i dołącza go do `CStatusBarCtrl` obiektu.  
  
 Jest to domyślne położenie okna stanu wzdłuż dolnej części okna nadrzędnego, ale można określić `CCS_TOP` styl, który był wyświetlany u góry obszaru klienckiego okna nadrzędnego. Można określić **SBARS_SIZEGRIP** stylu, aby uwzględnić uchwyt zmiany rozmiaru po prawej stronie okna stanu. Łączenie `CCS_TOP` i **SBARS_SIZEGRIP** style nie jest zalecane, ponieważ wynikowa uchwyt zmiany rozmiaru nie działa mimo że rysuje go w oknie Stan systemu.  
  
 Aby utworzyć pasek stanu z rozszerzone Style okna, należy wywołać [CStatusBarCtrl::CreateEx](#createex) zamiast **Utwórz**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CStatusBarCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CStatusBarCtrl` obiektu.  
  
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
 Określa styl formantu paska stanu. Zastosuj dowolną kombinację pasek stylów formantu na liście stanu [najczęściej używane style formantu](http://msdn.microsoft.com/library/windows/desktop/bb775498) w zestawie Windows SDK. Ten parametr musi zawierać **ws_child —** stylu. Należy uwzględnić również **ws_visible —** stylu.  
  
 `rect`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujące rozmiar i położenie okna, które ma zostać utworzony w współrzędne klienta `pParentWnd`.  
  
 `pParentWnd`  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 `nID`  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) dotyczyć rozszerzone style systemu Windows, określone przez wstępu rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="cstatusbarctrl"></a>CStatusBarCtrl::CStatusBarCtrl  
 Konstruuje `CStatusBarCtrl` obiektu.  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="drawitem"></a>CStatusBarCtrl::DrawItem  
 Wywoływane przez platformę, gdy visual aspekt zmiany formantu paska stanu rysowania przez właściciela.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Długie wskaźnik do [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) strukturę, która zawiera informacje o typie rysunku wymagane.  
  
### <a name="remarks"></a>Uwagi  
 **ItemAction** członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane.  
  
 Domyślnie ta funkcja członkowska nie działa. Przesłonić tę funkcję elementu członkowskiego, aby zaimplementować rysunku rysowania przez właściciela `CStatusBarCtrl` obiektu.  
  
 Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interfejsu (GDI), wybrane kontekst wyświetlania dostarczane w `lpDrawItemStruct` przed ten element członkowski kończy funkcji.  
  
##  <a name="getborders"></a>CStatusBarCtrl::GetBorders  
 Pobiera bieżący szerokości formantu paska stanu obramowań poziome i pionowe i odstęp między prostokąty.  
  
```  
BOOL GetBorders(int* pBorders) const;  
  
BOOL GetBorders(
    int& nHorz,  
    int& nVert,  
    int& nSpacing) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pBorders*  
 Adres o trzy elementy tablicy liczby całkowitej. Pierwszy element otrzymuje szerokość obramowania poziomy, drugi odbiera szerokość obramowania pionowy, a trzeci otrzymuje szerokość obramowania między prostokąty.  
  
 *nHorz*  
 Odwołanie do liczba całkowita, która odbiera szerokość obramowania poziomej.  
  
 *Konwertuj*  
 Odwołanie do liczba całkowita, która odbiera szerokość obramowania pionowej.  
  
 *nSpacing*  
 Odwołanie do liczba całkowita, która odbiera szerokość obramowania między prostokąty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Te granice określić odstępy między poza krawędzią formantu i prostokąty w formancie, zawierających tekst.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="geticon"></a>CStatusBarCtrl::GetIcon  
 Pobiera ikonę części (okienko) w bieżącym formantu paska stanu.  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`iPart`|Liczony od zera indeks części, która zawiera ikonę, które mają zostać pobrane. Jeśli ten parametr ma wartość -1, na pasku stanu zakłada się, że tryb prosty paska stanu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do ikony Jeśli metoda pomyślnie; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [SB_GETICON](http://msdn.microsoft.com/library/windows/desktop/bb760744) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
 Formantu paska stanu składa się z szeregu okienek tekstu wyjściowego, które są również znane jako części. Aby uzyskać więcej informacji na temat na pasku stanu, zobacz [implementacja paska stanu w MFC](../../mfc/status-bar-implementation-in-mfc.md) i [Ustawianie trybu obiektu CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_statusBar`, która jest używane do dostępu bieżącego formantu paska stanu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod kopiuje ikony do dwóch okienek bieżącego formantu paska stanu. W starszych sekcji przykładu kodu możemy utworzony formantu paska stanu z trzech okienka i następnie dodać ikony do pierwszego okienka. W tym przykładzie pobiera ikonę z pierwszego okienka i dodaje go do okienka drugiego i trzeciego.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="getparts"></a>CStatusBarCtrl::GetParts  
 Pobiera liczbę elementów w formancie paska stanu.  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nParts`  
 Liczba części, dla których mają zostać pobrane współrzędnych. Jeśli ten parametr jest większa niż liczba elementów w formancie, komunikat pobiera współrzędne tylko istniejącej części.  
  
 *pParts*  
 Adres mających taką samą liczbę elementów jak numer części określone w tablicy całkowitą `nParts`. Każdy element tablicy odbiera Współrzędna prawej krawędzi odpowiedniej części klienta. Jeśli element ma ustawioną wartość - 1, pozycja prawą krawędź w tej części rozszerza do prawej krawędzi paska stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba części w kontroli w przypadku powodzenia lub wartość zero, w przeciwnym razie.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska pobiera również Współrzędna prawej krawędzi danej liczby elementów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="getrect"></a>CStatusBarCtrl::GetRect  
 Pobiera prostokąt ograniczający części w formancie paska stanu.  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Liczony od zera indeks części, których prostokątem ma być pobrana.  
  
 `lpRect`  
 Adres [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która odbiera prostokątem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="gettext"></a>CStatusBarCtrl::GetText  
 Pobiera tekst z danej części formantu paska stanu.  
  
```  
CString GetText(
    int nPane,  
    int* pType = NULL) const;  
  
int GetText(
    LPCTSTR lpszText,  
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Adres buforu, który odbiera tekst. Ten parametr jest ciąg znaków zakończony znakiem null.  
  
 `nPane`  
 Liczony od zera indeks części, z których mają zostać pobrane tekstu.  
  
 `pType`  
 Wskaźnik do wartości całkowitej, która otrzymuje informacje o typie. Jako typ można określić jedną z następujących wartości:  
  
- **0** tekstu jest rysowana obramowaniem być niższe niż płaszczyzna na pasku stanu.  
  
- `SBT_NOBORDERS`Tekst jest rysowane bez granic.  
  
- `SBT_POPOUT`Tekst jest rysowany z obramowanie być wyższa niż rzutu na pasku stanu.  
  
- `SBT_OWNERDRAW`Jeśli tekst ma `SBT_OWNERDRAW` typu, rysunku `pType` odbiera ten komunikat i zwraca wartość 32-bitowych skojarzone z tekstem zamiast typu długość i operację.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość w znakach tekstu lub [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) zawierający dany tekst.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="gettextlength"></a>CStatusBarCtrl::GetTextLength  
 Pobiera długość w znakach tekstu z danym część formantu paska stanu.  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Liczony od zera indeks części, z których mają zostać pobrane tekstu.  
  
 `pType`  
 Wskaźnik do wartości całkowitej, która otrzymuje informacje o typie. Jako typ można określić jedną z następujących wartości:  
  
- **0** tekstu jest rysowana obramowaniem być niższe niż płaszczyzna na pasku stanu.  
  
- `SBT_NOBORDERS`Tekst jest rysowane bez granic.  
  
- `SBT_OWNERDRAW`Tekst jest rysowane przez okno nadrzędne.  
  
- `SBT_POPOUT`Tekst jest rysowany z obramowanie być wyższa niż rzutu na pasku stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość w znakach tekstu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="gettiptext"></a>CStatusBarCtrl::GetTipText  
 Pobiera tekst etykietki narzędzia dla okienka na pasku stanu.  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Liczony od zera indeks w okienku paska stanu do odbierania tekst etykietki narzędzia.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający tekst, który ma być używana w etykietce narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_GETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760751), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="issimple"></a>CStatusBarCtrl::IsSimple  
 Sprawdza stan formantu okna do określenia, czy jest w trybie proste.  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli formant okno stanu jest w trybie prostego; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_ISSIMPLE](http://msdn.microsoft.com/library/windows/desktop/bb760753), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor  
 Ustawia kolor tła na pasku stanu.  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Parametry  
 `cr`  
 **COLORREF** wartość, która określa nowy kolor tła. Określ `CLR_DEFAULT` wartość, aby spowodować, że pasek stanu, aby użyć jego domyślny kolor tła.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość, która reprezentuje poprzedniej domyślny kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760754), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="seticon"></a>CStatusBarCtrl::SetIcon  
 Ustawia okienko ikonę na pasku stanu.  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Liczony od zera indeks okienka, który będzie otrzymywał ikony. Jeśli ten parametr ma wartość -1, na pasku stanu zakłada się, że pasek stanu proste.  
  
 `hIcon`  
 Dojście do ikonę, aby ustawić. Jeśli ta wartość jest **NULL**, ikona jest usuwany z części.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_SETICON](http://msdn.microsoft.com/library/windows/desktop/bb760755), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CStatusBarCtrl::SetBkColor](#setbkcolor).  
  
##  <a name="setminheight"></a>CStatusBarCtrl::SetMinHeight  
 Ustawia minimalną wysokość stanu paska obszar rysowania formantu.  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Minimalna wysokość w pikselach formantu.  
  
### <a name="remarks"></a>Uwagi  
 Minimalna wysokość jest sumą `nMin` i dwukrotnie szerokość w pikselach pionowy obramowania formantu paska stanu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="setparts"></a>CStatusBarCtrl::SetParts  
 Ustawia numer części stan formantu i Współrzędna prawej krawędzi każdej części paska.  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>Parametry  
 `nParts`  
 Liczba części, aby ustawić. Liczba części nie może być większa niż 255.  
  
 *pWidths*  
 Adres mających taką samą liczbę elementów jako części określone w tablicy całkowitą `nParts`. Każdy element tablicy Określa położenie prawej krawędzi odpowiedniej części współrzędne klienta. Jeśli element ma wartość-1, pozycja prawą krawędź w tej części rozszerza prawą krawędzią formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="setsimple"></a>CStatusBarCtrl::SetSimple  
 Określa, czy formantu paska stanu wyświetla prosty tekst lub wyświetla wszystkie części kontroli przez poprzednie wywołanie [SetParts](#setparts).  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bSimple`  
 Typ monitora flagi. Jeśli ten parametr ma `TRUE`, kontrolka Wyświetla prosty tekst; Jeśli jest `FALSE`, zawiera wiele części.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku aplikacji zmiany formantu paska stanu z prostym, prosty lub odwrotnie, system od razu ponownie rysuje formantu.  
  
##  <a name="settext"></a>CStatusBarCtrl::SetText  
 Ustawia tekst w danej części formantu paska stanu.  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Adres zerem ciąg określający tekst do ustawienia. Jeśli `nType` jest `SBT_OWNERDRAW`, `lpszText` reprezentuje 32-bitowy danych.  
  
 `nPane`  
 Liczony od zera indeks części, aby ustawić. Jeśli ta wartość wynosi 255, formantu paska stanu zakłada się, że prostego formantu o tylko jedną część.  
  
 `nType`  
 Typ operacji rysowania. Zobacz [komunikat SB_SETTEXT](http://msdn.microsoft.com/library/bb760758\(vs.85\).aspx) listę możliwych wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Komunikat unieważnia części kontrolki, które uległy zmianie, powodując go, aby wyświetlić nowy tekst, gdy formant obok uzyskuje `WM_PAINT` wiadomości.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="settiptext"></a>CStatusBarCtrl::SetTipText  
 Ustawia tekst etykietki narzędzia dla okienko na pasku stanu.  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Liczony od zera indeks w okienku paska stanu do odbierania tekst etykietki narzędzia.  
  
 *pszTipText*  
 Wskaźnik do ciąg zawierający tekst etykietki narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [SB_SETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760759), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Ctoolbarctrl — klasa](../../mfc/reference/ctoolbarctrl-class.md)
