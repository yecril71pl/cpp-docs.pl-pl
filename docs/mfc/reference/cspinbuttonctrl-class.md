---
title: Klasa CSpinButtonCtrl
ms.date: 11/04/2016
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
ms.openlocfilehash: cedfe16a6870bc779121e8e864866cfcb711b148
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753101"
---
# <a name="cspinbuttonctrl-class"></a>Klasa CSpinButtonCtrl

Udostępnia funkcje systemu Windows wspólne przycisku pokrętła.

## <a name="syntax"></a>Składnia

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Konstruuje `CSpinButtonCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSpinButtonCtrl::Tworzenie](#create)|Tworzy formant przycisku pokrętła `CSpinButtonCtrl` i dołącza go do obiektu.|
|[CSpinButtonCtrl::CreateEx](#createex)|Tworzy kontrolkę przycisku pokrętła z określonymi `CSpinButtonCtrl` stylami rozszerzonymi systemu Windows i dołącza go do obiektu.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Pobiera informacje o przyspieszeniu dla sterowania przyciskiem pokrętła.|
|[CSpinButtonCtrl::GetBase](#getbase)|Pobiera bieżącą podstawę dla sterowania przyciskiem pokrętła.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Pobiera wskaźnik do bieżącego okna buddy.|
|[CSpinButtonCtrl::GetPos](#getpos)|Pobiera bieżącą pozycję formantu przycisku pokrętła.|
|[CSpinButtonCtrl::GetRange](#getrange)|Pobiera górne i dolne granice (zakres) dla sterowania przyciskiem pokrętła.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Ustawia przyspieszenie dla sterowania przyciskiem pokrętła.|
|[CSpinButtonCtrl::SetBase](#setbase)|Ustawia podstawę dla sterowania przyciskiem pokrętła.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Ustawia okno buddy dla formantu przycisku pokrętła.|
|[CSpinButtonCtrl::SetPos](#setpos)|Ustawia bieżącą pozycję formantu.|
|[CSpinButtonCtrl::SetRange](#setrange)|Ustawia górną i dolną granicę (zakres) dla sterowania przyciskiem pokrętła.|

## <a name="remarks"></a>Uwagi

"Sterowanie przyciskiem pokrętła" (znane również jako kontrolka w górę i w dół) to para przycisków strzałek, które użytkownik może kliknąć, aby przyrost lub zniego wartość, na przykład położenie przewijania lub numer wyświetlany w formancie towarzyszącym. Wartość skojarzona z formantem przycisku pokrętła jest nazywana jego bieżącą pozycją. Formant przycisku pokrętła jest najczęściej używany z formantem towarzyszącym, nazywanym "oknem buddy".

Ten formant (i `CSpinButtonCtrl` dlatego klasa) jest dostępny tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersji 3.51 lub nowszych.

Dla użytkownika formant przycisku pokrętła i jego okno buddy często wyglądają jak pojedynczy formant. Można określić, że kontrolka przycisku pokrętła automatycznie pozycjonuje się obok okna znajomego i automatycznie ustawia podpis okna buddy na jego bieżącą pozycję. Można użyć kontrolki przycisku pokrętła z kontrolką edycji, aby monitować użytkownika o podanie danych liczbowych.

Kliknięcie strzałki w górę powoduje przeniesienie bieżącej pozycji w kierunku maksimum, a kliknięcie strzałki w dół powoduje przeniesienie bieżącej pozycji w kierunku minimum. Domyślnie minimalna wynosi 100, a maksymalna 0. Za każdym razem, gdy ustawienie minimalne jest większe niż ustawienie maksymalne (na przykład, gdy używane są ustawienia domyślne), kliknięcie strzałki w górę zmniejsza wartość pozycji i kliknięcie strzałki w dół zwiększa ją.

Formant przycisku pokrętła bez okna buddy działa jako rodzaj uproszczonego paska przewijania. Na przykład formant karty czasami wyświetla kontrolkę przycisku pokrętła, aby umożliwić użytkownikowi przewijanie dodatkowych kart do widoku.

Aby uzyskać więcej `CSpinButtonCtrl`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl::Tworzenie

Tworzy formant przycisku pokrętła `CSpinButtonCtrl` i dołącza go do obiektu..

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl formantu przycisku pokrętła. Zastosuj dowolną kombinację stylów sterowania przyciskiem pokrętła do formantu. Style te są opisane w [stylach sterowania w górę iw dół](/windows/win32/Controls/up-down-control-styles) w panelu Windows SDK.

*Rect*<br/>
Określa rozmiar i położenie formantu przycisku pokrętła. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub struktura [RECT](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego formantu przycisku pokrętła, zwykle . `CDialog` Nie może być null.

*Nid*<br/>
Określa identyfikator formantu przycisku pokrętła.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruuj `CSpinButtonCtrl` obiekt w dwóch etapach Najpierw, `Create`wywołaj konstruktora, a następnie `CSpinButtonCtrl` wywołaj , który tworzy formant przycisku pokrętła i dołącza go do obiektu.

Aby utworzyć kontrolkę przycisku pokrętła z rozszerzonymi stylami okien, [zamiast](#createex) `Create`.

## <a name="cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl::CreateEx

Tworzy formant (okno podrzędne) i `CSpinButtonCtrl` kojarzy go z obiektem.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwexstyle*<br/>
Określa rozszerzony styl tworzonego formantu. Aby uzyskać listę rozszerzonych stylów systemu Windows, zobacz parametr *dwExStyle* dla [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) w zestawie Windows SDK.

*Dwstyle*<br/>
Określa styl formantu przycisku pokrętła. Zastosuj dowolną kombinację stylów sterowania przyciskiem pokrętła do formantu. Style te są opisane w [stylach sterowania w górę iw dół](/windows/win32/Controls/up-down-control-styles) w panelu Windows SDK.

*Rect*<br/>
Odwołanie do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest nadrzędnym formantu.

*Nid*<br/>
Identyfikator okna podrzędnego formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [utwórz,](#create) aby zastosować rozszerzone style systemu Windows, określone przez przedmową style rozszerzonego systemu Windows WS_EX_.

## <a name="cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl

Konstruuje `CSpinButtonCtrl` obiekt.

```
CSpinButtonCtrl();
```

## <a name="cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonCtrl::GetAccel

Pobiera informacje o przyspieszeniu dla sterowania przyciskiem pokrętła.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Parametry

*nKcel*<br/>
Liczba elementów w tablicy określonej przez *pAccel*.

*pAccel (własówce)*<br/>
Wskaźnik do tablicy [struktur UDACCEL,](/windows/win32/api/commctrl/ns-commctrl-udaccel) która odbiera informacje o przyspieszeniu.

### <a name="return-value"></a>Wartość zwracana

Liczba pobranych struktur akceleratora.

## <a name="cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl::GetBase

Pobiera bieżącą podstawę dla sterowania przyciskiem pokrętła.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość bazowa.

## <a name="cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy

Pobiera wskaźnik do bieżącego okna buddy.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego okna buddy.

## <a name="cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonCtrl::GetPos

Pobiera bieżącą pozycję formantu przycisku pokrętła.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpbError*<br/>
Wskaźnik do wartości logicznej, która jest ustawiona na zero, jeśli wartość jest pomyślnie pobrana lub niezerowa, jeśli wystąpi błąd. Jeśli ten parametr jest ustawiony na wartość NULL, błędy nie są zgłaszane.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca 16-bitową bieżącą pozycję w słowie niskiego rzędu. Wyraz wysokiego rzędu jest niezerowy, jeśli wystąpił błąd.

Druga wersja zwraca pozycję 32-bitową.

### <a name="remarks"></a>Uwagi

Podczas przetwarzania zwracanej wartości formant aktualizuje swoją bieżącą pozycję na podstawie podpisu okna buddy. Formant zwraca błąd, jeśli nie ma okna buddy lub jeśli podpis określa nieprawidłową lub wartość poza zakresem.

## <a name="cspinbuttonctrlgetrange"></a><a name="getrange"></a>CSpinButtonCtrl::GetRange

Pobiera górne i dolne granice (zakres) dla sterowania przyciskiem pokrętła.

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

*Niższe*<br/>
Odwołanie do liczby całkowitej, która odbiera dolny limit dla formantu.

*Górnej*<br/>
Odwołanie do liczby całkowitej, która odbiera górny limit dla formantu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość 32-bitową zawierającą górne i dolne limity. Słowo niskiego rzędu jest górną granicą formantu, a słowo wysokiego rzędu jest dolną granicą.

### <a name="remarks"></a>Uwagi

Funkcja `GetRange32` elementu członkowskiego pobiera zakres formantu przycisku pokrętła jako 32-bitową ćwięk.

## <a name="cspinbuttonctrlsetaccel"></a><a name="setaccel"></a>CSpinButtonCtrl::SetAccel

Ustawia przyspieszenie dla sterowania przyciskiem pokrętła.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Parametry

*nKcel*<br/>
Liczba struktur [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) określonych przez *pAccel*.

*pAccel (własówce)*<br/>
Wskaźnik do tablicy struktur UDACCEL, które zawierają informacje o przyspieszeniu. Elementy powinny być sortowane w porządku `nSec` rosnącym na podstawie elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="cspinbuttonctrlsetbase"></a><a name="setbase"></a>CSpinButtonCtrl::SetBase

Ustawia podstawę dla sterowania przyciskiem pokrętła.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Parametry

*nBaza*<br/>
Nowa wartość bazowa formantu. Może to być 10 dla dziesiętnych lub 16 dla szesnastkowych.

### <a name="return-value"></a>Wartość zwracana

Poprzednia wartość bazowa, jeśli zakończy się pomyślnie, lub zero, jeśli podano nieprawidłową podstawę.

### <a name="remarks"></a>Uwagi

Wartość bazowa określa, czy w oknie buddy są wyświetlane liczby w cyfrach dziesiętnych czy szesnastkowych. Liczby szesnastkowe są zawsze niepodpisane; liczby dziesiętne są podpisane.

## <a name="cspinbuttonctrlsetbuddy"></a><a name="setbuddy"></a>CSpinButtonCtrl::SetBuddy

Ustawia okno buddy dla formantu przycisku pokrętła.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Parametry

*pWndBuddy*<br/>
Wskaźnik do nowego okna buddy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do poprzedniego okna buddy.

### <a name="remarks"></a>Uwagi

Formant spin jest prawie zawsze skojarzony z innym oknem, takim jak kontrolka edycji, która wyświetla część zawartości. To inne okno jest nazywane "kumplem" kontroli spin.

## <a name="cspinbuttonctrlsetpos"></a><a name="setpos"></a>CSpinButtonCtrl::SetPos

Ustawia bieżącą pozycję dla sterowania przyciskiem pokrętła.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Nowa pozycja dla sterowania. Ta wartość musi znajdować się w zakresie określonym przez górne i dolne granice formantu.

### <a name="return-value"></a>Wartość zwracana

Poprzednia pozycja (16-bitowa precyzja dla `SetPos`, `SetPos32`32-bitowa precyzja dla ).

### <a name="remarks"></a>Uwagi

`SetPos32`ustawia pozycję 32-bitową.

## <a name="cspinbuttonctrlsetrange"></a><a name="setrange"></a>CSpinButtonCtrl::SetRange

Ustawia górną i dolną granicę (zakres) dla sterowania przyciskiem pokrętła.

```cpp
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parametry

*nLower* i *nUpper*<br/>
Górne i dolne granice sterowania. Dla `SetRange`, żaden z tych limitów nie może być większa niż UD_MAXVAL lub mniejsza niż UD_MINVAL; ponadto różnica między tymi dwoma limitami nie może przekraczać UD_MAXVAL. `SetRange32`nie nakłada żadnych ograniczeń na limity; używać żadnych całkowitych.

### <a name="remarks"></a>Uwagi

Funkcja `SetRange32` elementu członkowskiego ustawia zakres 32-bitowy dla sterowania przyciskiem pokrętła.

> [!NOTE]
> Domyślny zakres przycisku spin ma maksymalną ustawioną wartość zero (0), a minimalną ustawioną na 100. Ponieważ wartość maksymalna jest mniejsza niż wartość minimalna, kliknięcie strzałki w górę spowoduje zmniejszenie pozycji i kliknięcie strzałki w dół spowoduje jej zwiększenie. Służy `CSpinButtonCtrl::SetRange` do dostosowywania tych wartości.

## <a name="see-also"></a>Zobacz też

[Próbka MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CSliderCtrl](../../mfc/reference/csliderctrl-class.md)
