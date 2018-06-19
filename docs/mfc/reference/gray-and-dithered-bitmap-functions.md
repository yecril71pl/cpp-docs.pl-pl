---
title: Funkcje szarych i symulowanych map bitowych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: de887cdbe80642925bc935eb48726a59850f6f96
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375177"
---
# <a name="gray-and-dithered-bitmap-functions"></a>Funkcje szarych i symulowanych map bitowych
**Funkcje szarych map bitowych**  
  
 MFC oferuje dwie funkcje przyznawania wyglądu wyłączonego formantu mapy bitowej.  
  
 ![Porównanie wersji ikony szarego a wersją z oryginalnego](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
|||  
|-|-|  
|[Afxdrawgraybitmap —](#afxdrawgraybitmap)|Rysuje szarego wersji mapy bitowej.|  
|[Afxgetgraybitmap —](#afxgetgraybitmap)|Kopiuje szarego wersji mapy bitowej.|  
  
 **Funkcje symulowanych map bitowych**  
  
 MFC udostępnia dwie funkcje dla zastąpienia tła mapy bitowej symulowanych wzorca.  
  
 ![Porównanie wersji ikony symulowanych a wersją z oryginalnego](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
|||  
|-|-|  
|[Afxdrawditheredbitmap —](#afxdrawditheredbitmap)|Rysuje mapy bitowej z symulowanych tła.|  
|[Afxgetditheredbitmap —](#afxgetditheredbitmap)|Kopiuje mapy bitowej z symulowanych tła.|  
  
##  <a name="afxdrawgraybitmap"></a>  Afxdrawgraybitmap —  
 Rysuje szarego wersji mapy bitowej.  
  
```   
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Punkty do docelowego kontrolera domeny.  
  
 *x*  
 Współrzędna x docelowego.  
  
 *y*  
 Współrzędna y docelowego.  
  
 `rSrc`  
 Źródła mapy bitowej.  
  
 `crBackground`  
 Na nowy kolor tła (zazwyczaj szary, takie jak COLOR_MENU).  
  
### <a name="remarks"></a>Uwagi  
 Mapy bitowej narysowany `AfxDrawGrayBitmap` ma wygląd wyłączonego formantu.  
  
 ![Porównanie wersji ikony szarego a wersją z oryginalnego](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  

##  <a name="afxgetgraybitmap"></a>  Afxgetgraybitmap —  
 Kopiuje szarego wersji mapy bitowej.  
  
```   
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Źródła mapy bitowej.  
  
 `pDest`  
 Docelowy mapy bitowej.  
  
 `crBackground`  
 Na nowy kolor tła (zazwyczaj szary, takie jak COLOR_MENU).  
  
### <a name="remarks"></a>Uwagi  
 Mapy bitowej skopiowany z `AfxGetGrayBitmap` ma wygląd wyłączonego formantu.  
  
 ![Porównanie wersji ikony szarego a wersją z oryginalnego](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="afxdrawditheredbitmap"></a>  Afxdrawditheredbitmap —  
 Rysuje mapy bitowej, zastępując tła wzorzec symulowanych (sprawdzania).  
  
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
 `pDC`  
 Punkty do docelowego kontrolera domeny.  
  
 *x*  
 Współrzędna x docelowego.  
  
 *y*  
 Współrzędna y docelowego.  
  
 `rSrc`  
 Źródła mapy bitowej.  
  
 `cr1`  
 Jeden z dwóch symulacji kolorów, zwykle białe.  
  
 `cr2`  
 Inne symulacji kolor, zwykle światła szary (COLOR_MENU).  
  
### <a name="remarks"></a>Uwagi  
 Źródła mapy bitowej jest rysowana na docelowym kontrolerze domeny z dwóch kolorów ( `cr1` i `cr2`) szachownicą wzorów tła mapy bitowej. Tło źródła mapy bitowej jest zdefiniowany jako białe pikseli i wszystkie piksele uzgadniania kolorów pikseli w lewym górnym rogu mapy bitowej.  
  
 ![Porównanie wersji ikony symulowanych a wersją z oryginalnego](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  


##  <a name="afxgetditheredbitmap"></a>  Afxgetditheredbitmap —  
 Kopiuje mapy bitowej, zastępując tła wzorzec symulowanych (sprawdzania).  
  
```   
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Źródła mapy bitowej.  
  
 `pDest`  
 Docelowy mapy bitowej.  
  
 `cr1`  
 Jeden z dwóch symulacji kolorów, zwykle białe.  
  
 `cr2`  
 Inne symulacji kolor, zwykle światła szary (COLOR_MENU).  
  
### <a name="remarks"></a>Uwagi  
 Źródła mapy bitowej jest kopiowany do docelowej mapy bitowej z dwóch kolorów ( `cr1` i `cr2`) szachownicą wzorów tła mapy bitowej źródła. Tło źródła mapy bitowej jest zdefiniowany jako białe pikseli i wszystkie piksele uzgadniania kolorów pikseli w lewym górnym rogu mapy bitowej.  
  
 ![Porównanie wersji ikony symulowanych a wersją z oryginalnego](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
