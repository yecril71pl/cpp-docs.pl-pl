---
title: Klasa CProgressCtrl
ms.date: 11/04/2016
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
ms.openlocfilehash: c5eb6a93cd68c2dafb76af3b0e42da8b56566e25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364006"
---
# <a name="cprogressctrl-class"></a>Klasa CProgressCtrl

Udostępnia funkcje kontroli wspólnego paska postępu systemu Windows.

## <a name="syntax"></a>Składnia

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Konstruuje `CProgressCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CProgressCtrl::Tworzenie](#create)|Tworzy formant paska postępu i `CProgressCtrl` dołącza go do obiektu.|
|[CProgressCtrl::CreateEx](#createex)|Tworzy formant postępu z określonymi stylami rozszerzonymi `CProgressCtrl` systemu Windows i dołącza go do obiektu.|
|[CProgressCtrl::GetBarColor](#getbarcolor)|Pobiera kolor paska wskaźnika postępu dla bieżącej kontroli paska postępu.|
|[CProgressCtrl::GetBkColor](#getbkcolor)|Pobiera kolor tła bieżącego paska postępu.|
|[CProgressCtrl::GetPos](#getpos)|Pobiera bieżącą pozycję paska postępu.|
|[CProgressCtrl::GetRange](#getrange)|Pobiera dolne i górne granice zakresu kontroli paska postępu.|
|[CProgressCtrl::GetState](#getstate)|Pobiera stan bieżącej kontroli paska postępu.|
|[CProgressCtrl::GetStep](#getstep)|Pobiera przyrost kroku dla paska postępu bieżącej kontroli paska postępu.|
|[CProgressCtrl::OffsetPos](#offsetpos)|Przesuwa bieżącą pozycję formantu paska postępu o określony przyrost i ponownie rysuje pasek, aby odzwierciedlić nową pozycję.|
|[CProgressCtrl::SetBarColor](#setbarcolor)|Ustawia kolor paska wskaźnika postępu w bieżącej kontroli paska postępu.|
|[CProgressCtrl::SetBkColor](#setbkcolor)|Ustawia kolor tła paska postępu.|
|[CProgressCtrl::SetMarquee](#setmarquee)|Włącza lub wyłącza tryb ramki zaznaczenia dla bieżącej kontrolki paska postępu.|
|[CProgressCtrl::SetPos](#setpos)|Ustawia bieżącą pozycję dla kontroli paska postępu i ponownie rysuje pasek, aby odzwierciedlić nową pozycję.|
|[CProgressCtrl::SetRange](#setrange)|Ustawia minimalne i maksymalne zakresy dla kontroli paska postępu i ponownie rysuje pasek, aby odzwierciedlić nowe zakresy.|
|[CProgressCtrl::SetState](#setstate)|Ustawia stan bieżącej kontroli paska postępu.|
|[CProgressCtrl::SetStep](#setstep)|Określa przyrost kroku dla formantu paska postępu.|
|[CProgressCtrl::StepIt](#stepit)|Przesuwa bieżącą pozycję dla kontroli paska postępu o przyrost kroku (patrz [SetStep)](#setstep)i ponownie rysuje pasek, aby odzwierciedlić nową pozycję.|

## <a name="remarks"></a>Uwagi

Formant paska postępu jest oknem, którego aplikacja może użyć do wskazania postępu długiej operacji. Składa się z prostokąta, który jest stopniowo wypełniany, od lewej do prawej, z kolorem podświetlenia systemu w miarę postępu operacji.

Formant paska postępu ma zakres i bieżącą pozycję. Zakres reprezentuje całkowity czas trwania operacji, a bieżąca pozycja reprezentuje postęp, który aplikacja poczyniła w kierunku ukończenia operacji. Procedura okna używa zakresu i bieżącej pozycji do określenia procentu paska postępu do wypełnienia kolorem podświetlenia. Ponieważ wartości zakresu i bieżącej pozycji są wyrażone jako podpisane liczby całkowite, możliwy zakres bieżących wartości pozycji wynosi od -2 147 483 648 do 2 147 483 647 włącznie.

Aby uzyskać więcej `CProgressCtrl`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="cprogressctrlcprogressctrl"></a><a name="cprogressctrl"></a>CProgressCtrl::CProgressCtrl

Konstruuje `CProgressCtrl` obiekt.

```
CProgressCtrl();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CProgressCtrl` obiektu, `CProgressCtrl::Create` wywołać, aby utworzyć formant paska postępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

## <a name="cprogressctrlcreate"></a><a name="create"></a>CProgressCtrl::Tworzenie

Tworzy formant paska postępu i `CProgressCtrl` dołącza go do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl formantu paska postępu. Zastosuj dowolną kombinację stylów okien opisanych w [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) w windows SDK, oprócz następujących stylów kontroli paska postępu, do formantu:

- PBS_VERTICAL Wyświetla informacje o postępie w pionie, od góry do dołu. Bez tej flagi formant paska postępu jest wyświetlany w poziomie, od lewej do prawej.

- PBS_SMOOTH Wyświetla stopniowe, płynne wypełnianie kontrolki paska postępu. Bez tej flagi formant wypełni bloki.

*Rect*<br/>
Określa rozmiar i położenie formantu paska postępu. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT.](/previous-versions/dd162897\(v=vs.85\)) Ponieważ formant musi być oknem podrzędnym, określone współrzędne są względem obszaru klienta *pParentWnd*.

*pParentWnd*<br/>
Określa okno nadrzędne formantu paska `CDialog`postępu, zwykle okno . Nie może być null.

*Nid*<br/>
Określa identyfikator formantu paska postępu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, `CProgressCtrl` jeśli obiekt został pomyślnie utworzony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Konstruowanie `CProgressCtrl` obiektu w dwóch krokach. Najpierw wywołać konstruktora, `CProgressCtrl` który tworzy `Create`obiekt, a następnie wywołać , który tworzy formant paska postępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

## <a name="cprogressctrlcreateex"></a><a name="createex"></a>CProgressCtrl::CreateEx

Tworzy formant (okno podrzędne) i `CProgressCtrl` kojarzy go z obiektem.

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
Określa styl formantu paska postępu. Zastosuj dowolną kombinację stylów okien opisanych w [programie CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) w zestaw windows SDK.

*Rect*<br/>
Odwołanie do struktury [RECT](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest nadrzędnym formantu.

*Nid*<br/>
Identyfikator okna podrzędnego formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Create,](#create) aby zastosować rozszerzone style systemu Windows, określone przez przedmową styl rozszerzony systemu Windows **WS_EX_**.

## <a name="cprogressctrlgetbarcolor"></a><a name="getbarcolor"></a>CProgressCtrl::GetBarColor

Pobiera kolor paska wskaźnika postępu dla bieżącej kontroli paska postępu.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor bieżącego paska postępu, reprezentowanego jako wartość [COLORREF,](/windows/win32/gdi/colorref) lub CLR_DEFAULT, jeśli kolor paska wskaźnika postępu jest kolorem domyślnym.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PBM_GETBARCOLOR,](/windows/win32/Controls/pbm-getbarcolor) który jest opisany w windows SDK.

## <a name="cprogressctrlgetbkcolor"></a><a name="getbkcolor"></a>CProgressCtrl::GetBkColor

Pobiera kolor tła bieżącego paska postępu.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor tła bieżącego paska postępu, reprezentowany jako wartość [COLORREF.](/windows/win32/gdi/colorref)

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [komunikat PBM_GETBKCOLOR,](/windows/win32/Controls/pbm-getbkcolor) który jest opisany w windows SDK.

## <a name="cprogressctrlgetpos"></a><a name="getpos"></a>CProgressCtrl::GetPos

Pobiera bieżące położenie paska postępu.

```
int GetPos();
```

### <a name="return-value"></a>Wartość zwracana

Położenie kontrolki paska postępu.

### <a name="remarks"></a>Uwagi

Położenie kontrolki paska postępu nie jest fizyczną lokalizacją na ekranie, ale jest między górnym i dolnym zakresem wskazanym w [SetRange](#setrange).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

## <a name="cprogressctrlgetrange"></a><a name="getrange"></a>CProgressCtrl::GetRange

Pobiera bieżące dolne i górne limity lub zakres formantu paska postępu.

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Parametry

*nLower*<br/>
Odwołanie do liczby całkowitej odbierającej dolny limit formantu paska postępu.

*nUpper (nUpper)*<br/>
Odwołanie do liczby całkowitej odbierającej górną granicę formantu paska postępu.

### <a name="remarks"></a>Uwagi

Ta funkcja kopiuje wartości dolnej i górnej granicy do liczby całkowite, do których odwołuje się *odpowiednio nLower* i *nUpper.*

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

## <a name="cprogressctrlgetstate"></a><a name="getstate"></a>CProgressCtrl::GetState

Pobiera stan bieżącej kontroli paska postępu.

```
int GetState() const;
```

### <a name="return-value"></a>Wartość zwracana

Stan bieżącej kontroli paska postępu, która jest jedną z następujących wartości:

|Wartość|Stan|
|-----------|-----------|
|PBST_NORMAL|W toku|
|PBST_ERROR|Błąd|
|PBST_PAUSED|Wstrzymane|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PBM_GETSTATE,](/windows/win32/Controls/pbm-getstate) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_progressCtrl`zmienną , która jest używana do programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu pobiera stan bieżącej kontroli paska postępu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

## <a name="cprogressctrlgetstep"></a><a name="getstep"></a>CProgressCtrl::GetStep

Pobiera przyrost kroku dla paska postępu bieżącej kontroli paska postępu.

```
int GetStep() const;
```

### <a name="return-value"></a>Wartość zwracana

Przyrost kroku paska postępu.

### <a name="remarks"></a>Uwagi

Przyrost kroku jest kwotą, o którą wywołanie [CProgressCtrl::StepIt](#stepit) zwiększa bieżącą pozycję paska postępu.

Ta metoda wysyła komunikat [PBM_GETSTEP,](/windows/win32/Controls/pbm-getstep) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_progressCtrl`zmienną , która jest używana do programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu pobiera przyrost kroku bieżącej kontroli paska postępu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

## <a name="cprogressctrloffsetpos"></a><a name="offsetpos"></a>CProgressCtrl::OffsetPos

Przesuwa bieżącą pozycję formantu paska postępu o przyrost określony przez *nPos* i ponownie rysuje pasek, aby odzwierciedlić nową pozycję.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Kwota do góry pozycji.

### <a name="return-value"></a>Wartość zwracana

Poprzednia pozycja formantu paska postępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

## <a name="cprogressctrlsetbarcolor"></a><a name="setbarcolor"></a>CProgressCtrl::SetBarColor

Ustawia kolor paska wskaźnika postępu w bieżącej kontroli paska postępu.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*clrBar (clrBar)*|[w] Wartość [COLORREF](/windows/win32/gdi/colorref) określająca nowy kolor paska wskaźnika postępu. Określ CLR_DEFAULT, aby pasek postępu używał swojego domyślnego koloru.|

### <a name="return-value"></a>Wartość zwracana

Poprzedni kolor paska wskaźnika postępu, reprezentowany jako wartość [COLORREF,](/windows/win32/gdi/colorref) lub CLR_DEFAULT, jeśli kolor paska wskaźnika postępu jest kolorem domyślnym.

### <a name="remarks"></a>Uwagi

Metoda `SetBarColor` ustawia kolor paska postępu tylko wtedy, gdy [kompozycja](/windows/win32/Controls/visual-styles-overview) systemu Windows Vista nie jest obowiązuje.

Ta metoda wysyła komunikat [PBM_SETBARCOLOR,](/windows/win32/Controls/pbm-setbarcolor) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_progressCtrl`zmienną , która jest używana do programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu zmienia kolor paska postępu na czerwony, zielony, niebieski lub domyślny.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

## <a name="cprogressctrlsetbkcolor"></a><a name="setbkcolor"></a>CProgressCtrl::SetBkColor

Ustawia kolor tła paska postępu.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Parametry

*clrNowy*<br/>
Wartość COLORREF określająca nowy kolor tła. Określ CLR_DEFAULT wartość, aby użyć domyślnego koloru tła dla paska postępu.

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) wskazująca poprzedni kolor tła lub CLR_DEFAULT, jeśli kolor tła jest kolorem domyślnym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

## <a name="cprogressctrlsetmarquee"></a><a name="setmarquee"></a>CProgressCtrl::SetMarquee

Włącza lub wyłącza tryb ramki zaznaczenia dla bieżącej kontrolki paska postępu.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*fMarqueeMode (Mod)*|[w] PRAWDA, aby włączyć tryb ramki zaznaczenia, lub FALSE, aby wyłączyć tryb ramki zaznaczenia.|
|*nInterwal*|[w] Czas w milisekundach między aktualizacjami animacji ramki zaznaczenia.|

### <a name="return-value"></a>Wartość zwracana

Ta metoda zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Gdy tryb ramki zaznaczenia jest włączony, pasek postępu jest animowany i przewija się jak znak na ramce kinowej.

Ta metoda wysyła komunikat [PBM_SETMARQUEE,](/windows/win32/Controls/pbm-setmarquee) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_progressCtrl`zmienną , która jest używana do programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu rozpoczyna i zatrzymuje animację przewijania ramki zaznaczenia.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

## <a name="cprogressctrlsetpos"></a><a name="setpos"></a>CProgressCtrl::SetPos

Ustawia bieżącą pozycję formantu paska postępu określoną przez *nPos* i ponownie rysuje pasek, aby odzwierciedlić nową pozycję.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
Nowa pozycja kontrolki paska postępu.

### <a name="return-value"></a>Wartość zwracana

Poprzednia pozycja formantu paska postępu.

### <a name="remarks"></a>Uwagi

Położenie kontrolki paska postępu nie jest fizyczną lokalizacją na ekranie, ale jest między górnym i dolnym zakresem wskazanym w [SetRange](#setrange).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

## <a name="cprogressctrlsetrange"></a><a name="setrange"></a>CProgressCtrl::SetRange

Ustawia górne i dolne granice zakresu formantu paska postępu i ponownie rysuje pasek, aby odzwierciedlić nowe zakresy.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parametry

*nLower*<br/>
Określa dolną granicę zakresu (wartość domyślna to zero).

*nUpper (nUpper)*<br/>
Określa górną granicę zakresu (wartość domyślna to 100).

### <a name="remarks"></a>Uwagi

Funkcja `SetRange32` elementu członkowskiego ustawia zakres 32-bitowy dla kontroli postępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

## <a name="cprogressctrlsetstate"></a><a name="setstate"></a>CProgressCtrl::SetState

Ustawia stan bieżącej kontroli paska postępu.

```
int SetState(int iState);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iState*|[w] Stan, aby ustawić pasek postępu. Użyj jednej z następujących wartości:<br /><br /> - PBST_NORMAL - W toku<br />- PBST_ERROR - Błąd<br />- PBST_PAUSED - Wstrzymane|

### <a name="return-value"></a>Wartość zwracana

Poprzedni stan bieżącej kontroli paska postępu.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PBM_SETSTATE,](/windows/win32/Controls/pbm-setstate) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_progressCtrl`zmienną , która jest używana do programowego dostępu do formantu paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia stan bieżącego paska postępu formantu wstrzymane lub w toku.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

## <a name="cprogressctrlsetstep"></a><a name="setstep"></a>CProgressCtrl::SetStep

Określa przyrost kroku dla formantu paska postępu.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Parametry

*nStep (krok)*<br/>
Nowy przyrost krokowy.

### <a name="return-value"></a>Wartość zwracana

Przyrost poprzedniego kroku.

### <a name="remarks"></a>Uwagi

Przyrost kroku jest kwotą, o którą `CProgressCtrl::StepIt` wywołanie zwiększa bieżącą pozycję paska postępu.

Domyślny przyrost kroku wynosi 10.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

## <a name="cprogressctrlstepit"></a><a name="stepit"></a>CProgressCtrl::StepIt

Przesuwa bieżącą pozycję dla kontroli paska postępu o krok przyrost i ponownie rysuje pasek, aby odzwierciedlić nową pozycję.

```
int StepIt();
```

### <a name="return-value"></a>Wartość zwracana

Poprzednia pozycja formantu paska postępu.

### <a name="remarks"></a>Uwagi

Przyrost kroku jest ustawiany `CProgressCtrl::SetStep` przez funkcję elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
