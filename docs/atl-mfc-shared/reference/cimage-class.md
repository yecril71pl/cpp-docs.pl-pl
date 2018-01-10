---
title: "CImage — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d2720fb2b1e558b564615e1589735fe84688374b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cimage-class"></a>CImage — klasa
`CImage`zapewnia obsługę rozszerzonych mapy bitowej, łącznie z możliwością przy ładowaniu i zapisywaniu obrazów w formacie JPEG, GIF, BMP i Portable Network Graphics (PNG).  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
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
|[CImage::AlphaBlend](#alphablend)|Wyświetla bitmap przezroczysty lub półprzezroczysty pikseli.|  
|[CImage::Attach](#attach)|Dołącza `HBITMAP` do `CImage` obiektu. Może służyć map bitowych sekcji z systemem innym niż DIB lub DIB sekcji bitmapy.|  
|[CImage::BitBlt](#bitblt)|Kopiuje mapę bitową z kontekstu urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.|  
|[CImage::Create](#create)|Tworzy mapę bitową sekcji DIB i dołącza go do wcześniej utworzone `CImage` obiektu.|  
|[CImage::CreateEx](#createex)|Tworzy mapę bitową sekcji DIB (z dodatkowymi parametrami) i dołącza go do wcześniej utworzone `CImage` obiektu.|  
|[CImage::Destroy](#destroy)|Odłącza mapy bitowej z `CImage` obiektu i niszczy mapy bitowej.|  
|[CImage::Detach](#detach)|Odłącza mapy bitowej z `CImage` obiektu.|  
|[CImage::Draw](#draw)|Kopiuje mapy bitowej z prostokąta źródłowego do docelowego prostokąta. **Rysuj** rozciąga się lub kompresuje mapy bitowej do rozmiaru prostokąt docelowy, jeśli to konieczne i obsługuje przenikanie alfa i kolory przezroczyste.|  
|[CImage::GetBits](#getbits)|Pobiera wskaźnik do wartości rzeczywistej pikseli mapy bitowej.|  
|[CImage::GetBPP](#getbpp)|Pobiera bitów na piksel.|  
|[CImage::GetColorTable](#getcolortable)|Pobiera czerwony, zielony, niebieski wartości kolorów (RGB) z zakresu wpisów w tabeli kolorów.|  
|[CImage::GetDC](#getdc)|Pobiera kontekst urządzenia, do którego bieżący mapy bitowej jest zaznaczone.|  
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Umożliwia znalezienie formatów dostępnych obrazów i ich opisy.|  
|[CImage::GetHeight](#getheight)|Pobiera wysokość bieżącego obrazu w pikselach.|  
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Umożliwia znalezienie formatów dostępnych obrazów i ich opisy.|  
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Pobiera maksymalną liczbę wpisów w tabeli kolorów.|  
|[CImage::GetPitch](#getpitch)|Pobiera wysokość bieżący obraz w bajtach.|  
|[CImage::GetPixel](#getpixel)|Pobiera kolor piksela określony przez *x* i *y*.|  
|[CImage::GetPixelAddress](#getpixeladdress)|Pobiera adres danego piksela.|  
|[CImage::GetTransparentColor](#gettransparentcolor)|Pobiera położenie kolor przezroczysty w tabeli kolorów.|  
|[CImage::GetWidth](#getwidth)|Pobiera szerokość bieżącego obrazu w pikselach.|  
|[CImage::IsDIBSection](#isdibsection)|Określa, czy dołączone mapy bitowej jest sekcji DIB.|  
|[CImage::IsIndexed](#isindexed)|Wskazuje, że kolorów mapy bitowej są mapowane na indeksowanego palety.|  
|[CImage::IsNull](#isnull)|Wskazuje, czy źródła mapy bitowej jest aktualnie załadowany.|  
|[CImage::IsTransparencySupported](#istransparencysupported)|Wskazuje, czy aplikacja obsługuje bitmapy przezroczyste i został skompilowany dla systemu Windows 2000 lub nowszego.|  
|[CImage::Load](#load)|Ładuje obraz z określonego pliku.|  
|[CImage::LoadFromResource](#loadfromresource)|Ładuje obraz z określonego zasobu.|  
|[CImage::MaskBlt](#maskblt)|Łączy dane kolorów mapy bitowe źródłowych i docelowych przy użyciu określona maska i rastrowe operacji.|  
|[CImage::PlgBlt](#plgblt)|Wykonuje przesunięcia bitowego bloku z prostokąt w kontekście urządzenia źródłowego do równoległobok kontekstu urządzenia docelowego.|  
|[CImage::ReleaseDC](#releasedc)|Zwalnia kontekst urządzenia, który został pobrany z [CImage::GetDC](#getdc).|  
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Zwalnia zasoby używane przez GDI +. Musi zostać wywołana, aby zwolnić zasoby utworzone przez globalną `CImage` obiektu.|  
|[CImage::Save](#save)|Zapisuje obraz jako określonego typu. **Zapisz** nie można określić opcji obrazu.|  
|[CImage::SetColorTable](#setcolortable)|Ustawia RGB czerwony, zielony, niebieski) wartości w zakresie wpisów w tabeli kolorów sekcji DIB kolorów.|  
|[CImage::SetPixel](#setpixel)|Ustawia piksel w określonych współrzędnych do określonego koloru.|  
|[CImage::SetPixelIndexed](#setpixelindexed)|Ustawia piksel w określonych współrzędnych na kolor pod określonym indeksem palety.|  
|[CImage::SetPixelRGB](#setpixelrgb)|Ustawia piksel w określonych współrzędnych wartość niebieskiego zielony, określony czerwony.|  
|[CImage::SetTransparentColor](#settransparentcolor)|Ustawia indeks kolor ma być traktowane jako przezroczysty. Tylko jeden kolor w palecie może być przezroczysty.|  
|[CImage::StretchBlt](#stretchblt)|Kopiuje mapy bitowej z prostokąta źródłowego do docelowego prostokąta, rozciąganie lub kompresowania mapy bitowej do rozmiaru prostokąt docelowy, jeśli to konieczne.|  
|[CImage::TransparentBlt](#transparentblt)|Kopiuje mapę bitową o kolor przezroczysty z kontekstu urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HBITMAP CImage::operator](#operator_hbitmap)|Zwraca dojście Windows dołączona do `CImage` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CImage`Trwa mapy bitowe, które są albo sekcje map bitowych niezależnych od urządzenia (DIB) czy nie; można jednak użyć [Utwórz](#create) lub [CImage::Load](#load) tylko DIB sekcje. Możesz dołączyć mapę bitową sekcji z systemem innym niż DIB do `CImage` przy użyciu [Attach](#attach), następnie można użyć następujących `CImage` metody, które obsługują tylko DIB sekcji bitmapy:  
  
- [GetBits](#getbits)  
  
- [GetColorTable](#getcolortable)  
  
- [GetMaxColorTableEntries](#getmaxcolortableentries)  
  
- [GetPitch](#getpitch)  
  
- [GetPixelAddress](#getpixeladdress)  
  
- [IsIndexed](#isindexed)  
  
- [SetColorTable](#setcolortable)  
  
 Aby określić, czy dołączone mapy bitowej jest sekcji DIB, należy wywołać [IsDibSection](#isdibsection)**.**  
  
> [!NOTE]
> **Uwaga** w programie Visual Studio .NET 2003, ta klasa śledzi liczbę liczbę `CImage` obiekty utworzone. Zawsze, gdy liczba wynosić 0, funkcja **GdiplusShutdown** jest wywoływana automatycznie, aby zwolnić zasoby używane przez GDI +. Gwarantuje to, że wszelkie `CImage` obiekty utworzone bezpośrednio lub pośrednio przez biblioteki dll zawsze zostaną zniszczone poprawnie i czy **GdiplusShutdown** nie jest wywoływany z `DllMain`.  
  
> [!NOTE]
>  Za pomocą globalnej `CImage` obiektów w bibliotece DLL nie jest zalecane. Jeśli musisz użyć globalnym `CImage` obiektu w bibliotece DLL, wywołanie [CImage::ReleaseGDIPlus](#releasegdiplus) jawnie zwolnić zasoby używane przez GDI +.  
  
 `CImage`Nie można wybrać do nowego [CDC](../../mfc/reference/cdc-class.md). `CImage`tworzy własne **elementu HDC** obrazu. Ponieważ `HBITMAP` można wybrać tylko do jednej **elementu HDC** w czasie, `HBITMAP` skojarzone z `CImage` nie można wybrać do innego **elementu HDC**. Jeśli potrzebujesz `CDC`, pobrać **elementu HDC** z `CImage` i nadaj [CDC::FromHandle] (.. /.. /MFC/Reference/CDC-Class.MD#cdc__fromhandle.  
  
## <a name="example"></a>Przykład  
```cpp  
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```  
  
 Jeśli używasz `CImage` w projekcie MFC należy pamiętać, które funkcje Członkowskie w projekcie oczekuje wskaźnika do [cbitmap —](../../mfc/reference/cbitmap-class.md) obiektu. Jeśli chcesz użyć `CImage` przy użyciu funkcji, takich jak [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), użyj [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), przekaż go z `CImage` `HBITMAP`i użyj zwrócony `CBitmap*`.  

  
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

  
 Za pomocą `CImage`, musisz mieć dostęp do rzeczywistej bitów sekcji DIB. Można użyć `CImage` obiekt dowolnym korzystał Win32 HBITMAP lub DIB sekcji.  
  
> [!NOTE]
>  Następujące `CImage` metody mają ograniczenia ich użycia:  
  
|Metoda|Ograniczenia|  
|------------|----------------|  
|[PlgBlt](#plgblt)|Działa tylko system Windows NT 4.0 lub nowszy. Nie będzie działać na aplikacje działające w systemie Windows 95/98 lub nowszym.|  
|[MaskBlt](#maskblt)|Działa tylko system Windows NT 4.0 lub nowszy. Nie będzie działać na aplikacje działające w systemie Windows 95/98 lub nowszym.|  
|[AlphaBlend](#alphablend)|Sprawdza się w systemie Windows 2000, Windows 98 lub nowszym.|  
|[TransparentBlt](#transparentblt)|Sprawdza się w systemie Windows 2000, Windows 98 lub nowszym.|  
|[Rysuj](#draw)|Obsługuje przezroczystość z systemu Windows 2000, Windows 98 lub nowszym.|  
  
 Można użyć `CImage` z MFC lub ATL.  
  
> [!NOTE]
>  Podczas tworzenia projektu za pomocą `CImage`, należy zdefiniować `CString` przed wprowadzeniem `atlimage.h`. Jeśli projekt używa ATL bez MFC, obejmują `atlstr.h` przed wprowadzeniem `atlimage.h`. Jeśli projekt używa MFC (lub jeśli jest to Projekt ATL o Obsługa MFC), obejmują `afxstr.h` przed wprowadzeniem `atlimage.h`.  
>   
>  Podobnie, należy uwzględnić `atlimage.h` przed wprowadzeniem `atlimpl.cpp`. W tym celu łatwo obejmują `atlimage.h` w Twojej `stdafx.h`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlimage.h  
  
##  <a name="alphablend"></a>CImage::AlphaBlend  
 Wyświetla bitmap przezroczysty lub półprzezroczysty pikseli.  
  
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
 `hDestDC`  
 Dojście do kontekstu urządzenia docelowego.  
  
 `xDest`  
 Współrzędna x, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 `yDest`  
 Współrzędna y, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 *bSrcAlpha*  
 Wartość alfa przezroczystości dla całego źródła mapy bitowej. Domyślnie 0xff (255) zakłada obraz ma być nieprzezroczyste, i chcesz używać każdego piksela tylko wartości alfanumeryczne.  
  
 `bBlendOp`  
 Przenikanie alfa funkcja dla źródłowego i docelowego mapy bitowe, wartości alfa globalnej ma zostać zastosowany do mapy bitowej całą źródłową i informacji o formacie źródła mapy bitowej. Funkcje programu blend źródłowy i docelowy są obecnie ograniczone do **AC_SRC_OVER**.  
  
 `pointDest`  
 Odwołanie do [punktu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktura, która identyfikuje lewym górnym rogu prostokąta docelowej, w jednostkach logicznych.  
  
 `nDestWidth`  
 Szerokość w jednostkach logicznych, prostokąta docelowego.  
  
 `nDestHeight`  
 Wysokość w jednostkach logicznych, prostokąta docelowego.  
  
 `xSrc`  
 Logiczne współrzędną x górnego lewego rogu prostokąta źródłowego.  
  
 `ySrc`  
 Logiczne współrzędną y górnego lewego rogu prostokąta źródłowego.  
  
 `nSrcWidth`  
 Szerokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `nSrcHeight`  
 Wysokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `rectDest`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, identyfikowanie miejsca docelowego.  
  
 `rectSrc`  
 Odwołanie do `RECT` struktury identyfikacji źródła.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Mapy bitowe Alpha blend obsługuje kolor mieszania na podstawie każdego piksela.  
  
 Gdy `bBlendOp` ma ustawioną wartość domyślną **AC_SRC_OVER**, mapy bitowej źródła znajduje się nad mapy bitowej docelowym na podstawie wartości alfa źródłowych.  

##  <a name="attach"></a>CImage::Attach  
 Dołącza `hBitmap` do `CImage` obiektu.  
  
```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hBitmap`  
 Dojście do `HBITMAP`.  
  
 *eOrientation*  
 Określa orientację mapy bitowej. Może to być jedna z następujących czynności:  
  
- **DIBOR_DEFAULT** orientację mapy bitowej jest określany przez system operacyjny. Jednak to może nie zawsze być zamierzone wyniki we wszystkich systemach operacyjnych. Aby uzyskać więcej informacji na ten, zobacz następujący artykuł bazy wiedzy Knowledge Base ( **Q186586**): PRB: GetObject() zawsze zwraca wartość dodatnią wysokości dla DIB sekcje.  
  
- **DIBOR_BOTTOMUP** linii mapy bitowej są w odwrotnej kolejności. Powoduje to [CImage::GetBits](#getbits) do zwraca wskaźnik zbliża się koniec buforu mapy bitowej i [CImage::GetPitch](#getpitch) aby zwrócić wartość ujemną.  
  
- **DIBOR_TOPDOWN** linii mapy bitowej są u góry do dołu zamówienia. Powoduje to [CImage::GetBits](#getbits) do zwraca wskaźnik do pierwszego bajtu buforu mapy bitowej i [CImage::GetPitch](#getpitch) do zwrócenia liczbą dodatnią.  
  
### <a name="remarks"></a>Uwagi  
 Mapa bitowa może być mapy bitowej sekcji z systemem innym niż DIB lub mapy bitowej sekcji DIB. Zobacz [IsDIBSection](#isdibsection) listę metod, które można używać tylko z DIB sekcji map bitowych.  
  
##  <a name="bitblt"></a>CImage::BitBlt  
 Kopiuje mapę bitową z kontekstu urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.  
  
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
 `hDestDC`  
 Miejsce docelowe **elementu HDC**.  
  
 `xDest`  
 Logiczne współrzędną x lewego górnego rogu prostokąta docelowego.  
  
 `yDest`  
 Logiczne współrzędną y lewego górnego rogu prostokąta docelowego.  
  
 `dwROP`  
 Operacja rastrowe do wykonania. Kody operacji rastrowe zdefiniować dokładnie sposób łączenia (zgodnie z definicją w aktualnie wybranej pędzla) bitów źródłowego, docelowego i wzorzec do miejsca docelowego. Zobacz [BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370) w zestawie Windows SDK dla listy innych kodów operacji rastrowe i ich opisy.  
  
 `pointDest`  
 A [punktu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktury wskazujący lewym górnym rogu prostokąta docelowego.  
  
 `nDestWidth`  
 Szerokość w jednostkach logicznych, prostokąta docelowego.  
  
 `nDestHeight`  
 Wysokość w jednostkach logicznych, prostokąta docelowego.  
  
 `xSrc`  
 Logiczne współrzędną x górnego lewego rogu prostokąta źródłowego.  
  
 `ySrc`  
 Logiczne współrzędną y górnego lewego rogu prostokąta źródłowego.  
  
 `rectDest`  
 A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury wskazujący prostokąt docelowy.  
  
 `pointSrc`  
 A **punktu** struktury wskazujący lewym górnym rogu prostokąta źródłowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370) w zestawie Windows SDK.  
  
##  <a name="cimage"></a>CImage::CImage  
 Konstruuje `CImage` obiektu.  
  
```
CImage() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Po zbudowania obiektu wywołania [Utwórz](#create), [obciążenia](#load), [LoadFromResource](#loadfromresource), lub [Attach](#attach) dołączyć mapy bitowej do obiektu.  
  
 **Uwaga** w programie Visual Studio, ta klasa śledzi liczbę liczbę `CImage` obiekty utworzone. Zawsze, gdy liczba wynosić 0, funkcja **GdiplusShutdown** jest wywoływana automatycznie, aby zwolnić zasoby używane przez GDI +. Gwarantuje to, że wszelkie `CImage` obiekty utworzone bezpośrednio lub pośrednio przez biblioteki dll zawsze zostaną zniszczone poprawnie i czy **GdiplusShutdown** nie jest wywoływana z funkcji DllMain.  
  
 Za pomocą globalnej `CImage` obiektów w bibliotece DLL nie jest zalecane. Jeśli musisz użyć globalnym `CImage` obiektu w bibliotece DLL, wywołanie [CImage::ReleaseGDIPlus](#releasegdiplus) jawnie zwolnić zasoby używane przez GDI +.  
  
##  <a name="create"></a>CImage::Create  
 Tworzy `CImage` bitmap i dołączenie go do wcześniej utworzone `CImage` obiektu.  
  
```
BOOL Create(
 int nWidth,
 int nHeight,
 int nBPP,
 DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Szerokość `CImage` mapy bitowej w pikselach.  
  
 `nHeight`  
 Wysokość `CImage` mapy bitowej w pikselach. Jeśli `nHeight` jest dodatnia, mapy bitowej jest DIB dołu do góry, a jego pochodzenie lewym dolnym rogu. Jeśli `nHeight` jest ujemna, mapy bitowej jest DIB góra dół i jego pochodzenie lewym górnym rogu.  
  
 `nBPP`  
 Liczby bitów na piksel w pliku mapy bitowej. Zazwyczaj 4, 8, 16, 24 lub 32. Może mieć wartość 1 dla monochromatyczny map bitowych lub maski.  
  
 `dwFlags`  
 Określa, czy obiekt mapy bitowej kanał alfa. Może być kombinacją zero lub więcej z następujących wartości:  
  
- **createAlphaChannel** można używać tylko jeśli `nBPP` wynosi 32, i `eCompression` jest **BI_RGB**. Jeśli zostanie określona, utworzony obraz ma wartość alfa (przezroczystości) dla każdego piksela przechowywane w 4 bajtów każdego piksela (i nieużywanych w obraz 32-bitowy alfa). Ten kanał alfa automatycznie jest używana przy wywoływaniu [CImage::AlphaBlend](#alphablend).  
  
> [!NOTE]
>  W wywołaniach [CImage::Draw](#draw), obrazów za pomocą kanału alfa są automatycznie alfa przenikaniem do miejsca docelowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="createex"></a>CImage::CreateEx  
 Tworzy `CImage` bitmap i dołączenie go do wcześniej utworzone `CImage` obiektu.  
  
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
 `nWidth`  
 Szerokość `CImage` mapy bitowej w pikselach.  
  
 `nHeight`  
 Wysokość `CImage` mapy bitowej w pikselach. Jeśli `nHeight` jest dodatnia, mapy bitowej jest DIB dołu do góry, a jego pochodzenie lewym dolnym rogu. Jeśli `nHeight` jest ujemna, mapy bitowej jest DIB góra dół i jego pochodzenie lewym górnym rogu.  
  
 `nBPP`  
 Liczby bitów na piksel w pliku mapy bitowej. Zazwyczaj 4, 8, 16, 24 lub 32. Może mieć wartość 1 dla monochromatyczny map bitowych lub maski.  
  
 `eCompression`  
 Określa typ kompresji dla skompresowanej mapy bitowej dołu do góry (nie mogą być kompresowane DIBs góra dół). Może to być jedna z następujących wartości:  
  
- **BI_RGB** nieskompresowanych ma format. Określenie tej wartości podczas wywoływania metody `CImage::CreateEx` jest odpowiednikiem wywołania `CImage::Create`.  
  
- **BI_BITFIELDS** nieskompresowanych format i tabeli kolorów składa się z trzech `DWORD` maski kolor, które określają czerwony, green i odpowiednio niebieski składniki każdego piksela. Jest to prawidłowa, gdy jest używany z bpp 16 i 32-bitowymi.  
  
 *pdwBitfields*  
 Używana, tylko jeśli `eCompression` ustawiono **BI_BITFIELDS**, w przeciwnym razie musi być **NULL**. Wskaźnik do tablicy trzech `DWORD` masek bitowych, określania, które bity każdego piksela służą do czerwony, green i odpowiednio niebieski składniki koloru,. Aby uzyskać informacji na temat ograniczeń dotyczących pola bitów, zobacz [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) w zestawie Windows SDK.  
  
 `dwFlags`  
 Określa, czy obiekt mapy bitowej kanał alfa. Może być kombinacją zero lub więcej z następujących wartości:  
  
- **createAlphaChannel** można używać tylko jeśli `nBPP` wynosi 32, i `eCompression` jest **BI_RGB**. Jeśli zostanie określona, utworzony obraz ma wartość alfa (przezroczystości) dla każdego piksela przechowywane w 4 bajtów każdego piksela (i nieużywanych w obraz 32-bitowy alfa). Ten kanał alfa automatycznie jest używana przy wywoływaniu [CImage::AlphaBlend](#alphablend).  
  
    > [!NOTE]
    >  W wywołaniach [CImage::Draw](#draw), obrazów za pomocą kanału alfa są automatycznie alfa przenikaniem do miejsca docelowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** w przypadku powodzenia. W przeciwnym razie **FALSE**.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy mapę bitową 100 x 100 pikseli, za pomocą 16 bitów do kodowania każdego piksela. W pikselu 16-bitowych bity 0-3 kodowania składnika czerwony, bitów 4-7 kodowania zielony i bits 8-11 kodowania niebieski. Pozostałe 4 bity są używane.  

```cpp  
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```


##  <a name="destroy"></a>CImage::Destroy  
 Odłącza mapy bitowej z `CImage` obiektu i niszczy mapy bitowej.  
  
```
void Destroy() throw();
```  
  
##  <a name="detach"></a>CImage::Detach  
 Odłącza mapę bitową z `CImage` obiektu.  
  
```
HBITMAP Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do mapy bitowej odłączyć, lub **NULL** Jeżeli nie jest podłączone nie mapy bitowej.  
  
##  <a name="draw"></a>CImage::Draw  
 Kopiuje mapę bitową z kontekstu urządzenia źródłowego dla bieżącego kontekstu urządzenia.  
  
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
 `hDestDC`  
 Dojście do kontekstu urządzenia docelowego.  
  
 `xDest`  
 Współrzędna x, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 `yDest`  
 Współrzędna y, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 `nDestWidth`  
 Szerokość w jednostkach logicznych, prostokąta docelowego.  
  
 `nDestHeight`  
 Wysokość w jednostkach logicznych, prostokąta docelowego.  
  
 `xSrc`  
 Współrzędna x, w jednostkach logicznych, górnego lewego rogu prostokąta źródłowego.  
  
 `ySrc`  
 Współrzędna y, w jednostkach logicznych, górnego lewego rogu prostokąta źródłowego.  
  
 `nSrcWidth`  
 Szerokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `nSrcHeight`  
 Wysokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `rectDest`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, identyfikowanie miejsca docelowego.  
  
 `rectSrc`  
 Odwołanie do `RECT` struktury identyfikacji źródła.  
  
 `pointDest`  
 Odwołanie do [punktu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktura, która identyfikuje lewym górnym rogu prostokąta docelowej, w jednostkach logicznych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 **Rysuj** wykonuje tę samą operację jako [StretchBlt](#stretchblt), chyba że obraz zawiera kolor przezroczysty lub kanał alfa. W takim przypadku **rysowania** wykonuje tę samą operację jako [TransparentBlt](#transparentblt) lub [AlphaBlend](#alphablend) zgodnie z wymaganiami.  
  
 W przypadku wersji **rysowania** nie określaj prostokąta źródłowego, całego obrazu źródłowego jest ustawieniem domyślnym. Dla wersji **rysowania** nie określa rozmiar docelowy prostokąt, rozmiar obrazu źródłowego jest domyślnie i nie rozciąganie lub zmniejszanie występuje.  
  
##  <a name="getbits"></a>CImage::GetBits  
 Pobiera wskaźnik z bitowego rzeczywisty wartościami pikselu mapy bitowej.  
  
```
void* GetBits() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do buforu mapy bitowej. Jeśli mapy bitowej jest DIB dołu do góry, wskaźnik wskazuje pod koniec buforu. Jeśli mapy bitowej jest DIB góry do dołu, wskazuje wskaźnik do pierwszego bajtu buforu.  
  
### <a name="remarks"></a>Uwagi  
 Przy użyciu tego wskaźnika, wraz z wartością zwróconą przez [GetPitch](#getpitch), można zlokalizować i zmienić piksele obrazu.  
  
> [!NOTE]
>  Ta metoda obsługuje tylko map bitowych sekcji DIB; w rezultacie dostęp piksele `CImage` obiektu tak samo jak pikseli sekcji DIB. Zwrócony wskaźnik wskazuje na piksel w lokalizacji (0, 0).  
  
##  <a name="getbpp"></a>CImage::GetBPP  
 Pobiera wartość bitów na piksel.  
  
```
int GetBPP() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bitów na piksel.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość określa liczbę bitów, które definiują każdego piksela i maksymalna liczba kolorów w mapie bitowej.  
  
 Bity na piksel jest zwykle 1, 4, 8, 16, 24 lub 32. Zobacz **biBitCount** członkiem [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat tej wartości.  
  
##  <a name="getcolortable"></a>CImage::GetColorTable  
 Pobiera czerwony, zielony, niebieski wartości kolorów (RGB) z zakresu zapisów w palecie sekcji DIB.  
  
```
void GetColorTable(UINT iFirstColor,
 UINT nColors,
 RGBQUAD* prgbColors) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iFirstColor`  
 Indeks tabeli kolor pierwszego zapisu do pobrania.  
  
 `nColors`  
 Liczba wpisów w tabeli kolorów do pobrania.  
  
 `prgbColors`  
 Wskaźnik do tablicy [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) struktury tak, aby pobrać kolor tabeli wpisów.  
  
##  <a name="getdc"></a>CImage::GetDC  
 Pobiera kontekst urządzenia, który aktualnie ma do niego obraz.  
  
```
HDC GetDC() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do kontekstu urządzenia.  
  
### <a name="remarks"></a>Uwagi  
 Dla każdego wywołania `GetDC`, musi mieć kolejne wywołanie [ReleaseDC](#releasedc).  
  
##  <a name="getexporterfilterstring"></a>CImage::GetExporterFilterString  
 Wyszukuje dostępne formatów obrazów zapisywanie obrazów.  
  
```
static HRESULT GetExporterFilterString(CSimpleString& strExporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultSave,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>Parametry  
 *strExporters*  
 Odwołanie do **CSimpleString** obiektu. Zobacz **uwagi** Aby uzyskać więcej informacji.  
  
 `aguidFileTypes`  
 Tablica identyfikatorów GUID, za pomocą jednego z typów plików, w ciągu każdego elementu. W przykładzie `pszAllFilesDescription` poniżej, `aguidFileTypes`[0] jest `GUID_NULL` , a pozostałe wartości tablicy są formatów plików obrazów, które są obsługiwane przez bieżący system operacyjny.  
  
> [!NOTE]
>  Aby uzyskać pełną listę stałych, zobacz **stałe Format pliku obrazu** w zestawie Windows SDK.  
  
 `pszAllFilesDescription`  
 Jeśli ten parametr nie jest **NULL**, ciąg filtru będzie mieć jeden dodatkowy filtr na początku listy. Ten filtr ma bieżącą wartość `pszAllFilesDescription` jego opis i akceptuje pliki dowolnego rozszerzenia obsługiwane przez inne eksportera na liście.  
  
 Na przykład:  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 Ustaw flagi bitowe określające, jakie typy plików do wykluczenia z listy. Flagi dopuszczalne są:  
  
- **excludeGIF** = plików GIF wyklucza 0x01.  
  
- **excludeBMP** = 0x02 pliki wyklucza BMP (mapy bitowej systemu Windows).  
  
- **excludeEMF** = 0x04 pliki wyklucza EMF (rozszerzony metaplik).  
  
- **excludeWMF** = 0x08 wyklucza WMF (Windows Metafile) plików.  
  
- **excludeJPEG** = pliki JPEG wyklucza 0x10.  
  
- **excludePNG** = pliki PNG wyklucza 0x20.  
  
- **excludeTIFF** = 0x40 wyklucza TIFF, pliki.  
  
- **excludeIcon** = 0x80 pliki ICO wyklucza (Windows ikona).  
  
- **excludeOther** = 0x80000000 wyklucza innego typu pliku nie są wymienione powyżej.  
  
- **excludeDefaultLoad** = 0 dla obciążenia, plik wszystkie typy są domyślnie dołączone  
  
- **excludeDefaultSave** = **excludeIcon &#124; excludeEMF &#124; excludeWMF** do zapisu, te pliki są wykluczone domyślnie, ponieważ mają one zwykle specjalnych wymagań.  
  
 `chSeparator`  
 Separator używany podczas komunikacji między formatów obrazów. Zobacz **uwagi** Aby uzyskać więcej informacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
### <a name="remarks"></a>Uwagi  
 Wynikowy ciąg formatu można przekazać do Twojej MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) obiektu do udostępnienia rozszerzenia plików obrazu dostępne formaty w oknie dialogowym Zapisz plik jako.  
  
 Parametr *strExporter* ma format:  
  
 description0 plik &#124; \*.ext0 &#124; filedescription1 &#124; \*.ext1 &#124;... opis pliku  *n* &#124;\*. Roz  *n* &#124; &#124;  
  
 gdzie "&#124;" określono znaku separatora za pomocą `chSeparator`. Na przykład:  
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 Użyj ustawienia domyślne "&#124;", jeśli te parametry są przekazywane do MFC `CFileDialog` obiektu. Użyj wartości null separatora '\0', jeśli te parametry są przekazywane do wspólnego okno dialogowe Zapisz plik.  
  
##  <a name="getheight"></a>CImage::GetHeight  
 Pobiera wysokość w pikselach obrazu.  
  
```
int GetHeight() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość w pikselach obrazu.  
  
##  <a name="getimporterfilterstring"></a>CImage::GetImporterFilterString  
 Wyszukuje dostępne formatów obrazów ładowania obrazów.  
  
```
static HRESULT GetImporterFilterString(CSimpleString& strImporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultLoad,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>Parametry  
 *strImporters*  
 Odwołanie do **CSimpleString** obiektu. Zobacz **uwagi** Aby uzyskać więcej informacji.  
  
 `aguidFileTypes`  
 Tablica identyfikatorów GUID, za pomocą jednego z typów plików, w ciągu każdego elementu. W przykładzie `pszAllFilesDescription` poniżej, `aguidFileTypes`[0] jest `GUID_NULL` z pozostałych tablicy wartości są formatów plików obrazów, które są obsługiwane przez bieżący system operacyjny.  
  
> [!NOTE]
>  Aby uzyskać pełną listę stałych, zobacz **stałe Format pliku obrazu** w zestawie Windows SDK.  
  
 `pszAllFilesDescription`  
 Jeśli ten parametr nie jest **NULL**, ciąg filtru będzie mieć jeden dodatkowy filtr na początku listy. Ten filtr ma bieżącą wartość `pszAllFilesDescription` jego opis i akceptuje pliki dowolnego rozszerzenia obsługiwane przez inne eksportera na liście.  
  
 Na przykład:  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 Ustaw flagi bitowe określające, jakie typy plików do wykluczenia z listy. Flagi dopuszczalne są:  
  
- **excludeGIF** = plików GIF wyklucza 0x01.  
  
- **excludeBMP** = 0x02 pliki wyklucza BMP (mapy bitowej systemu Windows).  
  
- **excludeEMF** = 0x04 pliki wyklucza EMF (rozszerzony metaplik).  
  
- **excludeWMF** = 0x08 wyklucza WMF (Windows Metafile) plików.  
  
- **excludeJPEG** = pliki JPEG wyklucza 0x10.  
  
- **excludePNG** = pliki PNG wyklucza 0x20.  
  
- **excludeTIFF** = 0x40 wyklucza TIFF, pliki.  
  
- **excludeIcon** = 0x80 pliki ICO wyklucza (Windows ikona).  
  
- **excludeOther** = 0x80000000 wyklucza innego typu pliku nie są wymienione powyżej.  
  
- **excludeDefaultLoad** = 0 dla obciążenia, plik wszystkie typy są domyślnie dołączone  
  
- **excludeDefaultSave** = **excludeIcon &#124; excludeEMF &#124; excludeWMF** do zapisu, te pliki są wykluczone domyślnie, ponieważ mają one zwykle specjalnych wymagań.  
  
 `chSeparator`  
 Separator używany podczas komunikacji między formatów obrazów. Zobacz **uwagi** Aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 Wynikowy ciąg formatu można przekazać do Twojej MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) obiektu do udostępnienia rozszerzenia plików obrazu dostępne formaty w **Otwórz plik** okno dialogowe.  
  
 Parametr *strImporter* ma format:  
  
 description0 plik &#124; \*.ext0 &#124; filedescription1 &#124; \*.ext1 &#124;... opis pliku  *n* &#124;\*. Roz  *n* &#124; &#124;  
  
 gdzie "&#124;" określono znaku separatora za pomocą `chSeparator`. Na przykład:  
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 Użyj ustawienia domyślne "&#124;", jeśli te parametry są przekazywane do MFC `CFileDialog` obiektu. Użyj wartości null separatora '\0', jeśli te parametry są przekazywane do wspólnego **Otwórz plik** okno dialogowe.  
  
##  <a name="getmaxcolortableentries"></a>CImage::GetMaxColorTableEntries  
 Pobiera maksymalną liczbę wpisów w tabeli kolorów.  
  
```
int GetMaxColorTableEntries() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wpisów w tabeli kolorów.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje tylko DIB sekcji bitmapy.  
  
##  <a name="getpitch"></a>CImage::GetPitch  
 Pobiera wysokość obrazu.  
  
```
int GetPitch() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość obrazu. Jeśli wartość zwracana jest ujemna, mapy bitowej jest DIB dołu do góry, a jego pochodzenie jest lewym dolnym rogu. Jeśli wartość zwracana jest dodatnia, mapy bitowej jest DIB góra dół, a jego pochodzenie lewym górnym rogu.  
  
### <a name="remarks"></a>Uwagi  
 Wysokość jest odległość, w bajtach między dwa adresy pamięci, które reprezentują początku jeden wiersz mapy bitowej i początek następnego wiersza mapy bitowej. Ponieważ wysokość jest wyrażona w bajtach, wysokość obrazu pomaga określić format piksela. Wysokość mogą również obejmować więcej pamięci, zastrzeżone mapy bitowej.  
  
 Użyj `GetPitch` z [GetBits](#getbits) można znaleźć piksele obrazu.  
  
> [!NOTE]
>  Ta metoda obsługuje tylko DIB sekcji bitmapy.  
  
##  <a name="getpixel"></a>CImage::GetPixel  
 Pobiera kolor pikseli w lokalizacji określonej przez *x* i *y*.  
  
```
COLORREF GetPixel(int x,int y) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Współrzędna x piksela.  
  
 *y*  
 Współrzędna y piksela.  
  
### <a name="return-value"></a>Wartość zwracana  
 Czerwony, zielony, niebieski (RGB) wartość piksela. Jeśli spoza obszaru przycinania bieżącego piksela, jest zwracana wartość **CLR_INVALID**.  
  
##  <a name="getpixeladdress"></a>CImage::GetPixelAddress  
 Pobiera dokładny adres piksela.  
  
```
void* GetPixelAddress(int x,int y) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Współrzędna x piksela.  
  
 *y*  
 Współrzędna y piksela.  
  
### <a name="remarks"></a>Uwagi  
 Adres zależy od współrzędne piksel, wysokość mapy bitowej i bitów na piksel.  
  
 Formatów, które mają mniej niż 8 bitów na piksel ta metoda zwraca adres bajtów zawierająca piksela. Na przykład, jeśli 4 bity na piksel, formatu obrazu `GetPixelAddress` zwraca adres piksela pierwszy bajt, i należy obliczyć 2 pikseli na bajt.  
  
> [!NOTE]
>  Ta metoda obsługuje tylko DIB sekcji bitmapy.  
  
##  <a name="gettransparentcolor"></a>CImage::GetTransparentColor  
 Pobiera lokalizację indeksowanego przezroczysty kolor w palecie kolorów.  
  
```
LONG GetTransparentColor() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks kolor przezroczysty.  
  
##  <a name="getwidth"></a>CImage::GetWidth  
 Pobiera szerokość obrazu w pikselach,.  
  
```
int GetWidth() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość mapy bitowej w pikselach.  
  
##  <a name="isdibsection"></a>CImage::IsDIBSection  
 Określa, czy dołączone mapy bitowej jest sekcji DIB.  
  
```
bool IsDIBSection() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** jeśli dołączone mapy bitowej jest sekcją DIB. W przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Mapa bitowa nie jest sekcji DIB, nie można użyć następujących `CImage` metody, które obsługują tylko DIB sekcji bitmapy:  
  
- [GetBits](#getbits)  
  
- [GetColorTable](#getcolortable)  
  
- [GetMaxColorTableEntries](#getmaxcolortableentries)  
  
- [GetPitch](#getpitch)  
  
- [GetPixelAddress](#getpixeladdress)  
  
- [IsIndexed](#isindexed)  
  
- [SetColorTable](#setcolortable)  
  
##  <a name="isindexed"></a>CImage::IsIndexed  
 Określa, czy pikseli mapy bitowej są zamapowane do palety kolorów.  
  
```
bool IsIndexed() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli indeksowanego; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca **true** tylko wtedy, gdy bitmapa jest 8-bitową (256 kolorów) lub mniej.  
  
> [!NOTE]
>  Ta metoda obsługuje tylko DIB sekcji bitmapy.  
  
##  <a name="isnull"></a>CImage::IsNull  
 Określa, czy mapy bitowej jest aktualnie załadowany.  
  
```
bool IsNull() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca **True** Jeśli bitmapy nie jest aktualnie załadowany; w przeciwnym razie **False**.  
  
##  <a name="istransparencysupported"></a>CImage::IsTransparencySupported  
 Wskazuje, czy aplikacja obsługuje bitmapy przezroczyste i został skompilowany dla systemu Windows 2000 lub nowszego.  
  
```
static BOOL IsTransparencySupported() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli bieżąca platforma obsługuje przezroczystość. W przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana jest niezerowa i przezroczystość jest obsługiwana, wywołanie [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt), lub [rysowania](#draw) obsłuży kolory przezroczyste.  
  
 Jeśli aplikacja została skompilowana do użytku w systemach operacyjnych Windows 2000 lub Windows 98, ta metoda zawsze zwraca 0, nawet na nowszych systemów operacyjnych.  
  

##  <a name="load"></a>CImage::Load  
 Ładuje obraz.  
  
```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszFileName`  
 Wskaźnik do ciąg zawierający nazwę pliku obrazu do załadowania.  
  
 `pStream`  
 Wskaźnik do strumienia zawierającą nazwę pliku obrazu do załadowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
### <a name="remarks"></a>Uwagi  
 Ładuje obraz określony przez *pszFileName* lub `pStream`.  
  
 Nieprawidłowy obraz typy BMP, GIF, JPEG, PNG i TIFF.  
  
##  <a name="loadfromresource"></a>CImage::LoadFromResource  
 Ładuje obraz z `BITMAP` zasobów.  
  
```
void LoadFromResource(
 HINSTANCE hInstance,
 LPCTSTR pszResourceName) throw();

void LoadFromResource(
 HINSTANCE hInstance,
 UINT nIDResource) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Dojście do wystąpienia modułu, który zawiera obraz, który ma zostać załadowany.  
  
 `pszResourceName`  
 Wskaźnik do ciągu zawierającego nazwę zasobu zawierającego obraz, aby załadować.  
  
 `nIDResource`  
 Identyfikator zasobu do załadowania.  
  
### <a name="remarks"></a>Uwagi  
 Zasób musi być typu `BITMAP`.  
  
##  <a name="maskblt"></a>CImage::MaskBlt  
 Łączy dane kolorów mapy bitowe źródłowych i docelowych przy użyciu określona maska i rastrowe operacji.  
  
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
 `hDestDC`  
 Dojście do modułu, którego pliku wykonywalnego zawiera zasób.  
  
 `xDest`  
 Współrzędna x, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 `yDest`  
 Współrzędna y, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 `nDestWidth`  
 Szerokość w logiczne jednostki docelowej prostokąt i źródła mapy bitowej.  
  
 `nDestHeight`  
 Wysokość w logiczne jednostki docelowej prostokąt i źródła mapy bitowej.  
  
 `xSrc`  
 Logiczne współrzędną x górnego lewego rogu źródła mapy bitowej.  
  
 `ySrc`  
 Logiczne współrzędną y lewego górnego rogu źródła mapy bitowej.  
  
 `hbmMask`  
 Dojście do mapy bitowej maski monochromatyczny połączone z kolorów mapy bitowej w kontekście urządzenia źródłowego.  
  
 `xMask`  
 Przesunięcie pikseli poziome mapy bitowej maski określony przez `hbmMask` parametru.  
  
 `yMask`  
 Przesunięcie pikseli w pionie mapy bitowej maski określony przez `hbmMask` parametru.  
  
 `dwROP`  
 Określa pierwszego planu i tła kody operacji trójargumentowy rastrowe, które używa metody do sterowania kombinację danych źródłowych i docelowych. Kod operacji rastrowe tła jest przechowywany w znaczącym bajcie Word znaczących tej wartości; Kod operacji rastrowe pierwszego planu są przechowywane w mniej znaczącego bajtu Word znaczących tej wartości; word znaczącymi bitami tej wartości jest ignorowany i powinien być równy zero. Omówienie pierwszego planu i tła w kontekście tej metody, zobacz `MaskBlt` w zestawie Windows SDK. Listę typowych kody operacji rastrowe, zobacz `BitBlt` w zestawie Windows SDK.  
  
 `rectDest`  
 Odwołanie do `RECT` struktury, identyfikowanie miejsca docelowego.  
  
 `pointSrc`  
 A `POINT` struktury wskazujący lewym górnym rogu prostokąta źródłowego.  
  
 `pointMask`  
 A **punktu** struktury wskazujący lewym górnym rogu mapy bitowej maski.  
  
 `pointDest`  
 Odwołanie do **punktu** struktura, która identyfikuje lewym górnym rogu prostokąta docelowej, w jednostkach logicznych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ma zastosowanie do systemu Windows NT w wersji 4.0 i późniejsze.  
  
##  <a name="operator_hbitmap"></a>HBITMAP CImage::operator  
 Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CImage` obiektu. Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia `HBITMAP` obiektu.  
  
##  <a name="plgblt"></a>CImage::PlgBlt  
 Wykonuje przesunięcia bitowego bloku z prostokąt w kontekście urządzenia źródłowego do równoległobok kontekstu urządzenia docelowego.  
  
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
 `hDestDC`  
 Dojście do kontekstu urządzenia docelowego.  
  
 *pPoints*  
 Wskaźnik do tablicy trzech punktach logicznego miejsca identyfikujące trzy narożników równoległobok docelowego. Lewym górnym rogu prostokąta źródłowego jest zamapowane do pierwszego punktu w tej macierzy, prawym górnym rogu do drugiego w tej macierzy i lewym dolnym rogu trzeci punktu. Prawym dolnym rogu prostokąta źródłowego jest mapowana na niejawne punkt czwarty w równoległobok.  
  
 `hbmMask`  
 Dojście do opcjonalne monochromatyczny mapy bitowej używanego do zamaskowania kolory prostokąta źródłowego.  
  
 `xSrc`  
 Współrzędna x, w jednostkach logicznych, górnego lewego rogu prostokąta źródłowego.  
  
 `ySrc`  
 Współrzędna y, w jednostkach logicznych, górnego lewego rogu prostokąta źródłowego.  
  
 `nSrcWidth`  
 Szerokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `nSrcHeight`  
 Wysokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `xMask`  
 Współrzędna x lewym górnym rogu monochromatyczny mapy bitowej.  
  
 `yMask`  
 Współrzędna y lewym górnym rogu monochromatyczny mapy bitowej.  
  
 `rectSrc`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, określając współrzędne prostokąta źródłowego.  
  
 `pointMask`  
 A [punktu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktury wskazujący lewym górnym rogu mapy bitowej maski.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `hbmMask` identyfikuje prawidłowe mapy bitowej monochromatyczny, **PlgBit** nawiązywał tej mapy bitowej maski bitów danych kolor prostokąta źródła.  
  
 Ta metoda ma zastosowanie do systemu Windows NT w wersji 4.0 i późniejsze. Zobacz [PlgBlt](http://msdn.microsoft.com/library/windows/desktop/dd162804) w zestawie SDK systemu Windows, aby uzyskać szczegółowe informacje.  
  
##  <a name="releasedc"></a>CImage::ReleaseDC  
 Udostępnia kontekst urządzenia.  
  
```
void ReleaseDC() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ do kontekstu urządzenia można wybrać tylko jeden mapy bitowej w czasie, należy wywołać `ReleaseDC` dla każdego wywołania [GetDC](#getdc).  
  
##  <a name="releasegdiplus"></a>CImage::ReleaseGDIPlus  
 Zwalnia zasoby używane przez GDI +.  
  
```
void ReleaseGDIPlus() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda musi zostać wywołana, aby zwolnić zasoby przydzielone przez globalną `CImage` obiektu. Zobacz [CImage::CImage](#cimage).  
  
##  <a name="save"></a>CImage::Save  
 Zapisuje obraz do określonego obiektu stream lub pliku na dysku.  
  
```
HRESULT Save(IStream* pStream,
 REFGUID guidFileType) const throw();

HRESULT Save(LPCTSTR pszFileName,
 REFGUID guidFileType= GUID_NULL) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 Wskaźnik do obiektu COM IStream zawierające dane obrazu.  
  
 *pszFileName*  
 Wskaźnik do nazwy pliku obrazu.  
  
 `guidFileType`  
 Typ pliku do zapisania jako obrazu. Może to być jedna z następujących czynności:  
  
- **ImageFormatBMP** obrazu nieskompresowaną.  
  
- **ImageFormatPNG** skompresowanego obrazu A graficzne PNG (Portable Network).  
  
- **ImageFormatJPEG** skompresowanego obrazu A JPEG.  
  
- **ImageFormatGIF** skompresowanego obrazu A GIF.  
  
> [!NOTE]
>  Aby uzyskać pełną listę stałych, zobacz **stałe Format pliku obrazu** w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby zapisać obraz przy użyciu określonej nazwy i typu. Jeśli `guidFileType` parametru nie jest dołączana, rozszerzenie nazwy pliku będzie służyć do określenia format obrazu. Jeśli podano bez rozszerzenia, obraz zostaną zapisane w formacie BMP.  
  
##  <a name="setcolortable"></a>CImage::SetColorTable  
 Ustawia czerwony, zielony, niebieski () wartości kolorów RGB dla zakresu zapisów w palecie sekcji DIB.  
  
```
void SetColorTable(
  UINT iFirstColor, 
  UINT nColors,
  const RGBQUAD* prgbColors) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iFirstColor`  
 Indeks tabeli koloru pierwszego zapisu do ustawienia.  
  
 `nColors`  
 Liczba wpisów w tabeli kolorów można ustawić.  
  
 `prgbColors`  
 Wskaźnik do tablicy [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) struktury tak, aby ustawić kolor tabeli wpisów.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje tylko DIB sekcji bitmapy.  
  
##  <a name="setpixel"></a>CImage::SetPixel  
 Ustawia kolor piksel w danej lokalizacji w pliku mapy bitowej.  
  
```
void SetPixel(int x, int y, COLORREF color) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Lokalizacja poziome pikseli, aby ustawić.  
  
 *y*  
 Położenie w pionie piksela, aby ustawić.  
  
 `color`  
 Kolor, do którego można ustawić piksela.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda kończy się niepowodzeniem, jeśli piksela koordynuje znajdują się poza region wybrany wycinka.  
  
##  <a name="setpixelindexed"></a>CImage::SetPixelIndexed  
 Ustawia kolor pikseli na kolor znajdujący się w `iIndex` palety kolorów.  
  
```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Lokalizacja poziome pikseli, aby ustawić.  
  
 *y*  
 Położenie w pionie piksela, aby ustawić.  
  
 `iIndex`  
 Indeks kolorów palety kolorów.  
  
##  <a name="setpixelrgb"></a>CImage::SetPixelRGB  
 Ustawia piksel w lokalizacjach określonych przez *x* i *y* kolory wskazywanym przez *r*, *g*, i *b*, na czerwono zielone, niebieski obrazu (RGB).  
  
```
void SetPixelRGB(  
 int x,
 int y,
 BYTE r,
 BYTE g,
 BYTE b) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Lokalizacja poziome pikseli, aby ustawić.  
  
 *y*  
 Położenie w pionie piksela, aby ustawić.  
  
 *r*  
 Intensywność kolor czerwony.  
  
 *k*  
 Intensywność kolor zielony.  
  
 *b*  
 Intensywność kolor niebieski.  
  
### <a name="remarks"></a>Uwagi  
 Każdy parametry czerwonemu, zielonemu i niebieska są reprezentowane przez liczbą z zakresu od 0 do 255. Jeśli wszystkie trzy parametry można ustawić na zero, łączna kolor wynikowy będzie czarny. Jeśli ustawisz wszystkie trzy parametry do 255 Scalonej wynikowy kolor jest białe.  
  
##  <a name="settransparentcolor"></a>CImage::SetTransparentColor  
 Określa kolor w danej lokalizacji indeksowanych jako przezroczysty.  
  
```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *iTransparentColor*  
 Indeks w paletę kolorów koloru, aby ustawić do przezroczysty. Jeśli wartość-1, nie koloru zostanie ustawiona wartość przezroczysty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks koloru wcześniej ustawić jako przezroczysty.  
  
##  <a name="stretchblt"></a>CImage::StretchBlt  
 Kopiuje mapę bitową z kontekstu urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.  
  
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
 `hDestDC`  
 Dojście do kontekstu urządzenia docelowego.  
  
 `xDest`  
 Współrzędna x, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 `yDest`  
 Współrzędna y, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 `nDestWidth`  
 Szerokość w jednostkach logicznych, prostokąta docelowego.  
  
 `nDestHeight`  
 Wysokość w jednostkach logicznych, prostokąta docelowego.  
  
 `dwROP`  
 Operacja rastrowe do wykonania. Kody operacji rastrowe zdefiniować dokładnie sposób łączenia (zgodnie z definicją w aktualnie wybranej pędzla) bitów źródłowego, docelowego i wzorzec do miejsca docelowego. Zobacz [BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370) w zestawie Windows SDK dla listy innych kodów operacji rastrowe i ich opisy.  
  
 `rectDest`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, identyfikowanie miejsca docelowego.  
  
 `xSrc`  
 Współrzędna x, w jednostkach logicznych, górnego lewego rogu prostokąta źródłowego.  
  
 `ySrc`  
 Współrzędna y, w jednostkach logicznych, górnego lewego rogu prostokąta źródłowego.  
  
 `nSrcWidth`  
 Szerokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `nSrcHeight`  
 Wysokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `rectSrc`  
 Odwołanie do `RECT` struktury identyfikacji źródła.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [StretchBlt](http://msdn.microsoft.com/library/windows/desktop/dd145120) w zestawie Windows SDK.  
  
##  <a name="transparentblt"></a>CImage::TransparentBlt  
 Kopiuje mapę bitową z kontekstu urządzenia źródłowego dla tego bieżącego kontekstu urządzenia.  
  
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
 `hDestDC`  
 Dojście do kontekstu urządzenia docelowego.  
  
 `xDest`  
 Współrzędna x, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 `yDest`  
 Współrzędna y, w jednostkach logicznych lewym górnym rogu prostokąta docelowego.  
  
 `nDestWidth`  
 Szerokość w jednostkach logicznych, prostokąta docelowego.  
  
 `nDestHeight`  
 Wysokość w jednostkach logicznych, prostokąta docelowego.  
  
 *crTransparent*  
 Kolorów w mapie bitowej źródła można traktować jako przezroczysty. Domyślnie **CLR_INVALID**, wskazujący, że należy używać kolor aktualnie ustawione jako przezroczysty kolor obrazu.  
  
 `rectDest`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, identyfikowanie miejsca docelowego.  
  
 `xSrc`  
 Współrzędna x, w jednostkach logicznych, górnego lewego rogu prostokąta źródłowego.  
  
 `ySrc`  
 Współrzędna y, w jednostkach logicznych, górnego lewego rogu prostokąta źródłowego.  
  
 `nSrcWidth`  
 Szerokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `nSrcHeight`  
 Wysokość w jednostkach logicznych, prostokąta źródłowego.  
  
 `rectSrc`  
 Odwołanie do `RECT` struktury identyfikacji źródła.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** w przypadku powodzenia, w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 `TransparentBlt`jest obsługiwana dla mapy bitowe źródła 4 bitów na piksel i 8 bitów na piksel. Użyj [CImage::AlphaBlend](#alphablend) do określenia map bitowych 32 bity na piksel przezroczystości.  
  
  
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
 [Przykładowe MMXSwarm](../../visual-cpp-samples.md)   
 [Przykładowe SimpleImage](../../visual-cpp-samples.md)   
 [Map bitowych niezależnych od urządzenia](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   
 [Składniki COM pulpitu ATL](../../atl/atl-com-desktop-components.md) [map bitowych niezależnych od urządzenia](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   









