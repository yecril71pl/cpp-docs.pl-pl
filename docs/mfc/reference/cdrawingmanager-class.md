---
title: Klasa CDrawingManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 30
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 689d538c03a35175040663aedb7bd6130aae10fd
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="cdrawingmanager-class"></a>Klasa CDrawingManager
`CDrawingManager` Klasa implementuje złożonych algorytmów rysowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDrawingManager : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Konstruuje `CDrawingManager` obiektu.|  
|`CDrawingManager::~CDrawingManager`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Tworzy 32-bitowych niezależnych od urządzenia mapy bitowej (DIB) czy aplikacje można zapisywać do bezpośrednio.|  
|[CDrawingManager::DrawAlpha](#drawalpha)|Wyświetla bitmap przezroczysty lub półprzezroczysty pikseli.|  
|[CDrawingManager::DrawRotated](#drawrotated)|Obraca źródłowego kontrolera domeny zawartości wewnątrz danej prostokąt przez +/-90 stopni|  
|[CDrawingManager::DrawEllipse](#drawellipse)|Rysuje elipsę z podany kolor wypełnienia i obramowania.|  
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Rysuje pierścień i wypełnia je kolor gradientu.|  
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Rysuje linię.|  
|[CDrawingManager::DrawRect](#drawrect)|Rysuje prostokąt z podany kolor wypełnienia i obramowania.|  
|[CDrawingManager::DrawShadow](#drawshadow)|Rysuje cienia prostokątny obszar.|  
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Wstawia prostokątny obszar dwóch kolor gradientu.|  
|[CDrawingManager::FillGradient](#fillgradient)|Wstawia prostokątny obszar podany kolor gradientu.|  
|[CDrawingManager::FillGradient2](#fillgradient2)|Wstawia prostokątny obszar podany kolor gradientu. Kierunek Zmień kolor gradientu jest też określona.|  
|[CDrawingManager::GrayRect](#grayrect)|Wstawia prostokącie określonego koloru szarego.|  
|[CDrawingManager::HighlightRect](#highlightrect)|Prezentuje prostokątny obszar.|  
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Konwertuje kolor z reprezentacji HLS reprezentację RGB.|  
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Konwertuje kolor z reprezentacji HLS reprezentację RGB.|  
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Konwertuje kolor z reprezentacji HSV reprezentację RGB.|  
|[CDrawingManager::HuetoRGB](#huetorgb)|Metoda pomocnika, który konwertuje wartości hue do składnika czerwony, zielony lub niebieski.|  
|[CDrawingManager::MirrorRect](#mirrorrect)|Przerzuca prostokątny obszar.|  
|[CDrawingManager::PixelAlpha](#pixelalpha)|Metoda pomocnika, która określa końcowy kolor półprzezroczystych pikseli.|  
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Tworzy mapę bitową, który może służyć jako cienia.|  
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Konwertuje kolor z reprezentacji RGB reprezentację HSL.|  
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Konwertuje kolor z reprezentacji RGB reprezentację HSV.|  
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Metoda pomocnika kolory częściowo przezroczyste pikseli mapy bitowej.|  
|[CDrawingManager::SetPixel](#setpixel)|Metoda pomocnika zmiany określonego koloru piksela mapy bitowej.|  
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Łączy dwa kolory na podstawie współczynnika ważoną.|  
  
## <a name="remarks"></a>Uwagi  
 `CDrawingManager` Klasa udostępnia funkcje rysowania cieni, kolor gradientu i prostokąty zaznaczony. Wykonuje także przenikanie alfa. Ta klasa służy do bezpośrednio zmienić interfejsu użytkownika aplikacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
 `CDrawingManager`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdrawmanager.h  
  
##  <a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager  
 Konstruuje [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) obiektu.  
  
```  
CDrawingManager(CDC& dc);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`dc`  
 Odwołanie do kontekstu urządzenia. `CDrawingManager` Używa tego kontekstu do rysowania.  
  
##  <a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32  
 Tworzy 32-bitowych niezależnych od urządzenia mapy bitowej (DIB) czy aplikacje można zapisywać do bezpośrednio.  
  
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
|[in]`size`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) parametr, który wskazuje rozmiar mapy bitowej.|  
|[out]`pBits`|Wskaźnik do wskaźnika danych, który odbiera lokalizację DIB bit wartości.|  
|`bitmap`|Dojście do oryginalnego mapy bitowej|  
|`clrTransparent`|Określanie koloru przezroczystego bitmapy oryginalnej wartości RGB.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do nowo utworzonej mapy bitowej DIB Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat tworzenia mapy bitowej DIB zobacz [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183491).  
  
##  <a name="drawalpha"></a>CDrawingManager::DrawAlpha  
 Wyświetla bitmap przezroczysty lub półprzezroczysty pikseli.  
  
```  
void DrawAlpha(
    CDC* pDstDC,  
    const CRect& rectDst,  
    CDC* pSrcDC,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDstDC`  
 Wskaźnik do kontekstu urządzenia dla miejsca docelowego.  
  
 [in]`rectDst`  
 Prostokąt docelowy.  
  
 [in]`pSrcDC`  
 Wskaźnik do kontekstu urządzenia dla tego źródła.  
  
 [in]`rectSrc`  
 Prostokąt źródła.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wykonuje przenikanie alfa dla dwóch map bitowych. Aby uzyskać więcej informacji na temat przenikanie alfa, zobacz [AlphaBlend](http://msdn.microsoft.com/library/windows/desktop/dd183351) w zestawie Windows SDK.  
  
##  <a name="drawellipse"></a>CDrawingManager::DrawEllipse  
 Rysuje elipsę z podany kolor wypełnienia i obramowania.  
  
```  
void DrawEllipse(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
 Prostokąt ograniczający elipsy.  
  
 [in]`clrFill`  
 Kolor, który używa tej metody do wypełnienia elipsy.  
  
 [in]`clrLine`  
 Kolor ta metoda używa jako obramowania elipsy.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca bez rysunku elipsy niezależnie od koloru ma ustawioną wartość -1. Również zwraca bez rysowania elipsy, jeśli ma wartość 0 albo wymiaru prostokątem.  
  
##  <a name="drawgradientring"></a>CDrawingManager::DrawGradientRing  
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
 [in]`rect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) parametr określający granic dla gradientu pierścień.  
  
 [in]`colorStart`  
 Pierwszy kolor gradientu.  
  
 [in]`colorFinish`  
 Ostatni kolor gradientu.  
  
 [in]`colorBorder`  
 Kolor obramowania.  
  
 [in]`nAngle`  
 Parametr, który określa kąt początkowy rysowania gradientu. Wartość ta powinna być z zakresu od 0 do 360.  
  
 [in]`nWidth`  
 Szerokość obramowania dla pierścienia.  
  
 [in]`clrFace`  
 Kolor wnętrza pierścienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Prostokąt zdefiniowane przez `rect` musi być co najmniej 5 pikseli szerokości i 5 pikseli.  
  
##  <a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine, CDrawingManager::DrawLineA  
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
|[in]`x1`|Współrzędna x, gdzie uruchamiana wiersza.|  
|[in]`y1`|Współrzędna y, gdzie uruchamiana wiersza.|  
|[in]`x2`|Współrzędna x, gdy kończy się wiersz.|  
|[in]`y2`|Współrzędna y, gdzie kończy się wiersz.|  
|[in]`clrLine`|Kolor linii.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem, jeśli `clrLine` równa -1.  
  
##  <a name="drawrect"></a>CDrawingManager::DrawRect  
 Rysuje prostokąt z podany kolor wypełnienia i obramowania.  
  
```  
void DrawRect(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
 Granice prostokąta.  
  
 [in]`clrFill`  
 Kolor, który używa tej metody do wypełnienia prostokąta.  
  
 [in]`clrLine`  
 Kolor ta metoda używa obramowania prostokąta.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca bez rysowania prostokąta, jeśli niezależnie od koloru ma ustawioną wartość -1. Zwraca także, czy albo wymiaru prostokąta jest 0.  
  
##  <a name="drawshadow"></a>CDrawingManager::DrawShadow  
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
 [in]`rect`  
 Prostokątny obszar w aplikacji. Rysowanie Menedżera narysuje cienia pod tym obszarze.  
  
 [in]`nDepth`  
 Szerokość i wysokość cienia.  
  
 [in]`iMinBrightness`  
 Minimalna jasność cienia.  
  
 [in]`iMaxBrightness`  
 Maksymalna jasność cienia.  
  
 [in]`pBmpSaveBottom`  
 Wskaźnik do mapy bitowej, który zawiera obraz do dolnej części cienia.  
  
 [in]`pBmpSaveRight`  
 Wskaźnik do mapy bitowej zawierającego obraz dla cienia są rysowane w prawej krawędzi prostokąta.  
  
 [in]`clrBase`  
 Kolor cienia.  
  
 [in]`bRightShadow`  
 Parametrów typu Boolean wskazującą, w jaki sposób jest rysowany cień. Jeśli `bRightShadow` jest `TRUE`, `DrawShadow` rysuje cienia w prawej krawędzi prostokąta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz podać dwa prawidłowy map bitowych dolnych i prawych cieni przy użyciu parametrów `pBmpSaveBottom` i `pBmpSaveRight`. Jeśli te [cbitmap —](../../mfc/reference/cbitmap-class.md) obiekty mają przyłączonego obiektu GDI `DrawShadow` użyje tych map bitowych jako cieni. Jeśli `CBitmap` parametry nie mogą mieć przyłączonego obiektu GDI `DrawShadow` rysuje Cień i dołącza map bitowych z parametrami. W przyszłych wywołaniach `DrawShadow`, możesz podać te mapy bitowe, aby przyspieszyć proces rysowania. Aby uzyskać więcej informacji na temat `CBitmap` klasa i obiekty GDI, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).  
  
 Jeśli jest jeden z tych parametrów `NULL`, `DrawShadow` zostanie automatycznie Rysowanie cienia.  
  
 Jeśli ustawisz `bRightShadow` do `FALSE`, poniżej i w lewo prostokątny obszar będzie rysowany cień.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `DrawShadow` metody `CDrawingManager` klasy. Następujący fragment kodu jest częścią [próbka Demo arkusza właściwości](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]  
  
##  <a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient  
 Wstawia prostokątny obszar dwóch kolor gradientu.  
  
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
 [in]`rect`  
 Prostokąt do wypełnienia.  
  
 [in]`colorStart1`  
 Początkowy kolor pierwszy kolor gradientu.  
  
 [in]`colorFinish1`  
 Ostateczny kolor pierwszy kolor gradientu.  
  
 [in]`colorStart2`  
 Początkowy kolor drugi kolor gradientu.  
  
 [in]`colorFinish2`  
 Ostateczny kolor drugi kolor gradientu.  
  
 [in]`bHorz`  
 Parametrów typu Boolean, która wskazuje, czy `Fill4ColorsGradient` kolory gradientu pozioma lub pionowa. `TRUE`Wskazuje poziome gradientu.  
  
 [in]`nPercentage`  
 Liczba całkowita od 0 do 100. Ta wartość wskazuje procent prostokąta umożliwia wypełnienie pierwszy kolor gradientu.  
  
### <a name="remarks"></a>Uwagi  
 Po dwóch gradienty kolor prostokąta, są one znajduje się nad siebie lub dalej do innych, w zależności od wartości `bHorz`. Każdy kolor gradientu jest obliczana niezależnie z metodą [CDrawingManager::FillGradient](#fillgradient).  
  
 Ta metoda generuje błąd potwierdzenia, jeśli `nPercentage` jest mniejsza niż 0 lub więcej niż 100.  
  
##  <a name="fillgradient"></a>CDrawingManager::FillGradient  
 Wstawia prostokątny obszar podany kolor gradientu.  
  
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
 [in]`rect`  
 Prostokątny obszar do wypełnienia.  
  
 [in]`colorStart`  
 Pierwszy kolor gradientu.  
  
 [in]`colorFinish`  
 Końcowy kolor gradientu.  
  
 [in]`bHorz`  
 Parametr wartość logiczna określająca czy `FillGradient` powinien być rysowany gradientu pozioma lub pionowa.  
  
 [in]`nStartFlatPercentage`  
 Wartość procentowa prostokąta który `FillGradient` wypełnia `colorStart` przed rozpoczęciem gradientu.  
  
 [in]`nEndFlatPercentage`  
 Wartość procentowa prostokąta który `FillGradient` wypełnia `colorFinish` po jej zakończeniu gradientu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `FillGradient` metody `CDrawingManager` klasy. Następujący fragment kodu jest częścią [próbka MS Office 2007 Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]  
  
##  <a name="fillgradient2"></a>CDrawingManager::FillGradient2  
 Wstawia prostokątny obszar podany kolor gradientu.  
  
```  
void FillGradient2 (
    CRect rect,  
    COLORREF colorStart,  
    COLORREF colorFinish,  
    int nAngle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
 Prostokątny obszar do wypełnienia.  
  
 [in]`colorStart`  
 Pierwszy kolor gradientu.  
  
 [in]`colorFinish`  
 Ostatni kolor gradientu.  
  
 [in]`nAngle`  
 Całkowitą z przedziału od 0 do 360. Ten parametr określa kierunek kolor gradientu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `nAngle` do określania kierunku kolor gradientu. Po określeniu kierunek kolor gradientu, należy także określić gdzie uruchamiana kolor gradientu. Wartość 0 dla `nAngle` wskazuje gradientu zaczyna się od górnej krawędzi prostokąta. Jako `nAngle` zwiększa położenie początkowe dla gradientu przenosi kierunku oparte na kąt.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `FillGradient2` metody `CDrawingManager` klasy. Następujący fragment kodu jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]  
  
##  <a name="grayrect"></a>CDrawingManager::GrayRect  
 Wstawia prostokącie określonego koloru szarego.  
  
```  
BOOL GrayRect(
    CRect rect,  
    int nPercentage = -1,  
    COLORREF clrTransparent = (COLORREF)-1,  
    COLORREF clrDisabled = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
 Prostokątny obszar do wypełnienia.  
  
 [in]`nPercentage`  
 Wartość procentowa szary, który ma w prostokącie.  
  
 [in]`clrTransparent`  
 Przezroczysty kolor.  
  
 [in]`clrDisabled`  
 Kolor, którego ta metoda używa dla dezaktywowanie nasycenie `nPercentage` ma ustawioną wartość -1.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Dla parametru `nPercentage`, niższą wartość wskazuje kolor ciemniejszego.  
  
 Maksymalna wartość `nPercentage` 200. Wartość większą niż 200 nie zmienia wygląd prostokąta. Jeśli wartość wynosi -1, ta metoda używa `clrDisabled` ograniczenie nasycenie prostokąta.  
  
##  <a name="highlightrect"></a>CDrawingManager::HighlightRect  
 Prezentuje prostokątny obszar.  
  
```  
BOOL HighlightRect(
    CRect rect,  
    int nPercentage = -1,  
    COLORREF clrTransparent = (COLORREF)-1,  
    int nTolerance = 0,  
    COLORREF clrBlend = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
 Aby wyróżnić prostokątny obszar.  
  
 [in]`nPercentage`  
 Wartość procentową, która wskazuje, jak przezroczysty wyróżnienie powinien być.  
  
 [in]`clrTransparent`  
 Przezroczysty kolor.  
  
 [in]`nTolerance`  
 Liczba całkowita między 0 a 255 wskazującą tolerancja kolorów.  
  
 [in]`clrBlend`  
 Kolor podstawowy mieszania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `nPercentage` to od 0 do 99, `HighlightRect` używa alfa algorytm mieszania. Aby uzyskać więcej informacji na temat przenikanie alfa, zobacz [alfa mieszania linii i wypełnień](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Jeśli `nPercentage` wynosi -1, ta metoda używa domyślnego poziomu wyróżnienia. Jeśli `nPercentage` 100, ta metoda nie działa i zwraca `TRUE`.  
  
 Metoda używa parametru `nTolerance` do określenia, czy Wyróżnij prostokątny obszar. Aby wyróżnić prostokąt różnica między kolor tła aplikacji i `clrTransparent` musi być mniejsza niż `nTolerance` w każdym składniku kolorów (czerwony, zielony i niebieski).  
  
##  <a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE  
 Konwertuje kolor z reprezentacji HLS reprezentację RGB.  
  
```  
static COLORREF __stdcall HLStoRGB_ONE(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`H`  
 Liczba z przedziału od 0 do 1, który reprezentuje hue koloru.  
  
 [in]`L`  
 Liczbą z zakresu od 0 do 1, która wskazuje jasność koloru.  
  
 [in]`S`  
 Liczbą z zakresu od 0 do 1, który wskazuje nasycenie koloru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Reprezentacja RGB kolor HLS podane.  
  
### <a name="remarks"></a>Uwagi  
 Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji o różnych reprezentacji kolorów, zobacz [kolor](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Ta metoda i `CDrawingManager::HLStoRGB_TWO` metody do tej samej operacji, ale wymagają różnych wartości `H` parametru. W przypadku tej metody `H` procent okręgu. W `CDrawingManager::HLStoRGB_TWO` metody `H` jest wartością stopnia od 0 do 360, reprezentujące zarówno czerwony. Na przykład z `HLStoRGB_ONE`, wartość 0,25 dla `H` jest odpowiednikiem wartości 90 z `HLStoRGB_TWO`.  
  
##  <a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO  
 Konwertuje kolor z reprezentacji HLS reprezentację RGB.  
  
```  
static COLORREF __stdcall HLStoRGB_TWO(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`H`  
 Liczba z przedziału od 0 do 360, który reprezentuje hue koloru.  
  
 [in]`L`  
 Liczbą z zakresu od 0 do 1, która wskazuje jasność koloru.  
  
 [in]`S`  
 Liczbą z zakresu od 0 do 1, który wskazuje nasycenie koloru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Reprezentacja RGB kolor HLS podane.  
  
### <a name="remarks"></a>Uwagi  
 Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji o różnych reprezentacji kolorów, zobacz [kolor](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Ta metoda i [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metody do tej samej operacji, ale wymagają różnych wartości `H` parametru. W przypadku tej metody `H` jest wartością stopnia od 0 do 360, reprezentujące zarówno czerwony. W [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metody `H` procent okręgu. Na przykład z `HLStoRGB_ONE`, wartość 0,25 dla `H` jest odpowiednikiem wartości 90 z `HLStoRGB_TWO`.  
  
##  <a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB  
 Konwertuje kolor z reprezentacji HSV reprezentację RGB.  
  
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
|[in]`H`|Liczbą z zakresu od 0 do 360 wskazującą hue koloru.|  
|[in]`S`|Liczbą z zakresu od 0 do 1, który wskazuje nasycenie koloru.|  
|[in]`V`|Liczbą z zakresu od 0 do 1, która wskazuje wartość koloru.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Reprezentacja RGB kolor HSV podane.  
  
### <a name="remarks"></a>Uwagi  
 Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji o różnych reprezentacji kolorów, zobacz [kolor](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
##  <a name="huetorgb"></a>CDrawingManager::HuetoRGB  
 Konwertuje wartość hue składnika czerwony, zielony lub niebieski.  
  
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
 [in]`m1`  
 Zobacz uwagi.  
  
 [in]`m2`  
 Zobacz uwagi.  
  
 [in]`h`  
 Zobacz uwagi.  
  
 [in]`rm1`  
 Zobacz uwagi.  
  
 [in]`rm2`  
 Zobacz uwagi.  
  
 [in]`rh`  
 Zobacz uwagi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poszczególne czerwony, zielony lub niebieski składnika dla podanego hue.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest metodą pomocnika który `CDrawingManager` klasa używana do obliczenia pojedynczych składników czerwony, zielonemu i niebieskiemu koloru w reprezentacji HSV lub HSL. Ta metoda nie jest przeznaczony do wywołania bezpośrednio przez programistę. Parametry wejściowe są wartości, które są zależne od algorytmu konwersji.  
  
 Aby przekonwertować kolor HSV lub HSL reprezentację RGB, wywołaj jedną z następujących metod:  
  
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
 [in]`rect`  
 Prostokąt ograniczający obszaru do przerzucenia.  
  
 [in]`bHorz`  
 Parametrów typu Boolean wskazującą, czy prostokąt Przerzuca poziomo czy pionowo.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można przerzucić części należących do kontekstu urządzenia `CDrawingManager` klasy. Jeśli `bHorz` ma ustawioną wartość `TRUE`, ta metoda Przerzuca obszar w poziomie. W przeciwnym razie go Przerzuca obszaru pionowo.  
  
##  <a name="pixelalpha"></a>CDrawingManager::PixelAlpha  
 Oblicza kolor końcowy półprzezroczystych pikseli.  
  
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
 [in]`srcPixel`  
 Początkowy kolor piksela.  
  
 [in]`percent`  
 Liczbą z zakresu od 0 do 100, reprezentuje Procent przezroczystości. Wartość 100 wskazuje, że początkowy kolor jest całkowicie niewidoczne.  
  
 [in]`percentR`  
 Liczbą z zakresu od 0 do 100, reprezentuje Procent przezroczystości dla składnika czerwony.  
  
 [in]`percentG`  
 Liczbą z zakresu od 0 do 100, reprezentuje Procent przezroczystości dla składnika zielony.  
  
 [in]`percentB`  
 Liczbą z zakresu od 0 do 100, reprezentuje Procent przezroczystości dla składnika niebieski.  
  
 [in]`dstPixel`  
 Kolor podstawowy piksela.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ostateczny kolor półprzezroczystych pikseli.  
  
### <a name="remarks"></a>Uwagi  
 To jest klasa pomocy dla kolorowania półprzezroczystych mapy bitowe i nie ma być wywoływany bezpośrednio przez programistę.  
  
 Jeśli używasz wersji metody, która ma `dstPixel`, kolor końcowy jest kombinacją `dstPixel` i `srcPixel`. `srcPixel` Kolor jest częściowo przezroczysty kolor na kolor podstawowy `dstPixel`.  
  
##  <a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask  
 Tworzy mapę bitową, który może służyć jako cienia.  
  
```  
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,  
    COLORREF clrBase,  
    int iMinBrightness = 0,  
    int iMaxBrightness = 100);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nDepth`  
 Szerokość i wysokość cienia.  
  
 [in]`clrBase`  
 Kolor cienia.  
  
 [in]`iMinBrightness`  
 Minimalna jasność cienia.  
  
 [in]`iMaxBrightness`  
 Maksymalna jasność cienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do utworzonej mapy bitowej, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `nDepth` jest ustawiona na 0, ta metoda kończy działanie i zwraca `NULL`. Jeśli `nDepth` jest mniejsza niż 3, szerokość i wysokość cienia zostaną ustawione na 3 pikseli.  
  
##  <a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL  
 Konwertuje kolor czerwony, zielonemu i niebieskiemu reprezentacja (RGB) odcień, nasycenie i reprezentacja jasność (HSL).  
  
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
|[in]`rgb`|Kolor RGB wartości.|  
|[out]`H`|Wskaźnik na wartość typu double, której metody przechowuje hue koloru.|  
|[out]`S`|Wskaźnik na wartość typu double, której metody przechowuje nasycenie koloru.|  
|[out]`L`|Wskaźnik na wartość typu double, której metody przechowuje jasność koloru.|  
  
### <a name="remarks"></a>Uwagi  
 Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji o różnych reprezentacji kolorów, zobacz [kolor](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Zwrócona wartość dla `H` jest reprezentowany jako ułamek od 0 do 1, w którym zarówno 0 i 1 reprezentują czerwony. Wartości zwracane przez `S` i `L` są liczbami z przedziału od 0 do 1.  
  
##  <a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV  
 Konwertuje kolor z reprezentacji RGB reprezentację HSV.  
  
```  
static void __stdcall RGBtoHSV(
    COLORREF rgb,  
    double* H,  
    double* S,  
    double* V);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rgb`  
 Kolor, który można przekonwertować w reprezentacji RGB.  
  
 [out]`H`  
 Wskaźnik na wartość typu double, w której ta metoda przechowuje wynikowy hue koloru.  
  
 [out]`S`  
 Wskaźnik na wartość typu double, w której ta metoda przechowuje wynikowy nasycenie koloru.  
  
 [out]`V`  
 Wskaźnik na wartość typu double, w której ta metoda przechowuje wynikowej wartości koloru.  
  
### <a name="remarks"></a>Uwagi  
 Kolor może być reprezentowany jako HSV (odcień, nasycenie i wartość), HSL (odcień, nasycenie i jasność) lub RGB (czerwony, zielony i niebieski). Aby uzyskać więcej informacji o różnych reprezentacji kolorów, zobacz [kolor](http://go.microsoft.com/fwlink/p/?linkid=119126).  
  
 Zwrócona wartość dla `H` jest liczbą z zakresu od 0 do 360, gdzie zarówno 0 do 360 wskazać czerwony. Zwracane wartości dla `S` i `V` są liczbami z przedziału od 0 do 1.  
  
##  <a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel  
 Kolory przezroczyste piksele mapy bitowej.  
  
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
 [in]`pBits`  
 Wskaźnik do wartości bitowe mapy bitowej.  
  
 [in]`rect`  
 Prostokątny obszar w aplikacji. Rysowanie Menedżera rysuje cienia pod i w prawo w tym obszarze.  
  
 [in]`x`  
 Współrzędna pozioma piksela kolorów.  
  
 [in]`y`  
 Współrzędna pionowy piksela kolorów.  
  
 [in]`percent`  
 Procent przezroczystości.  
  
 [in]`iShadowSize`  
 Szerokość i wysokość cienia.  
  
 [in]`clrBase`  
 Kolor cienia.  
  
 [in]`bIsRight`  
 Parametrów typu Boolean wskazującą, które pikseli na kolor. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest używany przez metodę Pomocnika [CDrawingManager::DrawShadow](#drawshadow) metody. Firma Microsoft zaleca, aby narysować cienia, wywołujące `CDrawingManager::DrawShadow` zamiast tego.  
  
 Jeśli `bIsRight` ustawiono `TRUE`, pikseli na kolor jest mierzony `x` pikseli od prawej krawędzi `rect`. Jeśli jest `FALSE`, pikseli na kolor jest mierzony `x` pikseli od lewej krawędzi `rect`.  
  
##  <a name="setpixel"></a>CDrawingManager::SetPixel  
 Podany kolor zmiany piksela mapy bitowej.  
  
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
|[in]`pBits`|Wskaźnik do wartości bitowe mapy bitowej.|  
|[in]`cx`|Łączna szerokość mapy bitowej.|  
|[in]`cy`|Całkowita wysokość mapy bitowej.|  
|[in]`x`|Współrzędna x piksel w mapie bitowej można zmienić.|  
|[in]`y`|Współrzędna y piksel w mapie bitowej można zmienić.|  
|[in]`color`|Nowy kolor pikseli o podany współrzędnych.|  
  
##  <a name="smartmixcolors"></a>CDrawingManager::SmartMixColors  
 Łączy dwa kolory na podstawie współczynnika ważoną.  
  
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
|[in]`color1`|Kolor pierwszego zestawu.|  
|[in]`color2`|Drugi kolor mieszania.|  
|[in]`dblLumRatio`|Współczynnik jasność nowy kolor. `SmartMixColors`Mnoży jasność mieszanych koloru tego stosunku przed ustaleniem ostateczny kolor.|  
|[in]`k1`|Współczynnik ważoną pierwszy kolor.|  
|[in]`k2`|Współczynnik ważoną drugi kolor.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor, który reprezentuje ważoną kombinacja podana kolorów.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem z powodu błędu Jeśli `k1` lub `k2` jest mniejsza od zera. Jeśli oba te parametry są ustawione na 0, metoda zwraca `RGB(0, 0, 0)`.  
  
 Współczynnik ważoną oblicza się przy użyciu następującej formuły: (kolorem1 * k1 + color2 \* k2) /(k1 + k2). Po ważoną stosunek jest określony, metoda oblicza jasność koloru mieszanego. Następnie mnoży jasność przez `dblLumRatio`. Jeśli wartość jest większa niż 1.0, metoda ustawia jasność koloru mieszanego do nowej wartości. W przeciwnym razie jasność jest równa 1.0.  
  
##  <a name="drawrotated"></a>CDrawingManager::DrawRotated  
 Obraca źródłowego kontrolera domeny zawartości wewnątrz danej prostokąt o 90 stopni.  
  
```  
void DrawRotated(
    CRect rectDest,  
    CDC& dcSrc,  
    BOOL bClockWise);
```  
  
### <a name="parameters"></a>Parametry  
 `rectDest`  
 Prostokąt docelowy.  
  
 `dcSrc`  
 Kontekst urządzenia źródłowego.  
  
 `bClockWise`  
 `TRUE`Określa Obrót + 90 stopni; `FALSE` wskazuje obracania-90 stopni.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
