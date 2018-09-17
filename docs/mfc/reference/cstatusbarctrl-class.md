---
title: Klasa CStatusBarCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94d56a6defbc47a133e3f583daab188921622d84
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711811"
---
# <a name="cstatusbarctrl-class"></a>Klasa CStatusBarCtrl
Oferuje funkcje formantu Windows typowego paska stanu.  
  
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
|[CStatusBarCtrl::Create](#create)|Tworzy formant paska stanu i dołącza je do `CStatusBarCtrl` obiektu.|  
|[CStatusBarCtrl::CreateEx](#createex)|Tworzy formant paska stanu z określonego style rozszerzone Windows i dołącza go do `CStatusBarCtrl` obiektu.|  
|[CStatusBarCtrl::DrawItem](#drawitem)|Wywołuje się, gdy zmieni się wizualny aspekt rysowania przez właściciela stanu paska sterowania zmiany.|  
|[CStatusBarCtrl::GetBorders](#getborders)|Pobiera bieżący szerokość obramowań poziome i pionowe formant paska stanu.|  
|[CStatusBarCtrl::GetIcon](#geticon)|Pobiera ikonę dla części (okienko) w bieżącym formantu paska stanu.|  
|[CStatusBarCtrl::GetParts](#getparts)|Pobiera liczbę części w kontrolce paska stanu.|  
|[CStatusBarCtrl::GetRect](#getrect)|Pobiera prostokąt otaczający element w kontrolce paska stanu.|  
|[CStatusBarCtrl::GetText](#gettext)|Pobiera tekst z danej części formant paska stanu.|  
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Pobiera długość w znakach tekstu z danej części formant paska stanu.|  
|[CStatusBarCtrl::GetTipText](#gettiptext)|Pobiera tekst etykietki narzędzia dla okienka na pasku stanu.|  
|[CStatusBarCtrl::IsSimple](#issimple)|Sprawdza, czy formant okna stanu, aby ustalić, czy jest w trybie uproszczonym.|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła na pasku stanu.|  
|[CStatusBarCtrl::SetIcon](#seticon)|Ustawia okienko ikonę na pasku stanu.|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Ustawia minimalną wysokość stan powierzchni rysowania kontrolki paska.|  
|[CStatusBarCtrl::SetParts](#setparts)|Ustawia numer części stanu kontroli i współrzędne prawą krawędzią każdej części paska.|  
|[CStatusBarCtrl::SetSimple](#setsimple)|Określa, czy formant paska stanu wyświetla zwykły tekst lub wyświetla wszystkie części kontrolki ustawione przez poprzednie wywołanie `SetParts`.|  
|[CStatusBarCtrl::SetText](#settext)|Ustawia tekst w danej części formant paska stanu.|  
|[CStatusBarCtrl::SetTipText](#settiptext)|Ustawia tekst etykietki narzędzia dla okienka, w pasku stanu.|  
  
## <a name="remarks"></a>Uwagi  
 Formant"paska stanu" jest oknem poziomej, zwykle są wyświetlane w dolnej części okna nadrzędnego, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie. Formantu paska stanu można podzielić na części, aby wyświetlić więcej niż jeden typ danych.  
  
 Ta kontrolka (i w związku z tym `CStatusBarCtrl` klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Aby uzyskać więcej informacji na temat korzystania z `CStatusBarCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [za pomocą formantu CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="create"></a>  CStatusBarCtrl::Create  
 Tworzy formant paska stanu i dołącza je do `CStatusBarCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Określa styl formantu paska stanu. Zastosuj dowolną kombinację stanu paska style kontrolki, na liście [najczęściej używane style kontrolki](/windows/desktop/Controls/common-control-styles) w zestawie Windows SDK. Ten parametr musi zawierać styl WS_CHILD. Powinny również obejmować styl WS_VISIBLE.  
  
 *Rect*  
 Określa rozmiar i położenie formantu paska stanu. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.  
  
 *pParentWnd*  
 Określa stan paska okno nadrzędne kontrolki, zwykle `CDialog`. Nie może być równa NULL.  
  
 *nID*  
 Określa identyfikator formantu paska stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowanie `CStatusBarCtrl` w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołaj `Create`, która tworzy kontrolkę paska stanu i dołącza go do `CStatusBarCtrl` obiektu.  
  
 Domyślne położenie okna stanu jest wzdłuż dolnej części okna nadrzędnego, ale można określić styl CCS_TOP, aby był wyświetlany w górnej części obszaru klienckiego okna nadrzędnego. Można określić styl SBARS_SIZEGRIP obejmujący uchwyt zmiany rozmiaru po prawej stronie okna stanu. Łącząc style CCS_TOP i SBARS_SIZEGRIP nie jest zalecane, ponieważ wynikowy uchwyt zmiany rozmiaru nie działa mimo, że system rysuje go w oknie stanu.  
  
 Aby utworzyć pasek stanu przy użyciu rozszerzone Style okna, należy wywołać [CStatusBarCtrl::CreateEx](#createex) zamiast `Create`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CStatusBarCtrl::CreateEx  
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
 *dwExStyle*  
 Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.  
  
 *dwStyle*  
 Określa styl formantu paska stanu. Zastosuj dowolną kombinację stanu paska style kontrolki, na liście [najczęściej używane style kontrolki](/windows/desktop/Controls/common-control-styles) w zestawie Windows SDK. Ten parametr musi zawierać styl WS_CHILD. Powinny również obejmować styl WS_VISIBLE.  
  
 *Rect*  
 Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.  
  
 *pParentWnd*  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 *nID*  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="cstatusbarctrl"></a>  CStatusBarCtrl::CStatusBarCtrl  
 Konstruuje `CStatusBarCtrl` obiektu.  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="drawitem"></a>  CStatusBarCtrl::DrawItem  
 Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt rysowania przez właściciela stanu paska sterowania zmiany.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDrawItemStruct*  
 Długie wskaźnik do [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturę, która zawiera informacje o typie rysowania wymagane.  
  
### <a name="remarks"></a>Uwagi  
 `itemAction` Członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane.  
  
 Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpienie tej funkcji elementu członkowskiego do zaimplementowania rysunku do rysowania przez właściciela `CStatusBarCtrl` obiektu.  
  
 Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interface (GDI), wybrany dla kontekstu wyświetlana podana w *lpDrawItemStruct* przed ten element członkowski funkcja kończy.  
  
##  <a name="getborders"></a>  CStatusBarCtrl::GetBorders  
 Pobiera formantu paska stanu bieżącego szerokości obramowania poziome i pionowe i odstęp między prostokąty.  
  
```  
BOOL GetBorders(int* pBorders) const;  
  
BOOL GetBorders(
    int& nHorz,  
    int& nVert,  
    int& nSpacing) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pBorders*  
 Adres tablicę liczb całkowitych o trzy elementy. Pierwszy element otrzymuje szerokość obramowania poziome, drugi odbiera szerokość obramowania pionowy, a trzeci otrzymuje szerokość krawędzi między prostokąty.  
  
 *nHorz*  
 Odwołanie do liczba całkowita, która odbiera szerokość obramowania poziomej.  
  
 *Konweruj*  
 Odwołanie do liczba całkowita, która odbiera szerokość obramowania pionowy.  
  
 *nSpacing*  
 Odwołanie do liczba całkowita, która odbiera szerokość krawędzi między prostokąty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Te obramowania Określ odstępy między poza krawędzią formantu a prostokątów w kontrolce, które zawierają tekst.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="geticon"></a>  CStatusBarCtrl::GetIcon  
 Pobiera ikonę dla części (okienko) w bieżącym formantu paska stanu.  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*iPart*|[in] Liczony od zera indeks części, który zawiera ikonę, które mają zostać pobrane. Jeśli ten parametr ma wartość -1, na pasku stanu jest zakłada się, że pasek stanu tryb prosty.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt ikony Jeśli metoda kończy się pomyślnie; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [SB_GETICON](/windows/desktop/Controls/sb-geticon) komunikat, który jest opisany w zestawie Windows SDK.  
  
 Formant paska stanu składa się z wiersza tekstu okienka danych wyjściowych, które są również znane jako części. Aby uzyskać więcej informacji na temat paska stanu, zobacz [implementacja paska stanu w MFC](../../mfc/status-bar-implementation-in-mfc.md) i [Ustawianie trybu obiektu CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną `m_statusBar`, to znaczy umożliwiają dostęp do bieżącego formantu paska stanu. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod kopiuje ikony dwa okienka bieżącego formantu paska stanu. W wcześniejszej sekcji przykładu kodu możemy utworzony formant paska stanu za pomocą trzy okienka, a następnie dodawany ikony do pierwszego okienka. W tym przykładzie pobiera ikonę z okienka pierwszy, a następnie dodaje go do drugiego i trzeciego okienka.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="getparts"></a>  CStatusBarCtrl::GetParts  
 Pobiera liczbę części w kontrolce paska stanu.  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nParts*  
 Numer części, dla którego mają zostać pobrane współrzędnych. Jeśli ten parametr jest większa niż liczba części w kontrolce, komunikat pobiera współrzędne tylko istniejące składniki.  
  
 *pParts*  
 Adres tablicę liczb całkowitych, mające taką samą liczbę elementów jak numer części określone przez *nParts*. Każdy element w tablicy odbiera klienta współrzędne prawą krawędzią odpowiedniej części. Jeśli element jest ustawiony na wartość - 1, pozycja prawej krawędzi dla tej części rozszerza na prawej krawędzi paska stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer części kontrolki w przypadku powodzenia lub wartość zero, w przeciwnym razie.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego pobiera również współrzędne prawą krawędzią podanej liczby części.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="getrect"></a>  CStatusBarCtrl::GetRect  
 Pobiera prostokąt otaczający element w kontrolce paska stanu.  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nPane*  
 Liczony od zera indeks części, w których prostokąt otaczający ma zostać pobrane.  
  
 *lprect —*  
 Adres [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która odbiera prostokąt otaczający.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="gettext"></a>  CStatusBarCtrl::GetText  
 Pobiera tekst z danej części formant paska stanu.  
  
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
 *lpszText*  
 Adres buforu, który odbiera tekst. Ten parametr jest ciąg zakończony znakiem null.  
  
 *nPane*  
 Liczony od zera indeks części, z którego można pobrać tekstu.  
  
 *pType*  
 Wskaźnik na liczbę całkowitą, która otrzymuje informacje o typie. Typ może być jedną z następujących wartości:  
  
- **0** tekstu jest rysowana z obramowaniem się niższe niż płaszczyzna na pasku stanu.  
  
- SBT_NOBORDERS tekstu jest rysowana bez granic.  
  
- SBT_POPOUT tekstu jest rysowana z obramowaniem wyświetlane niż płaszczyzna na pasku stanu.  
  
- SBT_OWNERDRAW czy tekst ma SBT_OWNERDRAW typu, rysunku *pType* odbiera ten komunikat i zwraca 32-bitową wartość skojarzonych z tekstem zamiast typu długości i operacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość w znakach tekstu lub [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający tekst.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="gettextlength"></a>  CStatusBarCtrl::GetTextLength  
 Pobiera długość w znakach tekstu z danej części formant paska stanu.  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nPane*  
 Liczony od zera indeks części, z którego można pobrać tekstu.  
  
 *pType*  
 Wskaźnik na liczbę całkowitą, która otrzymuje informacje o typie. Typ może być jedną z następujących wartości:  
  
- **0** tekstu jest rysowana z obramowaniem się niższe niż płaszczyzna na pasku stanu.  
  
- SBT_NOBORDERS tekstu jest rysowana bez granic.  
  
- SBT_OWNERDRAW tekstu jest rysowana przez okno nadrzędne.  
  
- SBT_POPOUT tekstu jest rysowana z obramowaniem wyświetlane niż płaszczyzna na pasku stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość w znakach tekstu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="gettiptext"></a>  CStatusBarCtrl::GetTipText  
 Pobiera tekst etykietki narzędzia dla okienka na pasku stanu.  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nPane*  
 Liczony od zera indeks w okienku paska stanu, aby otrzymać tekst etykietki narzędzia.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający tekst, który ma być używane w etykietce narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [SB_GETTIPTEXT](/windows/desktop/Controls/sb-gettiptext), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="issimple"></a>  CStatusBarCtrl::IsSimple  
 Sprawdza, czy formant okna stanu, aby ustalić, czy jest w trybie uproszczonym.  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli formant okna stanu znajduje się w trybie uproszczonym; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [SB_ISSIMPLE](/windows/desktop/Controls/sb-issimple), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setbkcolor"></a>  CStatusBarCtrl::SetBkColor  
 Ustawia kolor tła na pasku stanu.  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Parametry  
 *CR*  
 Wartość COLORREF, która określa nowy kolor tła. Określ wartość CLR_DEFAULT, powodują pasek stanu, aby używać jej domyślny kolor tła.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](/windows/desktop/gdi/colorref) wartość, która reprezentuje poprzedniego domyślny kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [SB_SETBKCOLOR](/windows/desktop/Controls/sb-setbkcolor), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="seticon"></a>  CStatusBarCtrl::SetIcon  
 Ustawia okienko ikonę na pasku stanu.  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 *nPane*  
 Liczony od zera indeks okienko w którym będą otrzymywać ikony. Jeśli ten parametr ma wartość -1, na pasku stanu jest zakłada się, że pasek stanu proste.  
  
 *hIcon*  
 Uchwyt ikony, należy ustawić. Jeśli ta wartość wynosi NULL, ikona jest usuwany z części.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [SB_SETICON](/windows/desktop/Controls/sb-seticon), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CStatusBarCtrl::SetBkColor](#setbkcolor).  
  
##  <a name="setminheight"></a>  CStatusBarCtrl::SetMinHeight  
 Ustawia minimalną wysokość stan powierzchni rysowania kontrolki paska.  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>Parametry  
 *Nmin.*  
 Minimalna wysokość w pikselach formantu.  
  
### <a name="remarks"></a>Uwagi  
 Minimalna wysokość jest sumą *nMin* i dwa razy szerokość w pikselach, pionowa obramowania formantu paska stanu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="setparts"></a>  CStatusBarCtrl::SetParts  
 Ustawia numer części stanu kontroli i współrzędne prawą krawędzią każdej części paska.  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>Parametry  
 *nParts*  
 Numer części, aby ustawić. Liczba części nie może być większa niż 255.  
  
 *pWidths*  
 Adres tablicę liczb całkowitych, mające taką samą liczbę elementów na części określone przez *nParts*. Każdy element w tablicy Określa położenie prawej krawędzi odpowiedniej części współrzędne klienta. Jeśli element jest - 1, pozycja prawej krawędzi dla tej części rozszerza się na prawą krawędzią kontrolki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="setsimple"></a>  CStatusBarCtrl::SetSimple  
 Określa, czy formant paska stanu wyświetla zwykły tekst lub wyświetla wszystkie części kontrolki ustawione przez poprzednie wywołanie [SetParts](#setparts).  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bSimple*<br/>
[in] Flaga typ wyświetlania. Jeśli ten parametr ma wartość TRUE, kontrolka ma wyświetlać prosty tekst; Jeśli jest to wartość FALSE, wyświetla wiele części.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku aplikacji zmiany formantu paska stanu z innym niż prosty, Simple lub na odwrót, system natychmiast odrysowuje formantu.  
  
##  <a name="settext"></a>  CStatusBarCtrl::SetText  
 Ustawia tekst w danej części formant paska stanu.  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszText*  
 Adres określania tekstu, aby ustawić ciąg zakończony znakiem null. Jeśli *nNie* jest SBT_OWNERDRAW, *lpszText* reprezentuje 32 bity danych.  
  
 *nPane*  
 Liczony od zera indeks części do ustawienia. Jeśli ta wartość wynosi 255, formantu paska stanu będzie traktowana jako prosty formant mających tylko jednej części.  
  
 *nNie*  
 Typ operacji rysowania. Zobacz [komunikat SB_SETTEXT](/windows/desktop/Controls/sb-settext) listę możliwych wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Komunikat unieważnia części kontrolki, które uległy zmianie, powodując go, aby wyświetlić nowy tekst w przypadku, gdy formant uzyskuje następny komunikat WM_PAINT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="settiptext"></a>  CStatusBarCtrl::SetTipText  
 Ustawia tekst etykietki narzędzia dla okienka, w pasku stanu.  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Parametry  
 *nPane*  
 Liczony od zera indeks w okienku paska stanu, aby otrzymać tekst etykietki narzędzia.  
  
 *pszTipText*  
 Wskaźnik do ciągu zawierającego tekst etykietki narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [SB_SETTIPTEXT](/windows/desktop/Controls/sb-settiptext), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)
