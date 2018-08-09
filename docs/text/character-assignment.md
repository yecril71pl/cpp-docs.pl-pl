---
title: Przypisania znaków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 084cfd69a3742db10e09e9d97974a0666fa31a47
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010415"
---
# <a name="character-assignment"></a>Przypisanie znaku
Rozważmy następujący przykład, w którym **podczas** pętli skanuje ciągu, kopiując wszystkie znaki z wyjątkiem "X" do innego ciągu:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
        *sz1++ = *sz2++;  
    else  
        sz2++;  
}  
```  
  
 Kod kopiuje bajt `sz2` w lokalizacji wskazywanej przez `sz1`, następnie zwiększa `sz1` do odbierania następny bajt. Ale jeśli następny znak w `sz2` jest znak dwubajtowy, przypisanie do `sz1` kopiuje tylko pierwszy bajt. W poniższym kodzie użyto funkcji przenośny, aby bezpiecznie skopiować znak i innej, aby zwiększyć `sz1` i `sz2` prawidłowo:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
    {  
        _mbscpy_s( sz1, 1, sz2 );  
        sz1 = _mbsinc( sz1 );  
        sz2 = _mbsinc( sz2 );  
    }  
    else  
        sz2 = _mbsinc( sz2 );  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)   
 [Porównywanie znaków](../text/character-comparison.md)