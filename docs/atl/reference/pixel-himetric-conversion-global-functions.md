---
title: Funkcje globalne konwersji pikseli HIMETRIC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
dev_langs: C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9d670d667345c233fc499cda42194dfafa185dfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pixelhimetric-conversion-global-functions"></a>Funkcje globalne pikseli/HIMETRIC konwersji
Funkcje te zapewniają obsługę konwertowanie do i z pikseli i HIMETRIC jednostki.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
|||  
|-|-|  
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Konwertuje HIMETRIC jednostek (każdej jednostki 0,01 milimetra) pikseli.|  
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Konwertuje pikseli jednostki HIMETRIC (każda jednostka jest 0,01 milimetra).|  
  
##  <a name="atlhimetrictopixel"></a>AtlHiMetricToPixel  
 Konwertuje rozmiar obiektu w jednostkach HIMETRIC (każda jednostka to 0,01 milimetra) na rozmiar w pikselach na ekranie urządzenia.  
  
 
```
extern void AtlHiMetricToPixel(
  const SIZEL* lpSizeInHiMetric, 
  LPSIZEL lpSizeInPix);
```  
  
### <a name="parameters"></a>Parametry  
 `lpSizeInHiMetric`  
 [in] Wskaźnik do rozmiar obiektu w HIMETRIC jednostki.  
  
 `lpSizeInPix`  
 [out] Wskaźnik, na którym ma zostać zwrócone rozmiar obiektu w pikselach.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="atlpixeltohimetric"></a>AtlPixelToHiMetric  
 Konwertuje rozmiar obiektu w pikselach na ekranie urządzenia na rozmiar w jednostkach HIMETRIC (każda jednostka to 0,01 milimetra).  
  
```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix, 
    LPSIZEL lpSizeInHiMetric);
```  
  
### <a name="parameters"></a>Parametry  
 `lpSizeInPix`  
 [in] Wskaźnik do obiektu rozmiar w pikselach.  
  
 `lpSizeInHiMetric`  
 [out] Wskaźnik do przypadku rozmiar obiektu w jednostkach HIMETRIC ma zostać zwrócona.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  

## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
