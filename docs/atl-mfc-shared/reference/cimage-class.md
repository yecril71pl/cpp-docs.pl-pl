---
title: Klasa CImage
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
ms.openlocfilehash: a6d20e1bf12f5fe7d1e9b41d88b088ca9fad35ed
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747183"
---
# <a name="cimage-class"></a>Klasa CImage

`CImage`zapewnia ulepszoną obsługę bitmap, w tym możliwość ładowania i zapisywania obrazów w formatach JPEG, GIF, BMP i Portable Network Graphics (PNG).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

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
|[CImage::AlphaBlend](#alphablend)|Wyświetla mapy bitowe, które mają przezroczyste lub półprzezroczyste piksele.|
|[CImage::Dołącz](#attach)|Dołącza HBITMAP do `CImage` obiektu. Może być używany z mapami bitowymi sekcji innych niż DIB lub mapami bitowymi sekcji DIB.|
|[CImage::BitBlt](#bitblt)|Kopiuje mapę bitową z kontekstu urządzenia źródłowego do bieżącego kontekstu urządzenia.|
|[CImage::Tworzenie](#create)|Tworzy mapę bitową sekcji DIB i dołącza `CImage` ją do wcześniej skonstruowanego obiektu.|
|[CImage::CreateEx](#createex)|Tworzy mapę bitową sekcji DIB (z dodatkowymi parametrami) `CImage` i dołącza ją do wcześniej skonstruowanego obiektu.|
|[CImage::Destroja](#destroy)|Odłącza mapę bitową `CImage` od obiektu i niszczy mapę bitową.|
|[CImage::Detach](#detach)|Odłącza mapę bitową `CImage` od obiektu.|
|[CImage::Draw](#draw)|Kopiuje mapę bitową z prostokąta źródłowego do prostokąta docelowego. `Draw`rozciąga lub kompresuje mapę bitową, aby dopasować ją do wymiarów prostokąta docelowego, jeśli to konieczne, i obsługuje mieszanie alfa i przezroczyste kolory.|
|[CImage::GetBits](#getbits)|Pobiera wskaźnik do rzeczywistych wartości pikseli mapy bitowej.|
|[CImage::GetBPP](#getbpp)|Pobiera bity na piksel.|
|[CImage::GetColorTable](#getcolortable)|Pobiera wartości kolorów czerwony, zielony, niebieski (RGB) z zakresu wpisów w tabeli kolorów.|
|[CImage::GetDC](#getdc)|Pobiera kontekst urządzenia, do którego jest zaznaczona bieżąca mapa bitowa.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Wyszukuje dostępne formaty obrazów i ich opisy.|
|[CImage::GetHeight](#getheight)|Pobiera wysokość bieżącego obrazu w pikselach.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Wyszukuje dostępne formaty obrazów i ich opisy.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Pobiera maksymalną liczbę wpisów w tabeli kolorów.|
|[CImage::GetPitch](#getpitch)|Pobiera wysokość bieżącego obrazu w bajtach.|
|[CImage::GetPixel](#getpixel)|Pobiera kolor piksela określonego przez *x* i *y*.|
|[CImage::GetPixelAddress](#getpixeladdress)|Pobiera adres danego piksela.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Pobiera położenie koloru przezroczystego w tabeli kolorów.|
|[CImage::GetWidth](#getwidth)|Pobiera szerokość bieżącego obrazu w pikselach.|
|[CImage::IsDIBSekcja](#isdibsection)|Określa, czy załączona mapa bitowa jest sekcją DIB.|
|[CImage::IsIndexed](#isindexed)|Wskazuje, że kolory mapy bitowej są mapowane na paletę indeksowanych.|
|[CImage::Isnull](#isnull)|Wskazuje, czy źródłowa mapa bitowa jest aktualnie załadowana.|
|[CImage::IsTransparencySupported](#istransparencysupported)|Wskazuje, czy aplikacja obsługuje przezroczyste mapy bitowe.|
|[CImage::Obciążenie](#load)|Ładuje obraz z określonego pliku.|
|[CImage::LoadFromResource](#loadfromresource)|Ładuje obraz z określonego zasobu.|
|[CImage::MaskBlt](#maskblt)|Łączy dane kolorów dla źródłowych i docelowych map bitowych przy użyciu określonej maski i operacji rastrowej.|
|[CImage::PlgBlt](#plgblt)|Wykonuje transfer bloku bitowego z prostokąta w kontekście urządzenia źródłowego do równoległoboku w kontekście urządzenia docelowego.|
|[CImage::ReleaseDC](#releasedc)|Zwalnia kontekst urządzenia, który został pobrany z [CImage::GetDC](#getdc).|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Zwalnia zasoby używane przez GDI+. Musi być wywoływana do zwalniania zasobów utworzonych przez obiekt globalny. `CImage`|
|[CImage::Zapisz](#save)|Zapisuje obraz jako określony typ. `Save`nie można określić opcji obrazu.|
|[CImage::SetColorTable](#setcolortable)|Ustawia czerwone, zielone, niebieskie wartości kolorów RGB) w zakresie wpisów w tabeli kolorów sekcji DIB.|
|[CImage::SetPixel](#setpixel)|Ustawia piksel w określonych współrzędnych na określony kolor.|
|[CImage::SetPixelIndexed](#setpixelindexed)|Ustawia piksel w określonych współrzędnych na kolor w określonym indeksie palety.|
|[CImage::SetPixelRGB](#setpixelrgb)|Ustawia piksel na określone współrzędne na określoną wartość czerwony, zielony, niebieski (RGB).|
|[CImage::SetTransparentColor](#settransparentcolor)|Ustawia indeks koloru, który ma być traktowany jako przezroczysty. Tylko jeden kolor w palecie może być przezroczysty.|
|[CImage::Rozciągliwyblt](#stretchblt)|Kopiuje mapę bitową z prostokąta źródłowego do prostokąta docelowego, rozciągając lub kompresując mapę bitową, aby w razie potrzeby dopasować ją do wymiarów prostokąta docelowego.|
|[CImage::TransparentBlt](#transparentblt)|Kopiuje mapę bitową z przezroczystym kolorem z kontekstu urządzenia źródłowego do bieżącego kontekstu urządzenia.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CImage::operator HBITMAP](#operator_hbitmap)|Zwraca uchwyt systemu Windows `CImage` dołączony do obiektu.|

## <a name="remarks"></a>Uwagi

`CImage`pobiera mapy bitowe, które są sekcjami ddnu (DIB) niezależnymi od urządzenia lub nie; można jednak użyć [Create](#create) lub [CImage::Load](#load) tylko z sekcjami DIB. Do obiektu za pomocą funkcji [Dołącz](#attach)można `CImage` dołączyć mapę bitową sekcji `CImage` innych niż DIB, ale nie można użyć następujących metod, które obsługują tylko mapy bitowe sekcji DIB:

- [GetBits (GetBits)](#getbits)

- [Tabela GetColorTable](#getcolortable)

- [GetMaxColorTableEntries (Wyw.](#getmaxcolortableentries)

- [GetPitch ( GetPitch )](#getpitch)

- [Sukienka GetPixelAddress](#getpixeladdress)

- [IsIndexed ( IsIndexed )](#isindexed)

- [Tabela SetColorTable](#setcolortable)

Aby ustalić, czy załączona mapa bitowa jest sekcją DIB, zadzwoń do [isdibsection](#isdibsection).

> [!NOTE]
> W programie Visual Studio .NET 2003 ta klasa `CImage` przechowuje liczbę utworzonych obiektów. Za każdym razem, gdy liczba `GdiplusShutdown` przechodzi do 0, funkcja jest automatycznie wywoływana do zwalniania zasobów używanych przez GDI +. Gwarantuje to, `CImage` że wszystkie obiekty utworzone bezpośrednio lub pośrednio przez biblioteki `GdiplusShutdown` DLL `DllMain`są zawsze niszczone prawidłowo i nie jest wywoływane z .

> [!NOTE]
> Nie `CImage` zaleca się używania obiektów globalnych w biblioteki DLL. Jeśli chcesz użyć obiektu `CImage` globalnego w dll, wywołać [CImage::ReleaseGDIPlus](#releasegdiplus) jawnie zwolnić zasoby używane przez GDI +.

`CImage`nie można wybrać do nowej [CDC](../../mfc/reference/cdc-class.md). `CImage`tworzy własną hdc dla obrazu. Ponieważ HBITMAP można wybrać tylko w jednym HDC naraz, HBITMAP skojarzony z nim `CImage` nie można wybrać w innym HDC. Jeśli potrzebujesz CDC, pobierz HDC z `CImage` i dać go do [CDC::FromHandle](../../mfc/reference/cdc-class.md#fromhandle).

## <a name="example"></a>Przykład

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Podczas korzystania `CImage` w projekcie MFC, należy pamiętać, które funkcje członkowskie w projekcie oczekiwać wskaźnik do [obiektu CBitmap.](../../mfc/reference/cbitmap-class.md) Jeśli chcesz używać `CImage` z taką funkcją, taką jak [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), użyj [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), przekaż ją `CImage` za pomocą HBITMAP i użyj zwróconego `CBitmap*`.

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

Through `CImage`, masz dostęp do rzeczywistych bitów sekcji DIB. `CImage` Obiektu można używać w dowolnym miejscu, w której wcześniej była używana sekcja Win32 HBITMAP lub DIB.

Można użyć `CImage` z MFC lub ATL.

> [!NOTE]
> Podczas tworzenia projektu `CImage`przy użyciu `CString` programu , należy zdefiniować przed dołączeniem *atlimage.h*. Jeśli projekt używa ATL bez MFC, dołącz *atlstr.h* przed dołączeniem *atlimage.h*. Jeśli projekt używa MFC (lub jeśli jest to projekt ATL z obsługą MFC), dołącz *afxstr.h* przed dołączeniem *atlimage.h*.<br/>
> <br/>
> Podobnie, należy dołączyć *atlimage.h* przed dołączeniem *atlimpl.cpp*. Aby to łatwo osiągnąć, należy uwzględnić *plik atlimage.h* w *pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlimage.h

## <a name="cimagealphablend"></a><a name="alphablend"></a>CImage::AlphaBlend

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

*hDestDC (hDestDC)*<br/>
Dojmij do kontekstu urządzenia docelowego.

*xDest (xDest)*<br/>
Współrzędna x w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*yDest (właśc.*<br/>
Współrzędna y w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*bSrcAlpha*<br/>
Wartość przezroczystości alfa, która ma być używana na całej źródłowej mapie bitowej. Domyślna wartość 0xff (255) zakłada, że obraz jest nieprzezroczysty i że chcesz używać tylko wartości alfa na piksel.

*bBlendOp*<br/>
Funkcja mieszania alfa dla źródłowych i docelowych map bitowych, globalna wartość alfa, która ma być zastosowana do całej źródłowej mapy bitowej, oraz formatowanie informacji dla źródłowej mapy bitowej. Funkcje mieszania źródła i miejsca docelowego są obecnie ograniczone do AC_SRC_OVER.

*punktDest*<br/>
Odwołanie do struktury [POINT,](/windows/win32/api/windef/ns-windef-point) która identyfikuje lewy górny róg prostokąta docelowego w jednostkach logicznych.

*nDestWidth (nDestWidth)*<br/>
Szerokość w jednostkach logicznych prostokąta docelowego.

*nDestHeight (nDestHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta docelowego.

*xSrc (ks.*<br/>
Logiczna współrzędna x w lewym górnym rogu prostokąta źródłowego.

*ySrc ( ySrc )*<br/>
Logiczna współrzędna y w lewym górnym rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych prostokąta źródłowego.

*nSrcHeight (nSrcHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta źródłowego.

*reectDest*<br/>
Odwołanie do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) identyfikując miejsce docelowe.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikując źródło.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapy bitowe z mieszaniem alfa obsługują mieszanie kolorów na piksel.

Gdy *bBlendOp* jest ustawiona na domyślną wartość AC_SRC_OVER, źródłowa mapa bitowa jest umieszczana nad docelową mapą bitową na podstawie wartości alfa pikseli źródłowych.

## <a name="cimageattach"></a><a name="attach"></a>CImage::Dołącz

Dołącza *hBitmap* do `CImage` obiektu.

```cpp
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*hBitmapa*<br/>
Dojście do HBITMAP.

*eOrientacja*<br/>
Określa orientację mapy bitowej. Może być jedną z następujących czynności:

- DIBOR_DEFAULT Orientacja mapy bitowej jest określana przez system operacyjny.

- DIBOR_BOTTOMUP Wiersze mapy bitowej są w odwrotnej kolejności. Powoduje to [CImage::GetBits](#getbits) do zwrócenia wskaźnika na końcu buforu mapy bitowej i [CImage::GetPitch](#getpitch) do zwrócenia liczby ujemnej.

- DIBOR_TOPDOWN Wiersze mapy bitowej są w kolejności od góry do dołu. Powoduje to [CImage::GetBits](#getbits) do zwrócenia wskaźnika do pierwszego bajtu buforu mapy bitowej i [CImage::GetPitch](#getpitch) do zwrócenia liczby dodatniej.

### <a name="remarks"></a>Uwagi

Mapa bitowa może być bitmapą sekcji niezwiązanych z DIB lub bitmapą sekcji DIB. Zobacz [IsDIBSection](#isdibsection) listę metod, których można używać tylko z mapami bitowymi sekcji DIB.

## <a name="cimagebitblt"></a><a name="bitblt"></a>CImage::BitBlt

Kopiuje mapę bitową z kontekstu urządzenia źródłowego do bieżącego kontekstu urządzenia.

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

*hDestDC (hDestDC)*<br/>
Docelowy HDC.

*xDest (xDest)*<br/>
Logiczna współrzędna x lewego górnego rogu prostokąta docelowego.

*yDest (właśc.*<br/>
Logiczna współrzędna y lewego górnego rogu prostokąta docelowego.

*dwROP ( dwROP )*<br/>
Operacja rastrowa do wykonania. Kody operacji rastrowych definiują dokładnie sposób łączenia bitów źródła, miejsca docelowego i wzorca (zdefiniowanego przez aktualnie zaznaczony pędzel) w celu utworzenia miejsca docelowego. Zobacz [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) w zestawie Windows SDK, aby uzyskać listę innych kodów operacji rastrowych i ich opisów.

*punktDest*<br/>
Struktura [POINT](/windows/win32/api/windef/ns-windef-point) wskazująca lewy górny róg prostokąta docelowego.

*nDestWidth (nDestWidth)*<br/>
Szerokość w jednostkach logicznych prostokąta docelowego.

*nDestHeight (nDestHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta docelowego.

*xSrc (ks.*<br/>
Logiczna współrzędna x w lewym górnym rogu prostokąta źródłowego.

*ySrc ( ySrc )*<br/>
Logiczna współrzędna y w lewym górnym rogu prostokąta źródłowego.

*reectDest*<br/>
Struktura [RECT](/windows/win32/api/windef/ns-windef-rect) wskazująca prostokąt docelowy.

*pktSrc*<br/>
Struktura `POINT` wskazująca lewy górny róg prostokąta źródłowego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) w windows SDK.

## <a name="cimagecimage"></a><a name="cimage"></a>CImage::CImage

Konstruuje `CImage` obiekt.

```
CImage() throw();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu [wywołaj create,](#create) [load](#load), [loadfromresource](#loadfromresource)lub [Dołącz,](#attach) aby dołączyć mapę bitową do obiektu.

**Uwaga** W programie Visual Studio ta klasa przechowuje liczbę utworzonych `CImage` obiektów. Za każdym razem, gdy liczba `GdiplusShutdown` przechodzi do 0, funkcja jest automatycznie wywoływana do zwalniania zasobów używanych przez GDI +. Gwarantuje to, `CImage` że wszystkie obiekty utworzone bezpośrednio lub pośrednio przez biblioteki `GdiplusShutdown` DLL są zawsze niszczone poprawnie i że nie jest wywoływana z DllMain.

Nie `CImage` zaleca się używania obiektów globalnych w biblioteki DLL. Jeśli chcesz użyć obiektu `CImage` globalnego w dll, wywołać [CImage::ReleaseGDIPlus](#releasegdiplus) jawnie zwolnić zasoby używane przez GDI +.

## <a name="cimagecreate"></a><a name="create"></a>CImage::Tworzenie

Tworzy `CImage` mapę bitową i dołącza ją `CImage` do wcześniej skonstruowanego obiektu.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*nWidth (ww.*<br/>
Szerokość mapy `CImage` bitowej w pikselach.

*nFeksja*<br/>
Wysokość mapy `CImage` bitowej w pikselach. Jeśli *nHeight* jest dodatni, mapa bitowa jest dydajnie do góry DIB, a jej początek jest lewym dolnym rogu. Jeśli *nHeight* jest ujemny, mapa bitowa jest dib z góry na dół, a jej początek jest lewym górnym rogu.

*nBPP*<br/>
Liczba bitów na piksel w mapie bitowej. Zwykle 4, 8, 16, 24 lub 32. Może być 1 dla monochromatyczne mapy bitowe lub maski.

*Dwflags*<br/>
Określa, czy obiekt mapy bitowej ma kanał alfa. Może być kombinacją zero lub więcej z następujących wartości:

- *tworzenieAlfaChannel* Może być używany tylko wtedy, gdy *nBPP* wynosi 32, a *eCompression* jest BI_RGB. Jeśli zostanie określony, utworzony obraz ma wartość alfa (przezroczystość) dla każdego piksela, przechowywaną w 4 bajtowym każdym pikselu (nieużywane w obrazie 32-bitowym innym niż alfa). Ten kanał alfa jest automatycznie używany podczas wywoływania [CImage::AlphaBlend](#alphablend).

> [!NOTE]
> W wywołaniach [do CImage::Draw](#draw)obrazy z kanałem alfa są automatycznie mieszane alfa do miejsca docelowego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="cimagecreateex"></a><a name="createex"></a>CImage::CreateEx

Tworzy `CImage` mapę bitową i dołącza ją `CImage` do wcześniej skonstruowanego obiektu.

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

*nWidth (ww.*<br/>
Szerokość mapy `CImage` bitowej w pikselach.

*nFeksja*<br/>
Wysokość mapy `CImage` bitowej w pikselach. Jeśli *nHeight* jest dodatni, mapa bitowa jest dydajnie do góry DIB, a jej początek jest lewym dolnym rogu. Jeśli *nHeight* jest ujemny, mapa bitowa jest dib z góry na dół, a jej początek jest lewym górnym rogu.

*nBPP*<br/>
Liczba bitów na piksel w mapie bitowej. Zwykle 4, 8, 16, 24 lub 32. Może być 1 dla monochromatyczne mapy bitowe lub maski.

*eKompresja*<br/>
Określa typ kompresji skompresowanej mapy bitowej oddolnej (nie można skompresować z góry na dół bloków DIBs). Może być jedną z następujących wartości:

- BI_RGB Format jest nieskompresowany. Określenie tej wartości `CImage::CreateEx` podczas wywoływania `CImage::Create`jest równoznaczne z wywołaniem .

- BI_BITFIELDS Format jest nieskompresowany, a tabela kolorów składa się z trzech masek kolorów DWORD, które określają odpowiednio komponenty czerwony, zielony i niebieski każdego piksela. Jest to prawidłowe w przypadku użycia z bitmapami 16- i 32-bpp.

*pdwBitfields*<br/>
Używane tylko *wtedy, gdy eCompression* jest ustawiona na BI_BITFIELDS, w przeciwnym razie musi być null. Wskaźnik do tablicy trzech masek bitowych DWORD, określający, które bity każdego piksela są używane odpowiednio dla składników koloru czerwonego, zielonego i niebieskiego. Aby uzyskać informacje na temat ograniczeń dla pól bitowych, zobacz [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) w windows SDK.

*Dwflags*<br/>
Określa, czy obiekt mapy bitowej ma kanał alfa. Może być kombinacją zero lub więcej z następujących wartości:

- *tworzenieAlfaChannel* Może być używany tylko wtedy, gdy *nBPP* wynosi 32, a *eCompression* jest BI_RGB. Jeśli zostanie określony, utworzony obraz ma wartość alfa (przezroczystość) dla każdego piksela, przechowywaną w 4 bajtowym każdym pikselu (nieużywane w obrazie 32-bitowym innym niż alfa). Ten kanał alfa jest automatycznie używany podczas wywoływania [CImage::AlphaBlend](#alphablend).

   > [!NOTE]
   > W wywołaniach [do CImage::Draw](#draw)obrazy z kanałem alfa są automatycznie mieszane alfa do miejsca docelowego.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie. W przeciwnym razie FALSE.

### <a name="example"></a>Przykład

Poniższy przykład tworzy 100x100 pikseli bitmapy, przy użyciu 16 bitów do kodowania każdego piksela. W danym pikselu 16-bitowym bity 0-3 kodują czerwony składnik, bity 4-7 kodują na zielono, a bity 8-11 kodują na niebiesko. Pozostałe 4 bity są nieużywane.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a>CImage::Destroja

Odłącza mapę bitową `CImage` od obiektu i niszczy mapę bitową.

```cpp
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a>CImage::Detach

Odłącza mapę bitową `CImage` od obiektu.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do mapy bitowej odłączony lub NULL, jeśli nie jest dołączony bitmapa.

## <a name="cimagedraw"></a><a name="draw"></a>CImage::Draw

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

*hDestDC (hDestDC)*<br/>
Dojście do kontekstu urządzenia docelowego.

*xDest (xDest)*<br/>
Współrzędna x w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*yDest (właśc.*<br/>
Współrzędna y w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*nDestWidth (nDestWidth)*<br/>
Szerokość w jednostkach logicznych prostokąta docelowego.

*nDestHeight (nDestHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta docelowego.

*xSrc (ks.*<br/>
Współrzędna x w jednostkach logicznych w lewym górnym rogu prostokąta źródłowego.

*ySrc ( ySrc )*<br/>
Współrzędna y w jednostkach logicznych w lewym górnym rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych prostokąta źródłowego.

*nSrcHeight (nSrcHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta źródłowego.

*reectDest*<br/>
Odwołanie do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) identyfikując miejsce docelowe.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikując źródło.

*punktDest*<br/>
Odwołanie do struktury [POINT,](/windows/win32/api/windef/ns-windef-point) która identyfikuje lewy górny róg prostokąta docelowego w jednostkach logicznych.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Draw`wykonuje tę samą operację co [StretchBlt](#stretchblt), chyba że obraz zawiera przezroczysty kolor lub kanał alfa. W takim `Draw` przypadku wykonuje tę samą operację jako [TransparentBlt](#transparentblt) lub [AlphaBlend](#alphablend) zgodnie z wymaganiami.

W przypadku `Draw` wersji, które nie określają prostokąta źródłowego, domyślny jest cały obraz źródłowy. Dla `Draw` wersji, która nie określa rozmiar prostokąta docelowego, rozmiar obrazu źródłowego jest domyślny i nie rozciąganie lub zmniejszanie występuje.

## <a name="cimagegetbits"></a><a name="getbits"></a>CImage::GetBits

Pobiera wskaźnik do rzeczywistych wartości bitowych danego piksela w mapie bitowej.

```cpp
void* GetBits() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu mapy bitowej. Jeśli mapa bitowa jest dyb oddolne, wskaźnik wskazuje na końcu buforu. Jeśli mapa bitowa jest dib z góry na dół, wskaźnik wskazuje na pierwszy bajt buforu.

### <a name="remarks"></a>Uwagi

Za pomocą tego wskaźnika, wraz z wartością zwróconą przez [GetPitch,](#getpitch)można zlokalizować i zmienić poszczególne piksele obrazu.

> [!NOTE]
> Ta metoda obsługuje tylko bitmapy sekcji DIB; w związku z tym uzyskujesz `CImage` dostęp do pikseli obiektu w taki sam sposób, jak piksele sekcji DIB. Zwrócony wskaźnik wskazuje piksel w lokalizacji (0, 0).

## <a name="cimagegetbpp"></a><a name="getbpp"></a>CImage::GetBPP

Pobiera wartość bitów na piksel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba bitów na piksel.

### <a name="remarks"></a>Uwagi

Ta wartość określa liczbę bitów definiujących każdy piksel oraz maksymalną liczbę kolorów w mapie bitowej.

Bity na piksel to zwykle 1, 4, 8, 16, 24 lub 32. Zobacz `biBitCount` element członkowski [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) w usłudze Windows SDK, aby uzyskać więcej informacji na temat tej wartości.

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a>CImage::GetColorTable

Pobiera wartości kolorów czerwony, zielony, niebieski (RGB) z zakresu wpisów w palecie sekcji DIB.

```cpp
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Indeks tabeli kolorów pierwszego wpisu do pobrania.

*nKolory*<br/>
Liczba wpisów tabeli kolorów do pobrania.

*prgbKolory*<br/>
Wskaźnik do tablicy struktur [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) do pobierania wpisów tabeli kolorów.

## <a name="cimagegetdc"></a><a name="getdc"></a>CImage::GetDC

Pobiera kontekst urządzenia, w który aktualnie zaznaczono obraz.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Dla każdego `GetDC`wywołania , musisz mieć kolejne wywołanie [releaseDC](#releasedc).

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage::GetExporterFilterString

Wyszukuje formaty obrazów dostępne do zapisywania obrazów.

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
Odwołanie do `CSimpleString` obiektu. Zobacz **uwagi** uzyskać więcej informacji.

*aguidFileTypy*<br/>
Tablica identyfikatorów GUID, z każdym elementem odpowiadającym jednemu z typów plików w ciągu. W przykładzie w *pszAllFilesDescription* poniżej *aguidFileTypes*[0] jest GUID_NULL, a pozostałe wartości tablicy są formaty plików obrazu obsługiwane przez bieżący system operacyjny.

> [!NOTE]
> Aby uzyskać pełną listę stałych, zobacz **Stałe formatu pliku obrazu** w zestawie Windows SDK.

*pszAllFilesDescription (Opis)*<br/>
Jeśli ten parametr nie jest null, ciąg filtru będzie miał jeden dodatkowy filtr na początku listy. Ten filtr będzie miał bieżącą wartość *pszAllFilesDescription* dla jego opisu i akceptuje pliki dowolnego rozszerzenia obsługiwane przez innego eksportera na liście.

Przykład:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Zestaw flag bitowych określających typy plików, które mają być wykluczone z listy. Dopuszczalne flagi to:

- `excludeGIF`= 0x01 Wyklucza pliki GIF.

- `excludeBMP`= 0x02 Wyklucza pliki BMP (Windows Bitmap).

- `excludeEMF`= 0x04 Wyklucza pliki EMF (Enhanced Metafile).

- `excludeWMF`= 0x08 Wyklucza pliki WMF (Windows Metafile).

- `excludeJPEG`= 0x10 Wyklucza pliki JPEG.

- `excludePNG`= 0x20 Wyklucza pliki PNG.

- `excludeTIFF`= 0x40 Wyklucza pliki TIFF.

- `excludeIcon`= 0x80 Wyklucza pliki ICO (Windows Icon).

- `excludeOther`= 0x80000000 Wyklucza inny typ pliku niewymienione powyżej.

- `excludeDefaultLoad`= 0 W przypadku ładowania wszystkie typy plików są domyślnie uwzględniane

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Do zapisywania pliki te są domyślnie wykluczone, ponieważ zwykle mają specjalne wymagania.

*chPararytator*<br/>
Separator używany między formatami obrazu. Zobacz **uwagi** uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

### <a name="remarks"></a>Uwagi

Wynikowy ciąg formatu można przekazać do obiektu MFC [CFileDialog,](../../mfc/reference/cfiledialog-class.md) aby udostępnić rozszerzenia plików dostępnych formatów obrazów w oknie dialogowym Zapisywanie plików jako.

Parametr *strExporter* ma format:

opis pliku0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;... opis pliku *n*&#124;\*.ext *n*&#124;&#124;

gdzie "&#124;" jest znakiem separatora określonym `chSeparator`przez . Przykład:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Użyj domyślnego separatora "&#124;", jeśli przekażesz ten `CFileDialog` ciąg do obiektu MFC. Użyj separatora null "\0", jeśli przekażesz ten ciąg do wspólnego okna dialogowego Zapisywanie plików.

## <a name="cimagegetheight"></a><a name="getheight"></a>CImage::GetHeight

Pobiera wysokość obrazu w pikselach.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość obrazu w pikselach.

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage::GetImporterFilterString

Wyszukuje formaty obrazów dostępne do ładowania obrazów.

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
Odwołanie do `CSimpleString` obiektu. Zobacz **uwagi** uzyskać więcej informacji.

*aguidFileTypy*<br/>
Tablica identyfikatorów GUID, z każdym elementem odpowiadającym jednemu z typów plików w ciągu. W przykładzie w *pszAllFilesDescription* poniżej *aguidFileTypes*[0] jest GUID_NULL z pozostałymi wartościami tablicy są formaty plików obrazu obsługiwane przez bieżący system operacyjny.

> [!NOTE]
> Aby uzyskać pełną listę stałych, zobacz **Stałe formatu pliku obrazu** w zestawie Windows SDK.

*pszAllFilesDescription (Opis)*<br/>
Jeśli ten parametr nie jest null, ciąg filtru będzie miał jeden dodatkowy filtr na początku listy. Ten filtr będzie miał bieżącą wartość *pszAllFilesDescription* dla jego opisu i akceptuje pliki dowolnego rozszerzenia obsługiwane przez innego eksportera na liście.

Przykład:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Zestaw flag bitowych określających typy plików, które mają być wykluczone z listy. Dopuszczalne flagi to:

- `excludeGIF`= 0x01 Wyklucza pliki GIF.

- `excludeBMP`= 0x02 Wyklucza pliki BMP (Windows Bitmap).

- `excludeEMF`= 0x04 Wyklucza pliki EMF (Enhanced Metafile).

- `excludeWMF`= 0x08 Wyklucza pliki WMF (Windows Metafile).

- `excludeJPEG`= 0x10 Wyklucza pliki JPEG.

- `excludePNG`= 0x20 Wyklucza pliki PNG.

- `excludeTIFF`= 0x40 Wyklucza pliki TIFF.

- `excludeIcon`= 0x80 Wyklucza pliki ICO (Windows Icon).

- `excludeOther`= 0x80000000 Wyklucza inny typ pliku niewymienione powyżej.

- `excludeDefaultLoad`= 0 W przypadku ładowania wszystkie typy plików są domyślnie uwzględniane

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Do zapisywania pliki te są domyślnie wykluczone, ponieważ zwykle mają specjalne wymagania.

*chPararytator*<br/>
Separator używany między formatami obrazu. Zobacz **uwagi** uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Wynikowy ciąg formatu można przekazać do obiektu MFC [CFileDialog,](../../mfc/reference/cfiledialog-class.md) aby udostępnić rozszerzenia plików dostępnych formatów obrazów w oknie dialogowym **Otwieranie pliku.**

Parametr *strImporter* ma format:

opis pliku0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;... opis pliku *n*&#124;\*.ext *n*&#124;&#124;

gdzie "&#124;" jest znakiem separatora określonym przez *chSeparator*. Przykład:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Użyj domyślnego separatora "&#124;", jeśli przekażesz ten `CFileDialog` ciąg do obiektu MFC. Użyj separatora null "\0", jeśli przekażesz ten ciąg do wspólnego okna dialogowego **Otwieranie pliku.**

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage::GetMaxColorTableEntries

Pobiera maksymalną liczbę wpisów w tabeli kolorów.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wpisów w tabeli kolorów.

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje tylko bitmapy sekcji DIB.

## <a name="cimagegetpitch"></a><a name="getpitch"></a>CImage::GetPitch

Pobiera wysokość obrazu.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość obrazu. Jeśli zwracana wartość jest ujemna, mapa bitowa jest dib oddolnym, a jej początek jest lewym dolnym rogu. Jeśli zwracana wartość jest dodatnia, mapa bitowa jest dib z góry na dół, a jej początek jest lewym górnym rogu.

### <a name="remarks"></a>Uwagi

Podziałka jest odległością w bajtach między dwoma adresami pamięci reprezentującymi początek jednej linii bitmapy i początek następnej linii bitmapy. Ponieważ wysokość jest mierzona w bajtach, wysokość obrazu pomaga określić format piksela. Podziałka może również zawierać dodatkową pamięć, zarezerwowaną dla mapy bitowej.

Użyj `GetPitch` z [GetBits,](#getbits) aby znaleźć poszczególne piksele obrazu.

> [!NOTE]
> Ta metoda obsługuje tylko bitmapy sekcji DIB.

## <a name="cimagegetpixel"></a><a name="getpixel"></a>CImage::GetPixel

Pobiera kolor piksela w miejscu określonym przez *x* i *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Współrzędna x piksela.

*Y*<br/>
Współrzędna y piksela.

### <a name="return-value"></a>Wartość zwracana

Wartość piksela jest czerwona, zielona, niebieska (RGB). Jeśli piksel znajduje się poza bieżącym regionem przycinania, zwracana jest wartość CLR_INVALID.

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage::GetPixelAddress

Pobiera dokładny adres piksela.

```cpp
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Współrzędna x piksela.

*Y*<br/>
Współrzędna y piksela.

### <a name="remarks"></a>Uwagi

Adres jest określany zgodnie ze współrzędnymi piksela, wysokości mapy bitowej i bitów na piksel.

W przypadku formatów, które mają mniej niż 8 bitów na piksel, ta metoda zwraca adres bajtu zawierającego piksel. Jeśli na przykład format obrazu ma 4 `GetPixelAddress` bity na piksel, zwraca adres pierwszego piksela w bajcie i musi być obliczony dla 2 pikseli na bajt.

> [!NOTE]
> Ta metoda obsługuje tylko bitmapy sekcji DIB.

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage::GetTransparentColor

Pobiera indeksowane położenie koloru przezroczystego w palecie kolorów.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Indeks koloru przezroczystego.

## <a name="cimagegetwidth"></a><a name="getwidth"></a>CImage::GetWidth

Pobiera szerokość obrazu w pikselach.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Szerokość mapy bitowej w pikselach.

## <a name="cimageisdibsection"></a><a name="isdibsection"></a>CImage::IsDIBSekcja

Określa, czy załączona mapa bitowa jest sekcją DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli załączona mapa bitowa jest sekcją DIB. W przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli mapa bitowa nie jest sekcją DIB, nie można użyć następujących `CImage` metod, które obsługują tylko mapy bitowe sekcji DIB:

- [GetBits (GetBits)](#getbits)

- [Tabela GetColorTable](#getcolortable)

- [GetMaxColorTableEntries (Wyw.](#getmaxcolortableentries)

- [GetPitch ( GetPitch )](#getpitch)

- [Sukienka GetPixelAddress](#getpixeladdress)

- [IsIndexed ( IsIndexed )](#isindexed)

- [Tabela SetColorTable](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a>CImage::IsIndexed

Określa, czy piksele mapy bitowej są mapowane na paletę kolorów.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli jest indeksowana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość TRUE tylko wtedy, gdy mapa bitowa jest 8-bitowa (256 kolorów) lub mniejsza.

> [!NOTE]
> Ta metoda obsługuje tylko bitmapy sekcji DIB.

## <a name="cimageisnull"></a><a name="isnull"></a>CImage::Isnull

Określa, czy mapa bitowa jest aktualnie załadowana.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość TRUE, jeśli mapa bitowa nie jest aktualnie załadowana; w przeciwnym razie FALSE.

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a>CImage::IsTransparencySupported

Wskazuje, czy aplikacja obsługuje przezroczyste mapy bitowe.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli bieżąca platforma obsługuje przezroczystość. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli zwracana wartość jest niezerowa, a przezroczystość jest obsługiwana, wywołanie [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)lub [Draw](#draw) będzie obsługiwać przezroczyste kolory.

## <a name="cimageload"></a><a name="load"></a>CImage::Obciążenie

Ładuje obraz.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pszFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku obrazu do załadowania.

*pStream (Strumień)*<br/>
Wskaźnik do strumienia zawierający nazwę pliku obrazu do załadowania.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

### <a name="remarks"></a>Uwagi

Ładuje obraz określony przez *pszFileName* lub *pStream*.

Prawidłowe typy obrazów to BMP, GIF, JPEG, PNG i TIFF.

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a>CImage::LoadFromResource

Ładuje obraz z zasobu BITMAP.

```cpp
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>Parametry

*hInstance (Nieumieja)*<br/>
Dojście do wystąpienia modułu, który zawiera obraz do załadowania.

*pszResourceName*<br/>
Wskaźnik do ciągu zawierający nazwę zasobu zawierającego obraz do załadowania.

*nIDSerwród*<br/>
Identyfikator zasobu do załadowania.

### <a name="remarks"></a>Uwagi

Zasób musi być typu BITMAP.

## <a name="cimagemaskblt"></a><a name="maskblt"></a>CImage::MaskBlt

Łączy dane kolorów dla źródłowych i docelowych map bitowych przy użyciu określonej maski i operacji rastrowej.

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

*hDestDC (hDestDC)*<br/>
Dojście do modułu, którego plik wykonywalny zawiera zasób.

*xDest (xDest)*<br/>
Współrzędna x w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*yDest (właśc.*<br/>
Współrzędna y w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*nDestWidth (nDestWidth)*<br/>
Szerokość w jednostkach logicznych prostokąta docelowego i źródłowej mapy bitowej.

*nDestHeight (nDestHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta docelowego i źródłowej mapy bitowej.

*xSrc (ks.*<br/>
Logiczna współrzędna x w lewym górnym rogu źródłowej mapy bitowej.

*ySrc ( ySrc )*<br/>
Logiczna współrzędna y w lewym górnym rogu źródłowej mapy bitowej.

*hbmMask (hbmMask)*<br/>
Obsługa mapy bitowej maski monochromatycznej w połączeniu z bitmapą kolorów w kontekście urządzenia źródłowego.

*Maska x*<br/>
Odsunięcie piksela poziomego dla mapy bitowej maski określonej przez parametr *hbmMask.*

*yMask (yMask)*<br/>
Przesunięcie piksela pionowego dla mapy bitowej maski określonej przez parametr *hbmMask.*

*dwROP ( dwROP )*<br/>
Określa zarówno pierwszy, jak i tno trójstające kody operacji rastrowych, których metoda używa do kontrolowania kombinacji danych źródłowych i docelowych. Kod operacji rastrowej tła jest przechowywany w bajcie wysokiego rzędu słowa wysokiego rzędu tej wartości; pierwszy plan kod operacji rastrowej jest przechowywany w bajcie niskiej kolejności słowa wysokiego rzędu tej wartości; słowo niskiej kolejności tej wartości jest ignorowane i powinno wynosić zero. Aby zapoznać się z omówienia pierwszego planu `MaskBlt` i tła w kontekście tej metody, zobacz w windows SDK. Aby uzyskać listę typowych kodów `BitBlt` operacji rastrowych, zobacz w zestawie Windows SDK.

*reectDest*<br/>
Odwołanie do `RECT` struktury, identyfikując miejsce docelowe.

*pktSrc*<br/>
Struktura `POINT` wskazująca lewy górny róg prostokąta źródłowego.

*maska punktna*<br/>
Struktura `POINT` wskazująca lewy górny róg mapy bitowej maski.

*punktDest*<br/>
Odwołanie do `POINT` struktury, która identyfikuje lewy górny róg prostokąta docelowego w jednostkach logicznych.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda dotyczy tylko systemu Windows NT w wersji 4.0 i nowszej.

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage::operator HBITMAP

Użyj tego operatora, aby uzyskać dołączony uchwyt `CImage` GDI systemu Windows obiektu. Ten operator jest operatorem odlewania, który obsługuje bezpośrednie użycie obiektu HBITMAP.

## <a name="cimageplgblt"></a><a name="plgblt"></a>CImage::PlgBlt

Wykonuje transfer bloku bitowego z prostokąta w kontekście urządzenia źródłowego do równoległoboku w kontekście urządzenia docelowego.

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

*hDestDC (hDestDC)*<br/>
Dojście do kontekstu urządzenia docelowego.

*p Punkty*<br/>
Wskaźnik do tablicy trzech punktów w przestrzeni logicznej, które identyfikują trzy rogi równoległoboku docelowego. Lewy górny róg prostokąta źródłowego jest mapowany na pierwszy punkt w tej tablicy, prawy górny róg do drugiego punktu w tej tablicy, a lewy dolny róg do trzeciego punktu. Prawy dolny róg prostokąta źródłowego jest mapowany na niejawny czwarty punkt w równoległoboku.

*hbmMask (hbmMask)*<br/>
Uchwyt do opcjonalnej monochromatycznej mapy bitowej, która służy do maskowania kolorów prostokąta źródłowego.

*xSrc (ks.*<br/>
Współrzędna x w jednostkach logicznych w lewym górnym rogu prostokąta źródłowego.

*ySrc ( ySrc )*<br/>
Współrzędna y w jednostkach logicznych w lewym górnym rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych prostokąta źródłowego.

*nSrcHeight (nSrcHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta źródłowego.

*Maska x*<br/>
Współrzędna x lewego górnego rogu monochromatycznej mapy bitowej.

*yMask (yMask)*<br/>
Współrzędna y w lewym górnym rogu monochromatycznej mapy bitowej.

*rectSrc*<br/>
Odwołanie do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) określające współrzędne prostokąta źródłowego.

*maska punktna*<br/>
Struktura [POINT](/windows/win32/api/windef/ns-windef-point) wskazująca lewy górny róg mapy bitowej maski.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *hbmMask* identyfikuje prawidłową monochromatyczną mapę bitową, `PlgBit` używa tej mapy bitowej do maskowania bitów danych kolorów z prostokąta źródłowego.

Ta metoda dotyczy tylko systemu Windows NT w wersji 4.0 i nowszej. Aby uzyskać bardziej szczegółowe informacje, zobacz [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) w programie Windows SDK.

## <a name="cimagereleasedc"></a><a name="releasedc"></a>CImage::ReleaseDC

Zwalnia kontekst urządzenia.

```cpp
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Uwagi

Ponieważ w kontekście urządzenia można jednocześnie wybrać tylko jedną `ReleaseDC` mapę bitową, należy wywołać każde wywołanie [getDc](#getdc).

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a>CImage::ReleaseGDIPlus

Zwalnia zasoby używane przez GDI+.

```cpp
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda musi być wywoływana do `CImage` wolnych zasobów przydzielonych przez obiekt globalny. Zobacz [CImage::CImage](#cimage).

## <a name="cimagesave"></a><a name="save"></a>CImage::Zapisz

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

*pStream (Strumień)*<br/>
Wskaźnik do obiektu IStream COM zawierającego dane obrazu pliku.

*pszFileName*<br/>
Wskaźnik do nazwy pliku obrazu.

*typ guidFileType*<br/>
Typ pliku, aby zapisać obraz jako. Może być jedną z następujących czynności:

- `ImageFormatBMP`Nieskompresowany obraz bitmapowy.

- `ImageFormatPNG`Skompresowany obraz przenośnej grafiki sieciowej (PNG).

- `ImageFormatJPEG`Skompresowany obraz JPEG.

- `ImageFormatGIF`Skompresowany obraz GIF.

> [!NOTE]
> Aby uzyskać pełną listę stałych, zobacz **Stałe formatu pliku obrazu** w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zapisać obraz przy użyciu określonej nazwy i typu. Jeśli parametr *guidFileType* nie jest uwzględniony, rozszerzenie pliku nazwy pliku zostanie użyte do określenia formatu obrazu. Jeśli nie podano żadnego rozszerzenia, obraz zostanie zapisany w formacie BMP.

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a>CImage::SetColorTable

Ustawia wartości kolorów czerwony, zielony, niebieski (RGB) dla zakresu wpisów w palecie sekcji DIB.

```cpp
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Indeks tabeli kolorów pierwszego wpisu do ustawionego.

*nKolory*<br/>
Liczba wpisów tabeli kolorów do ustawionego.

*prgbKolory*<br/>
Wskaźnik do tablicy struktur [RGBQUAD,](/windows/win32/api/wingdi/ns-wingdi-rgbquad) aby ustawić wpisy tabeli kolorów.

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje tylko bitmapy sekcji DIB.

## <a name="cimagesetpixel"></a><a name="setpixel"></a>CImage::SetPixel

Ustawia kolor piksela w danym miejscu na mapie bitowej.

```cpp
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Pozioma lokalizacja piksela do ustawienia.

*Y*<br/>
Pionowa lokalizacja piksela do ustawienia.

*color*<br/>
Kolor, na który ustawiono piksel.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli współrzędne piksela znajdują się poza wybranym regionem przycinania.

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage::SetPixelIndexed

Ustawia kolor piksela na kolor znajdujący się w pliku *iIndex* w palecie kolorów.

```cpp
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Pozioma lokalizacja piksela do ustawienia.

*Y*<br/>
Pionowa lokalizacja piksela do ustawienia.

*Iindex*<br/>
Indeks koloru w palecie kolorów.

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage::SetPixelRGB

Ustawia piksel w miejscach określonych przez *x* i *y* na kolorach wskazanych przez *r*, *g*i *b*, w obrazie czerwonym, zielonym, niebieskim (RGB).

```cpp
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Pozioma lokalizacja piksela do ustawienia.

*Y*<br/>
Pionowa lokalizacja piksela do ustawienia.

*R*<br/>
Intensywność koloru czerwonego.

*G*<br/>
Intensywność koloru zielonego.

*B*<br/>
Intensywność koloru niebieskiego.

### <a name="remarks"></a>Uwagi

Parametry czerwony, zielony i niebieski są reprezentowane przez liczbę z 0 do 255. Jeśli wszystkie trzy parametry zostanie ustawione na zero, połączony kolor wynikowy będzie czarny. Jeśli ustawisz wszystkie trzy parametry na 255, połączony wynikowy kolor będzie biały.

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage::SetTransparentColor

Ustawia kolor w danej lokalizacji indeksowane jako przezroczyste.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parametry

*iTransparentColor*<br/>
Indeks w palecie kolorów koloru, który ma być ustawiony na przezroczysty. Jeśli -1, żaden kolor nie jest ustawiony na przezroczysty.

### <a name="return-value"></a>Wartość zwracana

Indeks koloru wcześniej ustawionego jako przezroczysty.

## <a name="cimagestretchblt"></a><a name="stretchblt"></a>CImage::Rozciągliwyblt

Kopiuje mapę bitową z kontekstu urządzenia źródłowego do bieżącego kontekstu urządzenia.

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

*hDestDC (hDestDC)*<br/>
Dojście do kontekstu urządzenia docelowego.

*xDest (xDest)*<br/>
Współrzędna x w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*yDest (właśc.*<br/>
Współrzędna y w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*nDestWidth (nDestWidth)*<br/>
Szerokość w jednostkach logicznych prostokąta docelowego.

*nDestHeight (nDestHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta docelowego.

*dwROP ( dwROP )*<br/>
Operacja rastrowa do wykonania. Kody operacji rastrowych definiują dokładnie sposób łączenia bitów źródła, miejsca docelowego i wzorca (zdefiniowanego przez aktualnie zaznaczony pędzel) w celu utworzenia miejsca docelowego. Zobacz [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) w zestawie Windows SDK, aby uzyskać listę innych kodów operacji rastrowych i ich opisów.

*reectDest*<br/>
Odwołanie do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) identyfikując miejsce docelowe.

*xSrc (ks.*<br/>
Współrzędna x w jednostkach logicznych w lewym górnym rogu prostokąta źródłowego.

*ySrc ( ySrc )*<br/>
Współrzędna y w jednostkach logicznych w lewym górnym rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych prostokąta źródłowego.

*nSrcHeight (nSrcHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta źródłowego.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikując źródło.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) w windows SDK.

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a>CImage::TransparentBlt

Kopiuje mapę bitową z kontekstu urządzenia źródłowego do bieżącego kontekstu urządzenia.

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

*hDestDC (hDestDC)*<br/>
Dojście do kontekstu urządzenia docelowego.

*xDest (xDest)*<br/>
Współrzędna x w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*yDest (właśc.*<br/>
Współrzędna y w jednostkach logicznych w lewym górnym rogu prostokąta docelowego.

*nDestWidth (nDestWidth)*<br/>
Szerokość w jednostkach logicznych prostokąta docelowego.

*nDestHeight (nDestHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta docelowego.

*crPrzezroczysty*<br/>
Kolor w źródłowej mapie bitowej, aby traktować jako przezroczysty. Domyślnie CLR_INVALID, wskazując, że należy użyć koloru aktualnie ustawionego jako przezroczysty kolor obrazu.

*reectDest*<br/>
Odwołanie do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) identyfikując miejsce docelowe.

*xSrc (ks.*<br/>
Współrzędna x w jednostkach logicznych w lewym górnym rogu prostokąta źródłowego.

*ySrc ( ySrc )*<br/>
Współrzędna y w jednostkach logicznych w lewym górnym rogu prostokąta źródłowego.

*nSrcWidth*<br/>
Szerokość w jednostkach logicznych prostokąta źródłowego.

*nSrcHeight (nSrcHeight)*<br/>
Wysokość w jednostkach logicznych prostokąta źródłowego.

*rectSrc*<br/>
Odwołanie do `RECT` struktury, identyfikując źródło.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`TransparentBlt`jest obsługiwana dla źródłowych bitmap 4 bitów na piksel i 8 bitów na piksel. Użyj [CImage::AlphaBlend,](#alphablend) aby określić 32 bity na piksel mapy bitowe z przezroczystością.

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

[Próbka MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Próbka SimpleImage](../../overview/visual-cpp-samples.md)<br/>
[Mapy bitowe niezależne od urządzenia](/windows/win32/gdi/device-independent-bitmaps)<br/>
[Utwórz Pozycję](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)<br/>
[Mapy bitowe niezależne od urządzenia](/windows/win32/gdi/device-independent-bitmaps)<br/>
[Utwórz Pozycję](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
