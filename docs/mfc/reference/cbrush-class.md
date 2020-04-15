---
title: Klasa CBrush
ms.date: 11/04/2016
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
ms.openlocfilehash: 15132bb5497886638edfe431ae769dd446785df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352477"
---
# <a name="cbrush-class"></a>Klasa CBrush

Hermetyzuje pędzel interfejsu urządzenia graficznego systemu Windows (GDI).

## <a name="syntax"></a>Składnia

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|Konstruuje `CBrush` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Inicjuje pędzel ze stylem, kolorem i wzorkiem określonym w strukturze [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Inicjuje pędzel ze wzorem określonym przez mapę bitową niezależną od urządzenia (DIB).|
|[CBrush::CreateHatchbrush](#createhatchbrush)|Inicjuje pędzel z określonym kreskowanym wzorem i kolorem.|
|[CBrush::CreatePatternBrush](#createpatternbrush)|Inicjuje pędzel ze wzorem określonym przez mapę bitową.|
|[CBrush::CreateSolidBrush](#createsolidbrush)|Inicjuje pędzel o określonym jednolitym kolorze.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Tworzy pędzel, który jest domyślnym kolorem systemu.|
|[CBrush::FromHandle](#fromhandle)|Zwraca wskaźnik do `CBrush` obiektu po podaniu `HBRUSH` dojścia do obiektu systemu Windows.|
|[CBrush::GetLogBrush](#getlogbrush)|Pobiera [strukturę LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBrush::operator HBRUSH](#operator_hbrush)|Zwraca uchwyt systemu Windows `CBrush` dołączony do obiektu.|

## <a name="remarks"></a>Uwagi

Aby użyć `CBrush` obiektu, `CBrush` należy skonstruować obiekt `CDC` i przekazać go do dowolnej funkcji elementu członkowskiego, który wymaga pędzla.

Pędzle mogą być stałe, kreskowane lub wzorzyste.

Aby uzyskać `CBrush`więcej informacji na temat , zobacz [Obiekty graficzne](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cgdiobject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cbrushcbrush"></a><a name="cbrush"></a>CBrush::CBrush

Konstruuje `CBrush` obiekt.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*CrColor ( kolor)*<br/>
Określa kolor pierwszego planu pędzla jako kolor RGB. Jeśli pędzel jest kreskowany, parametr ten określa kolor kreskowania.

*Nindex*<br/>
Określa styl kreskowania pędzla. Może to być jedna z następujących wartości:

- HS_BDIAGONAL Kreskowanie w dół (od lewej do prawej) w 45 stopniach

- HS_CROSS Kreskowanie poziome i pionowe

- HS_DIAGCROSS Crosshatch w 45 stopniach

- HS_FDIAGONAL kreskowanie w górę (od lewej do prawej) w temperaturze 45 stopni

- HS_HORIZONTAL Kreskowanie poziome

- HS_VERTICAL Pionowy kreskowanie

*pBitmapa*<br/>
Wskazuje `CBitmap` obiekt określający mapę bitową, za pomocą której maluje pędzel.

### <a name="remarks"></a>Uwagi

`CBrush`ma cztery przeciążone konstruktory. Konstruktor bez argumentów konstruuje `CBrush` niezainicjowany obiekt, który musi zostać zainicjowany, zanim będzie można go użyć.

Jeśli konstruktora jest używany bez argumentów, `CBrush` należy zainicjować wynikowy obiekt za pomocą [createsolidbrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush)lub [CreateDIBPatternBrush](#createdibpatternbrush). Jeśli używasz jednego z konstruktorów, który przyjmuje argumenty, a następnie nie dalsze inicjowanie jest konieczne. Konstruktory z argumentami można zgłosić wyjątek, jeśli wystąpią błędy, podczas gdy konstruktor bez argumentów zawsze zakończy się pomyślnie.

Konstruktor z pojedynczym parametrem [COLORREF](/windows/win32/gdi/colorref) konstruuje pędzel bryłowy o określonym kolorze. Kolor określa wartość RGB i może być konstruowany z makra RGB w systemie WINDOWS. H.

Konstruktor z dwoma parametrami konstruuje pędzel kreskowania. Parametr *nIndex* określa indeks kreskowanego wzorca. Parametr *crColor* określa kolor.

Konstruktor z `CBitmap` parametrem konstruuje pędzla wzorzyste. Parametr identyfikuje mapę bitową. Zakłada się, że mapa bitowa została utworzona przy użyciu [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)lub [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). Minimalny rozmiar mapy bitowej, która ma być używana we wzorcu wypełnienia, to 8 pikseli na 8 pikseli.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

## <a name="cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>CBrush::CreateBrushIndirect

Inicjuje pędzel ze stylem, kolorem i wzorkiem określonym w strukturze [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parametry

*lpLogBrush*<br/>
Wskazuje na [strukturę LOGBRUSH,](/windows/win32/api/wingdi/ns-wingdi-logbrush) która zawiera informacje o pędzlu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać jako bieżący pędzel dla dowolnego kontekstu urządzenia.

Pędzel utworzony przy użyciu mapy bitowej monochromatyczne (1 płaszczyzna, 1 bit na piksel) jest rysowany przy użyciu bieżącego tekstu i kolorów tła. Piksele reprezentowane przez bit ustawiony na 0 zostaną narysowane przy bieżącym kolorze tekstu. Piksele reprezentowane przez bit ustawiony na 1 zostaną narysowane z bieżącym kolorem tła.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

## <a name="cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush

Inicjuje pędzel ze wzorem określonym przez mapę bitową niezależną od urządzenia (DIB).

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>Parametry

*hPackedDIB (100 hPackedDIB)*<br/>
Identyfikuje obiekt pamięci globalnej zawierający spakowaną mapę bitową niezależną od urządzenia (DIB).

*nUchód*<br/>
Określa, czy `bmiColors[]` pola struktury danych [BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) (część "pakowane DIB") zawierają jawne wartości RGB lub indeksy do aktualnie zrealizowanej palety logicznej. Parametr musi być jedną z następujących wartości:

- DIB_PAL_COLORS Tabela kolorów składa się z tablicy indeksów 16-bitowych.

- DIB_RGB_COLORS Tabela kolorów zawiera dosłowne wartości RGB.

*lpPackedDIB*<br/>
Wskazuje zapakowany DIB składający `BITMAPINFO` się ze struktury bezpośrednio po tablicy bajtów definiujących piksele mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać dla dowolnego kontekstu urządzenia, który obsługuje operacje rastrowe.

Obie wersje różnią się sposobem obsługi DIB:

- W pierwszej wersji, aby uzyskać dojście do `GlobalAlloc` DIB, należy wywołać funkcję systemu Windows, aby przydzielić blok pamięci globalnej, a następnie wypełnić pamięć zapakowanym DIB.

- W drugiej wersji nie jest konieczne `GlobalAlloc` wywołanie przydzielenia pamięci dla pakowane DIB.

Zapakowany DIB składa `BITMAPINFO` się ze struktury danych, po której następuje tablica bajtów definiujących piksele mapy bitowej. Mapy bitowe używane jako wzory wypełnienia powinny mieć 8 na 8 pikseli. Jeśli mapa bitowa jest większa, system Windows tworzy wzorzec wypełnienia przy użyciu tylko bitów odpowiadających pierwszym 8 wierszom i 8 kolumnom pikseli w lewym górnym rogu mapy bitowej.

Gdy aplikacja wybiera dwukolorowy pędzel wzoru DIB w kontekście monochromatycznym, system Windows ignoruje kolory określone w DIB i zamiast tego wyświetla pędzel wzoru przy użyciu bieżącego tekstu i kolorów tła kontekstu urządzenia. Piksele mapowane na pierwszy kolor (z przesunięciem 0 w tabeli kolorów DIB) dib są wyświetlane przy użyciu koloru tekstu. Piksele mapowane na drugi kolor (przy odsunięciu 1 w tabeli kolorów) są wyświetlane przy użyciu koloru tła.

Aby uzyskać informacje dotyczące korzystania z następujących funkcji systemu Windows, zobacz SDK systemu Windows:

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) (Ta funkcja jest dostępna tylko dla zgodności z aplikacjami napisanymi dla wersji `CreateDIBPatternBrushPt` systemu Windows wcześniejszych niż 3.0; użyj tej funkcji.)

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) (Ta funkcja powinna być używana dla aplikacji opartych na win32.)

- [GlobalAlloc (GlobalnyAllok)](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

## <a name="cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>CBrush::CreateHatchbrush

Inicjuje pędzel z określonym kreskowanym wzorem i kolorem.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa styl kreskowania pędzla. Może to być jedna z następujących wartości:

- HS_BDIAGONAL Kreskowanie w dół (od lewej do prawej) w 45 stopniach

- HS_CROSS Kreskowanie poziome i pionowe

- HS_DIAGCROSS Crosshatch w 45 stopniach

- HS_FDIAGONAL kreskowanie w górę (od lewej do prawej) w temperaturze 45 stopni

- HS_HORIZONTAL Kreskowanie poziome

- HS_VERTICAL Pionowy kreskowanie

*CrColor ( kolor)*<br/>
Określa kolor pierwszego planu pędzla jako kolor RGB (kolor kreskowań). Aby uzyskać więcej informacji, zobacz [COLORREF](/windows/win32/gdi/colorref) w programie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać jako bieżący pędzel dla dowolnego kontekstu urządzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

## <a name="cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>CBrush::CreatePatternBrush

Inicjuje pędzel ze wzorem określonym przez mapę bitową.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmapa*<br/>
Identyfikuje mapę bitową.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać dla dowolnego kontekstu urządzenia, który obsługuje operacje rastrowe. Mapa bitowa identyfikowana przez *pBitmap* jest zazwyczaj inicjowana przy użyciu [funkcji CBitmap::CreateBitmap,](../../mfc/reference/cbitmap-class.md#createbitmap) [CBitmap::CreateBitmapIndirect,](../../mfc/reference/cbitmap-class.md#createbitmapindirect) [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)lub [CBitmap::CreateCompatibleBitmap.](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)

Mapy bitowe używane jako wzory wypełnienia powinny mieć 8 na 8 pikseli. Jeśli mapa bitowa jest większa, system Windows użyje tylko bitów odpowiadających pierwszym 8 wierszom i kolumnom pikseli w lewym górnym rogu mapy bitowej.

Pędzel wzorka można usunąć bez wpływu na skojarzoną mapę bitową. Oznacza to, że mapa bitowa może służyć do tworzenia dowolnej liczby pędzli desenia.

Pędzel utworzony przy użyciu monochromalnej mapy bitowej (1 płaszczyzna kolorów, 1 bit na piksel) jest rysowany przy użyciu bieżącego tekstu i kolorów tła. Piksele reprezentowane przez bit ustawiony na 0 są rysowane z bieżącym kolorem tekstu. Piksele reprezentowane przez bit ustawiony na 1 są rysowane z bieżącym kolorem tła.

Aby uzyskać informacje dotyczące korzystania z [createpatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush), funkcji systemu Windows, zobacz Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

## <a name="cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>CBrush::CreateSolidBrush

Inicjuje pędzel o określonym jednolitym kolorze.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*CrColor ( kolor)*<br/>
Struktura [COLORREF](/windows/win32/gdi/colorref) określająca kolor pędzla. Kolor określa wartość RGB i może być konstruowany z makra RGB w systemie WINDOWS. H.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać jako bieżący pędzel dla dowolnego kontekstu urządzenia.

Po zakończeniu aplikacji przy użyciu `CreateSolidBrush`pędzla utworzonego przez program , należy wybrać szczotkę z kontekstu urządzenia.

### <a name="example"></a>Przykład

  Zobacz przykład [CBrush::CBrush](#cbrush).

## <a name="cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush

Inicjuje kolor pędzla.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks kolorów. Ta wartość odpowiada kolorowi używanemu do malowania jednego z 21 elementów okna. Zobacz [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) w zestawie Windows SDK, aby uzyskać listę wartości.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać jako bieżący pędzel dla dowolnego kontekstu urządzenia.

Po zakończeniu aplikacji przy użyciu `CreateSysColorBrush`pędzla utworzonego przez program , należy wybrać szczotkę z kontekstu urządzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

## <a name="cbrushfromhandle"></a><a name="fromhandle"></a>CBrush::FromHandle

Zwraca wskaźnik do `CBrush` obiektu po podaniu dojścia do obiektu [HBRUSH](#operator_hbrush) systemu Windows.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parametry

*hBrush (pędzel)*<br/>
HANDLE do pędzla GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CBrush` obiektu, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CBrush` obiekt nie jest jeszcze dołączony do `CBrush` uchwytu, tworzony i dołączany jest obiekt tymczasowy. Ten `CBrush` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynny w pętli zdarzeń. W tej chwili wszystkie tymczasowe obiekty graficzne są usuwane. Innymi słowy obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania komunikatu okna.

Aby uzyskać więcej informacji na temat używania obiektów [graficznych,](/windows/win32/gdi/graphic-objects) zobacz Obiekty graficzne w sdk systemu Windows.

### <a name="example"></a>Przykład

  Zobacz przykład [CBrush::CBrush](#cbrush).

## <a name="cbrushgetlogbrush"></a><a name="getlogbrush"></a>CBrush::GetLogBrush

Wywołanie tej funkcji elementu `LOGBRUSH` członkowskiego, aby pobrać strukturę.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parametry

*pLogBrush (pędzel)*<br/>
Wskazuje na [strukturę LOGBRUSH,](/windows/win32/api/wingdi/ns-wingdi-logbrush) która zawiera informacje o pędzlu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, a *pLogBrush* jest prawidłowym wskaźnikiem, zwracana wartość to liczba bajtów przechowywanych w buforze.

Jeśli funkcja powiedzie się, a *pLogBrush* jest NULL, zwracana wartość jest liczba bajtów wymaganych do przechowywania informacji funkcja będzie przechowywać w buforze.

Jeśli funkcja nie powiedzie się, zwracana wartość wynosi 0.

### <a name="remarks"></a>Uwagi

Struktura `LOGBRUSH` definiuje styl, kolor i wzór pędzla.

Na przykład `GetLogBrush` wywołanie, aby dopasować określony kolor lub wzór mapy bitowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

## <a name="cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>CBrush::operator HBRUSH

Użyj tego operatora, aby uzyskać dołączony uchwyt `CBrush` GDI systemu Windows obiektu.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, dojście do obiektu `CBrush` GDI systemu Windows reprezentowanego przez obiekt; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem odlewania, który obsługuje bezpośrednie wykorzystanie obiektu HBRUSH.

Aby uzyskać więcej informacji na temat używania obiektów [graficznych,](/windows/win32/gdi/graphic-objects) zobacz Obiekty graficzne w sdk systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)
