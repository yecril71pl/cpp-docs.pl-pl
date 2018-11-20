---
title: Funkcje szarych i symulowanych map bitowych
ms.date: 11/19/2018
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: 7e1d4bd0e851a14680a46d7d6ae79dcf4bd190e4
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176734"
---
# <a name="gray-and-dithered-bitmap-functions"></a>Funkcje szarych i symulowanych map bitowych

**Szara funkcje**

Biblioteka MFC zawiera dwie funkcje do udzielania mapy bitowej wyglądu formantu wyłączone.

![Porównanie wersji oryginalnego i symulowanych map bitowych ikonę](../../mfc/reference/media/vcgraybitmap.gif "Porównanie wersji ikonę oryginalnego i symulowanych map bitowych")

|||
|-|-|
|[Afxdrawgraybitmap —](#afxdrawgraybitmap)|Rysuje szare wersję mapy bitowej.|
|[Afxgetgraybitmap —](#afxgetgraybitmap)|Kopiuje szarego wersję mapy bitowej.|

**Funkcje szarych mapy bitowej**

MFC udostępnia także dwie funkcje zastępując tła mapy bitowej szarych wzorca.

![Porównanie wersji ikonę szarych a wersją z oryginalnego](../../mfc/reference/media/vcditheredbitmap.gif "Porównanie wersji szarych a wersją z oryginalnego ikony")

|||
|-|-|
|[Afxdrawditheredbitmap —](#afxdrawditheredbitmap)|Rysuje mapę bitową z szarych tłem.|
|[Afxgetditheredbitmap —](#afxgetditheredbitmap)|Kopiuje mapę bitową z szarych tłem.|

##  <a name="afxdrawgraybitmap"></a>  Afxdrawgraybitmap —

Rysuje szare wersję mapy bitowej.

```
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskazuje docelowy kontroler domeny.

*x*<br/>
Współrzędna x docelowego.

*y*<br/>
Współrzędna y docelowego.

*rSrc*<br/>
Źródłową mapę bitową.

*crBackground*<br/>
Nowy kolor tła (zazwyczaj szary, takie jak COLOR_MENU).

### <a name="remarks"></a>Uwagi

Mapę bitową z `AfxDrawGrayBitmap` będzie miał wyglądu formantu wyłączone.

![Porównanie wersji oryginalnego i symulowanych map bitowych ikonę](../../mfc/reference/media/vcgraybitmap.gif "Porównanie wersji ikonę oryginalnego i symulowanych map bitowych")

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="afxgetgraybitmap"></a>  Afxgetgraybitmap —

Kopiuje szarego wersję mapy bitowej.

```
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Źródłową mapę bitową.

*pDest*<br/>
Docelową mapę bitową.

*crBackground*<br/>
Nowy kolor tła (zazwyczaj szary, takie jak COLOR_MENU).

### <a name="remarks"></a>Uwagi

Skopiowany z mapy bitowej `AfxGetGrayBitmap` będzie miał wyglądu formantu wyłączone.

![Porównanie wersji oryginalnego i symulowanych map bitowych ikonę](../../mfc/reference/media/vcgraybitmap.gif "Porównanie wersji ikonę oryginalnego i symulowanych map bitowych")

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="afxdrawditheredbitmap"></a>  Afxdrawditheredbitmap —

Rysuje mapy bitowej, zastępując tłem wzorzec szarych (sprawdzanie).

```
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskazuje docelowy kontroler domeny.

*x*<br/>
Współrzędna x docelowego.

*y*<br/>
Współrzędna y docelowego.

*rSrc*<br/>
Źródłową mapę bitową.

*cr1*<br/>
Jedną z dwóch symulowania kolorów, zwykle białe.

*cr2*<br/>
Inne symulacji kolor, zwykle światła szary (COLOR_MENU).

### <a name="remarks"></a>Uwagi

Źródłową mapę bitową jest rysowana na docelowy kontroler domeny z dwóch kolorów (*cr1* i *cr2*) szachownicą wzorzec, zastępując tła mapy bitowej. Tło źródłową mapę bitową jest zdefiniowany jako jego białe pikseli i wszystkie piksele dopasowanie koloru piksela w lewym górnym rogu mapy bitowej.

![Porównanie wersji ikonę szarych a wersją z oryginalnego](../../mfc/reference/media/vcditheredbitmap.gif "Porównanie wersji szarych a wersją z oryginalnego ikony")

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="afxgetditheredbitmap"></a>  Afxgetditheredbitmap —

Kopiuje mapę bitową, zastępując tłem wzorzec szarych (sprawdzanie).

```
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Źródłową mapę bitową.

*pDest*<br/>
Docelową mapę bitową.

*cr1*<br/>
Jedną z dwóch symulowania kolorów, zwykle białe.

*cr2*<br/>
Inne symulacji kolor, zwykle światła szary (COLOR_MENU).

### <a name="remarks"></a>Uwagi

Źródłową mapę bitową jest kopiowany do docelowej mapy bitowej przy użyciu dwóch kolorów (*cr1* i *cr2*) szachownicą wzorzec, zastępując tła źródłową mapę bitową. Tło źródłową mapę bitową jest zdefiniowany jako jego białe pikseli i wszystkie piksele dopasowanie koloru piksela w lewym górnym rogu mapy bitowej.

![Porównanie wersji ikonę szarych a wersją z oryginalnego](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
