---
title: Klasa CDrawingManager
ms.date: 11/04/2016
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
ms.openlocfilehash: 506ab7a06653942ecff05043a7e7efabd535115f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781695"
---
# <a name="cdrawingmanager-class"></a>Klasa CDrawingManager

`CDrawingManager` Klasa implementuje złożonych algorytmów rysowania.

## <a name="syntax"></a>Składnia

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name|Opis|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Konstruuje `CDrawingManager` obiektu.|
|`CDrawingManager::~CDrawingManager`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name|Opis|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Tworzy 32-bitowych niezależnych od urządzenia mapy bitowej (DIB) który aplikacji można napisać, aby bezpośrednio.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczystych pikseli.|
|[CDrawingManager::DrawRotated](#drawrotated)|Obraca się źródłowy kontroler domeny zawartość wewnątrz danego prostokąt przez +/-90 stopni|
|[CDrawingManager::DrawEllipse](#drawellipse)|Rysuje elipsę o podanej kolorów wypełnienia i obramowanie.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Rysuje pierścień i wypełnia je kolor gradientu.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Rysuje linię.|
|[CDrawingManager::DrawRect](#drawrect)|Rysuje prostokąt o podanej kolorów wypełnienia i obramowanie.|
|[CDrawingManager::DrawShadow](#drawshadow)|Rysuje cienia prostokątny obszar.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Wypełnia prostokątny obszar za pomocą dwóch gradientów kolorów.|
|[CDrawingManager::FillGradient](#fillgradient)|Wypełnia prostokątny obszar gradientem określonego koloru.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Wypełnia prostokątny obszar gradientem określonego koloru. Podano także kierunek Zmień kolor gradientu.|
|[CDrawingManager::GrayRect](#grayrect)|Wypełnia prostokąt przy użyciu określonego koloru szarego.|
|[CDrawingManager::HighlightRect](#highlightrect)|Wyróżnia prostokątny obszar.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Konwertuje kolor z reprezentacji HLS do reprezentacji RGB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Konwertuje kolor z reprezentacji HLS do reprezentacji RGB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Konwertuje kolor z reprezentacji HSV do reprezentacji RGB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Metoda pomocnika, która konwertuje wartość hue składników czerwonego, zielonego lub niebieski.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Przerzuca prostokątny obszar.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Metoda pomocnika, która określa końcowy kolor piksela półprzezroczystych.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Tworzy mapę bitową, który może służyć jako cienia.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Konwertuje kolor z reprezentacji RGB do reprezentacji HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Konwertuje kolor z reprezentacji RGB do reprezentacji HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Metoda pomocnika, która kolory częściowo przezroczyste pikseli mapy bitowej.|
|[CDrawingManager::SetPixel](#setpixel)|Metoda pomocnika, która zmienia piksela mapy bitowej na określony kolor.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Łączy dwa kolory oparte na ważona współczynnik.|

## <a name="remarks"></a>Uwagi

`CDrawingManager` Klasa oferuje funkcje rysowania cieni, gradientów kolorów i prostokąty wyróżnione. Wykonuje także używanie mieszania alfa. Ta klasa umożliwia bezpośrednio zmienić Interfejsem użytkownika aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdrawmanager.h

##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager

Konstruuje [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) obiektu.

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parametry

*dc*<br/>
[in] Odwołanie do kontekstu urządzenia. `CDrawingManager` Używa tego kontekstu do rysowania.

##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32

Tworzy 32-bitowych niezależnych od urządzenia mapy bitowej (DIB) który aplikacji można napisać, aby bezpośrednio.

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Rozmiar*|[in] A [CSize](../../atl-mfc-shared/reference/csize-class.md) parametr, który wskazuje rozmiar mapy bitowej.|
|*pBits*|[out] Wskaźnik do wskaźnika danych, który odbiera lokalizację DIB wartości bitowe.|
|*bitmap*|Dojście do oryginalnego mapy bitowej|
|*clrTransparent*|Wartość RGB, określając kolor przezroczysty, oryginalnym mapy bitowej.|

### <a name="return-value"></a>Wartość zwracana

Uchwyt do nowo utworzonej mapy bitowej DIB Jeśli ta metoda się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia mapy bitowej DIB zobacz [CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibitmap).

##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha

Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczystych pikseli.

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parametry

*pDstDC*<br/>
[in] Wskaźnik do kontekstu urządzenia dla miejsca docelowego.

*rectDst*<br/>
[in] Prostokąta docelowego.

*pSrcDC*<br/>
[in] Wskaźnik do kontekstu urządzenia dla źródła.

*rectSrc*<br/>
[in] Prostokąta źródłowego.

### <a name="remarks"></a>Uwagi

Ta metoda przeprowadza przenikaniem alfa dla dwóch map bitowych. Aby uzyskać więcej informacji na temat mieszania alfa, zobacz [AlphaBlend](/windows/desktop/api/wingdi/nf-wingdi-alphablend) w zestawie Windows SDK.

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

Rysuje elipsę o podanej kolorów wypełnienia i obramowanie.

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Prostokąt otaczający elipsy.

*clrFill*<br/>
[in] Kolor, którego ta metoda używa do następnie wypełniamy kształt.

*clrLine*<br/>
[in] Kolor, którego ta metoda korzysta z obramowaniem elipsy.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca bez Rysowanie elipsy, jeśli albo kolor jest ustawiona na wartość -1. Również zwraca bez Rysowanie elipsy, jeśli ma wartość 0 albo wymiaru prostokąt otaczający.

##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing

Rysuje pierścień i wypełnia je kolor gradientu.

```
BOOL DrawGradientRing(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    COLORREF colorBorder,
    int nAngle,
    int nWidth,
    COLORREF clrFace = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] A [CRect](../../atl-mfc-shared/reference/crect-class.md) parametr, który określa granic gradientu pierścienia.

*colorStart*<br/>
[in] Pierwszy kolor gradientu.

*colorFinish*<br/>
[in] Ostatni kolor gradientu.

*colorBorder*<br/>
[in] Kolor obramowania.

*nAngle*<br/>
[in] Parametr, który określa kąt początkowy rysowania gradientu. Wartość ta powinna być z zakresu od 0 do 360.

*nWidth*<br/>
[in] Szerokość obramowania pierścienia.

*clrFace*<br/>
[in] Kolor wewnętrznego pierścienia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Prostokąta zdefiniowanego przez *prostokąt* musi być co najmniej 5 pikseli szerokości i 5 pikseli.

##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Rysuje linię.

```
void DrawLine(
    int x1,
    int y1,
    int x2,
    int y2,
    COLORREF clrLine);

void DrawLineA(
    double x1,
    double y1,
    double x2,
    double y2,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*x1*|[in] Współrzędna x, gdzie rozpoczyna się wiersz.|
|*y1*|[in] Współrzędna y, gdzie rozpoczyna się wiersz.|
|*x2*|[in] Współrzędna x, gdzie kończy się wiersz.|
|*y2*|[in] Współrzędna y, gdzie kończy się wiersz.|
|*clrLine*|[in] Kolor linii.|

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli *clrLine* jest równa -1.

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

Rysuje prostokąt o podanej kolorów wypełnienia i obramowanie.

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Granice prostokąta.

*clrFill*<br/>
[in] Kolor, który używa tej metody, aby wypełnić prostokąt.

*clrLine*<br/>
[in] Kolor ta metoda używa obramowania prostokąta.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca bez Rysowanie prostokąta, jeśli albo kolor jest ustawiona na wartość -1. Zwraca również, jeśli albo wymiarów prostokąta wynosi 0.

##  <a name="drawshadow"></a>  CDrawingManager::DrawShadow

Rysuje cienia prostokątny obszar.

```
BOOL DrawShadow(
    CRect rect,
    int nDepth,
    int iMinBrightness = 100,
    int iMaxBrightness = 50,
    CBitmap* pBmpSaveBottom = NULL,
    CBitmap* pBmpSaveRight = NULL,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bRightShadow = TRUE);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Prostokątny obszar w aplikacji. Rysowanie Menedżera narysuje cień poniżej tego obszaru.

*nDepth*<br/>
[in] Szerokość i wysokość w tle.

*iMinBrightness*<br/>
[in] Minimalna jasność cienia.

*iMaxBrightness*<br/>
[in] Maksymalna jasność cienia.

*pBmpSaveBottom*<br/>
[in] Wskaźnik do mapy bitowej, który zawiera obraz dla dolnej części cienia.

*pBmpSaveRight*<br/>
[in] Wskaźnik do mapy bitowej, który zawiera obraz dla cienia są rysowane na prawej krawędzi prostokąta.

*clrBase*<br/>
[in] Kolor cienia.

*bRightShadow*<br/>
[in] Parametrów logiczny, który wskazuje, jak jest wstawiany w tle. Jeśli *bRightShadow* jest `TRUE`, `DrawShadow` rysuje cienia w prawej krawędzi prostokąta.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Możesz podać dwie prawidłowe mapy bitowe dolnych i prawych cieni przy użyciu parametrów *pBmpSaveBottom* i *pBmpSaveRight*. Jeśli te [CBitmap](../../mfc/reference/cbitmap-class.md) obiekty mają przyłączonego obiektu GDI `DrawShadow` użyje tych map bitowych jako cieni. Jeśli `CBitmap` parametry nie mogą mieć przyłączonego obiektu GDI `DrawShadow` rysuje w tle i dołącza bitmap do parametrów. W przyszłości wywołania `DrawShadow`, możesz podać te mapy bitowe, aby przyspieszyć proces rysowania. Aby uzyskać więcej informacji na temat `CBitmap` klasy i obiekty GDI, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).

Jeśli jest jeden z tych parametrów `NULL`, `DrawShadow` spowoduje automatyczne pobieranie w tle.

Jeśli ustawisz *bRightShadow* na wartość FALSE, będzie sięgał cień, poniżej i w lewo prostokątny obszar.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `DrawShadow` metody `CDrawingManager` klasy. Ten fragment kodu jest częścią [próbka Demo arkusza Prop](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>  CDrawingManager::Fill4ColorsGradient

Wypełnia prostokątny obszar za pomocą dwóch gradientów kolorów.

```
void Fill4ColorsGradient(
    CRect rect,
    COLORREF colorStart1,
    COLORREF colorFinish1,
    COLORREF colorStart2,
    COLORREF colorFinish2,
    BOOL bHorz = TRUE,
    int nPercentage = 50);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Prostokąt, aby wypełnić.

*colorStart1*<br/>
[in] Kolor początkowy pierwszy kolor gradientu.

*colorFinish1*<br/>
[in] Ostateczny kolor pierwszy kolor gradientu.

*colorStart2*<br/>
[in] Kolor początkowy drugi kolor gradientu.

*colorFinish2*<br/>
[in] Ostateczny kolor drugi kolor gradientu.

*bHorz*<br/>
[in] Parametr logiczny, który wskazuje, czy `Fill4ColorsGradient` kolory gradientu poziomej lub pionowej. Wartość TRUE wskazuje gradient poziomy.

*nPercentage*<br/>
[in] Liczba całkowita od 0 do 100. Ta wartość wskazuje procent prostokąt, aby wypełnić pierwszy kolor gradientu.

### <a name="remarks"></a>Uwagi

Po wypełnieniu prostokąt przy użyciu dwóch gradientów kolorów są znajduje się nad siebie lub dalej ze sobą, w zależności od wartości *bHorz*. Każdy kolor gradientu jest obliczany osobno przy użyciu metody [CDrawingManager::FillGradient](#fillgradient).

Ta metoda generuje błąd potwierdzenia, jeśli *nPercentage* jest mniejszy niż 0 lub większa niż 100.

##  <a name="fillgradient"></a>  CDrawingManager::FillGradient

Wypełnia prostokątny obszar gradientem określonego koloru.

```
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Prostokątny obszar, aby wypełnić.

*colorStart*<br/>
[in] Pierwszy kolor gradientu.

*colorFinish*<br/>
[in] Kolor końcowy gradientu.

*bHorz*<br/>
[in] Parametr logiczny, który określa, czy `FillGradient` powinien rysowania gradientu, poziomej lub pionowej.

*nStartFlatPercentage*<br/>
[in] Wartość procentowa prostokąt, `FillGradient` wypełnia *colorStart* , zanim zacznie gradientu.

*nEndFlatPercentage*<br/>
[in] Wartość procentowa prostokąt, `FillGradient` wypełnia *colorFinish* po jej zakończeniu gradientu.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `FillGradient` metody `CDrawingManager` klasy. Ten fragment kodu jest częścią [próbka MS Office 2007 Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>  CDrawingManager::FillGradient2

Wypełnia prostokątny obszar gradientem określonego koloru.

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Prostokątny obszar, aby wypełnić.

*colorStart*<br/>
[in] Pierwszy kolor gradientu.

*colorFinish*<br/>
[in] Ostatni kolor gradientu.

*nAngle*<br/>
[in] Liczba całkowita od 0 do 360. Ten parametr określa kierunek kolor gradientu.

### <a name="remarks"></a>Uwagi

Użyj *nAngle* do określania kierunku kolor gradientu. Po określeniu kierunek gradient kolorów, należy również określić gdzie rozpoczyna się gradient kolorów. Wartość 0 dla *nAngle* wskazuje gradientu, który zaczyna się od górnej krawędzi prostokąta. Jako *nAngle* zwiększa położenie początkowe dla gradientu przenosi wskazówek zegara, w oparciu o wartość kąta.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `FillGradient2` metody `CDrawingManager` klasy. Ten fragment kodu jest częścią [przykładowe nowych formantów](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>  CDrawingManager::GrayRect

Wypełnia prostokąt przy użyciu określonego koloru szarego.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Prostokątny obszar, aby wypełnić.

*nPercentage*<br/>
[in] Procent szary, które mają w prostokącie.

*clrTransparent*<br/>
[in] Przezroczysty kolor.

*clrDisabled*<br/>
[in] Kolor, który używa tej metody do cofnięcia stopniowania nasycenia, jeśli *nPercentage* jest ustawiona na wartość -1.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Dla parametru *nPercentage*, niższą wartość wskazuje ciemniejszy.

Maksymalna wartość *nPercentage* to 200. Wartość większą niż 200 nie zmienia się wygląd prostokąta. Jeśli wartość wynosi -1, ta metoda używa *clrDisabled* ograniczyć nasycenie prostokąta.

##  <a name="highlightrect"></a>  CDrawingManager::HighlightRect

Wyróżnia prostokątny obszar.

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Prostokątny obszar, aby wyróżnić.

*nPercentage*<br/>
[in] Wartość procentowa, który wskazuje, jak przezroczyste podświetlenie powinien być.

*clrTransparent*<br/>
[in] Przezroczysty kolor.

*nTolerance*<br/>
[in] Na liczbę całkowitą pomiędzy 0 a 255 wskazującą na uszkodzenia kolorów.

*clrBlend*<br/>
[in] Kolor podstawowy do mieszania.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli *nPercentage* zakresu od 0 do 99, `HighlightRect` używa alfa algorytmu mieszania. Aby uzyskać więcej informacji na temat przenikaniem alfa, zobacz [alfa mieszania linii i wypełnień](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Jeśli *nPercentage* wynosi -1, ta metoda używa domyślnego poziomu wyróżnienia. Jeśli *nPercentage* to 100, ta metoda nic nie robi i zwraca wartość TRUE.

Metoda używa parametru *nTolerance* do określenia, czy do wyróżnienia prostokątny obszar. Aby wyróżnić prostokąt, różnica między kolor tła, aplikacji i *clrTransparent* musi być mniejsza niż *nTolerance* w każdego składnika koloru (czerwony, zielony i niebieski).

##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE

Konwertuje kolor z reprezentacji HLS do reprezentacji RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[in] Liczba od 0 do 1, który reprezentuje odcień koloru.

*L*<br/>
[in] Liczba od 0 do 1, która wskazuje, jasność koloru.

*S*<br/>
[in] Liczba od 0 do 1, która wskazuje nasycenie koloru.

### <a name="return-value"></a>Wartość zwracana

Reprezentacja RGB kolor HLS, pod warunkiem.

### <a name="remarks"></a>Uwagi

Kolor, który może być reprezentowany jako HSV (odcień, nasycenie i wartości), HSL (hue, nasycenia i jasności) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolor zobacz [kolor](/windows/desktop/uxguide/vis-color).

Ta metoda i `CDrawingManager::HLStoRGB_TWO` metody do tej samej operacji, ale wymagają różnych wartości *H* parametru. W przypadku tej metody *H* jest wartością procentową koła. W `CDrawingManager::HLStoRGB_TWO` metody *H* jest wartością stopień zakresu od 0 do 360, które obie reprezentować czerwony. Na przykład za pomocą `HLStoRGB_ONE`, wartość 0,25 dla *H* jest odpowiednikiem wartości 90 z `HLStoRGB_TWO`.

##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO

Konwertuje kolor z reprezentacji HLS do reprezentacji RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[in] Liczba od 0 do 360, która przedstawia odcień koloru.

*L*<br/>
[in] Liczba od 0 do 1, która wskazuje, jasność koloru.

*S*<br/>
[in] Liczba od 0 do 1, która wskazuje nasycenie koloru.

### <a name="return-value"></a>Wartość zwracana

Reprezentacja RGB kolor HLS, pod warunkiem.

### <a name="remarks"></a>Uwagi

Kolor, który może być reprezentowany jako HSV (odcień, nasycenie i wartości), HSL (hue, nasycenia i jasności) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolor zobacz [kolor](/windows/desktop/uxguide/vis-color).

Ta metoda i [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metody do tej samej operacji, ale wymagają różnych wartości *H* parametru. W przypadku tej metody *H* jest wartością stopień zakresu od 0 do 360, które obie reprezentować czerwony. W [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metody *H* jest wartością procentową koła. Na przykład za pomocą `HLStoRGB_ONE`, wartość 0,25 dla *H* jest odpowiednikiem wartości 90 z `HLStoRGB_TWO`.

##  <a name="hsvtorgb"></a>  CDrawingManager::HSVtoRGB

Konwertuje kolor z reprezentacji HSV do reprezentacji RGB.

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*H*|[in] Liczba od 0 do 360, która określa odcień koloru.|
|*S*|[in] Liczba od 0 do 1, która wskazuje nasycenie koloru.|
|*V*|[in] Liczba od 0 do 1, która wskazuje wartość koloru.|

### <a name="return-value"></a>Wartość zwracana

Reprezentacja RGB kolor HSV podane.

### <a name="remarks"></a>Uwagi

Kolor, który może być reprezentowany jako HSV (odcień, nasycenie i wartości), HSL (hue, nasycenia i jasności) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolor zobacz [kolor](/windows/desktop/uxguide/vis-color).

##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB

Konwertuje wartość hue składników czerwonego, zielonego lub niebieski.

```
static double __stdcall HuetoRGB(
    double m1,
    double m2,
    double h);

static BYTE __stdcall HueToRGB(
    float rm1,
    float rm2,
    float rh);
```

### <a name="parameters"></a>Parametry

*m1*<br/>
[in] Zobacz uwagi.

*m2*<br/>
[in] Zobacz uwagi.

*h*<br/>
[in] Zobacz uwagi.

*rm1*<br/>
[in] Zobacz uwagi.

*rm2*<br/>
[in] Zobacz uwagi.

*Rh*<br/>
[in] Zobacz uwagi.

### <a name="return-value"></a>Wartość zwracana

Poszczególne red zielony i niebieski składnika dla podanego hue.

### <a name="remarks"></a>Uwagi

Ta metoda jest metodą pomocnika, `CDrawingManager` klasa używana do obliczenia poszczególnych składników czerwonego, zielonego i niebieskiego koloru w reprezentacji HSV lub HSL. Ta metoda nie jest przeznaczony do wywołania bezpośrednio przez programistę. Parametry wejściowe są wartości, które są zależne od algorytm konwersji.

Aby przekonwertować kolor HSV lub HSL reprezentację RGB, należy wywołać jedną z następujących metod:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>  CDrawingManager::MirrorRect

Przerzuca prostokątny obszar.

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Prostokąt otaczający obszar do przerzucenia.

*bHorz*<br/>
[in] Parametr logiczny, który wskazuje, czy prostokąt Przerzuca poziomo czy pionowo.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia przerzucenie dowolny obszar kontekstu urządzenia należące do `CDrawingManager` klasy. Jeśli *bHorz* jest ustawiona na wartość TRUE, ta metoda Przerzuca obszaru poziomie. W przeciwnym razie jego Przerzuca obszaru w pionie.

##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha

Oblicza końcowy kolor półprzezroczystych pikseli.

```
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    int percent);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    double percentR,
    double percentG,
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    COLORREF dstPixel,
    int percent);
```

### <a name="parameters"></a>Parametry

*srcPixel*<br/>
[in] Początkowy kolor piksela.

*percent*<br/>
[in] Liczba od 0 do 100, która przedstawia wartość procentową przezroczystości. Wartość 100 oznacza, że kolor początkowy jest całkowicie przezroczysty.

*percentR*<br/>
[in] Liczba od 0 do 100, który reprezentuje procent przezroczystość składnik czerwony.

*percentG*<br/>
[in] Liczba od 0 do 100, który reprezentuje procent przezroczystość składnik zielony.

*percentB*<br/>
[in] Liczba od 0 do 100, który reprezentuje procent przezroczystość składnik niebieski.

*dstPixel*<br/>
[in] Podstawowy kolor piksela.

### <a name="return-value"></a>Wartość zwracana

Końcowy kolor piksela półprzezroczystych.

### <a name="remarks"></a>Uwagi

To jest klasa pomocnicza do kolorowania półprzezroczystych mapy bitowe i nie jest przeznaczona do wywoływania bezpośrednio przez programistę.

Jeśli używasz wersji metody, która ma *dstPixel*, kolor końcowy to kombinacja *dstPixel* i *srcPixel*. *SrcPixel* kolor jest częściowo przezroczysty kolor na kolor podstawowy *dstPixel*.

##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask

Tworzy mapę bitową, który może służyć jako cienia.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parametry

*nDepth*<br/>
[in] Szerokość i wysokość w tle.

*clrBase*<br/>
[in] Kolor cienia.

*iMinBrightness*<br/>
[in] Minimalna jasność cienia.

*iMaxBrightness*<br/>
[in] Maksymalna jasność cienia.

### <a name="return-value"></a>Wartość zwracana

Dojście do utworzonej mapy bitowej, jeśli ta metoda się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli *nDepth* jest ustawiona na 0, ta metoda kończy działanie i zwraca wartość NULL. Jeśli *nDepth* jest mniejszy niż 3, szerokość i wysokość w tle są ustawione na 3 pikseli.

##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL

Konwertuje kolor z reprezentację czerwonego, zielonego i niebieskiego (RGB) na odcień, nasycenie i reprezentacji jasności (HSL).

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*rgb*|[in] Kolor wartości RGB.|
|*H*|[out] Wskaźnik na wartość typu double, której metody przechowuje odcień koloru.|
|*S*|[out] Wskaźnik na wartość typu double, której metody przechowuje nasycenie koloru.|
|*L*|[out] Wskaźnik na wartość typu double, której metody przechowuje jasność koloru.|

### <a name="remarks"></a>Uwagi

Kolor, który może być reprezentowany jako HSV (odcień, nasycenie i wartości), HSL (hue, nasycenia i jasności) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolor zobacz [kolor](/windows/desktop/uxguide/vis-color).

Wartość zwrócona *H* jest reprezentowany jako ułamek od 0 do 1, gdzie 0 i 1 reprezentują czerwony. Wartości zwracane przez *S* i *L* są liczby z zakresu od 0 do 1.

##  <a name="rgbtohsv"></a>  CDrawingManager::RGBtoHSV

Konwertuje kolor z reprezentacji RGB do reprezentacji HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parametry

*rgb*<br/>
[in] Kolor do przekonwertowania w reprezentacji RGB.

*H*<br/>
[out] Wskaźnik na wartość typu double, w której ta metoda przechowuje wynikowy odcień koloru.

*S*<br/>
[out] Wskaźnik na wartość typu double, w której ta metoda przechowuje wynikowy nasycenie koloru.

*V*<br/>
[out] Wskaźnik na wartość typu double, w której ta metoda przechowuje wartość wynikowa koloru.

### <a name="remarks"></a>Uwagi

Kolor, który może być reprezentowany jako HSV (odcień, nasycenie i wartości), HSL (hue, nasycenia i jasności) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolor zobacz [kolor](/windows/desktop/uxguide/vis-color).

Wartość zwrócona *H* jest liczbą z zakresu od 0 do 360, gdzie zarówno 0 do 360 wskazują czerwony. Zwracania wartości *S* i *V* są liczby z zakresu od 0 do 1.

##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel

Kolory przezroczyste pikseli mapy bitowej.

```
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,
    CRect rect,
    int x,
    int y,
    int percent,
    int iShadowSize,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bIsRight = TRUE);
```

### <a name="parameters"></a>Parametry

*pBits*<br/>
[in] Wskaźnik do wartości bitowe mapy bitowej.

*Rect*<br/>
[in] Prostokątny obszar w aplikacji. Rysowanie Menedżera rysuje w tle, poniżej i w prawo tego obszaru.

*x*<br/>
[in] Współrzędna poziomy pikseli na kolor.

*y*<br/>
[in] Współrzędna pionowy pikseli na kolor.

*percent*<br/>
[in] Procent przezroczystości.

*iShadowSize*<br/>
[in] Szerokość i wysokość w tle.

*clrBase*<br/>
[in] Kolor cienia.

*bIsRight*<br/>
[in] Parametrów logiczny, który wskazuje, które pikseli na kolor. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Ta metoda jest metodą pomocnika, która jest używana przez [CDrawingManager::DrawShadow](#drawshadow) metody. Firma Microsoft zaleca, aby narysować w tle, wywołujące `CDrawingManager::DrawShadow` zamiast tego.

Jeśli *bIsRight* jest ustawiona na wartość TRUE, piksel kolor jest mierzony *x* pikseli od prawej krawędzi *prostokąt*. Jeśli jest to wartość FALSE, piksel kolor jest mierzony *x* pikseli od lewej krawędzi *prostokąt*.

##  <a name="setpixel"></a>  CDrawingManager::SetPixel

Zmiany określonego koloru piksela mapy bitowej.

```
static void __stdcall SetPixel(
    COLORREF* pBits,
    int cx,
    int cy,
    int x,
    int y,
    COLORREF color);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pBits*|[in] Wskaźnik do wartości bitowe mapy bitowej.|
|*cx*|[in] Łączna szerokość mapy bitowej.|
|*cy*|[in] Całkowita wysokość mapy bitowej.|
|*x*|[in] Współrzędna x piksel w mapie bitowej można zmienić.|
|*y*|[in] Współrzędna y piksel w mapie bitowej można zmienić.|
|*Kolor*|[in] Nowy kolor piksela o podanej współrzędnych.|

##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors

Łączy dwa kolory oparte na ważona współczynnik.

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*color1*|[in] Pierwszy kolor połączenie.|
|*color2*|[in] Drugi kolor połączenie.|
|*dblLumRatio*|[in] Współczynnik jasność nowy kolor. `SmartMixColors` Mnoży jasność koloru mieszane przez ten stosunek przed ustaleniem ostateczny kolor.|
|*k1*|[in] Ważona współczynnik pierwszy kolor.|
|*k2*|[in] Ważona współczynnik drugi kolor.|

### <a name="return-value"></a>Wartość zwracana

Kolor, który reprezentuje ważona kombinację podane kolorów.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem z powodu błędu Jeśli *k1* lub *k2* jest mniejsza niż zero. Jeśli oba te parametry są ustawione na 0, metoda zwraca `RGB(0, 0, 0)`.

Ważona współczynnik oblicza się przy użyciu następującej formuły: (kolorem1 \* k1 + color2 \* k2) /(k1 + k2). Po ważona stosunek jest określony, metoda oblicza jasność koloru mieszanego. Następnie mnoży jasność przez *dblLumRatio*. Jeśli wartość jest większa niż 1.0, metody ustawia jasność koloru mieszane na nową wartość. W przeciwnym razie jasność jest równa 1.0.

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

Źródłowy kontroler domeny zawartość wewnątrz danego prostokąt obraca się o 90 stopni.

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parametry

*rectDest*<br/>
Prostokąta docelowego.

*dcSrc*<br/>
Kontekst urządzenia źródłowego.

*bClockWise*<br/>
Wartość TRUE wskazuje, obracania + 90 stopni; Wartość FALSE wskazuje, obracania-90 stopni.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
