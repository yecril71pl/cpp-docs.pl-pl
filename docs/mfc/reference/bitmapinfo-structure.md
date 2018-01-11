---
title: Struktura BITMAPINFO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BITMAPINFO
dev_langs: C++
helpviewer_keywords: BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9d704fec4a6ae0a95bd393b4a7fffa24884711e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bitmapinfo-structure"></a>Struktura BITMAPINFO
`BITMAPINFO` Definiuje strukturę, wymiarów i informacji o kolorze do mapy bitowej systemu Windows niezależnych od urządzenia (DIB).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagBITMAPINFO {  
    BITMAPINFOHEADER bmiHeader;  
    RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### <a name="parameters"></a>Parametry  
 `bmiHeader`  
 Określa [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) struktury, który zawiera informacje o wymiary i kolor format mapy bitowej niezależnych od urządzenia.  
  
 `bmiColors`  
 Określa tablicę [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) lub `DWORD` typy danych, które definiują kolorów w mapie bitowej.  
  
## <a name="remarks"></a>Uwagi  
 Mapy bitowej niezależnych od urządzenia składa się z dwóch części: `BITMAPINFO` strukturę, która opisuje wymiarów i kolorów mapy bitowej i tablicę bajtów, które określają pikseli w pliku mapy bitowej. Usługa bits w tablicy są pakowane, ale każdy wiersz skanowania musi być uzupełniana zerami kończy się z `LONG` granic. Gdy wysokość jest dodatnia, mapy bitowej pochodzi z lewym dolnym rogu. Jeśli wysokość jest ujemna, pochodzi lewym górnym rogu.  
  
 A *spakowana mapy bitowej* jest mapą bitową, w którym poniższą tablicy bajtów `BITMAPINFO` struktury. Spakowana map bitowych odwołuje się jednego wskaźnika.  
  
 Aby uzyskać więcej informacji na temat `BITMAPINFO` struktury i odpowiednie wartości dla elementów członkowskich `BITMAPINFOHEADER` i `RGBQUAD` struktury, zobacz następujące tematy w dokumentacji zestawu SDK systemu Windows.  
  
- [Struktura BITMAPINFO](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
- [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) — struktura  
  
- [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) — struktura  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)

