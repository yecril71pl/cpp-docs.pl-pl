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
ms.openlocfilehash: 4f6b5db22b956584507a2979a517ff26d5364a0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661646"
---
# <a name="cbrush-class"></a>Klasa CBrush

Hermetyzuje pędzel Windows graphics urządzenia interface (GDI).

## <a name="syntax"></a>Składnia

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|Konstruuje `CBrush` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Inicjuje pędzla, style, kolor i wzorcem określonym w [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) struktury.|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Inicjuje pędzla ze wzorcem określonym przez map bitowych niezależnych od urządzenia (DIB).|
|[CBrush::CreateHatchBrush](#createhatchbrush)|Inicjuje pędzla o określony wzorzec kreskowane i kolorze.|
|[CBrush::CreatePatternBrush](#createpatternbrush)|Inicjuje pędzla ze wzorcem określonym przez mapę bitową.|
|[CBrush::CreateSolidBrush](#createsolidbrush)|Inicjuje pędzla przy użyciu określonego jednolitego koloru.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Tworzy pędzla, który jest domyślny kolor systemu.|
|[CBrush::FromHandle](#fromhandle)|Zwraca wskaźnik do `CBrush` obiektu, kiedy podane dojście do Windows `HBRUSH` obiektu.|
|[CBrush::GetLogBrush](#getlogbrush)|Pobiera [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) struktury.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[HBRUSH CBrush::operator](#operator_hbrush)|Zwraca uchwyt Windows dołączonych do `CBrush` obiektu.|

## <a name="remarks"></a>Uwagi

Do użycia `CBrush` obiektów, konstruowania `CBrush` obiektu i przekaż go do dowolnych `CDC` funkcji elementu członkowskiego, która wymaga pędzla.

Pędzle może być stałe, wyklutych lub deseń.

Aby uzyskać więcej informacji na temat `CBrush`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cbrush"></a>  CBrush::CBrush

Konstruuje `CBrush` obiektu.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Określa kolor pierwszego planu pędzel jako kolor RGB. Jeśli jest wylęgłych pędzla, ten parametr określa kolor kreskowaniu.

*nIndex*<br/>
Określa styl kreskowania pędzla. Może być jednym z następujących wartości:

- Kreskowanie HS_BDIAGONAL dół (od lewej do prawej) na 45 stopni

- HS_CROSS poziome i pionowe kreskowany

- Kreskowanie HS_DIAGCROSS, na 45 stopni

- HS_FDIAGONAL stawki rabatowe zwiększone kreskowania (od lewej do prawej) na 45 stopni

- Kreskowanie poziome HS_HORIZONTAL

- Kreskowanie pionowe HS_VERTICAL

*pBitmap*<br/>
Wskazuje `CBitmap` obiekt, który określa mapę bitową za pomocą którego pędzla do malowania.

### <a name="remarks"></a>Uwagi

`CBrush` ma cztery przeciążone konstruktory. Konstruktor bez argumentów tworzy niezainicjowany `CBrush` obiekt, który musi zostać zainicjowany przed jego użyciem.

Jeśli korzystasz z konstruktora bez argumentów, należy zainicjować wynikowy `CBrush` obiekt z [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush), lub [CreateDIBPatternBrush](#createdibpatternbrush). Jeśli używasz jednego z konstruktorów, które przyjmuje argumentów, następnie żadne dodatkowe inicjowania jest konieczne. Konstruktory z argumentami może zgłosić wyjątek, jeśli zostaną napotkane błędy, gdy konstruktor bez argumentów zawsze powiedzie się.

Konstruktor za pomocą jednego [COLORREF](/windows/desktop/gdi/colorref) parametru tworzy pędzla przy użyciu określonego koloru. Kolor określa wartość RGB i może zostać utworzony przy użyciu makra RGB w systemie WINDOWS. H.

Konstruktor z dwoma parametrami tworzy kreskowania pędzla. *NIndex* parametr określa indeks zakreskowane wzorca. *CrColor* parametr określa kolor.

Konstruktor z `CBitmap` parametru tworzy deseniem pędzla. Parametr identyfikuje mapy bitowej. Mapa bitowa założono, że zostały utworzone przy użyciu [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), lub [ CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). Minimalny rozmiar mapy bitowej do użycia w deseń wypełnienia jest 8 pikseli 8 pikseli.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect

Inicjuje pędzla, style, kolor i wzorcem określonym w [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) struktury.

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parametry

*lpLogBrush*<br/>
Wskazuje [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) strukturę, która zawiera informacje o pędzla.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Następnie można wybrać pędzel jako aktualny pędzel we wszystkich kontekstach urządzenia.

Pędzel utworzone za pomocą mapy bitowej monochromatyczny (1 płaszczyzny, 1 bit na piksel) jest rysowany przy użyciu bieżących kolorów tła i tekstu. Piksele, reprezentowane przez nieco ustawione na 0 będą pobierane z bieżącym kolorem tekstu. Piksele, reprezentowane przez nieco ustawiona na 1 będą pobierane z bieżącym kolorem tła.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush

Inicjuje pędzla ze wzorcem określonym przez map bitowych niezależnych od urządzenia (DIB).

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
Identyfikuje obiekt pamięci globalnej, zawierający upakowaną map bitowych niezależnych od urządzenia (DIB).

*Nużycie*<br/>
Określa, czy `bmiColors[]` pola [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) struktury danych (część "pakowane DIB") zawiera jawne wartości RGB lub indeksów do aktualnie zrealizowane palety logiczne. Parametr musi mieć jedną z następujących wartości:

- DIB_PAL_COLORS tabeli kolorów składa się z tablicy indeksów 16-bitowych.

- DIB_RGB_COLORS tabeli kolorów zawiera wartości RGB literału.

*lpPackedDIB*<br/>
Wskazuje na upakowaną DIB, składający się z `BITMAPINFO` struktury bezpośrednio następuje tablicę bajtów Definiowanie piksele mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Następnie można wybrać pędzel we wszystkich kontekstach urządzenia obsługującą rastrowych.

W ten sposób obsługi DIB różnią się dwie wersje:

- W pierwszej wersji można uzyskać dojścia do DIB wywołujesz Windows `GlobalAlloc` funkcję, aby przydzielić blok pamięci globalnej, a następnie wprowadź ilość pamięci z upakowaną DIB.

- W drugiej wersji nie jest konieczne do wywołania `GlobalAlloc` można przydzielić pamięci dla spakowanych DIB.

Spakowane DIB składa się z `BITMAPINFO` struktury danych bezpośrednio po nim tablica bajtów, która definiuje piksele mapy bitowej. Mapy bitowe używane jako wzorców wypełnienia powinna być 8 pikseli 8 pikseli. W przypadku większych mapę bitową Windows tworzy deseń wypełnienia przy użyciu tylko usługi bits, odpowiadający pierwsze 8 wierszy i kolumn 8 pikseli w lewym górnym rogu mapy bitowej.

Gdy aplikacja wybierze dwóch kolorów DIB pędzla do kontekstu urządzenia monochromatyczny, Windows ignoruje kolorów, określona w DIB i zamiast tego zostanie pędzla wzoru przy użyciu bieżącego kolorów tekstu i tła kontekstu urządzenia. Piksele mapowane na pierwszy kolor DIB (przy przesunięciu 0 w tabeli kolorów DIB) są wyświetlane przy użyciu koloru tekstu. Piksele mapowane na drugi kolor (od przesunięcia 1 w tabeli kolorów) są wyświetlane przy użyciu koloru tła.

Aby dowiedzieć się, jak za pomocą następujących funkcji Windows zobacz zestaw Windows SDK:

- [CreateDIBPatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrush) (Ta funkcja jest dostępna tylko dla zgodności z aplikacji napisanych dla wersji systemu Windows starszych niż 3.0; użyj `CreateDIBPatternBrushPt` funkcji.)

- [CreateDIBPatternBrushPt](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrushpt) (tej funkcji należy używać dla aplikacji opartych na Win32).

- [Działanie funkcji GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush

Inicjuje pędzla o określony wzorzec kreskowane i kolorze.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa styl kreskowania pędzla. Może być jednym z następujących wartości:

- Kreskowanie HS_BDIAGONAL dół (od lewej do prawej) na 45 stopni

- HS_CROSS poziome i pionowe kreskowany

- Kreskowanie HS_DIAGCROSS, na 45 stopni

- HS_FDIAGONAL stawki rabatowe zwiększone kreskowania (od lewej do prawej) na 45 stopni

- Kreskowanie poziome HS_HORIZONTAL

- Kreskowanie pionowe HS_VERTICAL

*crColor*<br/>
Określa kolor pierwszego planu pędzel jako kolor RGB (kolor kreskowaniu). Zobacz [COLORREF](/windows/desktop/gdi/colorref) w zestawie Windows SDK, aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Następnie można wybrać pędzel jako aktualny pędzel we wszystkich kontekstach urządzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush

Inicjuje pędzla ze wzorcem określonym przez mapę bitową.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Identyfikuje mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Następnie można wybrać pędzel we wszystkich kontekstach urządzenia obsługującą rastrowych. Mapa bitowa oznaczona *pBitmap* jest zwykle inicjowana przy użyciu [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: Loadbitmap —](../../mfc/reference/cbitmap-class.md#loadbitmap), lub [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) funkcji.

Mapy bitowe używane jako wzorców wypełnienia powinna być 8 pikseli 8 pikseli. W przypadku większych mapę bitową Windows będzie używać tylko bity, odpowiadający pierwsze 8 wierszy i kolumn pikseli w lewym górnym rogu mapy bitowej.

Pędzla wzoru mogą zostać usunięte bez wywierania wpływu na skojarzone mapy bitowej. Oznacza to, że mapa bitowa można utworzyć dowolną liczbę pędzle wzorzec.

Pędzel, który został utworzony za pomocą monochromatycznych map bitowych (płaszczyzny kolorów 1, 1 bit na piksel) jest rysowany przy użyciu bieżących kolorów tła i tekstu. Bieżący kolor tekstu są rysowane pikseli, reprezentowane przez nieco ustawione na 0. Piksele, reprezentowane przez nieco ustawiona na 1 są rysowane w bieżącym kolorem tła.

Aby uzyskać informacje o używaniu [CreatePatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createpatternbrush), Windows funkcji, zobacz dokumentację Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush

Inicjuje pędzla jednolitym kolorem określony.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
A [COLORREF](/windows/desktop/gdi/colorref) strukturę, która określa kolor pędzla. Kolor określa wartość RGB i może zostać utworzony przy użyciu makra RGB w systemie WINDOWS. H.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Następnie można wybrać pędzel jako aktualny pędzel we wszystkich kontekstach urządzenia.

Gdy aplikacja zakończy pędzla, utworzone przez `CreateSolidBrush`, należy wybrać, pędzla poza kontekstem urządzenia.

### <a name="example"></a>Przykład

  Zobacz przykład [CBrush::CBrush](#cbrush).

##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush

Inicjuje kolor pędzla.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks koloru. Ta wartość odpowiada kolor używany do rysowania, jeden z elementów 21 okna. Zobacz [GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) w zestawie Windows SDK dla listy wartości.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Następnie można wybrać pędzel jako aktualny pędzel we wszystkich kontekstach urządzenia.

Gdy aplikacja zakończy pędzla, utworzone przez `CreateSysColorBrush`, należy wybrać, pędzla poza kontekstem urządzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>  CBrush::FromHandle

Zwraca wskaźnik do `CBrush` obiektu, kiedy podane dojście do Windows [HBRUSH](#operator_hbrush) obiektu.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parametry

*hBrush*<br/>
DOJŚCIE do pędzel Windows GDI.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CBrush` obiektu, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CBrush` obiektu nie jest już dołączony do uchwyt tymczasowego `CBrush` obiekt zostanie utworzony i dołączony. Ten tymczasowy `CBrush` obiekt jest prawidłowy tylko dopóki aplikacja ma czas bezczynności w jego pętlę zdarzeń. W tej chwili wszystkich tymczasowych obiektów graficznych są usuwane. Innymi słowy tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jednego okna.

Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz [obiektów grafiki](/windows/desktop/gdi/graphic-objects) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CBrush::CBrush](#cbrush).

##  <a name="getlogbrush"></a>  CBrush::GetLogBrush

Wywołaj tę funkcję elementu członkowskiego, aby pobrać `LOGBRUSH` struktury.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parametry

*pLogBrush*<br/>
Wskazuje [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) strukturę, która zawiera informacje o pędzla.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, i *pLogBrush* jest wskaźnikiem prawidłową wartość zwracana jest liczba bajtów przechowywanych w buforze.

Jeśli funkcja się powiedzie, i *pLogBrush* ma wartość NULL, wartość zwracana jest liczba bajtów potrzebnych do przechowywania informacji o funkcji będzie przechowywać w buforze.

Jeśli funkcja zawiedzie, wartość zwracana to 0.

### <a name="remarks"></a>Uwagi

`LOGBRUSH` Definiuje struktury, style, kolor i wzoru pędzla.

Na przykład wywołać `GetLogBrush` do dopasowania konkretny kolor lub deseń mapy bitowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>  HBRUSH CBrush::operator

Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CBrush` obiektu.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, dojścia do obiektu Windows GDI reprezentowany przez `CBrush` obiektu; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia obiektu HBRUSH.

Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz [obiektów grafiki](/windows/desktop/gdi/graphic-objects) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbki MFC PROPDLG](../../visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)
