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
ms.openlocfilehash: 73c5775c2cb83dea79401615b31f2194094fac8e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753240"
---
# <a name="cdrawingmanager-class"></a>Klasa CDrawingManager

Klasa `CDrawingManager` implementuje złożone algorytmy rysowania.

## <a name="syntax"></a>Składnia

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Konstruuje `CDrawingManager` obiekt.|
|`CDrawingManager::~CDrawingManager`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Tworzy 32-bitową mapę bitową niezależną od urządzenia (DIB), do którą aplikacje mogą zapisywać bezpośrednio.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczyste piksele.|
|[CDrawingManager::DrawRotated](#drawrotated)|Obraca źródłową zawartość dc wewnątrz danego prostokąta o +/- 90 stopni|
|[CDrawingManager::DrawEllipse](#drawellipse)|Rysuje elipsę z podanymi kolorami wypełnienia i obramowania.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Rysuje pierścień i wypełnia go gradientem kolorów.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Rysuje linię.|
|[CDrawingManager::DrawRect](#drawrect)|Rysuje prostokąt z dołączonymi kolorami wypełnienia i obramowania.|
|[CDrawingManager::DrawShadow](#drawshadow)|Rysuje cień dla prostokątnego obszaru.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Wypełnia prostokątny obszar dwoma gradientami kolorów.|
|[CDrawingManager::FillGradient](#fillgradient)|Wypełnia prostokątny obszar określonym gradientem kolorów.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Wypełnia prostokątny obszar określonym gradientem kolorów. Określono również kierunek zmiany koloru gradientu.|
|[CDrawingManager::GrayRect](#grayrect)|Wypełnia prostokąt określonym szarym kolorem.|
|[CDrawingManager::HighlightRect](#highlightrect)|Podświetla prostokątny obszar.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Konwertuje kolor z reprezentacji HLS na reprezentację RGB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Konwertuje kolor z reprezentacji HLS na reprezentację RGB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Konwertuje kolor z reprezentacji HSV na reprezentację RGB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Metoda pomocnika konwertuje wartość odcienia na składnik czerwony, zielony lub niebieski.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Odwraca prostokątny obszar.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Metoda pomocnika, która określa końcowy kolor dla piksela półprzezroczystego.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Tworzy mapę bitową, która może służyć jako cień.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Konwertuje kolor z reprezentacji RGB na reprezentację HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Konwertuje kolor z reprezentacji RGB na reprezentację HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Metoda pomocnika, która koloruje częściowo przezroczysty piksel na mapie bitowej.|
|[CDrawingManager::SetPixel](#setpixel)|Metoda pomocnika, która zmienia pojedynczy piksel w mapie bitowej na określony kolor.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Łączy dwa kolory na podstawie współczynnika ważonego.|

## <a name="remarks"></a>Uwagi

Klasa `CDrawingManager` udostępnia funkcje rysowania cieni, gradientów kolorów i wyróżnionych prostokątów. Wykonuje również mieszanie alfa. Tej klasy można użyć do bezpośredniej zmiany interfejsu użytkownika aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdrawmanager.h

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager

Konstruuje [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) obiektu.

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
[w] Odwołanie do kontekstu urządzenia. Używa `CDrawingManager` tego kontekstu do rysowania.

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32

Tworzy 32-bitową mapę bitową niezależną od urządzenia (DIB), do którą aplikacje mogą zapisywać bezpośrednio.

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
|*Rozmiar*|[w] Parametr [CSize,](../../atl-mfc-shared/reference/csize-class.md) który wskazuje rozmiar mapy bitowej.|
|*pBits (pBits)*|[na zewnątrz] Wskaźnik do wskaźnika danych, który odbiera lokalizację wartości bitowych DIB.|
|*Bitmapy*|Uchwyt do oryginalnej mapy bitowej|
|*clrPrzezroczysty*|Wartość RGB określająca przezroczysty kolor oryginalnej mapy bitowej.|

### <a name="return-value"></a>Wartość zwracana

Dojście do nowo utworzonej mapy bitowej DIB, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia mapy bitowej DIB, zobacz [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap).

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a>CDrawingManager::DrawAlpha

Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczyste piksele.

```cpp
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parametry

*pDstDC*<br/>
[w] Wskaźnik do kontekstu urządzenia dla miejsca docelowego.

*reectDst*<br/>
[w] Prostokąt docelowy.

*pSrcDC*<br/>
[w] Wskaźnik do kontekstu urządzenia dla źródła.

*rectSrc*<br/>
[w] Prostokąt źródłowy.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje alfa-mieszania dla dwóch map bitowych. Aby uzyskać więcej informacji na temat mieszania alfa, zobacz [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) w windows SDK.

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a>CDrawingManager::DrawEllipse

Rysuje elipsę z podanymi kolorami wypełnienia i obramowania.

```cpp
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[w] Prostokąt ograniczający elipsy.

*clrFill (wysyp*<br/>
[w] Kolor używany przez tę metodę do wypełnienia elipsy.

*clrLine (linia clrline)*<br/>
[w] Kolor, którego ta metoda używa jako obramowania elipsy.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca bez rysowania elipsy, jeśli którykolwiek kolor jest ustawiony na -1. Zwraca również bez rysowania elipsy, jeśli którykolwiek z wymiarów prostokąta ograniczającego wynosi 0.

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a>CDrawingManager::DrawGradientRing

Rysuje pierścień i wypełnia go gradientem kolorów.

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
[w] A [CRect](../../atl-mfc-shared/reference/crect-class.md) parametr, który określa granicę dla pierścienia gradientu.

*colorStart*<br/>
[w] Pierwszy kolor gradientu.

*colorFinish (wykańźnik kolorów*<br/>
[w] Ostatni kolor gradientu.

*colorBorder (nazwa)*<br/>
[w] Kolor obramowania.

*nAngle (właśc.*<br/>
[w] Parametr określający początkowy kąt rysowania gradientu. Ta wartość powinna wynosić od 0 do 360.

*nWidth (ww.*<br/>
[w] Szerokość obramowania pierścienia.

*clrFace (clrFace)*<br/>
[w] Kolor wnętrza pierścienia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Prostokąt zdefiniowany przez *rect* musi mieć co najmniej 5 pikseli szerokości i 5 pikseli wysokości.

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Rysuje linię.

```cpp
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
|*x1*|[w] Współrzędna x, w której rozpoczyna się linia.|
|*y1*|[w] Współrzędna y, w której rozpoczyna się linia.|
|*x2*|[w] Współrzędna x, na której kończy się linia.|
|*y2*|[w] Współrzędna y, na której kończy się linia.|
|*clrLine (linia clrline)*|[w] Kolor linii.|

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli *clrLine* jest równa -1.

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a>CDrawingManager::DrawRect

Rysuje prostokąt z dołączonymi kolorami wypełnienia i obramowania.

```cpp
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[w] Granice prostokąta.

*clrFill (wysyp*<br/>
[w] Kolor używany przez tę metodę do wypełnienia prostokąta.

*clrLine (linia clrline)*<br/>
[w] Kolor używany przez tę metodę dla obramowania prostokąta.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca bez rysowania prostokąta, jeśli którykolwiek kolor jest ustawiony na -1. Zwraca również, jeśli którykolwiek z wymiarów prostokąta jest 0.

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a>CDrawingManager::DrawShadow

Rysuje cień dla prostokątnego obszaru.

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
[w] Prostokątny obszar w aplikacji. Menedżer rysunku narysowa cień pod tym obszarem.

*nDepth*<br/>
[w] Szerokość i wysokość cienia.

*iMinBrightness (prawo) iMinBrightness*<br/>
[w] Minimalna jasność cienia.

*iMaxBrightness (prawo)*<br/>
[w] Maksymalna jasność cienia.

*pBmpSaveBottom*<br/>
[w] Wskaźnik do mapy bitowej zawierającej obraz dolnej części cienia.

*pBmpSaveRight*<br/>
[w] Wskaźnik do mapy bitowej zawierającej obraz cienia rysowanego po prawej stronie prostokąta.

*baza clrBase*<br/>
[w] Kolor cienia.

*bPrawaszdow*<br/>
[w] Parametr logiczny wskazujący sposób rysowania cienia. Jeśli *bRightShadow* jest `TRUE`, `DrawShadow` rysuje cień po prawej stronie prostokąta.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można podać dwie prawidłowe mapy bitowe dla dolnego i prawego cienia za pomocą parametrów *pBmpSaveBottom* i *pBmpSaveRight*. Jeśli te [CBitmap](../../mfc/reference/cbitmap-class.md) obiekty mają dołączony obiekt `DrawShadow` GDI, użyje tych map bitowych jako cienie. Jeśli `CBitmap` parametry nie mają dołączonego obiektu GDI, `DrawShadow` rysuje cień i dołącza mapy bitowe do parametrów. W przyszłych `DrawShadow`wywołaniach do , można podać te mapy bitowe, aby przyspieszyć proces rysowania. Aby uzyskać więcej `CBitmap` informacji na temat klasy i obiektów GDI, zobacz [Obiekty graficzne](../../mfc/graphic-objects.md).

Jeśli którykolwiek z `NULL`tych `DrawShadow` parametrów jest , automatycznie narysuje cień.

Jeśli ustawisz *wartość bRightShadow* na FAŁSZ, cień zostanie narysowany pod spodem i po lewej stronie prostokątnego obszaru.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `DrawShadow` metody `CDrawingManager` klasy. Ten fragment kodu jest częścią [próbki demo arkusza prop](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient

Wypełnia prostokątny obszar dwoma gradientami kolorów.

```cpp
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
[w] Prostokąt do wypełnienia.

*colorStart1*<br/>
[w] Początkowy kolor dla pierwszego gradientu kolorów.

*colorFinish1*<br/>
[w] Końcowy kolor dla pierwszego gradientu kolorów.

*colorStart2*<br/>
[w] Początkowy kolor dla drugiego gradientu kolorów.

*colorFinish2*<br/>
[w] Końcowy kolor dla drugiego gradientu kolorów.

*Bhorz*<br/>
[w] Parametr logiczny wskazujący, `Fill4ColorsGradient` czy kolory gradientu poziomego czy pionowego. Wartość TRUE wskazuje gradient poziomy.

*Npercentage*<br/>
[w] Całkowitej od 0-100. Ta wartość wskazuje procent prostokąta, który ma wypełnić pierwszym gradientem kolorów.

### <a name="remarks"></a>Uwagi

Gdy prostokąt jest wypełniony dwoma gradientami kolorów, znajdują się one nad sobą lub obok siebie, w zależności od wartości *bHorz*. Każdy gradient kolorów jest obliczany niezależnie metodą [CDrawingManager::FillGradient](#fillgradient).

Ta metoda generuje błąd potwierdzenia, jeśli *nPercentage* jest mniejsza niż 0 lub więcej niż 100.

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a>CDrawingManager::FillGradient

Wypełnia prostokątny obszar określonym gradientem kolorów.

```cpp
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
[w] Prostokątny obszar do wypełnienia.

*colorStart*<br/>
[w] Pierwszy kolor gradientu.

*colorFinish (wykańźnik kolorów*<br/>
[w] Końcowy kolor gradientu.

*Bhorz*<br/>
[w] Parametr logiczny określający, `FillGradient` czy należy narysować gradient poziomy czy pionowy.

*nStartFlatPercentage*<br/>
[w] Procent prostokąta wypełniającego `FillGradient` *kolorStart* przed rozpoczęciem gradientu.

*nEndFlatPercentage*<br/>
[w] Procent prostokąta wypełnianego `FillGradient` *koloremKończy* po zakończeniu gradientu.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `FillGradient` metody `CDrawingManager` klasy. Ten fragment kodu jest częścią [przykładu demo pakietu MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a>CDrawingManager::FillGradient2

Wypełnia prostokątny obszar określonym gradientem kolorów.

```cpp
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[w] Prostokątny obszar do wypełnienia.

*colorStart*<br/>
[w] Pierwszy kolor gradientu.

*colorFinish (wykańźnik kolorów*<br/>
[w] Ostatni kolor gradientu.

*nAngle (właśc.*<br/>
[w] Liczą całkowitą z 0 do 360. Ten parametr określa kierunek gradientu kolorów.

### <a name="remarks"></a>Uwagi

Użyj *nAngle,* aby określić kierunek gradientu kolorów. Po określeniu kierunku gradientu kolorów należy również określić, gdzie rozpoczyna się gradient kolorów. Wartość 0 dla *nAngle* wskazuje, że gradient zaczyna się od góry prostokąta. Wraz *ze wzrostem nAngle,* położenie początkowe gradientu przesuwa się w kierunku przeciwnym do ruchu wskazówek zegara w zależności od kąta.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `FillGradient2` metody `CDrawingManager` klasy. Ten fragment kodu jest częścią [próbki Nowe formanty](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a>CDrawingManager::GrayRect

Wypełnia prostokąt określonym szarym kolorem.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[w] Prostokątny obszar do wypełnienia.

*Npercentage*<br/>
[w] Procent szarości, który ma być szary w prostokącie.

*clrPrzezroczysty*<br/>
[w] Kolor przezroczysty.

*clrDisabled ( clrDisabled )*<br/>
[w] Kolor, który ta metoda używa do usuwania nasycenia if *nPercentage* jest ustawiona na -1.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Dla parametru *nPercentage*niższa wartość wskazuje ciemniejszy kolor.

Maksymalna wartość *nPercentage* wynosi 200. Wartość większa niż 200 nie zmienia wyglądu prostokąta. Jeśli wartość jest -1, ta metoda używa *clrDisabled* ograniczyć nasycenie prostokąta.

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a>CDrawingManager::HighlightRect

Podświetla prostokątny obszar.

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
[w] Prostokątny obszar do podświetlenia.

*Npercentage*<br/>
[w] Procent wskazujący, jak przezroczyste powinno być podświetlenie.

*clrPrzezroczysty*<br/>
[w] Kolor przezroczysty.

*nTolerancja*<br/>
[w] Liczba całkowita z 0 do 255 wskazująca tolerancję kolorów.

*clrBlend ( clrBlend )*<br/>
[w] Kolor bazowy do mieszania.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

If *nPercentage* jest między 0 `HighlightRect` i 99, używa algorytmu mieszania alfa. Aby uzyskać więcej informacji na temat mieszania alfa, zobacz [Alfa mieszanie linii i wypełnień](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Jeśli *nPercentage* wynosi -1, ta metoda używa domyślnego poziomu podświetlenia. Jeśli *nPercentage* wynosi 100, ta metoda nic nie robi i zwraca wartość TRUE.

Metoda używa parametru *nTolerancja,* aby ustalić, czy podświetlić prostokątny obszar. Aby wyróżnić prostokąt, różnica między kolorem tła aplikacji a *clrTransparent* musi być mniejsza niż *nTolerancja* w każdym składniku koloru (czerwonym, zielonym i niebieskim).

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE

Konwertuje kolor z reprezentacji HLS na reprezentację RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[w] Liczba z 0 do 1 reprezentująca barwę koloru.

*L*<br/>
[w] Liczba z 0 do 1, która wskazuje jasność koloru.

*S*<br/>
[w] Liczba z 0 do 1, która wskazuje nasycenie koloru.

### <a name="return-value"></a>Wartość zwracana

Reprezentacja RGB dostarczonego koloru HLS.

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Kolor](/windows/win32/uxguide/vis-color).

Ta metoda `CDrawingManager::HLStoRGB_TWO` i metoda wykonać tę samą operację, ale wymagają różnych wartości dla *H* parametru. W tej metodzie *H* jest procentem okręgu. W `CDrawingManager::HLStoRGB_TWO` metodzie *H* jest wartością stopnia między 0 i 360, które reprezentują kolor czerwony. Na przykład `HLStoRGB_ONE`z wartością 0,25 dla *H* jest odpowiednikiem wartości `HLStoRGB_TWO`90 z .

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO

Konwertuje kolor z reprezentacji HLS na reprezentację RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[w] Liczba z 0 do 360 reprezentująca odcień koloru.

*L*<br/>
[w] Liczba z 0 do 1, która wskazuje jasność koloru.

*S*<br/>
[w] Liczba z 0 do 1, która wskazuje nasycenie koloru.

### <a name="return-value"></a>Wartość zwracana

Reprezentacja RGB dostarczonego koloru HLS.

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Kolor](/windows/win32/uxguide/vis-color).

Ta metoda i [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metoda wykonać tę samą operację, ale wymagają różnych wartości dla *H* parametru. W tej metodzie *H* jest wartością stopnia między 0 i 360, które reprezentują kolor czerwony. W [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metoda *H* jest procent okręgu. Na przykład `HLStoRGB_ONE`z wartością 0,25 dla *H* jest odpowiednikiem wartości `HLStoRGB_TWO`90 z .

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB

Konwertuje kolor z reprezentacji HSV na reprezentację RGB.

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
|*H*|[w] Liczba z 0 do 360, która wskazuje odcień koloru.|
|*S*|[w] Liczba z 0 do 1, która wskazuje nasycenie koloru.|
|*V*|[w] Liczba z 0 do 1, która wskazuje wartość koloru.|

### <a name="return-value"></a>Wartość zwracana

Reprezentacja RGB dostarczonego koloru HSV.

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Kolor](/windows/win32/uxguide/vis-color).

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a>CDrawingManager::HuetoRGB

Konwertuje wartość odcienia na komponent czerwony, zielony lub niebieski.

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
[w] Zobacz uwagi.

*m2*<br/>
[w] Zobacz uwagi.

*H*<br/>
[w] Zobacz uwagi.

*rm1*<br/>
[w] Zobacz uwagi.

*rm2*<br/>
[w] Zobacz uwagi.

*Rh*<br/>
[w] Zobacz uwagi.

### <a name="return-value"></a>Wartość zwracana

Indywidualny czerwony, zielony lub niebieski składnik dla podanego odcienia.

### <a name="remarks"></a>Uwagi

Ta metoda jest metodą `CDrawingManager` pomocniczą, która jest używana przez klasę do obliczania poszczególnych składników czerwony, zielony i niebieski koloru w reprezentacji HSV lub HSL. Ta metoda nie jest przeznaczona do wywoływania bezpośrednio przez programistę. Parametry wejściowe są wartościami zależnymi od algorytmu konwersji.

Aby przekonwertować kolor HSV lub HSL na reprezentację RGB, należy wywołać jedną z następujących metod:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a>CDrawingManager::MirrorRect

Odwraca prostokątny obszar.

```cpp
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[w] Prostokąt ograniczający obszaru do przerzucenia.

*Bhorz*<br/>
[w] Parametr logiczny wskazujący, czy prostokąt przerzuca się w poziomie czy w pionie.

### <a name="remarks"></a>Uwagi

Ta metoda można przerzucić dowolny obszar `CDrawingManager` kontekstu urządzenia należącego do klasy. Jeśli *bHorz* jest ustawiona na WARTOŚĆ PRAWDA, ta metoda przerzuca obszar w poziomie. W przeciwnym razie przerzuca obszar w pionie.

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a>CDrawingManager::PixelAlpha

Oblicza końcowy kolor dla piksela półprzezroczystego.

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

*srcPixel (srcPixel)*<br/>
[w] Początkowy kolor piksela.

*Procent*<br/>
[w] Liczba z przedziału od 0 do 100 reprezentująca procent przezroczystości. Wartość 100 wskazuje, że początkowy kolor jest całkowicie przezroczysty.

*percentr (w tym)*<br/>
[w] Liczba z przedziału od 0 do 100 reprezentująca procent przezroczystości czerwonego składnika.

*percentg*<br/>
[w] Liczba z przedziału od 0 do 100 reprezentująca procent przezroczystości dla komponentu zielonego.

*percentB (1000*<br/>
[w] Liczba z przedziału od 0 do 100 reprezentująca procent przezroczystości dla niebieskiego składnika.

*dstPixel ( dstPixel )*<br/>
[w] Kolor bazowy piksela.

### <a name="return-value"></a>Wartość zwracana

Końcowy kolor dla piksela półprzezroczystego.

### <a name="remarks"></a>Uwagi

Jest to klasa pomocnika do kolorowania półprzezroczyste mapy bitowe i nie jest przeznaczony do wywoływania bezpośrednio przez programistę.

Podczas korzystania z wersji metody, która ma *dstPixel*, końcowy kolor jest kombinacją *dstPixel* i *srcPixel*. Kolor *srcPixel* jest częściowo przezroczysty kolor na kolor bazowy *dstPixel*.

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask

Tworzy mapę bitową, która może służyć jako cień.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parametry

*nDepth*<br/>
[w] Szerokość i wysokość cienia.

*baza clrBase*<br/>
[w] Kolor cienia.

*iMinBrightness (prawo) iMinBrightness*<br/>
[w] Minimalna jasność cienia.

*iMaxBrightness (prawo)*<br/>
[w] Maksymalna jasność cienia.

### <a name="return-value"></a>Wartość zwracana

Dojście do utworzonej mapy bitowej, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli *nDepth* jest ustawiona na 0, ta metoda kończy działanie i zwraca wartość NULL. Jeśli *nDepth* jest mniejsza niż 3, szerokość i wysokość cienia są ustawione na 3 piksele.

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL

Konwertuje kolor z reprezentacji czerwonej, zielonej i niebieskiej (RGB) na reprezentację odcienia, nasycenia i lekkości (HSL).

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
|*Rgb*|[w] Kolor w wartościach RGB.|
|*H*|[na zewnątrz] Wskaźnik do double, gdzie metoda przechowuje odcień dla koloru.|
|*S*|[na zewnątrz] Wskaźnik do double, gdzie metoda przechowuje nasycenie koloru.|
|*L*|[na zewnątrz] Wskaźnik do double, gdzie metoda przechowuje lekkość koloru.|

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Kolor](/windows/win32/uxguide/vis-color).

Zwrócona wartość dla *H* jest reprezentowana jako ułamek między 0 i 1, gdzie zarówno 0, jak i 1 reprezentują kolor czerwony. Zwracane wartości dla *S* i *L* są liczbami z 0 i 1.

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV

Konwertuje kolor z reprezentacji RGB na reprezentację HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parametry

*Rgb*<br/>
[w] Kolor do konwersji w reprezentacji RGB.

*H*<br/>
[na zewnątrz] Wskaźnik do double, gdzie ta metoda przechowuje wynikowy odcień dla koloru.

*S*<br/>
[na zewnątrz] Wskaźnik do double, gdzie ta metoda przechowuje wynikowe nasycenie koloru.

*V*<br/>
[na zewnątrz] Wskaźnik do double, gdzie ta metoda przechowuje wynikową wartość dla koloru.

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Kolor](/windows/win32/uxguide/vis-color).

Zwrócona wartość dla *H* jest liczbą z 0 a 360, gdzie zarówno 0, jak i 360 wskazują kolor czerwony. Zwracane wartości dla *S* i *V* są liczbami od 0 do 1.

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel

Koloryzuje przezroczysty piksel na mapie bitowej.

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

*pBits (pBits)*<br/>
[w] Wskaźnik do wartości bitowych mapy bitowej.

*Rect*<br/>
[w] Prostokątny obszar w aplikacji. Menedżer rysunku rysuje cień pod spodem i po prawej stronie tego obszaru.

*X*<br/>
[w] Pozioma współrzędna piksela do koloru.

*Y*<br/>
[w] Pionowa współrzędna piksela do koloru.

*Procent*<br/>
[w] Procent przezroczystości.

*Rozmiar iShadowSize*<br/>
[w] Szerokość i wysokość cienia.

*baza clrBase*<br/>
[w] Kolor cienia.

*bIsRight (Prawo)*<br/>
[w] Parametr logiczny wskazujący, który piksel ma być kolorowy. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Ta metoda jest metoda pomocnika, który jest używany przez [CDrawingManager::DrawShadow](#drawshadow) metody. Zaleca się, aby jeśli chcesz narysować cień, zamiast tego zadzwoń. `CDrawingManager::DrawShadow`

Jeśli *wartość bIsRight* jest ustawiona na WARTOŚĆ TRUE, piksel na kolor jest mierzony *x* pikselami od prawej krawędzi *rect*. Jeśli jest false, piksel do koloru jest mierzona *x* pikseli od lewej krawędzi *rect*.

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a>CDrawingManager::SetPixel

Zmienia pojedynczy piksel w mapie bitowej na określony kolor.

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
|*pBits (pBits)*|[w] Wskaźnik do wartości bitowych mapy bitowej.|
|*Cx*|[w] Całkowita szerokość mapy bitowej.|
|*Cy*|[w] Całkowita wysokość mapy bitowej.|
|*X*|[w] X-współrzędna piksela w mapie bitowej, aby zmienić.|
|*Y*|[w] Współrzędna y piksela w mapie bitowej do zmiany.|
|*color*|[w] Nowy kolor dla piksela identyfikowany przez dostarczone współrzędne.|

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a>CDrawingManager::SmartMixColors

Łączy dwa kolory na podstawie współczynnika ważonego.

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
|*kolor1*|[w] Pierwszy kolor do mieszania.|
|*kolor2*|[w] Drugi kolor do mieszania.|
|*dblLumRatio ( dblLumRatio )*|[w] Stosunek jasności nowego koloru. `SmartMixColors`mnoży jasność mieszanego koloru przez ten stosunek przed określeniem koloru końcowego.|
|*k1*|[w] Współczynnik ważony dla pierwszego koloru.|
|*k2*|[w] Współczynnik ważony dla drugiego koloru.|

### <a name="return-value"></a>Wartość zwracana

Kolor reprezentujący ważony mieszaninę dostarczonych kolorów.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem z błędem, jeśli *k1* lub *k2* jest mniejsza niż zero. Jeśli oba te parametry są ustawione na `RGB(0, 0, 0)`0, metoda zwraca .

Współczynnik ważony oblicza się za pomocą \* następującego wzoru: (kolor 1 k1 + kolor2 \* k2)/(k1 + k2). Po określeniu współczynnika ważonym metoda oblicza jasność dla koloru mieszanego. Następnie mnoży jasność przez *dblLumRatio*. Jeśli wartość jest większa niż 1,0, metoda ustawia jasność dla mieszanego koloru na nową wartość. W przeciwnym razie jasność jest ustawiona na 1,0.

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a>CDrawingManager::DrawRotated

Obraca źródłową zawartość kontrolera domeny wewnątrz danego prostokąta o 90 stopni.

```cpp
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parametry

*reectDest*<br/>
Prostokąt docelowy.

*dcSrc ( dcSrc )*<br/>
Kontekst urządzenia źródłowego.

*bClockWise*<br/>
WARTOŚĆ TRUE oznacza obrót o +90 stopni; FALSE oznacza obrót o -90 stopni.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
