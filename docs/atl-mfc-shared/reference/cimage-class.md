---
title: CImage, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/01/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
dev_langs:
- C++
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1c27d20970b8e8634e8438c25733fd90a3ad632
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064800"
---
# <a name="cimage-class"></a>CImage, klasa

`CImage` Zapewnia obsługę rozszerzonych mapy bitowej, łącznie z możliwością ładowania i zapisać obrazy w formacie JPEG, GIF, BMP i przenośnych Network Graphics (PNG).

> [!IMPORTANT]
> Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CImage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CImage::CImage](#cimage)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczystych pikseli.|
|[CImage::Attach](#attach)|Dołącza HBITMAP do `CImage` obiektu. Może służyć za pomocą mapy bitowe sekcji bez DIB lub mapy bitowe sekcji DIB.|
|[CImage::BitBlt](#bitblt)|Kopiuje mapę bitową z kontekstem urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.|
|[CImage::Create](#create)|Tworzy mapę bitową sekcji DIB i dołącza go do wcześniej stworzonego elementu `CImage` obiektu.|
|[CImage::CreateEx](#createex)|Tworzy mapę bitową sekcji DIB (z dodatkowych parametrów) i dołącza go do wcześniej skonstruowany `CImage` obiektu.|
|[CImage::Destroy](#destroy)|Odłącza mapę bitową z `CImage` obiektu i niszczy mapy bitowej.|
|[CImage::Detach](#detach)|Odłącza mapę bitową z `CImage` obiektu.|
|[CImage::Draw](#draw)|Kopiuje mapę bitową z prostokąta źródłowego do prostokąta docelowego. `Draw` Rozciąga lub kompresuje mapy bitowej, aby dopasować ją do wymiarów prostokąta docelowego, jeśli to konieczne i obsługuje przenikaniem alfa i kolory przezroczyste.|
|[CImage::GetBits](#getbits)|Pobiera wskaźnik do wartości rzeczywistej pikseli mapy bitowej.|
|[CImage::GetBPP](#getbpp)|Pobiera liczba bitów na piksel.|
|[CImage::GetColorTable](#getcolortable)|Pobiera czerwony, zielony, niebieski wartości kolorów (RGB) z szeroką gamę wpisów w tabeli kolorów.|
|[CImage::GetDC](#getdc)|Pobiera kontekst urządzenia, do którego wybrano bieżącego mapy bitowej.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Umożliwia znalezienie formatów obrazów dostępnych i ich opisy.|
|[CImage::GetHeight](#getheight)|Pobiera wysokość bieżącego obrazu w pikselach.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Umożliwia znalezienie formatów obrazów dostępnych i ich opisy.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Pobiera maksymalną liczbę wpisów w tabeli kolorów.|
|[CImage::GetPitch](#getpitch)|Pobiera wysokość bieżącego obrazu, w bajtach.|
|[CImage::GetPixel](#getpixel)|Pobiera kolor piksela określony przez *x* i *y*.|
|[CImage::GetPixelAddress](#getpixeladdress)|Pobiera adres piksela podanego.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Pobiera położenie przezroczysty kolor w tabeli kolorów.|
|[CImage::GetWidth](#getwidth)|Pobiera szerokość bieżącego obrazu w pikselach.|
|[CImage::IsDIBSection](#isdibsection)|Określa, czy dołączonych mapy bitowej sekcji DIB.|
|[CImage::IsIndexed](#isindexed)|Wskazuje, że kolory mapę bitową są mapowane na indeksowane palety.|
|[CImage::IsNull](#isnull)|Wskazuje, jeśli źródłową mapę bitową jest aktualnie załadowana.|
|[CImage::IsTransparencySupported](#istransparencysupported)|Wskazuje, czy aplikacja obsługuje przezroczysty map bitowych.|
|[CImage::Load](#load)|Ładuje obraz z określonego pliku.|
|[CImage::LoadFromResource](#loadfromresource)|Ładuje obraz z określonego zasobu.|
|[CImage::MaskBlt](#maskblt)|Łączy dane koloru dla map bitowych źródłowych i docelowych przy użyciu określonej maski i operacja rastrowa.|
|[CImage::PlgBlt](#plgblt)|Wykonuje przesunięcia bitowego bloku z prostokątem kontekst urządzenia źródłowego do równoległobok w kontekście urządzenia docelowego.|
|[CImage::ReleaseDC](#releasedc)|Zwalnia kontekstu urządzenia, które zostały pobrane z [CImage::GetDC](#getdc).|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Zwalnia zasoby używane przez interfejs GDI +. Musi zostać wywołana, aby zwolnić zasoby utworzone przez globalną `CImage` obiektu.|
|[CImage::Save](#save)|Zapisuje obraz jako określonego typu. `Save` Nie można określić opcji obrazu.|
|[CImage::SetColorTable](#setcolortable)|Ustawia czerwony, zielony, niebieski RGB) koloru wartości w zakresie wpisów w tabeli kolorów sekcji DIB.|
|[CImage::SetPixel](#setpixel)|Ustawia piksela na określonych współrzędnych określony kolor.|
|[CImage::SetPixelIndexed](#setpixelindexed)|Ustawia piksela na określonych współrzędnych kolor pod określonym indeksem palety.|
|[CImage::SetPixelRGB](#setpixelrgb)|Ustawia piksela na określonych współrzędnych określonego czerwony, zielony, wartość niebieskiego (RGB).|
|[CImage::SetTransparentColor](#settransparentcolor)|Ustawia indeks kolor, który ma być traktowany jako przezroczysty. Tylko jeden z palety kolorów może być przezroczysty.|
|[CImage::StretchBlt](#stretchblt)|Kopiuje mapę bitową z prostokąta źródłowego do prostokąta docelowego, rozciągając ją lub zmniejszając mapy bitowej, aby dopasować ją do wymiarów prostokąta docelowego, jeśli to konieczne.|
|[CImage::TransparentBlt](#transparentblt)|Kopiuje mapę bitową z kolorem przezroczystym z kontekstem urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[HBITMAP CImage::operator](#operator_hbitmap)|Zwraca uchwyt Windows dołączonych do `CImage` obiektu.|

## <a name="remarks"></a>Uwagi

`CImage` Trwa mapy bitowe, które są albo sekcje map bitowych niezależnych od urządzenia (DIB), czy nie; można jednak użyć [Utwórz](#create) lub [CImage::Load](#load) tylko DIB sekcje. Możesz dołączyć mapy bitowej sekcji bez DIB do `CImage` przy użyciu [Attach](#attach), ale następnie nie można użyć następujących `CImage` metody, które obsługują tylko DIB sekcji mapy bitowe:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Aby ustalić, czy sekcja DIB dołączonych mapy bitowej, należy wywołać [IsDibSection](#isdibsection).

> [!NOTE]
> W programie Visual Studio .NET 2003, ta klasa śledzi liczbę `CImage` obiekty utworzone. Zawsze, gdy liczba wynosić 0, funkcja `GdiplusShutdown` jest wywoływana automatycznie, aby zwolnić zasoby używane przez interfejs GDI +. Gwarantuje to, że dowolny `CImage` obiekty utworzone bezpośrednio lub pośrednio przez biblioteki dll zawsze są poprawnie niszczone oraz że `GdiplusShutdown` nie jest wywoływana z `DllMain`.

> [!NOTE]
> Za pomocą globalnego `CImage` obiektów w bibliotece DLL nie jest zalecane. Jeśli musisz użyć globalną `CImage` obiektu w bibliotece DLL, wywołanie [CImage::ReleaseGDIPlus](#releasegdiplus) jawnie zwolnić zasoby używane przez interfejs GDI +.

`CImage` Nie można wybrać w nowym [CDC](../../mfc/reference/cdc-class.md). `CImage` tworzy własne elementu HDC dla obrazu. Ponieważ HBITMAP można wybrać tylko do jednego elementu HDC naraz, HBITMAP skojarzone z `CImage` nie można wybrać do innego elementu HDC. Przechwytywanie zmian danych, należy pobrać elementu HDC z `CImage` i oferowanie [CDC::FromHandle] (.. /.. /MFC/Reference/CDC-Class.MD#cdc__fromhandle.

## <a name="example"></a>Przykład

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Kiedy używasz `CImage` w projekcie MFC, należy pamiętać, funkcje Członkowskie w projekcie oczekuje wskaźnika do [CBitmap](../../mfc/reference/cbitmap-class.md) obiektu. Jeśli chcesz używać `CImage` za pomocą takich funkcji, takich jak [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), użyj [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), przekazać go swoje `CImage` HBITMAP i użyj zwracanego `CBitmap*`.

## <a name="example"></a>Przykład

```cpp
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
    UNREFERENCED_PARAMETER(nFlags);

    CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
    m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
    ClientToScreen(&point);
    m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x,
    point.y, this);
}
```

Za pomocą `CImage`, masz dostęp do rzeczywistego bitów sekcji DIB. Możesz użyć `CImage` obiektu w dowolnym miejscu, wcześniej używano sekcji Win32 HBITMAP lub DIB.

Możesz użyć `CImage` z MFC ani ATL.

> [!NOTE]
> Po utworzeniu projektu używającego `CImage`, należy zdefiniować `CString` przed wprowadzeniem `atlimage.h`. Jeśli projekt używa ATL bez MFC, Uwzględnij `atlstr.h` przed wprowadzeniem `atlimage.h`. Jeśli projekt używa biblioteki MFC (lub jeśli jest to Projekt ATL z obsługi MFC), Uwzględnij `afxstr.h` przed wprowadzeniem `atlimage.h`.<br/>
> <br/>
> Podobnie, należy uwzględnić `atlimage.h` przed wprowadzeniem `atlimpl.cpp`. Aby łatwo to zrobić, należy dołączyć `atlimage.h` w swojej `stdafx.h`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlimage.h

##  <a name="alphablend"></a>  CImage::AlphaBlend

Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczystych pikseli.

```
BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    const POINT& pointDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Dojście do kontekstu urządzenia docelowego.

*xDest*<br/>
Współrzędną x, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędną y, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*bSrcAlpha*<br/>
Wartość alfa przezroczystości dla całego źródłową mapę bitową. Wartość domyślna 0xff (255) przyjęto założenie, że obraz jest nieprzezroczysta i chcesz używać każdego piksela tylko wartości alfa.

*bBlendOp*<br/>
Funkcja przenikaniem alfa dla źródłowego i docelowego, mapy bitowe, wartości alfa globalnej mają być stosowane do całego źródłową mapę bitową i informacji o formacie dla źródłową mapę bitową. Funkcje programu blend źródłowe i docelowe są obecnie ograniczone do AC_SRC_OVER.

*pointDest*<br/>
Odwołanie do [punktu](https://msdn.microsoft.com/library/windows/desktop/dd162805) struktura, która identyfikuje lewym górnym rogu prostokąta docelowego, w jednostkach logicznych.

*nDestWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta docelowego.

*nDestHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta docelowego.

*xSrc*<br/>
Logiczną współrzędną x lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Logiczną współrzędną y lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta źródłowego.

*rectDest*<br/>
Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, identyfikacji miejsca docelowego.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikacji źródła.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapy bitowe mieszania alfa obsługuje mieszania kolorów, na podstawie każdego piksela.

Gdy *bBlendOp* ustawiono domyślną AC_SRC_OVER źródłową mapę bitową znajduje się nad docelową mapę bitową na podstawie wartości alfa źródłowych.

##  <a name="attach"></a>  CImage::Attach

Dołącza *hBitmap* do `CImage` obiektu.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Dojście do HBITMAP.

*eOrientation*<br/>
Określa orientację mapy bitowej. Może to być jeden z następujących elementów:

- DIBOR_DEFAULT orientację mapy bitowej jest określany przez system operacyjny.

- DIBOR_BOTTOMUP wiersze mapy bitowej są w odwrotnej kolejności. Powoduje to, że [CImage::GetBits](#getbits) aby zwrócić wskaźnik osiągnie koniec buforu mapy bitowej i [CImage::GetPitch](#getpitch) zwracać wartość ujemną.

- DIBOR_TOPDOWN linie mapy bitowej znajdują się w od góry do dołu zamówienia. Powoduje to, że [CImage::GetBits](#getbits) aby zwrócić wskaźnik do pierwszego bajtu buforu mapy bitowej i [CImage::GetPitch](#getpitch) aby zwrócić liczbę dodatnią.

### <a name="remarks"></a>Uwagi

Mapa bitowa może być mapy bitowej DIB innych sekcji lub mapy bitowej DIB sekcji. Zobacz [IsDIBSection](#isdibsection) listę metod, których można używać tylko z DIB sekcji map bitowych.

##  <a name="bitblt"></a>  CImage::BitBlt

Kopiuje mapę bitową z kontekstem urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.

```
BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const POINT& pointDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Lokalizacja docelowa elementu HDC.

*xDest*<br/>
Logiczną współrzędną x lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Logiczną współrzędną y lewego górnego rogu prostokąta docelowego.

*dwROP*<br/>
Operację rastrową, która ma być wykonana. Kody operacji rastrowych definiują dokładnie, jak połączyć usługi bits źródła, miejsca docelowego i wzorca (zgodnie z definicją aktualnie wybrany pędzel) w celu utworzenia miejsca docelowego. Zobacz [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) w zestawie Windows SDK dla listy inne kody operacji rastrowych oraz ich opisy.

*pointDest*<br/>
A [punktu](https://msdn.microsoft.com/library/windows/desktop/dd162805) struktury wskazujący lewym górnym rogu prostokąta docelowego.

*nDestWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta docelowego.

*nDestHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta docelowego.

*xSrc*<br/>
Logiczną współrzędną x lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Logiczną współrzędną y lewego górnego rogu prostokąta źródłowego.

*rectDest*<br/>
A [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury wskazujący prostokąta docelowego.

*pointSrc*<br/>
A `POINT` struktury wskazujący lewym górnym rogu prostokąta źródłowego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) w zestawie Windows SDK.

##  <a name="cimage"></a>  CImage::CImage

Konstruuje `CImage` obiektu.

```
CImage() throw();
```

### <a name="remarks"></a>Uwagi

Gdy zostały zbudowane obiektu, wywołaj [Utwórz](#create), [obciążenia](#load), [loadfromresource —](#loadfromresource), lub [Dołącz](#attach) można dołączyć mapę bitową do obiektu.

**Uwaga** w programie Visual Studio, ta klasa śledzi liczbę `CImage` obiekty utworzone. Zawsze, gdy liczba wynosić 0, funkcja `GdiplusShutdown` jest wywoływana automatycznie, aby zwolnić zasoby używane przez interfejs GDI +. Gwarantuje to, że dowolny `CImage` obiekty utworzone bezpośrednio lub pośrednio przez biblioteki dll zawsze są poprawnie niszczone oraz że `GdiplusShutdown` nie jest wywoływana z funkcji DllMain.

Za pomocą globalnego `CImage` obiektów w bibliotece DLL nie jest zalecane. Jeśli musisz użyć globalną `CImage` obiektu w bibliotece DLL, wywołanie [CImage::ReleaseGDIPlus](#releasegdiplus) jawnie zwolnić zasoby używane przez interfejs GDI +.

##  <a name="create"></a>  CImage::Create

Tworzy `CImage` mapy bitowej i dołączyć go do wcześniej skonstruowany `CImage` obiektu.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Szerokość `CImage` mapy bitowej w pikselach.

*nHeight*<br/>
Wysokość `CImage` mapy bitowej w pikselach. Jeśli *nHeight* jest dodatnia, mapa bitowa jest DIB od dołu do góry i pochodzenia jest lewym dolnym rogu. Jeśli *nHeight* jest ujemna, mapy bitowej DIB góra dół i pochodzenia jest lewym górnym rogu.

*nBPP*<br/>
Liczby bitów na piksel w mapie bitowej. Zwykle 4, 8, 16, 24 lub 32. Może to być 1 w przypadku monochromatycznych map bitowych lub maski.

*Flagidw*<br/>
Określa, czy obiekt mapy bitowej ma kanału alfa. Może być kombinacją zero lub więcej z następujących wartości:

- *createAlphaChannel* można używać tylko jeśli *nBPP* wynosi 32, i *eCompression* jest BI_RGB. Jeśli zostanie określony, utworzony obraz ma wartość alfa (przezroczystości) każdego piksela, przechowywane w 4 bajtów każdego piksela (nieużywane obraz 32-bitowy innych niż alfanumeryczne). Ten kanał alfa automatycznie jest używany podczas wywoływania [CImage::AlphaBlend](#alphablend).

> [!NOTE]
> W wywołaniach [CImage::Draw](#draw), obrazów za pomocą kanału alfa są automatycznie alfa mieszane do miejsca docelowego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

##  <a name="createex"></a>  CImage::CreateEx

Tworzy `CImage` mapy bitowej i dołączyć go do wcześniej skonstruowany `CImage` obiektu.

```
BOOL CreateEx(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD eCompression,
    const DWORD* pdwBitmasks = NULL,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Szerokość `CImage` mapy bitowej w pikselach.

*nHeight*<br/>
Wysokość `CImage` mapy bitowej w pikselach. Jeśli *nHeight* jest dodatnia, mapa bitowa jest DIB od dołu do góry i pochodzenia jest lewym dolnym rogu. Jeśli *nHeight* jest ujemna, mapy bitowej DIB góra dół i pochodzenia jest lewym górnym rogu.

*nBPP*<br/>
Liczby bitów na piksel w mapie bitowej. Zwykle 4, 8, 16, 24 lub 32. Może to być 1 w przypadku monochromatycznych map bitowych lub maski.

*eCompression*<br/>
Określa typ kompresji skompresowany mapy bitowej od dołu do góry (nie mogą być kompresowane góra dół dib). Może być jednym z następujących wartości:

- BI_RGB format jest bez kompresji. Określenie tej wartości podczas wywoływania `CImage::CreateEx` jest równoważne z wywoływaniem `CImage::Create`.

- Nieskompresowane BI_BITFIELDS format i tabeli kolorów składa się z trzech maski kolor DWORD, które określają składników czerwonego, zielonego i niebieskiego, odpowiednio, każdego piksela. To jest prawidłowa, gdy jest używane z bpp 16 i 32-bitowe.

*pdwBitfields*<br/>
Używany tylko, jeśli *eCompression* jest ustawiona na BI_BITFIELDS, w przeciwnym razie musi być wartością NULL. Wskaźnik do tablicy trzy DWORD masek bitowych, określając bity każdego piksela, które są używane dla składników czerwonego, zielonego i niebieskiego koloru, odpowiednio. Aby uzyskać informacji na temat ograniczeń dla pola bitów, zobacz [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) w zestawie Windows SDK.

*Flagidw*<br/>
Określa, czy obiekt mapy bitowej ma kanału alfa. Może być kombinacją zero lub więcej z następujących wartości:

- *createAlphaChannel* można używać tylko jeśli *nBPP* wynosi 32, i *eCompression* jest BI_RGB. Jeśli zostanie określony, utworzony obraz ma wartość alfa (przezroczystości) każdego piksela, przechowywane w 4 bajtów każdego piksela (nieużywane obraz 32-bitowy innych niż alfanumeryczne). Ten kanał alfa automatycznie jest używany podczas wywoływania [CImage::AlphaBlend](#alphablend).

   > [!NOTE]
   > W wywołaniach [CImage::Draw](#draw), obrazów za pomocą kanału alfa są automatycznie alfa mieszane do miejsca docelowego.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie. W przeciwnym razie wartość FALSE.

### <a name="example"></a>Przykład

Poniższy przykład tworzy mapę bitową 100 x 100 pikseli, za pomocą 16 bitów do zakodowania każdego piksela. W danym piksela 16-bitowych bitów 0 – 3 kodowanie składnik czerwony, bity 4 – 7 kodowanie zielony i bity 8-11 kodowanie niebieski. Pozostałe 4 bity są nieużywane.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>  CImage::Destroy

Odłącza mapę bitową z `CImage` obiektu i niszczy mapy bitowej.

```
void Destroy() throw();
```

##  <a name="detach"></a>  CImage::Detach

Odłącza mapę bitową z `CImage` obiektu.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do mapy bitowej odłączone, lub wartość NULL, jeśli nie bitmapy jest dołączony.

##  <a name="draw"></a>  CImage::Draw

Kopiuje mapę bitową z kontekstem urządzenia źródłowego dla bieżącego kontekstu urządzenia.

```
BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest) const throw();

BOOL Draw(
    HDC hDestDC,
    const POINT& pointDest) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Dojście do kontekstu urządzenia docelowego.

*xDest*<br/>
Współrzędną x, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędną y, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*nDestWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta docelowego.

*nDestHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta docelowego.

*xSrc*<br/>
Współrzędną x, w jednostkach logicznych, lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Współrzędną y, w jednostkach logicznych, lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta źródłowego.

*rectDest*<br/>
Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, identyfikacji miejsca docelowego.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikacji źródła.

*pointDest*<br/>
Odwołanie do [punktu](https://msdn.microsoft.com/library/windows/desktop/dd162805) struktura, która identyfikuje lewym górnym rogu prostokąta docelowego, w jednostkach logicznych.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Draw` wykonuje tę samą operację jako [StretchBlt](#stretchblt), chyba że obraz, który zawiera kolor przezroczysty lub kanał alfa. W takim przypadku `Draw` wykonuje tę samą operację jako [TransparentBlt](#transparentblt) lub [AlphaBlend](#alphablend) stosownie do potrzeb.

W przypadku wersji `Draw` nieokreślenia prostokąta źródłowego, całego obrazu źródłowego jest ustawieniem domyślnym. Dla wersji `Draw` nie określa rozmiar prostokąta docelowego, rozmiar obrazu źródłowego jest to domyślny i bez rozciągania lub zmniejszanie występuje.

##  <a name="getbits"></a>  CImage::GetBits

Pobiera wskaźnik do wartości bitowe rzeczywiste pikselu mapy bitowej.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu mapy bitowej. Jeśli mapa bitowa jest DIB od dołu do góry, punkty wskaźnika pod koniec buforu. Jeśli mapa bitowa jest DIB góra dół, wskaźnik wskazuje na pierwszy bajt buforu.

### <a name="remarks"></a>Uwagi

Za pomocą tego wskaźnika, wraz z wartością zwróconą przez [GetPitch](#getpitch), można znaleźć i zmienić poszczególnych pikseli w obrazie.

> [!NOTE]
> Ta metoda obsługuje tylko mapy bitowe sekcji DIB; w związku z tym, możesz uzyskać dostęp do piksele `CImage` ten sam sposób, w jaki piksele sekcji DIB obiektu. Zwrócony wskaźnik wskazuje na piksel w lokalizacji (0, 0).

##  <a name="getbpp"></a>  CImage::GetBPP

Pobiera wartość bitów na piksel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba bitów na piksel.

### <a name="remarks"></a>Uwagi

Ta wartość określa liczbę bitów, które definiują każdego piksela i maksymalna liczba kolorów w mapie bitowej.

Liczba bitów na piksel jest zazwyczaj 1, 4, 8, 16, 24 lub 32. Zobacz `biBitCount` członkiem [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) w zestawie SDK Windows, aby uzyskać więcej informacji na temat tej wartości.

##  <a name="getcolortable"></a>  CImage::GetColorTable

Pobiera wartości kolorów (RGB) czerwony, zielony, niebieski z zakresu zapisów w palecie sekcji DIB.

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Indeks tabeli kolorów pierwszy wpis do pobrania.

*nColors*<br/>
Liczba wpisów tabeli kolorów do pobrania.

*prgbColors*<br/>
Wskaźnik do tablicy [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) struktur, aby pobrać kolor tabeli wpisów.

##  <a name="getdc"></a>  CImage::GetDC

Pobiera kontekst urządzenia, który aktualnie ma do niego obraz.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Dla każdego wywołania `GetDC`, konieczne jest posiadanie kolejne wywołanie [ReleaseDC](#releasedc).

##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString

Wyszukuje formatów obrazów dostępnych dla zapisywanie obrazów.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parametry

*strExporters*<br/>
Odwołanie do `CSimpleString` obiektu. Zobacz **uwagi** Aby uzyskać więcej informacji.

*aguidFileTypes*<br/>
Tablica identyfikatorów GUID, przy czym każdy element jednego z typów plików, w ciągu. W przykładzie w *pszAllFilesDescription* poniżej, *aguidFileTypes*[0] jest GUID_NULL, a pozostałe wartości w tablicy są formatów plików obrazów, które są obsługiwane przez bieżący system operacyjny.

> [!NOTE]
> Aby uzyskać pełną listę stałych, zobacz **stałe Format pliku obrazu** w zestawie Windows SDK.

*pszAllFilesDescription*<br/>
Jeśli ten parametr nie ma wartość NULL, ciąg filtru musi jeden dodatkowy filtr na początku listy. Ten filtr ma bieżącą wartość *pszAllFilesDescription* jego opis i akceptuje pliki dowolnego rozszerzenia obsługiwane przez inne eksportu, na liście.

Na przykład:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Zestaw flag bitowych, określając typy plików do wykluczenia z listy. Flagi dopuszczalny rozmiar to:

- `excludeGIF` = 0x01, pliki z wyłączeniem GIF.

- `excludeBMP` = 0x02, pliki z wyłączeniem BMP (mapa bitowa Windows).

- `excludeEMF` = 0x04 wyklucza EMF (rozszerzony metaplik) plików.

- `excludeWMF` = 0x08 wyklucza WMF (Windows metaplik) plików.

- `excludeJPEG` = pliki JPEG wyklucza 0x10.

- `excludePNG` = 0x20 wyklucza plików obrazów PNG.

- `excludeTIFF` = 0x40 TIFF nie obejmuje pliki.

- `excludeIcon` = 0x80, pliki z wyłączeniem ICO (ikona Windows).

- `excludeOther` = 0x80000000 nie obejmuje wszystkie inne typy plików, nie wymieniono powyżej.

- `excludeDefaultLoad` = 0 w przypadku obciążenia, wszystkie typy są domyślnie dołączone plików

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Do zapisywania, te pliki są wyłączone domyślnie, ponieważ zazwyczaj mają specjalne wymagania.

*chSeparator*<br/>
Separator oddzielający formatów obrazów. Zobacz **uwagi** Aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Wynikowy ciąg formatu można przekazać do usługi MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) obiektu do udostępnienia rozszerzenia plików obrazu dostępne formaty w oknie dialogowym Zapisz plik jako.

Parametr *strExporter* ma następujący format:

Plik description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;.. opis .xls *n*&#124;\*.roz *n*&#124;&#124;

gdzie "&#124;" znak separatora określoną przez `chSeparator`. Na przykład:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Użyj separatora domyślną "&#124;" w przypadku przekazania tego ciągu do MFC `CFileDialog` obiektu. Użyj separatora null '\0', jeśli te parametry są przekazywane do wspólne okno dialogowe Zapisz plik.

##  <a name="getheight"></a>  CImage::GetHeight

Pobiera wysokość w pikselach, obraz.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość w pikselach obrazu.

##  <a name="getimporterfilterstring"></a>  CImage::GetImporterFilterString

Wyszukiwanie dostępnych formatów obrazu podczas ładowania obrazów.

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parametry

*strImporters*<br/>
Odwołanie do `CSimpleString` obiektu. Zobacz **uwagi** Aby uzyskać więcej informacji.

*aguidFileTypes*<br/>
Tablica identyfikatorów GUID, przy czym każdy element jednego z typów plików, w ciągu. W przykładzie w *pszAllFilesDescription* poniżej, *aguidFileTypes*[0] jest GUID_NULL z wartości w pozostałych formatów plików obrazów, które są obsługiwane przez bieżący system operacyjny.

> [!NOTE]
> Aby uzyskać pełną listę stałych, zobacz **stałe Format pliku obrazu** w zestawie Windows SDK.

*pszAllFilesDescription*<br/>
Jeśli ten parametr nie ma wartość NULL, ciąg filtru musi jeden dodatkowy filtr na początku listy. Ten filtr ma bieżącą wartość *pszAllFilesDescription* jego opis i akceptuje pliki dowolnego rozszerzenia obsługiwane przez inne eksportu, na liście.

Na przykład:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Zestaw flag bitowych, określając typy plików do wykluczenia z listy. Flagi dopuszczalny rozmiar to:

- `excludeGIF` = 0x01, pliki z wyłączeniem GIF.

- `excludeBMP` = 0x02, pliki z wyłączeniem BMP (mapa bitowa Windows).

- `excludeEMF` = 0x04 wyklucza EMF (rozszerzony metaplik) plików.

- `excludeWMF` = 0x08 wyklucza WMF (Windows metaplik) plików.

- `excludeJPEG` = pliki JPEG wyklucza 0x10.

- `excludePNG` = 0x20 wyklucza plików obrazów PNG.

- `excludeTIFF` = 0x40 TIFF nie obejmuje pliki.

- `excludeIcon` = 0x80, pliki z wyłączeniem ICO (ikona Windows).

- `excludeOther` = 0x80000000 nie obejmuje wszystkie inne typy plików, nie wymieniono powyżej.

- `excludeDefaultLoad` = 0 w przypadku obciążenia, wszystkie typy są domyślnie dołączone plików

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Do zapisywania, te pliki są wyłączone domyślnie, ponieważ zazwyczaj mają specjalne wymagania.

*chSeparator*<br/>
Separator oddzielający formatów obrazów. Zobacz **uwagi** Aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Wynikowy ciąg formatu można przekazać do usługi MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) obiektu do udostępnienia rozszerzenia plików obrazu dostępnych formatów w **Otwórz plik** okno dialogowe.

Parametr *strImporter* ma następujący format:

Plik description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;.. opis .xls *n*&#124;\*.roz *n*&#124;&#124;

gdzie "&#124;" jest określony przez znak separatora *chSeparator*. Na przykład:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Użyj separatora domyślną "&#124;" w przypadku przekazania tego ciągu do MFC `CFileDialog` obiektu. Użyj separatora null '\0', jeśli te parametry są przekazywane do wspólnego **Otwórz plik** okno dialogowe.

##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries

Pobiera maksymalną liczbę wpisów w tabeli kolorów.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów w tabeli kolorów.

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje tylko DIB sekcji bitmapy.

##  <a name="getpitch"></a>  CImage::GetPitch

Pobiera wysokość obrazu.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość obrazu. Jeśli wartość zwracana jest ujemna, mapa bitowa jest DIB od dołu do góry i pochodzenia jest lewym dolnym rogu. Jeśli wartość zwracana jest dodatnia, mapa bitowa jest DIB góra dół i pochodzenia jest lewym górnym rogu.

### <a name="remarks"></a>Uwagi

Wysokość jest odległość, w bajtach między dwa adresy pamięci, które reprezentują początek jednowierszowy mapy bitowej a początkiem następnego wiersza mapy bitowej. Ponieważ skoku jest mierzony w bajtach, wysokość obrazu pomaga określić format pikseli. Wysokość mogą również obejmować dodatkową pamięć, zarezerwowane dla mapy bitowej.

Użyj `GetPitch` z [GetBits](#getbits) można znaleźć piksele obrazu.

> [!NOTE]
> Ta metoda obsługuje tylko DIB sekcji bitmapy.

##  <a name="getpixel"></a>  CImage::GetPixel

Pobiera kolor piksela w lokalizacji określonej przez *x* i *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Współrzędna x piksela.

*y*<br/>
Współrzędna y piksela.

### <a name="return-value"></a>Wartość zwracana

Czerwony, zielony, niebieski (RGB) wartość piksela. Jeśli piksel znajduje się poza bieżącym obszaru przycinania, wartość zwracana jest CLR_INVALID.

##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress

Pobiera adres dokładny piksel.

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Współrzędna x piksela.

*y*<br/>
Współrzędna y piksela.

### <a name="remarks"></a>Uwagi

Adres jest określana zgodnie z współrzędne piksel, wysokość mapy bitowej i bitów na piksel.

Formatów, które mają mniej niż 8 bitów na piksel metoda ta zwraca adres bajtów zawierającą piksela. Na przykład, jeśli Twoja format obrazu ma 4 bity na piksel `GetPixelAddress` zwraca adres piksela pierwszy bajt, a musisz obliczyć 2 pikseli na bajt.

> [!NOTE]
> Ta metoda obsługuje tylko DIB sekcji bitmapy.

##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor

Pobiera lokalizację indeksowanych przezroczysty kolor z palety kolorów.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Indeks kolor przezroczysty.

##  <a name="getwidth"></a>  CImage::GetWidth

Pobiera szerokość w pikselach, obraz.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Szerokość mapy bitowej w pikselach.

##  <a name="isdibsection"></a>  CImage::IsDIBSection

Określa, czy dołączonych mapy bitowej sekcji DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli dołączone bitmapa jest sekcja DIB. W przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Mapa bitowa nie jest sekcja DIB, nie można użyć następujących `CImage` metody, które obsługują tylko DIB sekcji mapy bitowe:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>  CImage::IsIndexed

Określa, czy mapę bitową pikseli są mapowane do palety kolorów.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli indeksowane; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość TRUE tylko wtedy, gdy 8-bitowych mapy bitowej (256 kolorów) lub mniej.

> [!NOTE]
> Ta metoda obsługuje tylko DIB sekcji bitmapy.

##  <a name="isnull"></a>  CImage::IsNull

Określa, jeśli mapa bitowa jest aktualnie załadowana.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość PRAWDA, jeśli mapa bitowa nie jest aktualnie załadowana; w przeciwnym razie wartość FALSE.

##  <a name="istransparencysupported"></a>  CImage::IsTransparencySupported

Wskazuje, czy aplikacja obsługuje przezroczysty map bitowych.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli bieżąca platforma obsługuje przezroczystość. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana jest wartość różną od zera i przezroczystości jest obsługiwany, wywołanie [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt), lub [Rysowanie](#draw) będzie obsługiwać kolory przezroczyste.

##  <a name="load"></a>  CImage::Load

Ładuje obraz.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pszFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku obrazu do załadowania.

*pStream*<br/>
Wskaźnik do strumienia, zawierający nazwę pliku obrazu do załadowania.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Ładuje obraz określony przez *pszFileName* lub *pStream*.

Obraz prawidłowe typy to BMP, GIF, JPEG, PNG i TIFF.

##  <a name="loadfromresource"></a>  CImage::LoadFromResource

Ładuje obraz z zasób mapy BITOWEJ.

```
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Dojście do wystąpienia modułu, który zawiera obraz, który ma zostać załadowany.

*pszResourceName*<br/>
Wskaźnik do ciągu zawierającego nazwę zasobu obrazu, aby załadować.

*nIDResource*<br/>
Identyfikator zasobu do załadowania.

### <a name="remarks"></a>Uwagi

Zasób musi być typu mapy BITOWEJ.

##  <a name="maskblt"></a>  CImage::MaskBlt

Łączy dane koloru dla map bitowych źródłowych i docelowych przy użyciu określonej maski i operacja rastrowa.

```
BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    HBITMAP hbmMask,
    int xMask,
    int yMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    HBITMAP hbmMask,
    const POINT& pointMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const POINT& pointDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Dojście do modułu, którego pliku wykonywalnego zawiera zasób.

*xDest*<br/>
Współrzędną x, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędną y, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*nDestWidth*<br/>
Szerokość w logiczne jednostki docelowej prostokąt i źródłowej mapy bitowej.

*nDestHeight*<br/>
Wysokość w logiczne jednostki docelowej prostokąt i źródłowej mapy bitowej.

*xSrc*<br/>
Logiczną współrzędną x lewego górnego rogu źródłową mapę bitową.

*ySrc*<br/>
Logiczną współrzędną y lewego górnego rogu źródłową mapę bitową.

*hbmMask*<br/>
Dojście do mapy bitowej maski monochromatyczny, w połączeniu z mapą bitową kolorów w kontekście urządzenia źródłowego.

*xMask*<br/>
Przesunięcie poziomy pikseli mapy bitowej maski określony przez *hbmMask* parametru.

*yMask*<br/>
Mapy bitowej maski określonej przez przesunięcie pikseli w pionie *hbmMask* parametru.

*dwROP*<br/>
Określa pierwszego planu i tła kody operacji rastrowych trójargumentowy, używanych przez metodę do kontrolowania kombinację danych źródłowych i docelowych. Kod operacji rastrowych tła jest przechowywany w bajt wyższego rzędu word wyższego rzędu tej wartości; Kod operacji rastrowych pierwszego planu jest przechowywany w mniej znaczący bajt, wyraz wyższego rzędu tej wartości; word niskiego rzędu tej wartości jest ignorowany i powinna wynosić zero. Omówienie pierwszego planu i tła w kontekście tej metody, zobacz `MaskBlt` w zestawie Windows SDK. Aby uzyskać listę typowych kody operacji rastrowych, zobacz `BitBlt` w zestawie Windows SDK.

*rectDest*<br/>
Odwołanie do `RECT` struktury, identyfikacji miejsca docelowego.

*pointSrc*<br/>
A `POINT` struktury wskazujący lewym górnym rogu prostokąta źródłowego.

*pointMask*<br/>
A `POINT` struktury wskazujący lewym górnym rogu mapy bitowej maski.

*pointDest*<br/>
Odwołanie do `POINT` struktura, która identyfikuje lewym górnym rogu prostokąta docelowego, w jednostkach logicznych.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda ma zastosowanie do systemu Windows NT, w wersji 4.0 lub nowsza.

##  <a name="operator_hbitmap"></a>  HBITMAP CImage::operator

Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CImage` obiektu. Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia obiektu HBITMAP.

##  <a name="plgblt"></a>  CImage::PlgBlt

Wykonuje przesunięcia bitowego bloku z prostokątem kontekst urządzenia źródłowego do równoległobok w kontekście urządzenia docelowego.

```
BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    HBITMAP hbmMask = NULL,
    int xMask = 0,
    int yMask = 0) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    const RECT& rectSrc,
    HBITMAP hbmMask = NULL,
    const POINT& pointMask = CPoint(0, 0)) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Dojście do kontekstu urządzenia docelowego.

*pPoints*<br/>
Wskaźnik do tablicy trzy punkty w przestrzeni logicznej, które identyfikują trzy narożników równoległobok docelowego. Lewym górnym rogu prostokąta źródłowego jest mapowana do pierwszego punktu, w tej tablicy, prawym górnym rogu do drugiego w tej tablicy i lewym dolnym rogu trzeci punktu. W prawym dolnym rogu prostokąta źródłowego jest zamapowana na czwarty niejawne momentów równoległobok.

*hbmMask*<br/>
Dojście do opcjonalne monochromatycznych map bitowych, służący do zamaskowania kolory prostokąta źródłowego.

*xSrc*<br/>
Współrzędną x, w jednostkach logicznych, lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Współrzędną y, w jednostkach logicznych, lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta źródłowego.

*xMask*<br/>
Współrzędna x lewy górny róg monochromatyczną mapę bitową.

*yMask*<br/>
Współrzędna y lewy górny róg monochromatyczną mapę bitową.

*rectSrc*<br/>
Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury określenia współrzędnych prostokąta źródłowego.

*pointMask*<br/>
A [punktu](https://msdn.microsoft.com/library/windows/desktop/dd162805) struktury wskazujący lewym górnym rogu mapy bitowej maski.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *hbmMask* identyfikuje Nieprawidłowa mapa bitowa monochromatyczna, `PlgBit` używa tej mapy bitowej do maski bitów dane koloru z prostokąta źródłowego.

Ta metoda ma zastosowanie do systemu Windows NT, w wersji 4.0 lub nowsza. Zobacz [PlgBlt](/windows/desktop/api/wingdi/nf-wingdi-plgblt) w zestawie Windows SDK dla bardziej szczegółowych informacji.

##  <a name="releasedc"></a>  CImage::ReleaseDC

Udostępnia kontekst urządzenia.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Uwagi

Ponieważ do kontekstu urządzenia można wybrać tylko jedną mapy bitowej w czasie, należy wywołać `ReleaseDC` dla każdego wywołania [getdc —](#getdc).

##  <a name="releasegdiplus"></a>  CImage::ReleaseGDIPlus

Zwalnia zasoby używane przez interfejs GDI +.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Uwagi

Można wywołać tej metody, aby zwolnić zasoby przydzielone przez globalną `CImage` obiektu. Zobacz [CImage::CImage](#cimage).

##  <a name="save"></a>  CImage::Save

Zapisuje obraz do określonego strumienia lub plik na dysku.

```
HRESULT Save(
    IStream* pStream,
    REFGUID guidFileType) const throw();

HRESULT Save(
    LPCTSTR pszFileName,
    REFGUID guidFileType = GUID_NULL) const throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Wskaźnik do obiektu COM IStream zawierający dane obrazu w pliku.

*pszFileName*<br/>
Wskaźnik na nazwę pliku obrazu.

*guidFileType*<br/>
Typ pliku, aby zapisać obraz jako. Może to być jeden z następujących elementów:

- `ImageFormatBMP` Obraz nieskompresowaną.

- `ImageFormatPNG` Skompresowany obraz Portable Network grafiki (PNG).

- `ImageFormatJPEG` Skompresowany obraz JPEG.

- `ImageFormatGIF` Skompresowany obraz GIF.

> [!NOTE]
> Aby uzyskać pełną listę stałych, zobacz **stałe Format pliku obrazu** w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zapisać obraz przy użyciu określonej nazwy i typu. Jeśli *guidFileType* parametr nie jest uwzględniony, rozszerzenie nazwy pliku zostanie użyta do określenia formatu obrazu. Jeśli rozszerzenie nie zostanie podany, obraz zostanie zapisany w formacie BMP.

##  <a name="setcolortable"></a>  CImage::SetColorTable

Ustawia czerwony, zielony, niebieski (RGB) koloru wartości zakresu zapisów w palecie sekcji DIB.

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Indeks tabeli kolorów pierwszy wpis do ustawienia.

*nColors*<br/>
Liczba wpisy tabeli kolorów do ustawienia.

*prgbColors*<br/>
Wskaźnik do tablicy [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) struktury, aby ustawić kolor tabeli wpisów.

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje tylko DIB sekcji bitmapy.

##  <a name="setpixel"></a>  CImage::SetPixel

Ustawia kolor piksel w danej lokalizacji w mapie bitowej.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Poziome położenie pikseli, aby ustawić.

*y*<br/>
Położenie w pionie piksela, aby ustawić.

*Kolor*<br/>
Kolor, dla którego należy ustawić piksela.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli piksel koordynuje znajdują się poza regionem wybranego wycinka.

##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed

Ustawia kolor piksela na kolor, znajdującym się w *iIndex* w palecie kolorów.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Poziome położenie pikseli, aby ustawić.

*y*<br/>
Położenie w pionie piksela, aby ustawić.

*iIndex*<br/>
Indeks kolor z palety kolorów.

##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB

Ustawia piksel w lokalizacjach, określonych przez *x* i *y* kolory wskazywanym przez *r*, *g*, i *b*, w czerwony, zielony, niebieski obrazu (RGB).

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Poziome położenie pikseli, aby ustawić.

*y*<br/>
Położenie w pionie piksela, aby ustawić.

*r*<br/>
Intensywność koloru czerwonego.

*g*<br/>
Intensywność kolor zielony.

*b*<br/>
Intensywność koloru niebieskiego.

### <a name="remarks"></a>Uwagi

Każdy czerwonego, zielonego i niebieskiego parametry są reprezentowane przez liczbą z zakresu od 0 do 255. Jeśli wszystkie trzy parametry jest ustawiona na zero, połączone kolor wynikowy będzie czarny. Jeśli wszystkie trzy parametry jest ustawiona na wartość 255, połączone kolor wynikowy jest białe.

##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor

Określa kolor w podanej lokalizacji indeksowanych jako przezroczysty.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parametry

*iTransparentColor*<br/>
Indeks w palecie kolorów, koloru, aby ustawić do przezroczysty. Jeśli wartość-1, Brak koloru jest ustawiony na przezroczysty.

### <a name="return-value"></a>Wartość zwracana

Indeks koloru wcześniej ustawione jako przezroczysty.

##  <a name="stretchblt"></a>  CImage::StretchBlt

Kopiuje mapę bitową z kontekstem urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.

```
BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Dojście do kontekstu urządzenia docelowego.

*xDest*<br/>
Współrzędną x, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędną y, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*nDestWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta docelowego.

*nDestHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta docelowego.

*dwROP*<br/>
Operację rastrową, która ma być wykonana. Kody operacji rastrowych definiują dokładnie, jak połączyć usługi bits źródła, miejsca docelowego i wzorca (zgodnie z definicją aktualnie wybrany pędzel) w celu utworzenia miejsca docelowego. Zobacz [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) w zestawie Windows SDK dla listy inne kody operacji rastrowych oraz ich opisy.

*rectDest*<br/>
Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, identyfikacji miejsca docelowego.

*xSrc*<br/>
Współrzędną x, w jednostkach logicznych, lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Współrzędną y, w jednostkach logicznych, lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta źródłowego.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikacji źródła.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [StretchBlt](/windows/desktop/api/wingdi/nf-wingdi-stretchblt) w zestawie Windows SDK.

##  <a name="transparentblt"></a>  CImage::TransparentBlt

Kopiuje mapę bitową z kontekstem urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.

```
BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    UINT crTransparent = CLR_INVALID) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Dojście do kontekstu urządzenia docelowego.

*xDest*<br/>
Współrzędną x, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędną y, w jednostkach logicznych, lewego górnego rogu prostokąta docelowego.

*nDestWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta docelowego.

*nDestHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta docelowego.

*crTransparent*<br/>
Kolor źródłową mapę bitową do traktowania jako przezroczysty. Domyślnie CLR_INVALID, wskazujący, że kolor jest obecnie ustawiony jako przezroczysty kolor obrazu należy używać.

*rectDest*<br/>
Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, identyfikacji miejsca docelowego.

*xSrc*<br/>
Współrzędną x, w jednostkach logicznych, lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Współrzędną y, w jednostkach logicznych, lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych, prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość w jednostkach logicznych, prostokąta źródłowego.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikacji źródła.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie, w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

`TransparentBlt` jest obsługiwana dla źródła mapy bitowe, 4 bitów na piksel i 8 bitów na piksel. Użyj [CImage::AlphaBlend](#alphablend) do określenia 32 bity na piksel map bitowych o przezroczystości.

### <a name="example"></a>Przykład

```cpp
// Performs a transparent blit from the source image to the destination
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage,
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
    HDC hDstDC = NULL;
    BOOL bResult;

    if(pSrcImage == NULL || pDstImage == NULL)
    {
        // Invalid parameter
        return FALSE;
    }

    // Obtain a DC to the destination image
    hDstDC = pDstImage->GetDC();
    // Perform the blit
    bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

    // Release the destination DC
    pDstImage->ReleaseDC();

    return bResult;
}
```

## <a name="see-also"></a>Zobacz też

[Przykładowe MMXSwarm](../../visual-cpp-samples.md)<br/>
[Przykładowe SimpleImage](../../visual-cpp-samples.md)<br/>
[Map bitowych niezależnych od urządzenia](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)<br/>
[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)<br/>
[Map bitowych niezależnych od urządzenia](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)
