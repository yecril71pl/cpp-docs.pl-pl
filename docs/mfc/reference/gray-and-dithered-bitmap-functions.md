---
title: Funkcje szarych i | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
dev_langs:
- C++
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46a1607b0d69be21e38cace117ec2c0e248827be
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339400"
---
# <a name="gray-and-dithered-bitmap-functions"></a>Funkcje szarych i symulowanych map bitowych
**Szara funkcje**  
  
 Biblioteka MFC zawiera dwie funkcje do udzielania mapy bitowej wyglądu formantu wyłączone.  
  
 ![Porównanie wersji oryginalnego i symulowanych map bitowych ikonę](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
|||  
|-|-|  
|[Afxdrawgraybitmap —](#afxdrawgraybitmap)|Rysuje szare wersję mapy bitowej.|  
|[Afxgetgraybitmap —](#afxgetgraybitmap)|Kopiuje szarego wersję mapy bitowej.|  
  
 **Funkcje szarych mapy bitowej**  
  
 MFC udostępnia także dwie funkcje zastępując tła mapy bitowej szarych wzorca.  
  
 ![Porównanie wersji ikonę szarych a wersją z oryginalnego](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
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
 *podstawowego kontrolera domeny*  
 Wskazuje docelowy kontroler domeny.  
  
 *x*  
 Współrzędna x docelowego.  
  
 *y*  
 Współrzędna y docelowego.  
  
 *rSrc*  
 Źródłową mapę bitową.  
  
 *crBackground*  
 Nowy kolor tła (zazwyczaj szary, takie jak COLOR_MENU).  
  
### <a name="remarks"></a>Uwagi  
 Mapę bitową z `AfxDrawGrayBitmap` będzie miał wyglądu formantu wyłączone.  
  
 ![Porównanie wersji oryginalnego i symulowanych map bitowych ikonę](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
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
 *rSrc*  
 Źródłową mapę bitową.  
  
 *pDest*  
 Docelową mapę bitową.  
  
 *crBackground*  
 Nowy kolor tła (zazwyczaj szary, takie jak COLOR_MENU).  
  
### <a name="remarks"></a>Uwagi  
 Skopiowany z mapy bitowej `AfxGetGrayBitmap` będzie miał wyglądu formantu wyłączone.  
  
 ![Porównanie wersji oryginalnego i symulowanych map bitowych ikonę](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
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
 *podstawowego kontrolera domeny*  
 Wskazuje docelowy kontroler domeny.  
  
 *x*  
 Współrzędna x docelowego.  
  
 *y*  
 Współrzędna y docelowego.  
  
 *rSrc*  
 Źródłową mapę bitową.  
  
 *cr1*  
 Jedną z dwóch symulowania kolorów, zwykle białe.  
  
 *cr2*  
 Inne symulacji kolor, zwykle światła szary (COLOR_MENU).  
  
### <a name="remarks"></a>Uwagi  
 Źródłową mapę bitową jest rysowana na docelowy kontroler domeny z dwóch kolorów (*cr1* i *cr2*) szachownicą wzorzec, zastępując tła mapy bitowej. Tło źródłową mapę bitową jest zdefiniowany jako jego białe pikseli i wszystkie piksele dopasowanie koloru piksela w lewym górnym rogu mapy bitowej.  
  
 ![Porównanie wersji ikonę szarych a wersją z oryginalnego](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
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
 *rSrc*  
 Źródłową mapę bitową.  
  
 *pDest*  
 Docelową mapę bitową.  
  
 *cr1*  
 Jedną z dwóch symulowania kolorów, zwykle białe.  
  
 *cr2*  
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
