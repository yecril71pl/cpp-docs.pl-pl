---
title: Cspinbuttonctrl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
dev_langs:
- C++
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43b0967309813603e4f683f35c3ca51dce99fd8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374694"
---
# <a name="cspinbuttonctrl-class"></a>Cspinbuttonctrl — klasa
Udostępnia funkcje systemu Windows wspólnej przycisku pokrętła.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Konstruuje `CSpinButtonCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSpinButtonCtrl::Create](#create)|Tworzy kontrolkę przycisku pokrętła i dołącza go do `CSpinButtonCtrl` obiektu.|  
|[CSpinButtonCtrl::CreateEx](#createex)|Tworzy spin button — formant w określonym stylu rozszerzonej systemu Windows i dołącza go do `CSpinButtonCtrl` obiektu.|  
|[CSpinButtonCtrl::GetAccel](#getaccel)|Pobiera informacje o przyspieszenie dla przycisku pokrętła.|  
|[CSpinButtonCtrl::GetBase](#getbase)|Pobiera bieżący podstawa przycisku pokrętła.|  
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Pobiera wskaźnik do bieżącego okna buddy.|  
|[CSpinButtonCtrl::GetPos](#getpos)|Pobiera bieżącą pozycję przycisku pokrętła.|  
|[CSpinButtonCtrl::GetRange](#getrange)|Pobiera górny i dolny limit (zakres) dla przycisku pokrętła.|  
|[CSpinButtonCtrl::SetAccel](#setaccel)|Ustawia przyspieszenie dla przycisku pokrętła.|  
|[CSpinButtonCtrl::SetBase](#setbase)|Ustawia podstawa przycisku pokrętła.|  
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Ustawia buddy okna dla formantu przycisku pokrętła.|  
|[CSpinButtonCtrl::SetPos](#setpos)|Ustawia bieżącego położenia kontrolki.|  
|[CSpinButtonCtrl::SetRange](#setrange)|Ustawia górny i dolny limit (zakres) dla przycisku pokrętła.|  
  
## <a name="remarks"></a>Uwagi  
 "Przycisku pokrętła" (określane również jako formantu góra dół) jest para przycisk strzałki, które użytkownik może kliknąć, aby zwiększyć lub zmniejszyć wartość, na przykład pozycji przewijania lub liczby wyświetlanych w formancie pomocnika. Wartość skojarzoną z przycisku pokrętła jest nazywany jego bieżącym położeniu. Kontrolka przycisku pokrętła jest najczęściej używana z formantem pomocnika "okno buddy".  
  
 Ten formant (i w związku z tym `CSpinButtonCtrl` klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Dla użytkownika przycisku pokrętła i jego zaprzyjaźnione okno często wygląda jak jeden formant. Można określić, czy kontrolka przycisku pokrętła automatycznie rozmieszczaj się obok jego zaprzyjaźnione okno i powoduje on automatyczne ustawienie podpis okna buddy w jego bieżące położenie. Kontrolka przycisku pokrętła z formantu edycyjnego służy do monitowania użytkownika o liczbowa na wejściu.  
  
 Klikając przycisk strzałki w górę przenosi bieżącego położenia kierunku maksymalna, oraz kliknij strzałkę w dół bieżącej pozycji do minimum. Domyślnie minimalna wynosi 100, a maksymalna to 0. Zawsze, gdy ustawienie minimalnej jest większa niż wartość maksymalna ustawienie (na przykład, gdy używane są ustawienia domyślne), klikając polecenie się spadku strzałkę wartość pozycji i klikając przycisk strzałki w dół zwiększa go.  
  
 Kontrolka przycisku pokrętła, bez okna buddy działa jako sortowania paska przewijania uproszczone. Na przykład formantu karty czasami wyświetla przycisku pokrętła, aby umożliwić użytkownikowi przewiń dodatkowe karty do widoku.  
  
 Aby uzyskać więcej informacji na temat używania `CSpinButtonCtrl`, zobacz [formanty](../../mfc/controls-mfc.md) i [przy użyciu CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="create"></a>  CSpinButtonCtrl::Create  
 Tworzy kontrolkę przycisku pokrętła i dołącza go do `CSpinButtonCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl formantu przycisku pokrętła. Zastosuj dowolną kombinację stylów formantu przycisku pokrętła do formantu. Te style są opisane w [stylów formantu góra-dół](http://msdn.microsoft.com/library/windows/desktop/bb759885) w zestawie Windows SDK.  
  
 `rect`  
 Określa rozmiar i położenie formantu przycisku pokrętła. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) — struktura  
  
 `pParentWnd`  
 Wskaźnik do okno nadrzędne kontrolki przycisku pokrętła, zwykle `CDialog`. Nie może być **wartości NULL.**  
  
 `nID`  
 Określa identyfikator formantu przycisku pokrętła.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CSpinButtonCtrl` obiekt w dwóch krokach, wywołanie konstruktora, a następnie wywołać **Utwórz**, która tworzy przycisku pokrętła i dołącza go do `CSpinButtonCtrl` obiektu.  
  
 Aby utworzyć przycisku pokrętła z rozszerzone Style okna, należy wywołać [CSpinButtonCtrl::CreateEx](#createex) zamiast **Utwórz**.  
  
##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CSpinButtonCtrl` obiektu.  
  
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
 Określa styl rozszerzony formantu tworzona. Lista style rozszerzonej systemu windows, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 `dwStyle`  
 Określa styl formantu przycisku pokrętła. Zastosuj dowolną kombinację stylów formantu przycisku pokrętła do formantu. Te style są opisane w [stylów formantu góra-dół](http://msdn.microsoft.com/library/windows/desktop/bb759885) w zestawie Windows SDK.  
  
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
  
##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl  
 Konstruuje `CSpinButtonCtrl` obiektu.  
  
```  
CSpinButtonCtrl();
```  
  
##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel  
 Pobiera informacje o przyspieszenie dla przycisku pokrętła.  
  
```  
UINT GetAccel(
    int nAccel,  
    UDACCEL* pAccel) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nAccel`  
 Liczba elementów w tablicy określona przez `pAccel`.  
  
 `pAccel`  
 Wskaźnik do tablicy [UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897) struktur, które otrzymuje informacje przyspieszenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba struktur akceleratora pobrać.  
  
##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase  
 Pobiera bieżący podstawa przycisku pokrętła.  
  
```  
UINT GetBase() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość podstawową.  
  
##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy  
 Pobiera wskaźnik do bieżącego okna buddy.  
  
```  
CWnd* GetBuddy() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego okna buddy.  
  
##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos  
 Pobiera bieżącą pozycję przycisku pokrętła.  
  
```  
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpbError*  
 Wskaźnik do wartość logiczna, która jest równa zero, jeśli wartość jest pobrane pomyślnie, lub zera w przypadku wystąpienia błędu. Jeśli ten parametr ma wartość **NULL**, nie zostały zgłoszone błędy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszą wersję zwraca bieżącą pozycję w programie word znaczącymi bitami 16-bitowych. Word znaczących jest różna od zera, jeśli wystąpił błąd.  
  
 Druga wersja zwraca pozycję 32-bitowych.  
  
### <a name="remarks"></a>Uwagi  
 Podczas przetwarzania wartość zwracana, formantu aktualizuje jego bieżącym położeniu oparte na podpis okna zaprzyjaźnionego. Formant zwraca błąd, jeśli nie ma żadnych zaprzyjaźnione okno lub jeśli podpis określa nieprawidłowy lub poza zakresem wartości.  
  
##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange  
 Pobiera górny i dolny limit (zakres) dla przycisku pokrętła.  
  
```  
DWORD GetRange() const;  
  
void GetRange(
    int& lower,  
    int& upper) const;  
  
void GetRange32(
    int& lower,  
    int &upper) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Niższe*  
 Odwołanie do liczba całkowita, która odbiera dolnej granicy formantu.  
  
 *górny*  
 Odwołanie do liczba całkowita, która odbiera górny limit dla formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszą wersję zwraca wartość 32-bitowej zawierającego górny i dolny limit. Word znaczącymi bitami jest górny limit dla formantu i word znaczących jest dolnej granicy.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska `GetRange32` pobiera zakres formantu przycisku pokrętła jako liczba całkowita 32-bitowych.  
  
##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel  
 Ustawia przyspieszenie dla przycisku pokrętła.  
  
```  
BOOL SetAccel(
    int nAccel,  
    UDACCEL* pAccel);
```  
  
### <a name="parameters"></a>Parametry  
 `nAccel`  
 Liczba [UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897) struktury określony przez `pAccel`.  
  
 `pAccel`  
 Wskaźnik do tablicy `UDACCEL` struktur, które zawierają informacje przyspieszenia. Elementy mają być sortowane w kolejności rosnącej według **nSec** elementu członkowskiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase  
 Ustawia podstawa przycisku pokrętła.  
  
```  
int SetBase(int nBase);
```  
  
### <a name="parameters"></a>Parametry  
 `nBase`  
 Nowa wartość podstawową dla formantu. Może być 10 dla typu decimal lub 16 w przypadku wartości szesnastkowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednia wartość podstawowego w przypadku powodzenia lub wartość zero, jeśli podano nieprawidłowy atrybut podstawowy.  
  
### <a name="remarks"></a>Uwagi  
 Podstawową wartość określa, czy okno buddy zawiera numery cyfry dziesiętne lub szesnastkowe. Szesnastkowe nigdy nie mają znaku; Zalogowano liczb dziesiętnych.  
  
##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy  
 Ustawia buddy okna dla formantu przycisku pokrętła.  
  
```  
CWnd* SetBuddy(CWnd* pWndBuddy);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndBuddy`  
 Wskaźnik do nowego okna buddy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do poprzedniego okna buddy.  
  
### <a name="remarks"></a>Uwagi  
 Pokrętła prawie zawsze jest skojarzony z innym oknie, takich jak kontrola edycji, który wyświetla zawartość. To inne okno jest nazywany "buddy" kontrolki pokrętła.  
  
##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos  
 Ustawia bieżącego położenia kontrolki przycisku pokrętła.  
  
```  
int SetPos(int nPos);  
int SetPos32(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Nowa pozycja dla formantu. Ta wartość musi być w zakresie określonym przez górny i dolny limit dla formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedniej pozycji (16-bitowych dokładność `SetPos`32- bitowy dokładności dla `SetPos32`).  
  
### <a name="remarks"></a>Uwagi  
 `SetPos32` Ustawia położenie 32-bitowych.  
  
##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange  
 Ustawia górny i dolny limit (zakres) dla przycisku pokrętła.  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 `nLower` I `nUpper`  
 Górny i dolny limit dla formantu. Dla `SetRange`, limit nie może być większa niż **UD_MAXVAL** lub mniej niż **UD_MINVAL**; Ponadto nie może przekraczać różnicę między dwiema granicami **UD_MAXVAL**. `SetRange32` nie nakłada żadnych ograniczeń na granicach; Użyj dowolnej liczby całkowite.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska `SetRange32` ustawia zakresu 32-bitowego dla przycisku pokrętła.  
  
> [!NOTE]
>  Domyślny zakres dla przycisku pokrętła ma maksymalną wartość zero (0) i minimalna wartość 100. Ponieważ wartość maksymalna jest mniejsza niż wartość minimalna, klikając strzałkę w górę zmniejszy pozycję i kliknij strzałkę w dół spowoduje zwiększenie jego. Użyj `CSpinButtonCtrl::SetRange` dostosowanie tych wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [CMNCTRL2 próbki MFC](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CSliderCtrl](../../mfc/reference/csliderctrl-class.md)
