---
title: Struktura BITMAP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAP
dev_langs:
- C++
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a60e4af31ba5da23f399f86175ed4fcf1e4ec14
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950307"
---
# <a name="bitmap-structure"></a>Struktura BITMAP
**Mapy BITOWEJ** struktury określa wysokość, szerokość, format koloru i wartości bitowe logiczne mapy bitowej **.**  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagBITMAP {  /* bm */  
    int bmType;  
    int bmWidth;  
    int bmHeight;  
    int bmWidthBytes;  
    BYTE bmPlanes;  
    BYTE bmBitsPixel;  
    LPVOID bmBits;  
} BITMAP;  
```  
  
#### <a name="parameters"></a>Parametry  
 *bmType*  
 Określa typ mapy bitowej. W przypadku logicznych map bitowych ten element członkowski musi mieć wartość 0.  
  
 *bmWidth*  
 Określa szerokość mapy bitowej w pikselach. Szerokość musi być większa od 0.  
  
 *bmHeight*  
 Określa wysokość mapy bitowej w wierszach rastrowych. Wysokość musi być większa od 0.  
  
 *bmWidthBytes*  
 Określa liczbę bajtów w każdym wierszu rastrowym. Ta wartość musi być liczbą parzystą, ponieważ graficzny interfejs urządzenia (GDI) zakłada, że wartości bitowe mapy bitowej tworzą tablicę wartości całkowitych (2-bajtowych). Innymi słowy *bmWidthBytes* \* 8 musi być dalej wielokrotnością 16 większa lub równa wartości uzyskać po *bmWidth* elementu członkowskiego jest mnożona przez *bmBitsPixel*  elementu członkowskiego.  
  
 *bmPlanes*  
 Określa liczbę płaszczyzn kolorów w mapie bitowej.  
  
 *bmBitsPixel*  
 Określa liczbę bitów sąsiadujących kolorów na każdej płaszczyźnie niezbędnej do zdefiniowania piksela.  
  
 *bmBits*  
 Wskazuje lokalizację wartości bitowych mapy bitowej. *BmBits* element członkowski musi być długi wskaźnika do tablicy wartości 1-bajtowego.  
  
## <a name="remarks"></a>Uwagi  
 Obecnie są stosowane dwa formaty map bitowych: monochromatyczne i kolorowe. Mapa bitowa monochromatyczna używa formatu 1-bitowego 1-płaszczyznowego. Każde skanowanie jest wielokrotnością 16 bitów.  
  
 Skanowania są zorganizowane w następujący sposób dla monochromatyczny mapy bitowej wysokości *n*:  
  
 `Scan 0`  
  
 `Scan 1`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 `Scan n-2`  
  
 `Scan n-1`  
  
 Piksele na urządzeniu monochromatycznym są czarne lub białe. Jeśli odnośny bit w mapie bitowej ma wartość 1, piksel jest włączony (biały). Gdy odnośny bit w mapie bitowej ma wartość 0, piksel jest wyłączony (czarny).  
  
 Wszystkie urządzenia obsługują bitmap **RC_BITBLT** w ustawiony bit **RASTERCAPS** indeks [CDC::GetDeviceCaps](../../mfc/reference/cdc-class.md#getdevicecaps) funkcję elementu członkowskiego.  
  
 Każde urządzenie ma własny unikatowy format koloru. Aby przenieść mapę bitową z jednego urządzenia do innego, użyj [GetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd144879) i [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) funkcje systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
