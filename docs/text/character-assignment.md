---
title: Znak przypisania | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e403a619fc4c900aca51503862ff8f9dc315c2a3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="character-assignment"></a>Przypisanie znaku
Rozważmy następujący przykład, w którym `while` pętli skanował ciąg, kopiowanie wszystkie znaki oprócz "X" w innym ciągu:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
        *sz1++ = *sz2++;  
    else  
        sz2++;  
}  
```  
  
 Kod kopiuje bajtów w `sz2` w lokalizacji wskazywanej przez `sz1`, następnie zwiększa `sz1` do odbierania następny bajt. Jeśli jednak następny znak w `sz2` jest znaków dwubajtowych, przypisanie do `sz1` kopiuje tylko pierwszy bajt. W poniższym kodzie użyto przenośnych funkcja bezpiecznie skopiować znak, a inny zwiększyć `sz1` i `sz2` prawidłowo:  
  
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