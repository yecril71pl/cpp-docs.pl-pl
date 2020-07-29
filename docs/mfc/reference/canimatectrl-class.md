---
title: Klasa korzystanie CAnimateCtrl
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
ms.openlocfilehash: 651b5775886374f3fcc95ab6b2cb3d892d9d77e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183386"
---
# <a name="canimatectrl-class"></a>Klasa korzystanie CAnimateCtrl

Oferuje funkcje formantu typowej animacji systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Korzystanie CAnimateCtrl:: Korzystanie CAnimateCtrl](#canimatectrl)|Konstruuje `CAnimateCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Korzystanie CAnimateCtrl:: Close](#close)|Zamyka klip AVI.|
|[Korzystanie CAnimateCtrl:: Create](#create)|Tworzy kontrolkę animacji i dołącza ją do `CAnimateCtrl` obiektu.|
|[Korzystanie CAnimateCtrl:: CreateEx](#createex)|Tworzy formant animacji z określonymi stylami rozszerzonymi systemu Windows i dołącza go do `CAnimateCtrl` obiektu.|
|[Korzystanie CAnimateCtrl:: isPlay](#isplaying)|Wskazuje, czy jest odtwarzany klip audio-wideo z przeplotem (AVI).|
|[Korzystanie CAnimateCtrl:: Open](#open)|Otwiera klip AVI z pliku lub zasobu i wyświetla pierwszą ramkę.|
|[Korzystanie CAnimateCtrl::P](#play)|Odtwarza klip AVI bez dźwięku.|
|[Korzystanie CAnimateCtrl:: Seek](#seek)|Wyświetla wybraną pojedynczą ramkę klipu AVI.|
|[Korzystanie CAnimateCtrl:: Stop](#stop)|Kończy odtwarzanie klipu AVI.|

## <a name="remarks"></a>Uwagi

Ten formant (i w związku z tym `CAnimateCtrl` Klasa) jest dostępny tylko dla programów uruchomionych w systemach windows 95, windows 98 i Windows NT w wersji 3,51 i nowszych.

Kontrolka animacji to prostokątne okno, które wyświetla klip w formacie AVI (Audio Video Interleaved) — standardowy format wideo/audio systemu Windows. Klip AVI to seria klatek mapy bitowej, takich jak film.

Kontrolki animacji mogą odtwarzać tylko proste klipy AVI. W przypadku klipów, które mają być odtwarzane przez kontrolkę animacji, muszą spełniać następujące wymagania:

- Musi istnieć dokładnie jeden strumień wideo i musi on zawierać co najmniej jedną ramkę.

- Może istnieć co najwyżej dwa strumienie w pliku (zazwyczaj jest to inny strumień, jeśli jest obecny, to strumień audio, chociaż formant animacji ignoruje informacje o dźwięku).

- Klip musi być nieskompresowany lub skompresowany za pomocą kompresji RLE8.

- W strumieniu wideo nie są dozwolone żadne zmiany palety.

Można dodać klip AVI do aplikacji jako zasób AVI lub dołączyć do aplikacji jako oddzielny plik AVI.

Ponieważ wątek kontynuuje wykonywanie podczas wyświetlania klipu AVI, jednym typowym zastosowaniem formantu animacji jest wskazanie działania systemu podczas długotrwałej operacji. Na przykład okno dialogowe Znajdowanie w Eksploratorze plików zawiera przesuwaną szklaną lupę jako system wyszukiwania pliku.

Jeśli utworzysz `CAnimateCtrl` obiekt w oknie dialogowym lub z poziomu zasobu okna dialogowego przy użyciu edytora okien dialogowych, zostanie on automatycznie zniszczony, gdy użytkownik zamknie okno dialogowe.

Jeśli utworzysz `CAnimateCtrl` obiekt w oknie, może być konieczne jego zniszczenie. Jeśli utworzysz `CAnimateCtrl` obiekt na stosie, zostanie on zniszczony automatycznie. Jeśli obiekt jest tworzony `CAnimateCtrl` na stercie przy użyciu **`new`** funkcji, należy wywołać **`delete`** obiekt, aby zniszczyć go. Jeśli tworzysz nową klasę z `CAnimateCtrl` i przydzielę pamięć w tej klasie, Zastąp `CAnimateCtrl` destruktor, aby usunąć alokacje.

Aby uzyskać więcej informacji na temat korzystania z programu `CAnimateCtrl` , zobacz [kontrolki](../../mfc/controls-mfc.md) i [Używanie korzystanie CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>Korzystanie CAnimateCtrl:: Korzystanie CAnimateCtrl

Konstruuje `CAnimateCtrl` obiekt.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Uwagi

Aby można było wykonywać inne operacje na tworzonym obiekcie, należy wywołać funkcję [Utwórz](#create) element członkowski.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>Korzystanie CAnimateCtrl:: Close

Zamyka klip AVI, który został wcześniej otwarty w kontrolce animacji (jeśli istnieje) i usuwa go z pamięci.

```
BOOL Close();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CAnimateCtrl:: Korzystanie CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreate"></a><a name="create"></a>Korzystanie CAnimateCtrl:: Create

Tworzy kontrolkę animacji i dołącza ją do `CAnimateCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl kontrolki animacji. Zastosuj dowolną kombinację stylów systemu Windows opisanych w poniższej sekcji uwagi i style kontrolek animacji opisane we [stylach kontrolki](/windows/win32/Controls/animation-control-styles) animacji w Windows SDK.

*cinania*<br/>
Określa położenie i rozmiar kontrolki animacji. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) [lub struktura.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki animacji, zazwyczaj a `CDialog` . Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki animacji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Tworzysz `CAnimateCtrl` dwa kroki. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create` , który tworzy formant animacji i dołącza go do `CAnimateCtrl` obiektu.

Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki animacji.

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

Jeśli chcesz użyć rozszerzonych stylów systemu Windows z kontrolką animacji, wywołaj [CreateEx](#createex) zamiast `Create` .

Oprócz stylów okna wymienionych powyżej, można zastosować jeden lub więcej stylów kontrolki animacji do kontrolki animacji. Zobacz Windows SDK, aby uzyskać więcej informacji na temat [stylów kontrolek animacji](/windows/win32/Controls/animation-control-styles).

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CAnimateCtrl:: Korzystanie CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreateex"></a><a name="createex"></a>Korzystanie CAnimateCtrl:: CreateEx

Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CAnimateCtrl` obiektem.

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
Określa styl kontrolki animacji. Zastosuj dowolną kombinację stylów okna i animacji, które opisano w [stylach kontrolek animacji](/windows/win32/Controls/animation-control-styles) w Windows SDK.

*cinania*<br/>
Odwołanie do struktury [Rect](/windows/win32/api/windef/ns-windef-rect) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator okna podrzędnego kontrolki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [tworzenia](#create) , aby zastosować rozszerzone style systemu Windows, które są określone przez **WS_EX_** przedniej stylu rozszerzonego systemu Windows.

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>Korzystanie CAnimateCtrl:: isPlay

Wskazuje, czy jest odtwarzany klip audio-wideo z przeplotem (AVI).

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli jest odtwarzany klip AVI; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying) , który jest opisany w Windows SDK.

## <a name="canimatectrlopen"></a><a name="open"></a>Korzystanie CAnimateCtrl:: Open

Wywołaj tę funkcję, aby otworzyć klip AVI i wyświetlić jego pierwszą ramkę.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
`CString`Obiekt lub wskaźnik do ciągu zakończonego wartością null, który zawiera nazwę pliku AVI lub nazwę zasobu AVI. Jeśli ten parametr ma wartość NULL, system zamknie klipu AVI, który został poprzednio otwarty dla formantu animacji, jeśli istnieje.

*nID*<br/>
Identyfikator zasobu AVI. Jeśli ten parametr ma wartość NULL, system zamknie klipu AVI, który został poprzednio otwarty dla formantu animacji, jeśli istnieje.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Zasób AVI jest ładowany z modułu, który utworzył kontrolkę animacji.

`Open`nie obsługuje dźwięku w klipie AVI; można otwierać tylko ciche klipy AVI.

Jeśli kontrolka animacji ma `ACS_AUTOPLAY` styl, kontrolka animacji automatycznie rozpocznie odtwarzanie klipu natychmiast po jego otwarciu. Odtwarzanie klipu w tle będzie kontynuowane, gdy wątek kontynuuje wykonywanie. Po zakończeniu odtwarzania klipu zostanie on automatycznie powtórzony.

Jeśli kontrolka animacji ma `ACS_CENTER` styl, klip AVI zostanie wyśrodkowany w kontrolce, a rozmiar kontrolki nie ulegnie zmianie. Jeśli kontrolka animacji nie ma `ACS_CENTER` stylu, rozmiar kontrolki zostanie zmieniony, gdy klip AVI zostanie otwarty na rozmiar obrazów w klipie AVI. Pozycja lewego górnego rogu kontrolki nie ulegnie zmianie, tylko rozmiar kontrolki.

Jeśli kontrolka animacji ma `ACS_TRANSPARENT` styl, pierwsza ramka zostanie narysowana przy użyciu przezroczystego tła, a nie koloru tła określonego w klipie animacji.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CAnimateCtrl:: Korzystanie CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlplay"></a><a name="play"></a>Korzystanie CAnimateCtrl::P

Wywołaj tę funkcję, aby odtworzyć klip AVI w kontrolce animacji.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Parametry

*NZE*<br/>
Indeks (liczony od zera) ramki, w której rozpoczyna się odtwarzanie. Wartość musi być mniejsza niż 65 536. Wartość 0 oznacza początek pierwszej ramki w klipie AVI.

*nAby*<br/>
Indeks (liczony od zera) ramki, w której nastąpi zakończenie odtwarzania. Wartość musi być mniejsza niż 65 536. Wartość-1 oznacza koniec ostatniej ramki w klipie AVI.

*nRep*<br/>
Liczba powtórzeń wycinka AVI. Wartość-1 oznacza powtarzanie pliku w nieskończoność.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Kontrolka animacji będzie odtwarzać klip w tle, gdy wątek kontynuuje wykonywanie. Jeśli kontrolka animacji ma `ACS_TRANSPARENT` styl, klip AVI zostanie odtworzony przy użyciu przezroczystego tła, a nie koloru tła określonego w klipie animacji.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CAnimateCtrl:: Korzystanie CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlseek"></a><a name="seek"></a>Korzystanie CAnimateCtrl:: Seek

Wywołaj tę funkcję, aby statycznie wyświetlić pojedynczą ramkę klipu AVI.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Parametry

*nAby*<br/>
Indeks (liczony od zera) ramki do wyświetlenia. Wartość musi być mniejsza niż 65 536. Wartość 0 oznacza wyświetlenie pierwszej ramki w klipie AVI. Wartość-1 oznacza wyświetlenie ostatniej ramki w klipie AVI.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Jeśli kontrolka animacji ma `ACS_TRANSPARENT` styl, klip AVI zostanie narysowany przy użyciu przezroczystego tła, a nie koloru tła określonego w klipie animacji.

### <a name="example"></a>Przykład

Zobacz przykład dla [Korzystanie CAnimateCtrl:: Korzystanie CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlstop"></a><a name="stop"></a>Korzystanie CAnimateCtrl:: Stop

Wywołaj tę funkcję, aby zatrzymać odtwarzanie klipu AVI w kontrolce animacji.

```
BOOL Stop();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CAnimateCtrl:: Korzystanie CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Korzystanie CAnimateCtrl:: Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
