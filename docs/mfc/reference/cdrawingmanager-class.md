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
ms.openlocfilehash: 69365b66b12d5a9284c9b097b225ba041e07b6b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506806"
---
# <a name="cdrawingmanager-class"></a>Klasa CDrawingManager

`CDrawingManager` Klasa implementuje złożone algorytmy rysowania.

## <a name="syntax"></a>Składnia

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Konstruuje `CDrawingManager` obiekt.|
|`CDrawingManager::~CDrawingManager`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Tworzy 32-bitową mapę bitową niezależną od urządzenia (DIB), do której aplikacje mogą bezpośrednio pisać.|
|[CDrawingManager::D rawAlpha](#drawalpha)|Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczyste piksele.|
|[CDrawingManager::D rawRotated](#drawrotated)|Obrót źródłowej zawartości kontrolera domeny wewnątrz danego prostokąta przez +/-90 stopni|
|[CDrawingManager::DrawEllipse](#drawellipse)|Rysuje elipsę z podanymi kolorami wypełnienia i obramowania.|
|[CDrawingManager::D rawGradientRing](#drawgradientring)|Rysuje pierścień i wypełnia go kolorem gradientu.|
|[CDrawingManager::D rawLine, CDrawingManager::D rawLineA](#drawline_cdrawingmanager__drawlinea)|Rysuje linię.|
|[CDrawingManager::D rawRect](#drawrect)|Rysuje prostokąt z podanymi kolorami wypełnienia i obramowania.|
|[CDrawingManager::D rawShadow](#drawshadow)|Rysuje cień prostokątnego obszaru.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Wypełnia prostokątny obszar dwoma gradientami koloru.|
|[CDrawingManager::FillGradient](#fillgradient)|Wypełnia prostokątny obszar za pomocą określonego gradientu koloru.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Wypełnia prostokątny obszar za pomocą określonego gradientu koloru. Określono również kierunek zmiany koloru gradientu.|
|[CDrawingManager::GrayRect](#grayrect)|Wypełnia prostokąt z określonym szarym kolorem.|
|[CDrawingManager::HighlightRect](#highlightrect)|Podświetla prostokątny obszar.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Konwertuje kolor z reprezentacji HLS na reprezentację RGB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Konwertuje kolor z reprezentacji HLS na reprezentację RGB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Konwertuje kolor z reprezentacji HSV na reprezentację RGB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Metoda pomocnika, która konwertuje wartość odcienia na składnik czerwony, zielony lub niebieski.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Przerzuca prostokątny obszar.|
|[CDrawingManager::P ixelAlpha](#pixelalpha)|Metoda pomocnika, która określa kolor końcowy dla półprzezroczystego piksela.|
|[CDrawingManager::P repareShadowMask](#prepareshadowmask)|Tworzy mapę bitową, która może być używana jako cień.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Konwertuje kolor z reprezentacji RGB na reprezentację HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Konwertuje kolor z reprezentacji RGB na reprezentację HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Metoda pomocnika, która koloruje częściowo przezroczysty piksel w mapie bitowej.|
|[CDrawingManager:: SetPixel](#setpixel)|Metoda pomocnika, która zmienia pojedynczy piksel w mapie bitowej z określonym kolorem.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Łączy dwa kolory na podstawie współczynnika ważonego.|

## <a name="remarks"></a>Uwagi

`CDrawingManager` Klasa zawiera funkcje do rysowania cieni, gradientów kolorów i wyróżnionych prostokątów. Wykonuje także mieszanie alfa. Możesz użyć tej klasy, aby bezpośrednio zmienić interfejs użytkownika aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdrawmanager. h

##  <a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager

Konstruuje obiekt [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) .

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parametry

*DC*<br/>
podczas Odwołanie do kontekstu urządzenia. `CDrawingManager` Używa tego kontekstu do rysowania.

##  <a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32

Tworzy 32-bitową mapę bitową niezależną od urządzenia (DIB), do której aplikacje mogą bezpośrednio pisać.

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
|*zmienia*|podczas Parametr [CSize](../../atl-mfc-shared/reference/csize-class.md) , który wskazuje rozmiar mapy bitowej.|
|*pBits*|określoną Wskaźnik do wskaźnika danych, który odbiera lokalizację wartości bitowych DIB.|
|*mapy*|Uchwyt do oryginalnej mapy bitowej|
|*clrTransparent*|Wartość RGB określająca przezroczysty kolor oryginalnej mapy bitowej.|

### <a name="return-value"></a>Wartość zwracana

Dojście do nowo utworzonej mapy bitowej DIB, jeśli ta metoda zakończy się pomyślnie. w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia mapy bitowej DIB, zobacz [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap).

##  <a name="drawalpha"></a>CDrawingManager::D rawAlpha

Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczyste piksele.

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parametry

*pDstDC*<br/>
podczas Wskaźnik do kontekstu urządzenia dla miejsca docelowego.

*rectDst*<br/>
podczas Prostokąt docelowy.

*pSrcDC*<br/>
podczas Wskaźnik do kontekstu urządzenia dla źródła.

*rectSrc*<br/>
podczas Prostokąt źródłowy.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje mieszanie alfa dla dwóch map bitowych. Aby uzyskać więcej informacji na temat mieszania alfa, zobacz [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) w Windows SDK.

##  <a name="drawellipse"></a>CDrawingManager::D rawEllipse

Rysuje elipsę z podanymi kolorami wypełnienia i obramowania.

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
podczas Prostokąt ograniczający dla elipsy.

*clrFill*<br/>
podczas Kolor, którego ta metoda używa do wypełnienia elipsy.

*clrLine*<br/>
podczas Kolor, którego ta metoda używa jako obramowania elipsy.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca bez rysowania elipsy, jeśli jeden z kolorów ma ustawioną wartość-1. Zwraca również bez rysowania elipsy, jeśli każdy wymiar prostokąta granicy ma wartość 0.

##  <a name="drawgradientring"></a>CDrawingManager::D rawGradientRing

Rysuje pierścień i wypełnia go kolorem gradientu.

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

*cinania*<br/>
podczas Parametr [CRect](../../atl-mfc-shared/reference/crect-class.md) , który określa granicę dla pierścienia gradientu.

*colorStart*<br/>
podczas Pierwszy kolor gradientu.

*colorFinish*<br/>
podczas Ostatni kolor gradientu.

*colorBorder*<br/>
podczas Kolor obramowania.

*nAngle*<br/>
podczas Parametr określający początkowy kąt rysowania gradientu. Ta wartość powinna należeć do zakresu od 0 do 360.

*nWidth*<br/>
podczas Szerokość obramowania dla pierścienia.

*clrFace*<br/>
podczas Kolor wnętrza pierścienia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Prostokąt zdefiniowany przez program *Rect* musi mieć co najmniej 5 pikseli szerokości i 5 pikseli.

##  <a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::D rawLine, CDrawingManager::D rawLineA

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
|*x1*|podczas Współrzędna x, w której uruchamiany jest wiersz.|
|*y1*|podczas Współrzędna y, w której uruchamiany jest wiersz.|
|*x2*|podczas Współrzędna x, w której znajduje się linia.|
|*Y2*|podczas Współrzędna y, w której znajduje się linia.|
|*clrLine*|podczas Kolor wiersza.|

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli *clrLine* jest równe-1.

##  <a name="drawrect"></a>CDrawingManager::D rawRect

Rysuje prostokąt z podanymi kolorami wypełnienia i obramowania.

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
podczas Granice prostokąta.

*clrFill*<br/>
podczas Kolor, którego ta metoda używa do wypełnienia prostokąta.

*clrLine*<br/>
podczas Kolor, którego używa ta metoda dla obramowania prostokąta.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca bez rysowania prostokąta, jeśli jeden z kolorów ma ustawioną wartość-1. Zwraca również wtedy, gdy jeden z wymiarów prostokąta ma wartość 0.

##  <a name="drawshadow"></a>CDrawingManager::D rawShadow

Rysuje cień prostokątnego obszaru.

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

*cinania*<br/>
podczas Prostokątny obszar w aplikacji. Menedżer rysunku rysuje cień poniżej tego obszaru.

*nDepth*<br/>
podczas Szerokość i wysokość cienia.

*iMinBrightness*<br/>
podczas Minimalna jasność cienia.

*iMaxBrightness*<br/>
podczas Maksymalna jasność cienia.

*pBmpSaveBottom*<br/>
podczas Wskaźnik do mapy bitowej, która zawiera obraz dla dolnej części cienia.

*pBmpSaveRight*<br/>
podczas Wskaźnik do mapy bitowej, która zawiera obraz dla cienia, który jest rysowany po prawej stronie prostokąta.

*clrBase*<br/>
podczas Kolor cienia.

*bRightShadow*<br/>
podczas Parametr logiczny, który wskazuje sposób rysowania cienia. Jeśli *bRightShadow* jest `TRUE`, `DrawShadow` rysuje cień po prawej stronie prostokąta.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można podać dwie prawidłowe mapy bitowe dla dolnego i prawego cienia przy użyciu parametrów *pBmpSaveBottom* i *pBmpSaveRight*. Jeśli te obiekty [CBitmap](../../mfc/reference/cbitmap-class.md) mają dołączony obiekt GDI, `DrawShadow` będą używać tych map bitowych jako cieni. Jeśli parametry nie mają dołączonego obiektu GDI, program `DrawShadow` rysuje cień i dołącza mapy bitowe do parametrów. `CBitmap` W przyszłych wywołaniach `DrawShadow`do, możesz podać te mapy bitowe, aby przyspieszyć proces rysowania. Aby uzyskać więcej informacji na `CBitmap` temat klas i obiektów GDI, zobacz [grafika Objects](../../mfc/graphic-objects.md).

Jeśli jeden z tych parametrów jest `NULL`, `DrawShadow` program automatycznie narysuje cień.

Jeśli ustawisz *bRightShadow* na false, cień zostanie narysowany poniżej i po lewej stronie prostokątnego obszaru.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `DrawShadow` metody `CDrawingManager` klasy. Ten fragment kodu jest częścią [przykładu demonstracyjnego arkusza prop](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient

Wypełnia prostokątny obszar dwoma gradientami koloru.

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

*cinania*<br/>
podczas Prostokąt do wypełnienia.

*colorStart1*<br/>
podczas Początkowy kolor pierwszego gradientu koloru.

*colorFinish1*<br/>
podczas Kolor końcowy pierwszego gradientu koloru.

*colorStart2*<br/>
podczas Początkowy kolor drugiego gradientu koloru.

*colorFinish2*<br/>
podczas Kolor końcowy drugiego gradientu koloru.

*bHorz*<br/>
podczas Parametr logiczny, który wskazuje, `Fill4ColorsGradient` czy kolory gradientu poziomego lub pionowego. Wartość TRUE wskazuje gradient poziomy.

*nPercentage*<br/>
podczas Liczba całkowita z zakresu od 0-100. Ta wartość wskazuje procent prostokąta do wypełnienia z pierwszym gradientem koloru.

### <a name="remarks"></a>Uwagi

Gdy prostokąt jest wypełniony dwoma gradientami koloru, znajdują się one powyżej siebie lub obok siebie, w zależności od wartości *bHorz*. Każdy gradient koloru jest obliczany niezależnie przy użyciu metody [CDrawingManager:: FillGradient](#fillgradient).

Ta metoda generuje błąd potwierdzenia, jeśli wartość *nPercentage* jest mniejsza niż 0 lub większa niż 100.

##  <a name="fillgradient"></a>CDrawingManager::FillGradient

Wypełnia prostokątny obszar za pomocą określonego gradientu koloru.

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

*cinania*<br/>
podczas Prostokątny obszar do wypełnienia.

*colorStart*<br/>
podczas Pierwszy kolor gradientu.

*colorFinish*<br/>
podczas Końcowy kolor gradientu.

*bHorz*<br/>
podczas Parametr logiczny określający, czy `FillGradient` ma być rysowany gradient poziomy, czy pionowy.

*nStartFlatPercentage*<br/>
podczas Procent prostokąta `FillGradient` wypełniany przy użyciu *colorStart* przed rozpoczęciem gradientu.

*nEndFlatPercentage*<br/>
podczas Procent prostokąta `FillGradient` wypełniany przy użyciu *colorFinish* po zakończeniu gradientu.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `FillGradient` metody `CDrawingManager` klasy. Ten fragment kodu jest częścią [przykładu demonstracyjnego pakietu MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>CDrawingManager::FillGradient2

Wypełnia prostokątny obszar za pomocą określonego gradientu koloru.

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
podczas Prostokątny obszar do wypełnienia.

*colorStart*<br/>
podczas Pierwszy kolor gradientu.

*colorFinish*<br/>
podczas Ostatni kolor gradientu.

*nAngle*<br/>
podczas Liczba całkowita z zakresu od 0 do 360. Ten parametr określa kierunek gradientu koloru.

### <a name="remarks"></a>Uwagi

Użyj *nAngle* , aby określić kierunek gradientu koloru. Po określeniu kierunku gradientu koloru należy również określić miejsce uruchomienia gradientu koloru. Wartość 0 dla *nAngle* wskazuje, że gradient zaczyna się od góry prostokąta. W miarę wzrostu *nAngle* początkowa lokalizacja gradientu przesuwa się w kierunku do prawej w zależności od kąta.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `FillGradient2` metody `CDrawingManager` klasy. Ten fragment kodu jest częścią [nowych formantów przykładowych](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>CDrawingManager::GrayRect

Wypełnia prostokąt z określonym szarym kolorem.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
podczas Prostokątny obszar do wypełnienia.

*nPercentage*<br/>
podczas Procentowa szara w prostokącie.

*clrTransparent*<br/>
podczas Kolor przezroczysty.

*clrDisabled*<br/>
podczas Kolor, którego ta metoda używa dla nienasycenia, jeśli *nPercentage* jest ustawiona na wartość-1.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Dla parametru *nPercentage*niższa wartość oznacza ciemniejszy kolor.

Maksymalna wartość parametru *nPercentage* to 200. Wartość większa niż 200 nie zmienia wyglądu prostokąta. Jeśli wartość to-1, ta metoda używa *clrDisabled* , aby ograniczyć nasycenie prostokąta.

##  <a name="highlightrect"></a>CDrawingManager::HighlightRect

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

*cinania*<br/>
podczas Prostokątny obszar, który ma zostać wyróżniony.

*nPercentage*<br/>
podczas Wartość procentowa, która wskazuje, jak przezroczyste powinno być wyróżnienie.

*clrTransparent*<br/>
podczas Kolor przezroczysty.

*nTolerance*<br/>
podczas Liczba całkowita z zakresu od 0 do 255, która wskazuje tolerancję koloru.

*clrBlend*<br/>
podczas Kolor bazowy dla mieszania.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończy się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli *nPercentage* jest z zakresu od 0 do `HighlightRect` 99, używa algorytmu mieszania alfa. Aby uzyskać więcej informacji na temat mieszania alfa, zobacz [linie mieszania alfa i wypełnienia](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Jeśli *nPercentage* jest-1, ta metoda używa domyślnego poziomu wyróżniania. Jeśli *nPercentage* jest 100, ta metoda nie wykonuje żadnych operacji i zwraca wartość true.

Metoda używa parametru *nTolerance* do określenia, czy wyróżnić prostokątny obszar. Aby wyróżnić prostokąt, różnica między kolorem tła aplikacji i *clrTransparent* musi być mniejsza niż *nTolerance* w każdym składniku koloru (czerwony, zielony i niebieski).

##  <a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE

Konwertuje kolor z reprezentacji HLS na reprezentację RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
podczas Liczba z zakresu od 0 do 1 reprezentująca odcień koloru.

*L*<br/>
podczas Liczba z zakresu od 0 do 1, która wskazuje jaskrawość koloru.

*S*<br/>
podczas Liczba z zakresu od 0 do 1, która wskazuje nasycenie koloru.

### <a name="return-value"></a>Wartość zwracana

Reprezentacja RGB podanego koloru HLS.

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (barwa, nasycenie i wartość), HSL (barwa, nasycenie i jasność), lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Color](/windows/win32/uxguide/vis-color).

Ta metoda i `CDrawingManager::HLStoRGB_TWO` Metoda wykonują tę samą operację, ale wymagają różnych wartości parametru *H* . W tej metodzie *H* jest wartością procentową okręgu. W metodzie H jest wartością stopnia z zakresu od 0 do 360, co reprezentuje czerwony. `CDrawingManager::HLStoRGB_TWO` Na przykład, w `HLStoRGB_ONE`przypadku, wartość 0,25 dla *H* jest równa wartości 90 z `HLStoRGB_TWO`.

##  <a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO

Konwertuje kolor z reprezentacji HLS na reprezentację RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
podczas Liczba z zakresu od 0 do 360, która reprezentuje odcień koloru.

*L*<br/>
podczas Liczba z zakresu od 0 do 1, która wskazuje jaskrawość koloru.

*S*<br/>
podczas Liczba z zakresu od 0 do 1, która wskazuje nasycenie koloru.

### <a name="return-value"></a>Wartość zwracana

Reprezentacja RGB podanego koloru HLS.

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (barwa, nasycenie i wartość), HSL (barwa, nasycenie i jasność), lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Color](/windows/win32/uxguide/vis-color).

Ta metoda oraz Metoda [CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one) wykonują tę samą operację, ale wymagają różnych wartości parametru *H* . W tej metodzie *H* jest wartością stopnia z zakresu od 0 do 360, co reprezentuje czerwony. W metodzie [CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one) *H* jest wartością procentową okręgu. Na przykład, w `HLStoRGB_ONE`przypadku, wartość 0,25 dla *H* jest równa wartości 90 z `HLStoRGB_TWO`.

##  <a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB

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
|*H*|podczas Liczba z zakresu od 0 do 360, która wskazuje odcień koloru.|
|*S*|podczas Liczba z zakresu od 0 do 1, która wskazuje nasycenie koloru.|
|*V*|podczas Liczba z zakresu od 0 do 1, która wskazuje wartość koloru.|

### <a name="return-value"></a>Wartość zwracana

Reprezentacja RGB podanego koloru HSV.

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (barwa, nasycenie i wartość), HSL (barwa, nasycenie i jasność), lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Color](/windows/win32/uxguide/vis-color).

##  <a name="huetorgb"></a>CDrawingManager::HuetoRGB

Konwertuje wartość odcienia na składnik czerwony, zielony lub niebieski.

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

*M1*<br/>
podczas Zobacz uwagi.

*m*<br/>
podczas Zobacz uwagi.

*h*<br/>
podczas Zobacz uwagi.

*rm1*<br/>
podczas Zobacz uwagi.

*rm2*<br/>
podczas Zobacz uwagi.

*RH*<br/>
podczas Zobacz uwagi.

### <a name="return-value"></a>Wartość zwracana

Pojedynczy składnik czerwony, zielony lub niebieski dla podanego odcienia.

### <a name="remarks"></a>Uwagi

Ta metoda jest metodą pomocniczą używaną `CDrawingManager` przez klasę do obliczania pojedynczych składników czerwony, zielony i niebieski koloru w reprezentacji HSV lub HSL. Ta metoda nie jest przeznaczona do wywoływania bezpośrednio przez programistę. Parametry wejściowe są wartościami, które są zależne od algorytmu konwersji.

Aby skonwertować kolor HSV lub HSL na reprezentację RGB, wywołaj jedną z następujących metod:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>CDrawingManager::MirrorRect

Przerzuca prostokątny obszar.

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
podczas Prostokąt ograniczający obszaru, który ma zostać przerzucony.

*bHorz*<br/>
podczas Parametr logiczny, który wskazuje, czy prostokąt przerzuca poziomo lub pionowo.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia Przerzucanie dowolnego obszaru kontekstu urządzenia należącego do `CDrawingManager` klasy. Jeśli *bHorz* ma wartość true, ta metoda przerzuca obszar w poziomie. W przeciwnym razie przerzuca obszar pionowy.

##  <a name="pixelalpha"></a>CDrawingManager::P ixelAlpha

Oblicza kolor końcowy dla półprzezroczystego piksela.

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
podczas Początkowy kolor piksela.

*wartością*<br/>
podczas Liczba z zakresu od 0 do 100, która reprezentuje procent przezroczystości. Wartość 100 wskazuje, że początkowy kolor jest całkowicie przezroczysty.

*percentR*<br/>
podczas Liczba z zakresu od 0 do 100, która reprezentuje procent przezroczystości składnika czerwony.

*percentG*<br/>
podczas Liczba z zakresu od 0 do 100, która reprezentuje procent przezroczystości dla zielonego składnika.

*percentB*<br/>
podczas Liczba z zakresu od 0 do 100, która reprezentuje wartość procentową przezroczystości dla komponentu niebieskiego.

*dstPixel*<br/>
podczas Kolor podstawowy piksela.

### <a name="return-value"></a>Wartość zwracana

Kolor końcowy dla półprzezroczystego piksela.

### <a name="remarks"></a>Uwagi

Jest to Klasa pomocnika do kolorowania półprzezroczystych map bitowych i nie jest przeznaczona do wywoływania bezpośrednio przez programistę.

W przypadku korzystania z wersji metody, która ma *dstPixel*, końcowy kolor jest kombinacją *dstPixel* i *srcPixel*. Kolor *srcPixel* to częściowo przezroczysty kolor koloru bazowego *dstPixel*.

##  <a name="prepareshadowmask"></a>CDrawingManager::P repareShadowMask

Tworzy mapę bitową, która może być używana jako cień.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parametry

*nDepth*<br/>
podczas Szerokość i wysokość cienia.

*clrBase*<br/>
podczas Kolor cienia.

*iMinBrightness*<br/>
podczas Minimalna jasność cienia.

*iMaxBrightness*<br/>
podczas Maksymalna jasność cienia.

### <a name="return-value"></a>Wartość zwracana

Dojście do utworzonej mapy bitowej, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli wartość *nDepth* jest równa 0, ta metoda kończy działanie i zwraca wartość null. Jeśli wartość *nDepth* jest mniejsza niż 3, Szerokość i wysokość cienia są ustawiane na 3 piksele.

##  <a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL

Konwertuje kolor z reprezentacji czerwoną, zieloną i niebieską (RGB) na reprezentację barwy, nasycenia i jasności (HSL).

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
|*rgb*|podczas Kolor w wartościach RGB.|
|*H*|określoną Wskaźnik do podwójnej lokalizacji, w której metoda przechowuje odcień koloru.|
|*S*|określoną Wskaźnik do podwójnej lokalizacji, gdzie metoda przechowuje nasycenie koloru.|
|*L*|określoną Wskaźnik do podwójnej lokalizacji, gdzie metoda przechowuje jasność dla koloru.|

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (barwa, nasycenie i wartość), HSL (barwa, nasycenie i jasność), lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Color](/windows/win32/uxguide/vis-color).

Zwracana wartość parametru *H* jest reprezentowana jako ułamek między 0 i 1, gdzie oba 0 i 1 reprezentują kolor czerwony. Zwracane wartości *S* i *L* są liczbami z zakresu od 0 do 1.

##  <a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV

Konwertuje kolor z reprezentacji RGB na reprezentację HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parametry

*rgb*<br/>
podczas Kolor do przekonwertowania w reprezentacji RGB.

*H*<br/>
określoną Wskaźnik do podwójnej lokalizacji, w której ta metoda przechowuje otrzymany odcień koloru.

*S*<br/>
określoną Wskaźnik do podwójnej lokalizacji, w której ta metoda przechowuje uzyskane Nasycenie dla koloru.

*V*<br/>
określoną Wskaźnik do podwójnej lokalizacji, w której ta metoda przechowuje wartość wyniku dla koloru.

### <a name="remarks"></a>Uwagi

Kolor może być reprezentowany jako HSV (barwa, nasycenie i wartość), HSL (barwa, nasycenie i jasność), lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji na temat różnych reprezentacji kolorów, zobacz [Color](/windows/win32/uxguide/vis-color).

Zwracana wartość parametru *H* to liczba z zakresu od 0 do 360, gdzie oba 0 i 360 wskazują kolor czerwony. Wartości zwracane dla *S* i *V* są liczbami z zakresu od 0 do 1.

##  <a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel

Kolor przezroczystego piksela w mapie bitowej.

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
podczas Wskaźnik do wartości bitowych dla mapy bitowej.

*cinania*<br/>
podczas Prostokątny obszar w aplikacji. Menedżer rysunku rysuje cień poniżej i po prawej stronie tego obszaru.

*x*<br/>
podczas Pozioma Współrzędna pikseli do koloru.

*y*<br/>
podczas Współrzędna pionowa pikseli do koloru.

*wartością*<br/>
podczas Wartość procentowa przezroczystości.

*iShadowSize*<br/>
podczas Szerokość i wysokość cienia.

*clrBase*<br/>
podczas Kolor cienia.

*bIsRight*<br/>
podczas Parametr logiczny, który wskazuje piksel do koloru. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Ta metoda jest metodą pomocnika, która jest używana przez metodę [CDrawingManager::D rawshadow](#drawshadow) . Zalecamy, aby narysować cień, zamiast tego wywołać `CDrawingManager::DrawShadow` .

Jeśli *bIsRight* ma wartość true, piksel do koloru jest mierzony *x* pikseli od prawej krawędzi *prostokąta*. Jeśli wartość jest równa FALSE, piksel do koloru jest mierzony *x* pikseli od lewej krawędzi *prostokąta*.

##  <a name="setpixel"></a>CDrawingManager:: SetPixel

Zmienia pojedynczy piksel w mapie bitowej z określonym kolorem.

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
|*pBits*|podczas Wskaźnik do wartości bitowych mapy bitowej.|
|*cx*|podczas Łączna szerokość mapy bitowej.|
|*cy*|podczas Łączna wysokość mapy bitowej.|
|*x*|podczas Współrzędna x pikseli w mapie bitowej, która ma zostać zmieniona.|
|*y*|podczas Współrzędna y pikseli w mapie bitowej, która ma zostać zmieniona.|
|*Kolor*|podczas Nowy kolor pikseli identyfikowany przez podane współrzędne.|

##  <a name="smartmixcolors"></a>CDrawingManager::SmartMixColors

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
|*color1*|podczas Pierwszy kolor, który ma zostać zmieszany.|
|*color2*|podczas Drugi kolor, który ma zostać zmieszany.|
|*dblLumRatio*|podczas Współczynnik jaskrawości nowego koloru. `SmartMixColors`Mnoży jaskrawość mieszanego koloru przez ten współczynnik przed określeniem koloru końcowego.|
|*k1*|podczas Ważony współczynnik dla pierwszego koloru.|
|*k2*|podczas Ważony współczynnik dla drugiego koloru.|

### <a name="return-value"></a>Wartość zwracana

Kolor, który reprezentuje ważoną mieszaninę podanych kolorów.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem z błędem, jeśli wartość *K1* lub *K2* jest mniejsza od zera. Jeśli oba te parametry są ustawione na 0, metoda zwraca `RGB(0, 0, 0)`.

Współczynnik ważony jest obliczany przy użyciu następującej formuły: (color1 \* K1 + COLOR2 \* K2)/(K1 + K2). Po ustaleniu współczynnika ważonego Metoda oblicza jaskrawość koloru mieszanego. Następnie mnoży jasność przez *dblLumRatio*. Jeśli wartość jest większa niż 1,0, Metoda ustawia jaskrawość mieszanego koloru dla nowej wartości. W przeciwnym razie jasność jest ustawiona na 1,0.

##  <a name="drawrotated"></a>CDrawingManager::D rawRotated

Obraca zawartość źródłowego kontrolera domeny w danym prostokącie o 90 stopni.

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parametry

*rectDest*<br/>
Prostokąt docelowy.

*dcSrc*<br/>
Kontekst urządzenia źródłowego.

*bClockWise*<br/>
PRAWDA wskazuje obrót + 90 stopni; Wartość FALSE wskazuje obrót-90 stopni.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
