---
title: Klasa funkcji CImage
ms.date: 08/19/2019
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
ms.openlocfilehash: 3b278f37bbcbe2ee879d9c3d2837267fe31e57e2
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630716"
---
# <a name="cimage-class"></a>Klasa funkcji CImage

`CImage`zapewnia obsługę ulepszonej mapy bitowej, w tym możliwość ładowania i zapisywania obrazów w formatach JPEG, GIF, BMP i Portable Network Graphics (PNG).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CImage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Funkcji CImage:: funkcji CImage](#cimage)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Funkcji CImage:: AlphaBlend](#alphablend)|Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczyste piksele.|
|[CImage::Attach](#attach)|Dołącza HBITMAP do `CImage` obiektu. Można go używać z mapami bitowymi sekcji innym niż DIB lub mapy bitowe sekcji DIB.|
|[CImage::BitBlt](#bitblt)|Kopiuje mapę bitową z kontekstu urządzenia źródłowego do tego bieżącego kontekstu urządzenia.|
|[Funkcji CImage:: Create](#create)|Tworzy mapę bitową sekcji DIB i dołącza ją do wcześniej skonstruowanego `CImage` obiektu.|
|[Funkcji CImage:: CreateEx](#createex)|Tworzy mapę bitową sekcji DIB (z dodatkowymi parametrami) i dołącza ją do wcześniej `CImage` skonstruowanego obiektu.|
|[Funkcji CImage::D Estroy](#destroy)|Odłącza mapę bitową od `CImage` obiektu i niszczy mapę bitową.|
|[CImage::Detach](#detach)|Odłącza mapę bitową od `CImage` obiektu.|
|[Funkcji CImage::D RAW](#draw)|Kopiuje mapę bitową z prostokąta źródłowego do docelowego prostokąta. `Draw`rozciąga lub kompresuje mapę bitową, aby dopasować ją do wymiarów prostokąta docelowego, w razie potrzeby, i obsługuje mieszanie alfa i przezroczyste kolory.|
|[Funkcji CImage:: GetBits](#getbits)|Pobiera wskaźnik do rzeczywistych wartości pikseli mapy bitowej.|
|[Funkcji CImage:: GetBPP](#getbpp)|Pobiera bity na piksel.|
|[CImage::GetColorTable](#getcolortable)|Pobiera kolor czerwony, zielony, niebieski (RGB) z zakresu wpisów w tabeli kolorów.|
|[CImage::GetDC](#getdc)|Pobiera kontekst urządzenia, do którego została wybrana bieżąca Mapa bitowa.|
|[Funkcji CImage:: GetExporterFilterString](#getexporterfilterstring)|Umożliwia znalezienie dostępnych formatów obrazów i ich opisów.|
|[Funkcji CImage:: GetHeight](#getheight)|Pobiera wysokość bieżącego obrazu (w pikselach).|
|[Funkcji CImage:: GetImporterFilterString](#getimporterfilterstring)|Umożliwia znalezienie dostępnych formatów obrazów i ich opisów.|
|[Funkcji CImage:: GetMaxColorTableEntries](#getmaxcolortableentries)|Pobiera maksymalną liczbę wpisów w tabeli kolorów.|
|[CImage::GetPitch](#getpitch)|Pobiera wysokość bieżącego obrazu, w bajtach.|
|[CImage::GetPixel](#getpixel)|Pobiera kolor pikseli określony przez *x* i *y*.|
|[Funkcji CImage:: GetPixelAddress](#getpixeladdress)|Pobiera adres danego piksela.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Pobiera pozycję przezroczystego koloru w tabeli kolorów.|
|[Funkcji CImage:: getwidth](#getwidth)|Pobiera szerokość bieżącego obrazu (w pikselach).|
|[Funkcji CImage:: IsDIBSection](#isdibsection)|Określa, czy załączona Mapa bitowa jest sekcją DIB.|
|[Funkcji CImage:: IsIndexed](#isindexed)|Wskazuje, że kolory mapy bitowej są mapowane na zaindeksowaną paletę.|
|[Funkcji CImage:: IsNull](#isnull)|Wskazuje, czy źródłowa Mapa bitowa jest aktualnie załadowana.|
|[Funkcji CImage:: IsTransparencySupported](#istransparencysupported)|Wskazuje, czy aplikacja obsługuje przezroczyste mapy bitowe.|
|[Funkcji CImage:: Load](#load)|Ładuje obraz z określonego pliku.|
|[Funkcji CImage:: LoadFromResource](#loadfromresource)|Ładuje obraz z określonego zasobu.|
|[Funkcji CImage:: MaskBlt](#maskblt)|Łączy dane koloru dla źródłowej i docelowej mapy bitowej przy użyciu określonej maski i operacji rastrowej.|
|[CImage::PlgBlt](#plgblt)|Wykonuje transfer bloku bitowego z prostokąta w kontekście urządzenia źródłowego do pliku równoległobok w kontekście urządzenia docelowego.|
|[CImage::ReleaseDC](#releasedc)|Zwalnia kontekst urządzenia, który został pobrany z [funkcji CImage:: GetDC —](#getdc).|
|[Funkcji CImage:: ReleaseGDIPlus](#releasegdiplus)|Zwalnia zasoby używane przez GDI+. Musi być wywołana, aby zwolnić zasoby utworzone przez obiekt `CImage` globalny.|
|[Funkcji CImage:: Save](#save)|Zapisuje obraz jako określony typ. `Save`nie można określić opcji obrazu.|
|[CImage::SetColorTable](#setcolortable)|Ustawia kolor czerwony, zielony, niebieski RGB) w zakresie wpisów w tabeli kolorów sekcji DIB.|
|[CImage::SetPixel](#setpixel)|Ustawia piksel na określonych współrzędnych na określony kolor.|
|[Funkcji CImage:: SetPixelIndexed](#setpixelindexed)|Ustawia piksel dla określonych współrzędnych koloru w określonym indeksie palety.|
|[Funkcji CImage:: SetPixelRGB](#setpixelrgb)|Ustawia piksel na określonych współrzędnych z określoną czerwoną, zieloną, niebieską (RGB) wartością.|
|[Funkcji CImage:: SetTransparentColor](#settransparentcolor)|Ustawia indeks koloru, który ma być traktowany jako przezroczysty. Tylko jeden kolor w palecie może być przezroczysty.|
|[CImage::StretchBlt](#stretchblt)|Kopiuje mapę bitową ze prostokąta źródłowego do docelowego prostokąta, rozciągając lub kompresując mapę bitową do wymiarów prostokąta docelowego, w razie potrzeby.|
|[Funkcji CImage:: TransparentBlt](#transparentblt)|Kopiuje mapę bitową z przezroczystym kolorem z kontekstu urządzenia źródłowego do tego bieżącego kontekstu urządzenia.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Funkcji CImage:: operator HBITMAP](#operator_hbitmap)|Zwraca dojście systemu Windows dołączone do `CImage` obiektu.|

## <a name="remarks"></a>Uwagi

`CImage`Pobiera mapy bitowe, które są albo niezależne od urządzenia mapy bitowe (DIB); można jednak użyć [Create](#create) lub [funkcji CImage:: Load](#load) tylko z sekcjami DIB. Do `CImage` obiektu można dołączyć mapę bitową innych niż DIB, ale nie [](#attach)można użyć następujących `CImage` metod, które obsługują tylko mapy bitowe sekcji DIB:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Aby określić, czy dołączona mapa bitowa jest sekcją DIB, wywołaj [IsDibSection](#isdibsection).

> [!NOTE]
> W programie Visual Studio .NET 2003 ta klasa przechowuje `CImage` liczbę utworzonych obiektów. Za każdym razem, gdy liczba jest równa `GdiplusShutdown` 0, funkcja jest automatycznie wywoływana w celu zwolnienia zasobów używanych przez GDI+. Dzięki temu wszystkie `CImage` obiekty utworzone bezpośrednio lub pośrednio przez biblioteki DLL są zawsze niszczone `GdiplusShutdown` i nie są wywoływane z programu `DllMain`.

> [!NOTE]
> Nie zaleca `CImage` się używania obiektów globalnych w bibliotece DLL. Jeśli musisz użyć obiektu globalnego `CImage` w bibliotece DLL, wywołaj [funkcji CImage:: ReleaseGDIPlus](#releasegdiplus) , aby jawnie zwolnić zasoby używane przez GDI+.

`CImage`nie można wybrać nowego elementu [przechwytywania](../../mfc/reference/cdc-class.md). `CImage`tworzy własne używający HDC dla obrazu. Ponieważ HBITMAP można wybrać tylko w jednej używający HDC naraz, HBITMAP skojarzona z elementem `CImage` nie może zostać wybrana w innym używający HDC. Jeśli potrzebujesz przeszukiwania danych, Pobierz używający HDC z `CImage` i przekaż go do [przechwytywania:: FromHandle](../../mfc/reference/cdc-class.md#fromhandle).

## <a name="example"></a>Przykład

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

W przypadku użycia `CImage` w projekcie MFC należy zauważyć, które funkcje członkowskie w projekcie oczekują wskaźnika do obiektu [CBitmap](../../mfc/reference/cbitmap-class.md) . Jeśli `CImage` chcesz użyć tej funkcji, takiej jak [CMenu:: AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), użyj [CBitmap:: FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), przekaż ją do swojego `CImage` elementu HBITMAP, a następnie użyj zwróconego `CBitmap*`elementu.

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

Za `CImage`pomocą programu masz dostęp do rzeczywistych bitów sekcji DIB. Możesz użyć `CImage` obiektu wszędzie tam, gdzie wcześniej użyto sekcji Win32 HBITMAP lub DIB.

Można użyć `CImage` z MFC lub ATL.

> [!NOTE]
> Podczas tworzenia projektu przy użyciu `CImage`, należy zdefiniować `CString` przed dołączeniem *atlimage. h*. Jeśli projekt używa biblioteki ATL bez MFC, Dołącz *pliku atlstr. h* przed dołączeniem *atlimage. h*. Jeśli projekt korzysta z MFC (lub jeśli jest to projekt ATL z obsługą MFC), Dołącz *afxstr. h* przed dołączeniem *atlimage. h*.<br/>
> <br/>
> Podobnie należy dołączyć *atlimage. h* przed dołączeniem *atlimpl. cpp*. Aby to ułatwić, należy uwzględnić *atlimage. h* w Twoim *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i jego wcześniejszych).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlimage. h

##  <a name="alphablend"></a>Funkcji CImage:: AlphaBlend

Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczyste piksele.

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
Współrzędna x (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędna y (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*bSrcAlpha*<br/>
Wartość przezroczystości alfa, która ma być używana w całej źródłowej mapie bitowej. Domyślna wartość 0xFF (255) zakłada, że obraz jest nieprzezroczysty i że chcesz używać tylko wartości alfa na piksel.

*bBlendOp*<br/>
Funkcja alfa-Blend dla źródłowej i docelowej mapy bitowej, globalnej wartości alfa, która ma zostać zastosowana do całej źródłowej mapy bitowej i informacje o formacie dla źródłowej mapy bitowej. Źródłowa i docelowa funkcja mieszania są obecnie ograniczone do AC_SRC_OVER.

*pointDest*<br/>
Odwołanie do struktury [punktu](/previous-versions/dd162805\(v=vs.85\)) , która identyfikuje górny lewy róg prostokąta docelowego w jednostkach logicznych.

*nDestWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta docelowego.

*nDestHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta docelowego.

*xSrc*<br/>
Logiczna Współrzędna x lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Logiczna Współrzędna y lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta źródłowego.

*rectDest*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , identyfikując miejsce docelowe.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikujące źródło.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapy bitowe alfa-Blend obsługują mieszanie kolorów w pikselach.

Gdy *bBlendOp* jest ustawiona na wartość domyślną AC_SRC_OVER, źródłowa Mapa bitowa jest umieszczana na docelowej mapie bitowej na podstawie wartości alfa pikseli źródłowych.

##  <a name="attach"></a>Funkcji CImage:: Attach

Dołącza *hBitmap* do `CImage` obiektu.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Dojście do HBITMAP.

*eOrientation*<br/>
Określa orientację mapy bitowej. Może to być jeden z następujących elementów:

- DIBOR_DEFAULT orientacji mapy bitowej jest określana przez system operacyjny.

- DIBOR_BOTTOMUP linie mapy bitowej są w kolejności odwrotnej. Powoduje to, że [funkcji CImage:: GetBits](#getbits) , aby zwrócić wskaźnik blisko końca buforu mapy bitowej i [funkcji CImage:: getgęstość](#getpitch) do zwrócenia liczby ujemnej.

- DIBOR_TOPDOWN linie mapy bitowej są w kolejności od góry do dołu. Powoduje to, że [funkcji CImage:: GetBits](#getbits) zwraca wskaźnik do pierwszego bajtu buforu mapy bitowej i [funkcji CImage:: getskoku](#getpitch) , aby zwrócić liczbę dodatnią.

### <a name="remarks"></a>Uwagi

Mapa bitowa może być mapą bitową sekcji innej niż DIB lub mapą bitową sekcji DIB. Zobacz [IsDIBSection](#isdibsection) , aby uzyskać listę metod, których można używać tylko z mapami bitowymi sekcji DIB.

##  <a name="bitblt"></a>Funkcji CImage:: BitBlt

Kopiuje mapę bitową z kontekstu urządzenia źródłowego do tego bieżącego kontekstu urządzenia.

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
UŻYWAJĄCY HDC docelowy.

*xDest*<br/>
Logiczna Współrzędna x lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Logiczna Współrzędna y lewego górnego rogu prostokąta docelowego.

*dwROP*<br/>
Operacja rastrowa, która ma zostać wykonana. Kody operacji rastrowych definiują dokładnie sposób łączenia bitów źródła, miejsca docelowego i wzorca (zgodnie z definicją aktualnie wybranego pędzla) w celu utworzenia miejsca docelowego. Zobacz [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) w Windows SDK, aby zapoznać się z listą innych kodów operacji rastrowych i ich opisów.

*pointDest*<br/>
Struktura [punktu](/previous-versions/dd162805\(v=vs.85\)) wskazująca górny lewy róg prostokąta docelowego.

*nDestWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta docelowego.

*nDestHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta docelowego.

*xSrc*<br/>
Logiczna Współrzędna x lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Logiczna Współrzędna y lewego górnego rogu prostokąta źródłowego.

*rectDest*<br/>
Struktura obiektu [Rect](/previous-versions/dd162897\(v=vs.85\)) wskazująca prostokąt docelowy.

*pointSrc*<br/>
`POINT` Struktura wskazująca lewy górny róg prostokąta źródłowego.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) w Windows SDK.

##  <a name="cimage"></a>Funkcji CImage:: funkcji CImage

Konstruuje `CImage` obiekt.

```
CImage() throw();
```

### <a name="remarks"></a>Uwagi

Po skompilowaniu obiektu, wywołaj polecenie [Utwórz](#create), [Załaduj](#load), [LoadFromResource](#loadfromresource)lub [Dołącz](#attach) , aby dołączyć mapę bitową do obiektu.

**Uwaga** W programie Visual Studio ta klasa przechowuje `CImage` liczbę utworzonych obiektów. Za każdym razem, gdy liczba jest równa `GdiplusShutdown` 0, funkcja jest automatycznie wywoływana w celu zwolnienia zasobów używanych przez GDI+. Dzięki temu wszystkie `CImage` obiekty utworzone bezpośrednio lub pośrednio przez biblioteki DLL są zawsze niszczone `GdiplusShutdown` i nie są wywoływane z DllMain.

Nie zaleca `CImage` się używania obiektów globalnych w bibliotece DLL. Jeśli musisz użyć obiektu globalnego `CImage` w bibliotece DLL, wywołaj [funkcji CImage:: ReleaseGDIPlus](#releasegdiplus) , aby jawnie zwolnić zasoby używane przez GDI+.

##  <a name="create"></a>Funkcji CImage:: Create

Tworzy mapę bitową i dołącza ją do wcześniej skonstruowanego `CImage` obiektu. `CImage`

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
Wysokość `CImage` mapy bitowej w pikselach. Jeśli *nHeight* ma wartość dodatnią, mapa bitowa jest dolną KRAWĘDZIą DIB, a jej źródłem jest Dolny lewy róg. Jeśli *nHeight* jest ujemna, mapa bitowa jest w górnym lewym rogu.

*nBPP*<br/>
Liczba bitów na piksel w mapie bitowej. Zwykle 4, 8, 16, 24 lub 32. Może być 1 dla map bitowych i masek monochromatyczny.

*flagiDW*<br/>
Określa, czy obiekt mapy bitowej ma kanał alfa. Może być kombinacją zero lub więcej z następujących wartości:

- *createAlphaChannel* Można go użyć tylko wtedy, gdy *NBPP* jest 32, a *eCompression* to BI_RGB. Jeśli zostanie określony, utworzony obraz ma wartość alfa (przezroczystość) dla każdego piksela, która jest przechowywana w czwartym bajcie każdego piksela (nieużywane w obrazie niebędącym alfa 32-bitowym). Ten kanał alfa jest automatycznie używany podczas wywoływania [funkcji CImage:: AlphaBlend](#alphablend).

> [!NOTE]
> W wywołaniach do [funkcji CImage::D RAW](#draw), obrazy z kanałem alfa są automatycznie alfa zmieszane do miejsca docelowego.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="createex"></a>Funkcji CImage:: CreateEx

Tworzy mapę bitową i dołącza ją do wcześniej skonstruowanego `CImage` obiektu. `CImage`

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
Wysokość `CImage` mapy bitowej w pikselach. Jeśli *nHeight* ma wartość dodatnią, mapa bitowa jest dolną KRAWĘDZIą DIB, a jej źródłem jest Dolny lewy róg. Jeśli *nHeight* jest ujemna, mapa bitowa jest w górnym lewym rogu.

*nBPP*<br/>
Liczba bitów na piksel w mapie bitowej. Zwykle 4, 8, 16, 24 lub 32. Może być 1 dla map bitowych i masek monochromatyczny.

*eCompression*<br/>
Określa typ kompresji skompresowanej mapy bitowej, która nie może być skompresowana (DIB góry). Może być jedną z następujących wartości:

- BI_RGB format jest nieskompresowany. Określenie tej wartości, gdy `CImage::CreateEx` wywołanie jest równoważne wywołaniu `CImage::Create`.

- BI_BITFIELDS format jest nieskompresowany, a tabela kolorów składa się z trzech masek kolorów DWORD, które określają odpowiednio czerwone, zielone i niebieskie składniki, każdego piksela. Jest to prawidłowe, gdy jest używany z 16-i 32-BPP mapy bitowe.

*pdwBitfields*<br/>
Używane tylko wtedy, gdy *eCompression* jest ustawiona na BI_BITFIELDS, w przeciwnym razie musi mieć wartość null. Wskaźnik do tablicy trzech masek bitowych DWORD, określający, które bity poszczególnych pikseli są używane odpowiednio dla składników czerwony, zielony i niebieskiego koloru. Aby uzyskać informacje na temat ograniczeń dotyczących pola bitów, zobacz [BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) w Windows SDK.

*flagiDW*<br/>
Określa, czy obiekt mapy bitowej ma kanał alfa. Może być kombinacją zero lub więcej z następujących wartości:

- *createAlphaChannel* Można go użyć tylko wtedy, gdy *NBPP* jest 32, a *eCompression* to BI_RGB. Jeśli zostanie określony, utworzony obraz ma wartość alfa (przezroczystość) dla każdego piksela, która jest przechowywana w czwartym bajcie każdego piksela (nieużywane w obrazie niebędącym alfa 32-bitowym). Ten kanał alfa jest automatycznie używany podczas wywoływania [funkcji CImage:: AlphaBlend](#alphablend).

   > [!NOTE]
   > W wywołaniach do [funkcji CImage::D RAW](#draw), obrazy z kanałem alfa są automatycznie alfa zmieszane do miejsca docelowego.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie. W przeciwnym razie FALSE.

### <a name="example"></a>Przykład

Poniższy przykład tworzy mapę bitową 100x100 pikseli przy użyciu 16 bitów do kodowania każdego piksela. W danym 16-bitowym pikselu usługa BITS 0-3 zakodować składnik czerwony, wartość BITS 4-7 Encode Green i BITS 8-11 w kolorze niebieskim. Pozostałe 4 bity nie są używane.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>Funkcji CImage::D Estroy

Odłącza mapę bitową od `CImage` obiektu i niszczy mapę bitową.

```
void Destroy() throw();
```

##  <a name="detach"></a>Funkcji CImage::D etach

Odłącza mapę bitową od `CImage` obiektu.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Dołączono dojście do mapy bitowej lub wartość NULL, jeśli nie jest dołączona żadna mapa bitowa.

##  <a name="draw"></a>Funkcji CImage::D RAW

Kopiuje mapę bitową z kontekstu urządzenia źródłowego do bieżącego kontekstu urządzenia.

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
Uchwyt do kontekstu urządzenia docelowego.

*xDest*<br/>
Współrzędna x (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędna y (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*nDestWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta docelowego.

*nDestHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta docelowego.

*xSrc*<br/>
Współrzędna x (w jednostkach logicznych) lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Współrzędna y (w jednostkach logicznych) lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta źródłowego.

*rectDest*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , identyfikując miejsce docelowe.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikujące źródło.

*pointDest*<br/>
Odwołanie do struktury [punktu](/previous-versions/dd162805\(v=vs.85\)) , która identyfikuje górny lewy róg prostokąta docelowego w jednostkach logicznych.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Draw`wykonuje tę samą operację co [StretchBlt](#stretchblt), chyba że obraz zawiera przezroczysty kolor lub kanał alfa. W takim przypadku program `Draw` wykonuje tę samą operację co [TransparentBlt](#transparentblt) lub [AlphaBlend](#alphablend) , zgodnie z wymaganiami.

W przypadku wersji `Draw` programu, które nie określają źródłowego prostokąta, domyślnym źródłem jest cały obraz źródłowy. W przypadku wersji programu `Draw` , która nie określa rozmiaru prostokąta docelowego, rozmiar obrazu źródłowego jest domyślny i nie występuje rozciąganie ani zmniejszanie.

##  <a name="getbits"></a>Funkcji CImage:: GetBits

Pobiera wskaźnik do rzeczywistych wartości bitowych danego piksela w mapie bitowej.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu mapy bitowej. Jeśli mapa bitowa jest dolną literą DIB, wskaźnik wskazuje blisko końca buforu. Jeśli mapa bitowa jest w górnej części DIB, wskaźnik wskazuje na pierwszy bajt buforu.

### <a name="remarks"></a>Uwagi

Przy użyciu tego wskaźnika wraz z wartością zwracaną przez [getgęstość](#getpitch)można lokalizować i zmieniać poszczególne piksele w obrazie.

> [!NOTE]
> Ta metoda obsługuje tylko mapy bitowe sekcji DIB; w związku z tym, uzyskujesz dostęp do `CImage` pikseli obiektu w taki sam sposób jak w przypadku pikseli sekcji DIB. Zwrócony wskaźnik wskazuje piksel w lokalizacji (0, 0).

##  <a name="getbpp"></a>Funkcji CImage:: GetBPP

Pobiera wartość bitów na piksel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba bitów na piksel.

### <a name="remarks"></a>Uwagi

Ta wartość określa liczbę bitów, które definiują poszczególne piksele i maksymalną liczbę kolorów w mapie bitowej.

Bity na piksel są zwykle 1, 4, 8, 16, 24 lub 32. Aby uzyskać więcej informacji [](/previous-versions//dd183376\(v=vs.85\)) na temat tej wartości, zobacz elementczłonkowskiBITMAPINFOHEADERw`biBitCount` Windows SDK.

##  <a name="getcolortable"></a>Funkcji CImage:: getcolors

Pobiera kolor czerwony, zielony, niebieski (RGB) z zakresu wpisów w palecie sekcji DIB.

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Indeks tabeli kolorów pierwszego wpisu do pobrania.

*nColors*<br/>
Liczba wpisów tabeli kolorów do pobrania.

*prgbColors*<br/>
Wskaźnik do tablicy struktur [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) w celu pobrania wpisów tabeli kolorów.

##  <a name="getdc"></a>Funkcji CImage:: GetDC —

Pobiera kontekst urządzenia, dla którego obraz został zaznaczony.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Dla każdego wywołania do `GetDC`, musisz mieć kolejne wywołanie do [ReleaseDC](#releasedc).

##  <a name="getexporterfilterstring"></a>Funkcji CImage:: GetExporterFilterString

Znajduje formaty obrazów dostępne do zapisywania obrazów.

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
Odwołanie do `CSimpleString` obiektu. Aby uzyskać więcej informacji, zobacz **uwagi** .

*aguidFileTypes*<br/>
Tablica identyfikatorów GUID, z każdym elementem odpowiadającym jednemu z typów plików w ciągu. W przykładzie w *pszAllFilesDescription* poniżej *aguidFileTypes*[0] jest GUID_NULL, a pozostałe wartości tablicy to formaty plików obrazów obsługiwane przez bieżący system operacyjny.

> [!NOTE]
> Aby zapoznać się z pełną listą stałych, zobacz **Format pliku obrazu — stałe** w Windows SDK.

*pszAllFilesDescription*<br/>
Jeśli ten parametr nie ma wartości NULL, ciąg filtru będzie miał jeden dodatkowy filtr na początku listy. Ten filtr będzie miał bieżącą wartość *pszAllFilesDescription* dla jego opisu i akceptuje pliki dowolnego rozszerzenia obsługiwanego przez dowolnego innego eksportera na liście.

Na przykład:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Zestaw flag bitowych określający, które typy plików mają zostać wykluczone z listy. Flagi dozwolone:

- `excludeGIF`= 0x01 wyklucza pliki GIF.

- `excludeBMP`= 0x02 wyklucza pliki BMP (Windows Bitmap).

- `excludeEMF`= 0x04 wyklucza pliki EMF (Enhanced Metafile).

- `excludeWMF`= 0x08 wyklucza pliki WMF (Windows Metafile).

- `excludeJPEG`= 0x10 wyklucza pliki JPEG.

- `excludePNG`= 0x20 wyklucza pliki PNG.

- `excludeTIFF`= 0x40 wyklucza pliki TIFF.

- `excludeIcon`= 0x80 wyklucza pliki ICO (ikony systemu Windows).

- `excludeOther`= 0x80000000 wyklucza wszystkie inne typy plików, których nie wymieniono powyżej.

- `excludeDefaultLoad`= 0 do załadowania, domyślnie są uwzględniane wszystkie typy plików

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`W przypadku zapisywania te pliki są domyślnie wykluczone, ponieważ zazwyczaj mają specjalne wymagania.

*chSeparator*<br/>
Separator używany między formatami obrazu. Aby uzyskać więcej informacji, zobacz **uwagi** .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Można przekazać otrzymany ciąg formatu do obiektu MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) , aby udostępnić rozszerzenia plików dla dostępnych formatów obrazu w oknie dialogowym Zapisz jako.

Parametr *strExporter* ma format:

plik description0&#124;\*. ext0&#124;&#124;filedescription1\*. EXT1&#124;... Opis pliku *n*&#124;\*. ext *n*&#124;&#124;

gdzie "&#124;" jest znakiem separatora określonym `chSeparator`przez. Przykład:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Użyj domyślnego separatora "&#124;", Jeśli przekażesz ten ciąg do obiektu `CFileDialog` MFC. Użyj separatora wartości null ' \ 0 ', Jeśli przekażesz ten ciąg do okna dialogowego typowe zapisywanie plików.

##  <a name="getheight"></a>Funkcji CImage:: GetHeight

Pobiera wysokość obrazu (w pikselach).

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość obrazu w pikselach.

##  <a name="getimporterfilterstring"></a>Funkcji CImage:: GetImporterFilterString

Znajduje formaty obrazów dostępne do ładowania obrazów.

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
Odwołanie do `CSimpleString` obiektu. Aby uzyskać więcej informacji, zobacz **uwagi** .

*aguidFileTypes*<br/>
Tablica identyfikatorów GUID, z każdym elementem odpowiadającym jednemu z typów plików w ciągu. W przykładzie w *pszAllFilesDescription* poniżej *aguidFileTypes*[0] jest GUID_NULL z pozostałymi wartościami tablicy są formaty plików obrazów obsługiwane przez bieżący system operacyjny.

> [!NOTE]
> Aby zapoznać się z pełną listą stałych, zobacz **Format pliku obrazu — stałe** w Windows SDK.

*pszAllFilesDescription*<br/>
Jeśli ten parametr nie ma wartości NULL, ciąg filtru będzie miał jeden dodatkowy filtr na początku listy. Ten filtr będzie miał bieżącą wartość *pszAllFilesDescription* dla jego opisu i akceptuje pliki dowolnego rozszerzenia obsługiwanego przez dowolnego innego eksportera na liście.

Przykład:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Zestaw flag bitowych określający, które typy plików mają zostać wykluczone z listy. Flagi dozwolone:

- `excludeGIF`= 0x01 wyklucza pliki GIF.

- `excludeBMP`= 0x02 wyklucza pliki BMP (Windows Bitmap).

- `excludeEMF`= 0x04 wyklucza pliki EMF (Enhanced Metafile).

- `excludeWMF`= 0x08 wyklucza pliki WMF (Windows Metafile).

- `excludeJPEG`= 0x10 wyklucza pliki JPEG.

- `excludePNG`= 0x20 wyklucza pliki PNG.

- `excludeTIFF`= 0x40 wyklucza pliki TIFF.

- `excludeIcon`= 0x80 wyklucza pliki ICO (ikony systemu Windows).

- `excludeOther`= 0x80000000 wyklucza wszystkie inne typy plików, których nie wymieniono powyżej.

- `excludeDefaultLoad`= 0 do załadowania, domyślnie są uwzględniane wszystkie typy plików

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`W przypadku zapisywania te pliki są domyślnie wykluczone, ponieważ zazwyczaj mają specjalne wymagania.

*chSeparator*<br/>
Separator używany między formatami obrazu. Aby uzyskać więcej informacji, zobacz **uwagi** .

### <a name="remarks"></a>Uwagi

Można przekazać otrzymany ciąg formatu do obiektu MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) , aby uwidocznić rozszerzenia plików dostępne formaty obrazu w oknie dialogowym **otwieranie pliku** .

Parametr *strImporter* ma format:

plik description0&#124;\*. ext0&#124;&#124;filedescription1\*. EXT1&#124;... Opis pliku *n*&#124;\*. ext *n*&#124;&#124;

gdzie "&#124;" jest znakiem separatora określonym przez *chSeparator*. Na przykład:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Użyj domyślnego separatora "&#124;", Jeśli przekażesz ten ciąg do obiektu `CFileDialog` MFC. Użyj separatora o wartości null ' \ 0 ', Jeśli przekażesz ten ciąg do okna dialogowego wspólne **otwieranie pliku** .

##  <a name="getmaxcolortableentries"></a>Funkcji CImage:: GetMaxColorTableEntries

Pobiera maksymalną liczbę wpisów w tabeli kolorów.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów w tabeli kolorów.

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje tylko mapy bitowe sekcji DIB.

##  <a name="getpitch"></a>Funkcji CImage:: getgęstość

Pobiera wysokość obrazu.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość obrazu. Jeśli wartość zwracana jest ujemna, mapa bitowa jest dolną krawędzią DIB, a jej źródłem jest Dolny lewy róg. Jeśli wartość zwracana jest dodatnia, mapa bitowa jest w górnym lewym rogu.

### <a name="remarks"></a>Uwagi

Gęstość to odległość, w bajtach, między dwoma adresami pamięci reprezentującymi początek jednej linii mapy bitowej i początkiem kolejnej linii bitowej. Ponieważ gęstość jest mierzona w bajtach, gęstość obrazu pomaga określić format pikseli. Gęstość może również zawierać dodatkową pamięć zarezerwowaną dla mapy bitowej.

Użyj `GetPitch` with [GetBits](#getbits) , aby znaleźć poszczególne piksele obrazu.

> [!NOTE]
> Ta metoda obsługuje tylko mapy bitowe sekcji DIB.

##  <a name="getpixel"></a>Funkcji CImage:: GetPixel

Pobiera kolor piksela w lokalizacji określonej przez wartości *x* i *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Współrzędna x piksela.

*y*<br/>
Współrzędna y piksela.

### <a name="return-value"></a>Wartość zwracana

Czerwony, zielony, niebieski (RGB) wartość piksela. Jeśli piksel znajduje się poza bieżącym regionem przycinania, wartość zwracana to CLR_INVALID.

##  <a name="getpixeladdress"></a>Funkcji CImage:: GetPixelAddress

Pobiera dokładny adres piksela.

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Współrzędna x piksela.

*y*<br/>
Współrzędna y piksela.

### <a name="remarks"></a>Uwagi

Adres jest określany na podstawie współrzędnych pikseli, szerokości mapy bitowej i bitów na piksel.

W przypadku formatów, które mają mniej niż 8 bitów na piksel, ta metoda zwraca adres bajtu zawierającego piksel. Na przykład jeśli format obrazu ma 4 bity na piksel, `GetPixelAddress` zwraca adres pierwszego piksela w bajtie i należy obliczyć na 2 piksele na bajt.

> [!NOTE]
> Ta metoda obsługuje tylko mapy bitowe sekcji DIB.

##  <a name="gettransparentcolor"></a>Funkcji CImage:: GetTransparentColor

Pobiera indeksowaną lokalizację przezroczystego koloru w palecie kolorów.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Indeks przezroczystego koloru.

##  <a name="getwidth"></a>Funkcji CImage:: getwidth

Pobiera szerokość obrazu (w pikselach).

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Szerokość mapy bitowej w pikselach.

##  <a name="isdibsection"></a>Funkcji CImage:: IsDIBSection

Określa, czy załączona Mapa bitowa jest sekcją DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli załączona Mapa bitowa jest sekcją DIB. W przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli mapa bitowa nie jest sekcją DIB, nie można użyć następujących `CImage` metod, które obsługują tylko mapy bitowe sekcji DIB:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>Funkcji CImage:: IsIndexed

Określa, czy piksele mapy bitowej są mapowane na paletę kolorów.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli indeksowane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość TRUE tylko wtedy, gdy mapa bitowa ma 8-bitową (256 kolorów) lub mniejszą.

> [!NOTE]
> Ta metoda obsługuje tylko mapy bitowe sekcji DIB.

##  <a name="isnull"></a>Funkcji CImage:: IsNull

Określa, czy mapa bitowa jest aktualnie załadowana.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość PRAWDA, jeśli mapa bitowa nie jest aktualnie załadowana; w przeciwnym razie FALSE.

##  <a name="istransparencysupported"></a>Funkcji CImage:: IsTransparencySupported

Wskazuje, czy aplikacja obsługuje przezroczyste mapy bitowe.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli bieżąca platforma obsługuje przezroczystość. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli wartość zwracana jest różna od zera, a przezroczystość jest obsługiwana, wywołanie [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)lub [Draw](#draw) będzie obsługiwać przezroczyste kolory.

##  <a name="load"></a>Funkcji CImage:: Load

Ładuje obraz.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pszFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku obrazu do załadowania.

*pStream*<br/>
Wskaźnik do strumienia zawierającego nazwę pliku obrazu do załadowania.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ładuje obraz określony przez *pszFileName* lub *pStream*.

Prawidłowymi typami obrazów są BMP, GIF, JPEG, PNG i TIFF.

##  <a name="loadfromresource"></a>Funkcji CImage:: LoadFromResource

Ładuje obraz z zasobu mapy BITOWEJ.

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
Dojście do wystąpienia modułu zawierającego obraz do załadowania.

*pszResourceName*<br/>
Wskaźnik do ciągu zawierającego nazwę zasobu zawierającego obraz do załadowania.

*nIDResource*<br/>
Identyfikator zasobu do załadowania.

### <a name="remarks"></a>Uwagi

Zasób musi być typu map bitowych.

##  <a name="maskblt"></a>Funkcji CImage:: MaskBlt

Łączy dane koloru dla źródłowej i docelowej mapy bitowej przy użyciu określonej maski i operacji rastrowej.

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
Uchwyt do modułu, którego plik wykonywalny zawiera zasób.

*xDest*<br/>
Współrzędna x (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędna y (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*nDestWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta docelowego i źródłowa Mapa bitowa.

*nDestHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta docelowego i źródłowa Mapa bitowa.

*xSrc*<br/>
Logiczna Współrzędna x lewego górnego rogu źródłowej mapy bitowej.

*ySrc*<br/>
Logiczna Współrzędna y lewego górnego rogu źródłowej mapy bitowej.

*hbmMask*<br/>
Obsługuj mapę bitowej mapy obrazkowej w połączeniu z mapą bitową koloru w kontekście urządzenia źródłowego.

*xMask*<br/>
Przesunięcie w poziomie pikseli dla mapy bitowej maski określonej przez parametr *hbmMask* .

*yMask*<br/>
Przesunięcie w pionie dla mapy bitowej określonej przez parametr *hbmMask* .

*dwROP*<br/>
Określa, że zarówno kod operacji w tle, jak i tło, są używane przez metodę do kontrolowania kombinacji danych źródłowych i docelowych. Kod operacji rastrowej w tle jest przechowywany w jednokierunkowym bajcie wyrazu o tej wartości. kod operacji rastrowych na pierwszym planie jest przechowywany w niskiej kolejności wyrazów tej wartości. wyraz o niskiej kolejności jest ignorowany i powinien mieć wartość zero. Aby zapoznać się z omówieniem pierwszego planu i tła w kontekście tej metody, zobacz `MaskBlt` w Windows SDK. Aby uzyskać listę typowych kodów operacji rastrowych, zobacz `BitBlt` w Windows SDK.

*rectDest*<br/>
Odwołanie do `RECT` struktury, identyfikujące miejsce docelowe.

*pointSrc*<br/>
`POINT` Struktura wskazująca lewy górny róg prostokąta źródłowego.

*pointMask*<br/>
`POINT` Struktura wskazująca górny lewy róg mapy bitowej maski.

*pointDest*<br/>
Odwołanie do `POINT` struktury, która identyfikuje górny lewy róg prostokąta docelowego w jednostkach logicznych.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda ma zastosowanie tylko do systemu Windows NT, wersji 4,0 i nowszych.

##  <a name="operator_hbitmap"></a>Funkcji CImage:: operator HBITMAP

Użyj tego operatora, aby uzyskać dojście `CImage` do dołączonego interfejsu GDI systemu Windows. Ten operator jest operatorem rzutowania, który obsługuje bezpośrednie użycie obiektu HBITMAP.

##  <a name="plgblt"></a>  CImage::PlgBlt

Wykonuje transfer bloku bitowego z prostokąta w kontekście urządzenia źródłowego do pliku równoległobok w kontekście urządzenia docelowego.

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
Uchwyt do kontekstu urządzenia docelowego.

*pPoints*<br/>
Wskaźnik do tablicy trzech punktów w przestrzeni logicznej, który identyfikuje trzy rogi równoległobok docelowego. Lewy górny róg prostokąta źródłowego jest mapowany do pierwszego punktu w tej tablicy, prawego górnego rogu do drugiego punktu w tej tablicy oraz dolnego lewego rogu do trzeciego punktu. Prawy dolny róg prostokąta źródłowego jest mapowany do niejawnego czwartego punktu w równoległobok.

*hbmMask*<br/>
Uchwyt do opcjonalnej mapy bitowej monochromatycznej, która jest używana do maskowania kolorów prostokąta źródłowego.

*xSrc*<br/>
Współrzędna x (w jednostkach logicznych) lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Współrzędna y (w jednostkach logicznych) lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta źródłowego.

*xMask*<br/>
Współrzędna x górnego lewego rogu mapy bitowej monochromatycznej.

*yMask*<br/>
Współrzędna y lewego górnego rogu mapy bitowej monochromatyczny.

*rectSrc*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) określające współrzędne prostokąta źródłowego.

*pointMask*<br/>
Struktura [punktu](/previous-versions/dd162805\(v=vs.85\)) wskazująca górny lewy róg mapy bitowej maski.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *hbmMask* identyfikuje poprawną mapę bitową monochromatyczny, `PlgBit` używa tej mapy bitowej do maskowania bitów danych koloru z prostokąta źródłowego.

Ta metoda ma zastosowanie tylko do systemu Windows NT, wersji 4,0 i nowszych. Aby uzyskać szczegółowe informacje, zobacz [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) w Windows SDK.

##  <a name="releasedc"></a>Funkcji CImage:: ReleaseDC

Zwalnia kontekst urządzenia.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Uwagi

Ponieważ tylko jedną mapę bitową można wybrać w kontekście urządzenia naraz, należy wywołać `ReleaseDC` dla każdego wywołania do [GetDC —](#getdc).

##  <a name="releasegdiplus"></a>Funkcji CImage:: ReleaseGDIPlus

Zwalnia zasoby używane przez GDI+.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda musi zostać wywołana, aby zwolnić zasoby przydzielone przez `CImage` obiekt globalny. Zobacz [funkcji CImage:: funkcji CImage](#cimage).

##  <a name="save"></a>Funkcji CImage:: Save

Zapisuje obraz do określonego strumienia lub pliku na dysku.

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
Wskaźnik do obiektu COM IStream zawierającego dane obrazu pliku.

*pszFileName*<br/>
Wskaźnik do nazwy pliku obrazu.

*guidFileType*<br/>
Typ pliku, w którym ma zostać zapisany obraz. Może to być jeden z następujących elementów:

- `ImageFormatBMP`Obraz nieskompresowanej mapy bitowej.

- `ImageFormatPNG`Skompresowany obraz Portable Network Graphics (PNG).

- `ImageFormatJPEG`Skompresowany obraz JPEG.

- `ImageFormatGIF`Skompresowany obraz GIF.

> [!NOTE]
> Aby zapoznać się z pełną listą stałych, zobacz **Format pliku obrazu — stałe** w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zapisać obraz przy użyciu określonej nazwy i typu. Jeśli parametr *guidFileType* nie jest uwzględniony, rozszerzenie pliku nazwy pliku zostanie użyte do określenia formatu obrazu. Jeśli nie podano rozszerzenia, obraz zostanie zapisany w formacie BMP.

##  <a name="setcolortable"></a>Funkcji CImage:: setcolors

Ustawia kolor czerwony, zielony, niebieski (RGB) dla zakresu wpisów w palecie sekcji DIB.

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Indeks tabeli kolorów pierwszego wpisu do ustawienia.

*nColors*<br/>
Liczba wpisów tabeli kolorów do ustawienia.

*prgbColors*<br/>
Wskaźnik do tablicy struktur [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) w celu ustawienia wpisów tabeli kolorów.

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje tylko mapy bitowe sekcji DIB.

##  <a name="setpixel"></a>Funkcji CImage:: SetPixel

Ustawia kolor piksela w danej lokalizacji mapy bitowej.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Położenie w poziomie pikseli do ustawienia.

*y*<br/>
Położenie w pionie pikseli do ustawienia.

*Kolor*<br/>
Kolor, dla którego ustawisz piksel.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli współrzędne pikseli znajdują się poza wybranym regionem przycinania.

##  <a name="setpixelindexed"></a>Funkcji CImage:: SetPixelIndexed

Ustawia kolor piksela na kolor znajdujący się w *IIndex* w palecie kolorów.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Położenie w poziomie pikseli do ustawienia.

*y*<br/>
Położenie w pionie pikseli do ustawienia.

*iIndex*<br/>
Indeks koloru w palecie kolorów.

##  <a name="setpixelrgb"></a>Funkcji CImage:: SetPixelRGB

Ustawia piksel w miejscach określonych przez wartości *x* i *y* na kolory wskazane przez *r*, *g*i *b*, w czerwonym, zielonym, niebieskim (RGB) obrazie.

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
Położenie w poziomie pikseli do ustawienia.

*y*<br/>
Położenie w pionie pikseli do ustawienia.

*r*<br/>
Intensywność koloru czerwonego.

*g*<br/>
Intensywność koloru zielonego.

*b*<br/>
Intensywność niebieskiego koloru.

### <a name="remarks"></a>Uwagi

Parametry Red, Green i Blue są reprezentowane przez liczbę z zakresu od 0 do 255. Jeśli ustawisz wszystkie trzy parametry na zero, połączony kolor uzyskany jest czarny. Jeśli ustawisz wszystkie trzy parametry na 255, połączony kolor uzyskany jest biały.

##  <a name="settransparentcolor"></a>Funkcji CImage:: SetTransparentColor

Ustawia kolor w danej indeksowanej lokalizacji jako przezroczysty.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parametry

*iTransparentColor*<br/>
Indeks w palecie kolorów koloru, który ma zostać ustawiony jako przezroczysty. Jeśli-1, żaden kolor nie jest ustawiony jako przezroczysty.

### <a name="return-value"></a>Wartość zwracana

Indeks koloru poprzednio ustawiony jako przezroczysty.

##  <a name="stretchblt"></a>  CImage::StretchBlt

Kopiuje mapę bitową z kontekstu urządzenia źródłowego do tego bieżącego kontekstu urządzenia.

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
Uchwyt do kontekstu urządzenia docelowego.

*xDest*<br/>
Współrzędna x (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędna y (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*nDestWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta docelowego.

*nDestHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta docelowego.

*dwROP*<br/>
Operacja rastrowa, która ma zostać wykonana. Kody operacji rastrowych definiują dokładnie sposób łączenia bitów źródła, miejsca docelowego i wzorca (zgodnie z definicją aktualnie wybranego pędzla) w celu utworzenia miejsca docelowego. Zobacz [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) w Windows SDK, aby zapoznać się z listą innych kodów operacji rastrowych i ich opisów.

*rectDest*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , identyfikując miejsce docelowe.

*xSrc*<br/>
Współrzędna x (w jednostkach logicznych) lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Współrzędna y (w jednostkach logicznych) lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta źródłowego.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikujące źródło.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) w Windows SDK.

##  <a name="transparentblt"></a>Funkcji CImage:: TransparentBlt

Kopiuje mapę bitową z kontekstu urządzenia źródłowego do tego bieżącego kontekstu urządzenia.

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
Uchwyt do kontekstu urządzenia docelowego.

*xDest*<br/>
Współrzędna x (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*yDest*<br/>
Współrzędna y (w jednostkach logicznych) lewego górnego rogu prostokąta docelowego.

*nDestWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta docelowego.

*nDestHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta docelowego.

*crTransparent*<br/>
Kolor w źródłowej mapie bitowej, który ma być traktowany jako przezroczysty. Domyślnie CLR_INVALID, wskazujący, że kolor jest obecnie ustawiony jako przezroczysty kolor obrazu.

*rectDest*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , identyfikując miejsce docelowe.

*xSrc*<br/>
Współrzędna x (w jednostkach logicznych) lewego górnego rogu prostokąta źródłowego.

*ySrc*<br/>
Współrzędna y (w jednostkach logicznych) lewego górnego rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość (w jednostkach logicznych) prostokąta źródłowego.

*nSrcHeight*<br/>
Wysokość (w jednostkach logicznych) prostokąta źródłowego.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikujące źródło.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`TransparentBlt`jest obsługiwana dla źródłowych map bitowych o wartości 4 bitów na piksel i 8 bitów na piksel. Użyj [funkcji CImage:: AlphaBlend](#alphablend) , aby określić mapy bitowe o 32 bitów na piksel z przezroczystością.

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

## <a name="see-also"></a>Zobacz także

[Przykład MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Przykład SimpleImage](../../overview/visual-cpp-samples.md)<br/>
[Mapy bitowe niezależne od urządzenia](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)<br/>
[Mapy bitowe niezależne od urządzenia](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
