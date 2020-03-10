---
title: Klasa korzystanie CProgressCtrl
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
ms.openlocfilehash: 9d63a1113e521eb73c99c47b335eb7ab00ccd753
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866327"
---
# <a name="cprogressctrl-class"></a>Klasa korzystanie CProgressCtrl

Oferuje funkcje formantu typowego paska postępu systemu Windows.

## <a name="syntax"></a>Składnia

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Korzystanie CProgressCtrl:: Korzystanie CProgressCtrl](#cprogressctrl)|Konstruuje obiekt `CProgressCtrl`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Korzystanie CProgressCtrl:: Create](#create)|Tworzy kontrolkę pasek postępu i dołącza ją do obiektu `CProgressCtrl`.|
|[Korzystanie CProgressCtrl:: CreateEx](#createex)|Tworzy kontrolkę postępu z określonymi stylami rozszerzonymi systemu Windows i dołącza je do obiektu `CProgressCtrl`.|
|[Korzystanie CProgressCtrl:: GetBarColor](#getbarcolor)|Pobiera kolor paska wskaźnika postępu dla bieżącego formantu paska postępu.|
|[Korzystanie CProgressCtrl:: GetBkColor](#getbkcolor)|Pobiera kolor tła bieżącego paska postępu.|
|[Korzystanie CProgressCtrl:: GetPos](#getpos)|Pobiera bieżącą pozycję paska postępu.|
|[Korzystanie CProgressCtrl:: GetRange](#getrange)|Pobiera dolny i górny limit zakresu kontrolki paska postępu.|
|[Korzystanie CProgressCtrl:: GetState](#getstate)|Pobiera stan bieżącej kontrolki paska postępu.|
|[Korzystanie CProgressCtrl:: getstep](#getstep)|Pobiera przyrost kroków dla paska postępu bieżącej kontrolki paska postępu.|
|[Korzystanie CProgressCtrl:: OffsetPos](#offsetpos)|Przesuwa bieżącą pozycję kontrolki paska postępu o określony przyrost i ponownie rysuje pasek w celu odzwierciedlenia nowej pozycji.|
|[Korzystanie CProgressCtrl:: SetBarColor](#setbarcolor)|Ustawia kolor paska wskaźnika postępu w bieżącym formancie paska postępu.|
|[Korzystanie CProgressCtrl:: SetBkColor](#setbkcolor)|Ustawia kolor tła paska postępu.|
|[Korzystanie CProgressCtrl:: setneon](#setmarquee)|Włącza lub wyłącza tryb neonu dla bieżącej kontrolki paska postępu.|
|[Korzystanie CProgressCtrl:: SetPos](#setpos)|Ustawia bieżącą pozycję dla kontrolki pasek postępu i ponownie rysuje pasek w celu odzwierciedlenia nowego położenia.|
|[Korzystanie CProgressCtrl:: SetRange](#setrange)|Ustawia minimalną i maksymalną liczbę zakresów dla kontrolki paska postępu i ponownie rysuje pasek w celu odzwierciedlenia nowych zakresów.|
|[Korzystanie CProgressCtrl:: setstate](#setstate)|Ustawia stan bieżącej kontrolki paska postępu.|
|[Korzystanie CProgressCtrl:: SetStep](#setstep)|Określa przyrost kroków dla kontrolki paska postępu.|
|[Korzystanie CProgressCtrl:: StepIt](#stepit)|Przesuwa bieżącą pozycję kontrolki paska postępu o przyrost kroku (zobacz [SetStep](#setstep)) i ponownie rysuje pasek w celu odzwierciedlenia nowego położenia.|

## <a name="remarks"></a>Uwagi

Kontrolka paska postępu jest oknem, którego aplikacja może użyć do wskazania postępu długotrwałej operacji. Składa się prostokąt, który jest stopniowo wypełniany od lewej do prawej, z kolorem wyróżniania systemu jako postęp operacji.

Kontrolka paska postępu ma zakres i bieżące położenie. Zakres reprezentuje łączny czas trwania operacji, a bieżąca pozycja reprezentuje postęp aplikacji w kierunku ukończenia operacji. Procedura okna używa zakresu i bieżącego położenia, aby określić procent paska postępu, który ma zostać wypełniony kolorem wyróżnienia. Ponieważ zakres i bieżące wartości pozycji są wyrażane jako liczby całkowite ze znakami, możliwy zakres bieżących wartości pozycji to od-2 147 483 648 do 2 147 483 647 włącznie.

Aby uzyskać więcej informacji na temat używania `CProgressCtrl`, zobacz [Controls](../../mfc/controls-mfc.md) and [using korzystanie CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="cprogressctrl"></a>Korzystanie CProgressCtrl:: Korzystanie CProgressCtrl

Konstruuje obiekt `CProgressCtrl`.

```
CProgressCtrl();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu `CProgressCtrl` Wywołaj `CProgressCtrl::Create`, aby utworzyć kontrolkę pasek postępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

##  <a name="create"></a>Korzystanie CProgressCtrl:: Create

Tworzy kontrolkę pasek postępu i dołącza ją do obiektu `CProgressCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl kontrolki paska postępu. Zastosuj dowolną kombinację okna [stylesdescribed w Windows SDK](/windows/win32/api/winuser/nf-winuser-createwindoww) , oprócz następujących stylów kontrolki paska postępu, do kontrolki:

- PBS_VERTICAL wyświetla informacje o postępie pionowym, od góry do dołu. Bez tej flagi kontrolka paska postępu jest wyświetlana poziomo, od lewej do prawej.

- PBS_SMOOTH wyświetla stopniowe i gładkie wypełnianie w kontrolce pasek postępu. Bez tej flagi formant zostanie wypełniony blokami.

*cinania*<br/>
Określa rozmiar i położenie kontrolki paska postępu. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) [lub struktura.](/previous-versions/dd162897\(v=vs.85\)) Ponieważ kontrolka musi być oknem podrzędnym, określone współrzędne są względem obszaru klienckiego *pParentWnd*.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki pasek postępu, zazwyczaj `CDialog`. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki paska postępu.

### <a name="return-value"></a>Wartość zwrócona

Ma wartość TRUE, jeśli obiekt `CProgressCtrl` został pomyślnie utworzony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Należy skonstruować obiekt `CProgressCtrl` w dwóch krokach. Najpierw Wywołaj konstruktora, który tworzy obiekt `CProgressCtrl`, a następnie Wywołaj `Create`, który tworzy kontrolkę pasek postępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

##  <a name="createex"></a>Korzystanie CProgressCtrl:: CreateEx

Tworzy kontrolkę (okno podrzędne) i kojarzy ją z obiektem `CProgressCtrl`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Określa rozszerzony styl formantu, który jest tworzony. Aby zapoznać się z listą rozszerzonych stylów systemu Windows, zobacz *dwExStyle* parametru [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w Windows SDK.

*dwStyle*<br/>
Określa styl kontrolki paska postępu. Zastosuj dowolną kombinację stylów okna opisaną w [oknie Moje okna](/windows/win32/api/winuser/nf-winuser-createwindoww) w Windows SDK.

*cinania*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator okna podrzędnego kontrolki.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [tworzyć](#create) , aby zastosować rozszerzone style systemu Windows, określone przez **WS_EX_** prekroju stylu systemu Windows.

##  <a name="getbarcolor"></a>Korzystanie CProgressCtrl:: GetBarColor

Pobiera kolor paska wskaźnika postępu dla bieżącego formantu paska postępu.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Wartość zwrócona

Kolor bieżącego paska postępu reprezentowany jako wartość [COLORREF](/windows/win32/gdi/colorref) lub CLR_DEFAULT, jeśli kolor paska wskaźnika postępu jest kolorem domyślnym.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor) , który jest opisany w Windows SDK.

##  <a name="getbkcolor"></a>Korzystanie CProgressCtrl:: GetBkColor

Pobiera kolor tła bieżącego paska postępu.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Wartość zwrócona

Kolor tła bieżącego paska postępu reprezentowany jako wartość [COLORREF](/windows/win32/gdi/colorref) .

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor) , który jest opisany w Windows SDK.

##  <a name="getpos"></a>Korzystanie CProgressCtrl:: GetPos

Pobiera bieżącą pozycję paska postępu.

```
int GetPos();
```

### <a name="return-value"></a>Wartość zwrócona

Pozycja kontrolki paska postępu.

### <a name="remarks"></a>Uwagi

Pozycja kontrolki paska postępu nie jest fizyczną lokalizacją na ekranie, ale nie jest między górnym i dolnym zakresem wskazanym w [SetRange](#setrange).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

##  <a name="getrange"></a>Korzystanie CProgressCtrl:: GetRange

Pobiera bieżące dolne i górne limity lub zakres kontrolki paska postępu.

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Parametry

*nLower*<br/>
Odwołanie do liczby całkowitej otrzymującej dolny limit kontrolki paska postępu.

*nUpper*<br/>
Odwołanie do liczby całkowitej otrzymującej górny limit kontrolki paska postępu.

### <a name="remarks"></a>Uwagi

Ta funkcja kopiuje wartości dolnego i górnego limitu do liczb całkowitych przywoływanych odpowiednio przez *nLower* i *nUpper*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

##  <a name="getstate"></a>Korzystanie CProgressCtrl:: GetState

Pobiera stan bieżącej kontrolki paska postępu.

```
int GetState() const;
```

### <a name="return-value"></a>Wartość zwrócona

Stan bieżącej kontrolki paska postępu, która jest jedną z następujących wartości:

|Wartość|Stan|
|-----------|-----------|
|PBST_NORMAL|W toku|
|PBST_ERROR|Błąd|
|PBST_PAUSED|Wstrzymane|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PBM_GETSTATE](/windows/win32/Controls/pbm-getstate) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_progressCtrl`, która jest używana do programistycznego dostępu do kontrolki paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu pobiera stan bieżącej kontrolki paska postępu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

##  <a name="getstep"></a>Korzystanie CProgressCtrl:: getstep

Pobiera przyrost kroków dla paska postępu bieżącej kontrolki paska postępu.

```
int GetStep() const;
```

### <a name="return-value"></a>Wartość zwrócona

Przyrost kroku paska postępu.

### <a name="remarks"></a>Uwagi

Przyrost kroków to wielkość, przez jaką wywołanie [Korzystanie CProgressCtrl:: StepIt](#stepit) zwiększa bieżącą pozycję paska postępu.

Ta metoda wysyła komunikat [PBM_GETSTEP](/windows/win32/Controls/pbm-getstep) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_progressCtrl`, która jest używana do programistycznego dostępu do kontrolki paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu pobiera przyrostowy krok bieżącej kontrolki paska postępu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

##  <a name="offsetpos"></a>Korzystanie CProgressCtrl:: OffsetPos

Przesuwa bieżącą pozycję kontrolki paska postępu o przyrost określony przez *nPos* i ponownie rysuje pasek w celu odzwierciedlenia nowego położenia.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Kwota do naliczania pozycji.

### <a name="return-value"></a>Wartość zwrócona

Poprzednia pozycja kontrolki paska postępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

##  <a name="setbarcolor"></a>Korzystanie CProgressCtrl:: SetBarColor

Ustawia kolor paska wskaźnika postępu w bieżącym formancie paska postępu.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*clrBar*|podczas Wartość [COLORREF](/windows/win32/gdi/colorref) , która określa nowy kolor paska wskaźnika postępu. Określ CLR_DEFAULT, aby pasek postępu używał jego domyślnego koloru.|

### <a name="return-value"></a>Wartość zwrócona

Poprzedni kolor paska wskaźnika postępu, reprezentowany jako wartość [COLORREF](/windows/win32/gdi/colorref) , lub CLR_DEFAULT, jeśli kolor paska wskaźnika postępu jest kolorem domyślnym.

### <a name="remarks"></a>Uwagi

Metoda `SetBarColor` ustawia kolor paska postępu tylko wtedy, gdy [motyw](/windows/win32/Controls/visual-styles-overview) systemu Windows Vista nie jest uwzględniony.

Ta metoda wysyła komunikat [PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_progressCtrl`, która jest używana do programistycznego dostępu do kontrolki paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu zmienia kolor paska postępu na czerwony, zielony, niebieski lub domyślny.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

##  <a name="setbkcolor"></a>Korzystanie CProgressCtrl:: SetBkColor

Ustawia kolor tła paska postępu.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Parametry

*clrNew*<br/>
Wartość COLORREF, która określa nowy kolor tła. Określ wartość CLR_DEFAULT, aby użyć domyślnego koloru tła paska postępu.

### <a name="return-value"></a>Wartość zwrócona

Wartość [COLORREF](/windows/win32/gdi/colorref) wskazująca poprzedni kolor tła lub CLR_DEFAULT, jeśli kolor tła jest kolorem domyślnym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

##  <a name="setmarquee"></a>Korzystanie CProgressCtrl:: setneon

Włącza lub wyłącza tryb neonu dla bieżącej kontrolki paska postępu.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*fMarqueeMode*|podczas PRAWDA, aby włączyć tryb neonu, lub FALSE, aby wyłączyć tryb neonu.|
|*Ninterwał*|podczas Czas (w milisekundach) między aktualizacjami animacji neonu.|

### <a name="return-value"></a>Wartość zwrócona

Ta metoda zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Gdy tryb Neon jest włączony, pasek postępu jest animowany i przewija się jak znak na neonie.

Ta metoda wysyła komunikat [PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_progressCtrl`, która jest używana do programistycznego dostępu do kontrolki paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu jest uruchamiany i zatrzyma animację przewijania neonu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

##  <a name="setpos"></a>Korzystanie CProgressCtrl:: SetPos

Ustawia bieżącą pozycję kontrolki pasek postępu określony przez *nPos* i ponownie rysuje pasek w celu odzwierciedlenia nowego położenia.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Nowa pozycja kontrolki paska postępu.

### <a name="return-value"></a>Wartość zwrócona

Poprzednia pozycja kontrolki paska postępu.

### <a name="remarks"></a>Uwagi

Pozycja kontrolki paska postępu nie jest fizyczną lokalizacją na ekranie, ale nie jest między górnym i dolnym zakresem wskazanym w [SetRange](#setrange).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

##  <a name="setrange"></a>Korzystanie CProgressCtrl:: SetRange

Ustawia górny i dolny limit zakresu formantu paska postępu i ponownie rysuje pasek w celu odzwierciedlenia nowych zakresów.

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
Określa dolny limit zakresu (wartość domyślna to zero).

*nUpper*<br/>
Określa górny limit zakresu (wartość domyślna to 100).

### <a name="remarks"></a>Uwagi

Funkcja członkowska `SetRange32` ustawia zakres 32-bitowy dla kontrolki postępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

##  <a name="setstate"></a>Korzystanie CProgressCtrl:: setstate

Ustawia stan bieżącej kontrolki paska postępu.

```
int SetState(int iState);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*IState*|podczas Stan, w którym ma zostać ustawiony pasek postępu. Użyj jednej z następujących wartości:<br /><br /> -PBST_NORMAL w toku<br />-PBST_ERROR-błąd<br />-PBST_PAUSED-wstrzymany|

### <a name="return-value"></a>Wartość zwrócona

Poprzedni stan bieżącej kontrolki paska postępu.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [PBM_SETSTATE](/windows/win32/Controls/pbm-setstate) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_progressCtrl`, która jest używana do programistycznego dostępu do kontrolki paska postępu. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia stan bieżącej kontrolki paska postępu do wstrzymania lub w toku.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

##  <a name="setstep"></a>Korzystanie CProgressCtrl:: SetStep

Określa przyrost kroków dla kontrolki paska postępu.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Parametry

*nStep*<br/>
Nowy przyrost kroku.

### <a name="return-value"></a>Wartość zwrócona

Poprzedni krok przyrostowy.

### <a name="remarks"></a>Uwagi

Przyrost kroków to wielkość, o jaką wywołanie `CProgressCtrl::StepIt` zwiększa bieżącą pozycję paska postępu.

Domyślny przyrost kroków to 10.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

##  <a name="stepit"></a>Korzystanie CProgressCtrl:: StepIt

Przesuwa bieżącą pozycję kontrolki paska postępu przez krok przyrostowy i ponownie rysuje pasek w celu odzwierciedlenia nowej pozycji.

```
int StepIt();
```

### <a name="return-value"></a>Wartość zwrócona

Poprzednia pozycja kontrolki paska postępu.

### <a name="remarks"></a>Uwagi

Przyrost kroku jest ustawiany przez funkcję członkowską `CProgressCtrl::SetStep`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykład CMNCTRL2 MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
