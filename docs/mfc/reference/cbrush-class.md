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
ms.openlocfilehash: a99d8c8022d23f627320b66c3f376be803c9c839
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420541"
---
# <a name="cbrush-class"></a>Klasa CBrush

Hermetyzuje pędzel interfejsu urządzenia graficznego (GDI) systemu Windows.

## <a name="syntax"></a>Składnia

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CBrush:: CBrush](#cbrush)|Konstruuje obiekt `CBrush`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CBrush:: CreateBrushIndirect](#createbrushindirect)|Inicjuje pędzel z stylem, kolorem i wzorkiem określonym w strukturze [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) .|
|[CBrush:: CreateDIBPatternBrush](#createdibpatternbrush)|Inicjuje pędzel ze wzorcem określonym przez niezależną od urządzenia mapę bitową (DIB).|
|[CBrush:: CreateHatchBrush](#createhatchbrush)|Inicjuje pędzel z określonym wzorcem i kolorem.|
|[CBrush:: CreatePatternBrush](#createpatternbrush)|Inicjuje pędzel ze wzorcem określonym przez mapę bitową.|
|[CBrush:: CreateSolidBrush](#createsolidbrush)|Inicjuje pędzel o określonym kolorze kryjącym.|
|[CBrush:: CreateSysColorBrush](#createsyscolorbrush)|Tworzy Pędzel, który jest domyślnym kolorem systemu.|
|[CBrush:: FromHandle](#fromhandle)|Zwraca wskaźnik do obiektu `CBrush`, gdy ma dojść do obiektu `HBRUSH` systemu Windows.|
|[CBrush:: GetLogBrush](#getlogbrush)|Pobiera strukturę [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) .|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CBrush:: operator HBRUSH](#operator_hbrush)|Zwraca dojście systemu Windows dołączone do obiektu `CBrush`.|

## <a name="remarks"></a>Uwagi

Aby użyć obiektu `CBrush`, Utwórz obiekt `CBrush` i przekaż go do dowolnej funkcji składowej `CDC`, która wymaga pędzla.

Pędzle mogą być pełne, kreskowane lub desenie.

Aby uzyskać więcej informacji na temat `CBrush`, zobacz [grafika Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="cbrush"></a>CBrush:: CBrush

Konstruuje obiekt `CBrush`.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Określa kolor pierwszego planu pędzla jako kolor RGB. Jeśli pędzel jest zakreskowany, ten parametr określa kolor wylęgu.

*nIndex*<br/>
Określa styl kreskowania pędzla. Może to być jedna z następujących wartości:

- HS_BDIAGONAL kreskowanie w dół (od lewej do prawej) o 45 stopni

- HS_CROSS w poziomie i w pionie

- HS_DIAGCROSS kreskowany o 45 stopni

- HS_FDIAGONAL w górę (od lewej do prawej) o 45 stopni

- HS_HORIZONTAL Kreskowanie poziome

- HS_VERTICAL Kreskowanie pionowe

*pBitmap*<br/>
Wskazuje obiekt `CBitmap`, który określa mapę bitową, z którą maluje pędzel.

### <a name="remarks"></a>Uwagi

`CBrush` ma cztery przeciążone konstruktory. Konstruktor bez argumentów tworzy Niezainicjowany obiekt `CBrush`, który musi zostać zainicjowany, zanim będzie można go użyć.

Jeśli używasz konstruktora bez argumentów, musisz zainicjować otrzymany `CBrush` obiekt z [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush)lub [CreateDIBPatternBrush](#createdibpatternbrush). W przypadku użycia jednego z konstruktorów, które pobierają argumenty, dalsze inicjowanie nie jest konieczne. Konstruktory z argumentami mogą zgłosić wyjątek w przypadku napotkania błędów, natomiast Konstruktor bez argumentów zawsze zakończy się powodzeniem.

Konstruktor z pojedynczym parametrem [COLORREF](/windows/win32/gdi/colorref) konstruuje Pełny pędzel z określonym kolorem. Kolor określa wartość RGB i można ją utworzyć za pomocą makra RGB w systemie WINDOWS. C.

Konstruktor z dwoma parametrami konstruuje pędzel kreskowy. Parametr *nIndex* Określa indeks kreskowanego wzorca. Parametr *crColor* określa kolor.

Konstruktor z parametrem `CBitmap` konstruuje pędzel z deseniem. Parametr identyfikuje mapę bitową. Mapa bitowa jest założono, że została utworzona przy użyciu [CBitmap::](../../mfc/reference/cbitmap-class.md#createbitmap) [CBitmap:: CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)lub [CBitmap:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). Minimalny rozmiar mapy bitowej, która ma być używana w wzorcu wypełnienia, to 8 pikseli na 8 pikseli.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>CBrush:: CreateBrushIndirect

Inicjuje pędzel z stylem, kolorem i wzorkiem określonym w strukturze [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) .

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parametry

*lpLogBrush*<br/>
Wskazuje strukturę [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) , która zawiera informacje o pędzlu.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać jako bieżący pędzel dla dowolnego kontekstu urządzenia.

Pędzel utworzony przy użyciu czarno-bitowej (1 płaszczyzny, 1 bit na piksel) jest rysowany przy użyciu bieżącego koloru tekstu i tła. Piksele reprezentowane przez bit o wartości 0 będą rysowane z bieżącym kolorem tekstu. Piksele reprezentowane przez bit o wartości 1 będą rysowane z bieżącym kolorem tła.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>CBrush:: CreateDIBPatternBrush

Inicjuje pędzel ze wzorcem określonym przez niezależną od urządzenia mapę bitową (DIB).

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>Parametry

*hPackedDIB*<br/>
Identyfikuje Obiekt pamięci globalnej zawierający spakowaną niezależną od urządzenia mapę bitową (DIB).

*nUsage*<br/>
Określa, czy `bmiColors[]` pola struktury danych [BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) (część "spakowanej DIB") zawierają jawne wartości RGB lub indeksy do obecnie zrealizowanej palety logicznej. Parametr musi mieć jedną z następujących wartości:

- DIB_PAL_COLORS tabela kolorów składa się z tablicy 16-bitowych indeksów.

- DIB_RGB_COLORS tabela kolorów zawiera literały wartości RGB.

*lpPackedDIB*<br/>
Wskazuje spakowaną wersję DIB składającą się ze struktury `BITMAPINFO` bezpośrednio po której następuje tablica bajtów definiująca piksele mapy bitowej.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać dla dowolnego kontekstu urządzenia obsługującego operacje rastrowe.

Dwie wersje różnią się w sposób obsługi DIB:

- W pierwszej wersji, aby uzyskać uchwyt do formatu DIB, należy wywołać funkcję `GlobalAlloc` systemu Windows w celu przydzielenia bloku pamięci globalnej, a następnie wypełniania pamięci zapakowanej DIB.

- W drugiej wersji nie jest konieczne Wywołaj `GlobalAlloc` w celu przydzielenia pamięci dla spakowanej DIB.

Spakowana DIB składa się ze struktury danych `BITMAPINFO` bezpośrednio po której następuje tablica bajtów, która definiuje piksele mapy bitowej. Mapy bitowe używane jako wzorce wypełnienia powinny mieć 8 pikseli na 8 pikseli. Jeśli mapa bitowa jest większa, system Windows tworzy deseń wypełnienia przy użyciu tylko bitów odpowiadających pierwsze 8 wierszy i 8 kolumn pikseli w lewym górnym rogu mapy bitowej.

Gdy aplikacja wybierze dwukolorowy pędzel wzorca DIB do kontekstu urządzenia monochromatycznego, system Windows ignoruje kolory określone w formacie DIB, a zamiast tego wyświetla pędzel wzorca przy użyciu bieżących kolorów tekstu i tła kontekstu urządzenia. Piksele zamapowane na pierwszy kolor (przesunięcie 0 w tabeli koloru DIB) dla DIB są wyświetlane przy użyciu koloru tekstu. Piksele mapowane na drugi kolor (przesunięcie 1 w tabeli kolorów) są wyświetlane przy użyciu koloru tła.

Aby uzyskać informacje o używaniu następujących funkcji systemu Windows, zobacz Windows SDK:

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) (Ta funkcja jest dostępna tylko w celu zapewnienia zgodności z aplikacjami zapisanymi w wersjach systemu Windows starszych niż 3,0; użyj funkcji `CreateDIBPatternBrushPt`).

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) (Ta funkcja powinna być używana dla aplikacji opartych na Win32).

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>CBrush:: CreateHatchBrush

Inicjuje pędzel z określonym wzorcem i kolorem.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa styl kreskowania pędzla. Może to być jedna z następujących wartości:

- HS_BDIAGONAL kreskowanie w dół (od lewej do prawej) o 45 stopni

- HS_CROSS w poziomie i w pionie

- HS_DIAGCROSS kreskowany o 45 stopni

- HS_FDIAGONAL w górę (od lewej do prawej) o 45 stopni

- HS_HORIZONTAL Kreskowanie poziome

- HS_VERTICAL Kreskowanie pionowe

*crColor*<br/>
Określa kolor pierwszego planu pędzla jako kolor RGB (kolor kreskowań). Aby uzyskać więcej informacji, zobacz [COLORREF](/windows/win32/gdi/colorref) w Windows SDK.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać jako bieżący pędzel dla dowolnego kontekstu urządzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>CBrush:: CreatePatternBrush

Inicjuje pędzel ze wzorcem określonym przez mapę bitową.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Identyfikuje mapę bitową.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać dla dowolnego kontekstu urządzenia obsługującego operacje rastrowe. Mapa bitowa identyfikowana *przez pBitmap* jest zwykle inicjowana przy [użyciu CBitmap::](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap:: CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)lub [CBitmap:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) .

Mapy bitowe używane jako wzorce wypełnienia powinny mieć 8 pikseli na 8 pikseli. Jeśli mapa bitowa jest większa, system Windows będzie używać tylko bitów odpowiadających pierwszych 8 wierszom i kolumnom pikseli w lewym górnym rogu mapy bitowej.

Pędzel wzorca można usunąć bez wpływu na skojarzoną mapę bitową. Oznacza to, że mapa bitowa może służyć do tworzenia dowolnej liczby pędzli wzorcowych.

Pędzel utworzony przy użyciu czarno-białej mapy bitowej (1 płaszczyzna kolorów, 1 bit na piksel) jest rysowany przy użyciu bieżącego koloru tekstu i tła. Piksele reprezentowane przez bit o wartości 0 są rysowane z bieżącym kolorem tekstu. Piksele reprezentowane przez bit mają ustawioną wartość 1 są rysowane z bieżącym kolorem tła.

Aby uzyskać informacje dotyczące używania [CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush), funkcji systemu Windows, zobacz Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>CBrush:: CreateSolidBrush

Inicjuje pędzel z określonym pełnym kolorem.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Struktura [COLORREF](/windows/win32/gdi/colorref) , która określa kolor pędzla. Kolor określa wartość RGB i można ją utworzyć za pomocą makra RGB w systemie WINDOWS. C.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać jako bieżący pędzel dla dowolnego kontekstu urządzenia.

Po zakończeniu działania aplikacji przy użyciu pędzla utworzonego przez `CreateSolidBrush`należy wybrać pędzel z kontekstu urządzenia.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CBrush:: CBrush](#cbrush).

##  <a name="createsyscolorbrush"></a>CBrush:: CreateSysColorBrush

Inicjuje kolor pędzla.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks koloru. Ta wartość odpowiada kolorowi użytemu do malowania jednego z 21 elementów okna. Aby uzyskać listę wartości, zobacz [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) w Windows SDK.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pędzel można następnie wybrać jako bieżący pędzel dla dowolnego kontekstu urządzenia.

Po zakończeniu działania aplikacji przy użyciu pędzla utworzonego przez `CreateSysColorBrush`należy wybrać pędzel z kontekstu urządzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>CBrush:: FromHandle

Zwraca wskaźnik do obiektu `CBrush`, gdy ma dojść do obiektu [HBRUSH](#operator_hbrush) systemu Windows.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parametry

*hBrush*<br/>
Dojście do pędzla GDI systemu Windows.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `CBrush`, jeśli się to powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli obiekt `CBrush` nie jest już dołączony do dojścia, zostanie utworzony i dołączony tymczasowy obiekt `CBrush`. Ten tymczasowy `CBrush` obiektu jest prawidłowy tylko do następnego czasu bezczynności aplikacji w pętli zdarzeń. W tej chwili wszystkie tymczasowe obiekty graficzne są usuwane. Innymi słowy, obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania jednego komunikatu w oknie.

Aby uzyskać więcej informacji na temat używania obiektów graficznych, zobacz temat [obiekty graficzne](/windows/win32/gdi/graphic-objects) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CBrush:: CBrush](#cbrush).

##  <a name="getlogbrush"></a>CBrush:: GetLogBrush

Wywołaj tę funkcję elementu członkowskiego, aby pobrać strukturę `LOGBRUSH`.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parametry

*pLogBrush*<br/>
Wskazuje strukturę [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) , która zawiera informacje o pędzlu.

### <a name="return-value"></a>Wartość zwrócona

Jeśli funkcja się powiedzie, a *pLogBrush* jest prawidłowym wskaźnikiem, wartość zwracana jest liczbą bajtów przechowywanych w buforze.

Jeśli funkcja się powiedzie, a *pLogBrush* ma wartość null, wartość zwracana jest liczbą bajtów wymaganą do przechowywania informacji, które funkcja będzie przechowywać w buforze.

Jeśli funkcja się nie powiedzie, zwracana wartość wynosi 0.

### <a name="remarks"></a>Uwagi

Struktura `LOGBRUSH` definiuje styl, kolor i deseń pędzla.

Na przykład Wywołaj `GetLogBrush`, aby dopasować określony kolor lub wzór mapy bitowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>CBrush:: operator HBRUSH

Użyj tego operatora, aby uzyskać dojście do dołączonego interfejsu GDI systemu Windows obiektu `CBrush`.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli to się powiedzie, dojście do obiektu GDI systemu Windows reprezentowanego przez obiekt `CBrush`; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem rzutowania, który obsługuje bezpośrednie użycie obiektu HBRUSH.

Aby uzyskać więcej informacji na temat używania obiektów graficznych, zobacz temat [obiekty graficzne](/windows/win32/gdi/graphic-objects) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykład PROPDLG MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)
