---
title: Klasa CAnimateCtrl
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: fcee569659d732c26e274c8ca189042a16f13557
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371064"
---
# <a name="canimatectrl-class"></a>Klasa CAnimateCtrl

Udostępnia funkcje kontroli animacji wspólnego systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Konstruuje `CAnimateCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimateCtrl::Zamknij](#close)|Zamyka klip AVI.|
|[CAnimateCtrl::Utwórz](#create)|Tworzy formant animacji i `CAnimateCtrl` dołącza go do obiektu.|
|[CAnimateCtrl::CreateEx](#createex)|Tworzy formant animacji z określonymi stylami rozszerzonymi systemu Windows i dołącza go do `CAnimateCtrl` obiektu.|
|[CAnimateCtrl::IsPlaying](#isplaying)|Wskazuje, czy odtwarzany jest klip audio-wideo z przeplotem (AVI).|
|[CAnimateCtrl::Otwórz](#open)|Otwiera klip AVI z pliku lub zasobu i wyświetla pierwszą klatkę.|
|[CAnimateCtrl::Play](#play)|Odtwarza klip AVI bez dźwięku.|
|[CAnimateCtrl::Szukaj](#seek)|Wyświetla wybraną pojedynczą klatkę klipu AVI.|
|[CAnimateCtrl::Zatrzymaj](#stop)|Przestaje odtwarzać klip AVI.|

## <a name="remarks"></a>Uwagi

Ten formant (i `CAnimateCtrl` dlatego klasa) jest dostępny tylko dla programów działających w systemach Windows 95, Windows 98 i Windows NT w wersji 3.51 lub nowszej.

Kontrolka animacji to prostokątne okno, które wyświetla klip w formacie AVI (Audio Video Interleaved) — standardowym formacie wideo/audio systemu Windows. Klip AVI to seria klatek bitmapowych, takich jak film.

Kontrolki animacji mogą odtwarzać tylko proste klipy AVI. W szczególności klipy, które mają być odtwarzane przez formant animacji, muszą spełniać następujące wymagania:

- Musi istnieć dokładnie jeden strumień wideo i musi mieć co najmniej jedną klatkę.

- Może istnieć co najwyżej dwa strumienie w pliku (zazwyczaj inny strumień, jeśli jest obecny, jest strumieniem audio, chociaż formant animacji ignoruje informacje audio).

- Klips musi być nieskompresowany lub skompresowany za pomocą kompresji RLE8.

- W strumieniu wideo nie są dozwolone żadne zmiany palety.

Klip AVI można dodać do aplikacji jako zasób AVI lub może on towarzyszyć aplikacji jako osobnemu plikowi AVI.

Ponieważ wątek kontynuuje wykonywanie podczas wyświetlania klipu AVI, jednym z typowych zastosowań formantu animacji jest wskazanie aktywności systemu podczas długiej operacji. Na przykład w oknie dialogowym Znajdowanie Eksploratora plików jest wyświetlana ruchoma lupa podczas wyszukiwania pliku przez system.

Jeśli obiekt `CAnimateCtrl` zostanie utworzony w oknie dialogowym lub z zasobu okna dialogowego za pomocą edytora dialogów, zostanie on automatycznie zniszczony po zamknięciu okna dialogowego przez użytkownika.

Jeśli utworzysz `CAnimateCtrl` obiekt w oknie, może być konieczne jego zniszczenie. Jeśli utworzysz `CAnimateCtrl` obiekt na stosie, zostanie on automatycznie zniszczony. Jeśli `CAnimateCtrl` obiekt zostanie utworzony na stosie przy użyciu **nowej** funkcji, należy **wywołać delete** na obiekcie, aby go zniszczyć. Jeśli wyprowadzisz nową klasę `CAnimateCtrl` z tej klasy i przydzielisz dowolną pamięć, należy zastąpić `CAnimateCtrl` destruktora w celu usunięcia alokacji.

Aby uzyskać więcej `CAnimateCtrl`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>CAnimateCtrl::CAnimateCtrl

Konstruuje `CAnimateCtrl` obiekt.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Uwagi

Należy wywołać create funkcji [elementu](#create) członkowskiego, zanim będzie można wykonać inne operacje na utworzonym obiekcie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>CAnimateCtrl::Zamknij

Zamyka klip AVI, który został wcześniej otwarty w formancie animacji (jeśli istnieje) i usuwa go z pamięci.

```
BOOL Close();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl::Utwórz

Tworzy formant animacji i `CAnimateCtrl` dołącza go do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl formantu animacji. Zastosuj dowolną kombinację stylów systemu Windows opisanych w sekcji Uwagi poniżej i stylów formantów animacji opisanych w [stylach sterowania animacją](/windows/win32/Controls/animation-control-styles) w zestaw windows SDK.

*Rect*<br/>
Określa położenie i rozmiar formantu animacji. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Określa okno nadrzędne formantu animacji, zwykle `CDialog`. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu animacji.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Konstruujesz `CAnimateCtrl` w dwóch krokach. Najpierw wywołaj konstruktora, `Create`a następnie wywołaj , co `CAnimateCtrl` tworzy formant animacji i dołącza go do obiektu.

Zastosuj następujące [style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) do formantu animacji.

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

Jeśli chcesz używać rozszerzonych stylów okien z formantem `Create`animacji, należy wywołać [createex](#createex) zamiast .

Oprócz stylów okien wymienionych powyżej można zastosować jeden lub więcej stylów formantu animacji do formantu animacji. Zobacz sdk systemu Windows, aby uzyskać więcej informacji na temat [stylów sterowania animacją](/windows/win32/Controls/animation-control-styles).

### <a name="example"></a>Przykład

  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreateex"></a><a name="createex"></a>CAnimateCtrl::CreateEx

Tworzy formant (okno podrzędne) i `CAnimateCtrl` kojarzy go z obiektem.

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
Określa styl formantu animacji. Zastosuj dowolną kombinację stylów sterowania okna i animacji opisanych w [stylach sterowania animacją](/windows/win32/Controls/animation-control-styles) w zestaw windows SDK.

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

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl::IsPlaying

Wskazuje, czy odtwarzany jest klip audio-wideo z przeplotem (AVI).

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli odtwarzany jest klip AVI; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [ACM_ISPLAYING,](/windows/win32/Controls/acm-isplaying) który jest opisany w windows SDK.

## <a name="canimatectrlopen"></a><a name="open"></a>CAnimateCtrl::Otwórz

Wywołanie tej funkcji, aby otworzyć klip AVI i wyświetlić jego pierwszą klatkę.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Obiekt `CString` lub wskaźnik do ciągu zakończonego z wartością null, który zawiera nazwę pliku AVI lub nazwę zasobu AVI. Jeśli ten parametr ma wartość NULL, system zamyka klip AVI, który został wcześniej otwarty dla formantu animacji, jeśli istnieje.

*Nid*<br/>
Identyfikator zasobu AVI. Jeśli ten parametr ma wartość NULL, system zamyka klip AVI, który został wcześniej otwarty dla formantu animacji, jeśli istnieje.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Zasób AVI jest ładowany z modułu, który utworzył formant animacji.

`Open`nie obsługuje dźwięku w klipie AVI; można otwierać tylko ciche klipy AVI.

Jeśli formant animacji ma `ACS_AUTOPLAY` styl, formant animacji automatycznie rozpocznie odtwarzanie klipu natychmiast po jego otwarciu. Będzie nadal odtwarzać klip w tle, podczas gdy wątek będzie kontynuował wykonywanie. Po zakończeniu odtwarzania klipu zostanie on automatycznie powtórzony.

Jeśli formant animacji ma `ACS_CENTER` styl, klip AVI zostanie wyśrodkowany w formancie, a rozmiar formantu nie ulegnie zmianie. Jeśli formant animacji `ACS_CENTER` nie ma stylu, formant zostanie zmieniony po otwarciu klipu AVI do rozmiaru obrazów w klipie AVI. Położenie lewego górnego rogu formantu nie ulegnie zmianie, tylko rozmiar formantu.

Jeśli formant animacji ma `ACS_TRANSPARENT` styl, pierwsza klatka zostanie narysowana przy użyciu przezroczystego tła, a nie koloru tła określonego w klipie animacji.

### <a name="example"></a>Przykład

  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlplay"></a><a name="play"></a>CAnimateCtrl::Play

Wywołanie tej funkcji, aby odtworzyć klip AVI w formancie animacji.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Parametry

*nZ*<br/>
Indeks zerowy ramki, w której rozpoczyna się odtwarzanie. Wartość musi być mniejsza niż 65 536. Wartość 0 oznacza rozpocząć się od pierwszej klatki w klipie AVI.

*Nto*<br/>
Indeks zerowy ramki, w której kończy się odtwarzanie. Wartość musi być mniejsza niż 65 536. Wartość - 1 oznacza koniec z ostatnią klatką w klipie AVI.

*nRep (wychowaw)*<br/>
Ile razy można odtworzyć klip AVI. Wartość - 1 oznacza powtarzanie pliku przez czas nieokreślony.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Formant animacji będzie odtwarzać klip w tle, podczas gdy wątek kontynuuje wykonywanie. Jeśli formant `ACS_TRANSPARENT` animacji ma styl, klip AVI będzie odtwarzany przy użyciu przezroczystego tła, a nie koloru tła określonego w klipie animacji.

### <a name="example"></a>Przykład

  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl::Szukaj

Wywołanie tej funkcji, aby statycznie wyświetlić jedną klatkę klipu AVI.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Parametry

*Nto*<br/>
Indeks ramki od zera do wyświetlenia. Wartość musi być mniejsza niż 65 536. Wartość 0 oznacza wyświetlanie pierwszej klatki w klipie AVI. Wartość -1 oznacza wyświetlanie ostatniej klatki w klipie AVI.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Jeśli formant `ACS_TRANSPARENT` animacji ma styl, klip AVI zostanie narysowany przy użyciu przezroczystego tła, a nie koloru tła określonego w klipie animacji.

### <a name="example"></a>Przykład

Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlstop"></a><a name="stop"></a>CAnimateCtrl::Zatrzymaj

Wywołanie tej funkcji, aby zatrzymać odtwarzanie klipu AVI w formancie animacji.

```
BOOL Stop();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Utwórz](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
