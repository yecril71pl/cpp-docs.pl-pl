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
ms.openlocfilehash: bbc64aad0d65c0430ad23b96f635be8fe2b396e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357041"
---
# <a name="gray-and-dithered-bitmap-functions"></a>Funkcje szarych i symulowanych map bitowych

**Funkcje szarej mapy bitowej**

MFC udostępnia dwie funkcje dając bitmapy wygląd formantu wyłączone.

![Porównanie wersji szarych i oryginalnych ikon](../../mfc/reference/media/vcgraybitmap.gif "Porównanie wersji szarych i oryginalnych ikon")

|||
|-|-|
|[AfxDrawGrayBitmapa](#afxdrawgraybitmap)|Rysuje szarą wersję mapy bitowej.|
|[AfxGetGrayBitmap (Mapa AfxGetGrayBitmap)](#afxgetgraybitmap)|Kopiuje szarą wersję mapy bitowej.|

**Funkcje roztrząsanych bitmap**

MFC udostępnia również dwie funkcje zastępowania tła mapy bitowej wzorem roztrząsanym.

![Porównanie wersji z roztrząsanym i oryginalnymi ikonami](../../mfc/reference/media/vcditheredbitmap.gif "Porównanie wersji z roztrząsanym i oryginalnymi ikonami")

|||
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|Rysuje mapę bitową z roztrząsanym tłem.|
|[AfxGetDitheredBitmapa](#afxgetditheredbitmap)|Kopiuje mapę bitową z roztrząsanym tłem.|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a>AfxDrawGrayBitmapa

Rysuje szarą wersję mapy bitowej.

```
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje docelowy kontroler domeny.

*X*<br/>
Docelowa współrzędna x.

*Y*<br/>
Cel y-współrzędne.

*Rsrc*<br/>
Źródłowa mapa bitowa.

*crBackground (na terenie zgieł*<br/>
Nowy kolor tła (zazwyczaj szary, na przykład COLOR_MENU).

### <a name="remarks"></a>Uwagi

Mapa bitowa `AfxDrawGrayBitmap` narysowana z będzie miała wygląd wyłączonego formantu.

![Porównanie wersji szarych i oryginalnych ikon](../../mfc/reference/media/vcgraybitmap.gif "Porównanie wersji szarych i oryginalnych ikon")

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a>AfxGetGrayBitmap (Mapa AfxGetGrayBitmap)

Kopiuje szarą wersję mapy bitowej.

```
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parametry

*Rsrc*<br/>
Źródłowa mapa bitowa.

*pDest (właśc.*<br/>
Docelowa mapa bitowa.

*crBackground (na terenie zgieł*<br/>
Nowy kolor tła (zazwyczaj szary, na przykład COLOR_MENU).

### <a name="remarks"></a>Uwagi

Mapa bitowa skopiowana z `AfxGetGrayBitmap` będzie miała wygląd wyłączonego formantu.

![Porównanie wersji szarych i oryginalnych ikon](../../mfc/reference/media/vcgraybitmap.gif "Porównanie wersji szarych i oryginalnych ikon")

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a>AfxDrawDitheredBitmap

Rysuje mapę bitową, zastępując jej tło wzorem roztrząsanym (kontrolerem).

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

*Pdc*<br/>
Wskazuje docelowy kontroler domeny.

*X*<br/>
Docelowa współrzędna x.

*Y*<br/>
Cel y-współrzędne.

*Rsrc*<br/>
Źródłowa mapa bitowa.

*cr1*<br/>
Jeden z dwóch kolorów roztrząsać, zazwyczaj biały.

*cr2*<br/>
Drugi kolor roztrząsać, zazwyczaj jasnoszary (COLOR_MENU).

### <a name="remarks"></a>Uwagi

Źródłowna mapa bitowa jest rysowana na docelowym kontrolerze domeny z dwukolorowym wzorem w kratkę *(cr1* i *cr2),* zastępującym tło mapy bitowej. Tło źródłowej mapy bitowej jest definiowane jako jej białe piksele i wszystkie piksele pasujące do koloru piksela w lewym górnym rogu mapy bitowej.

![Porównanie wersji z roztrząsanym i oryginalnymi ikonami](../../mfc/reference/media/vcditheredbitmap.gif "Porównanie wersji z roztrząsanym i oryginalnymi ikonami")

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a>AfxGetDitheredBitmapa

Kopiuje mapę bitową, zastępując jej tło wzorem roztrząsanym (kontrolerem).

```
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parametry

*Rsrc*<br/>
Źródłowa mapa bitowa.

*pDest (właśc.*<br/>
Docelowa mapa bitowa.

*cr1*<br/>
Jeden z dwóch kolorów roztrząsać, zazwyczaj biały.

*cr2*<br/>
Drugi kolor roztrząsać, zazwyczaj jasnoszary (COLOR_MENU).

### <a name="remarks"></a>Uwagi

Źródłowna mapa bitowa jest kopiowana do docelowej mapy bitowej z dwukolorowym wzorem w kratkę *(cr1* i *cr2),* zastępującym tło źródłowej mapy bitowej. Tło źródłowej mapy bitowej jest definiowane jako jej białe piksele i wszystkie piksele pasujące do koloru piksela w lewym górnym rogu mapy bitowej.

![Porównanie wersji z roztrząsanym i oryginalnymi ikonami](../../mfc/reference/media/vcditheredbitmap.gif "mapa vcditheredbitmap")

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
