---
title: Przepełnienie buforu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 13d01460e7ed9cb95d92303d82ea136803737331
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854655"
---
# <a name="buffer-overflow"></a>Przepełnienie buforu
Różne rozmiary znaków może spowodować problemy, po wprowadzeniu znaków w buforze. Należy rozważyć następujący kod, który kopiuje znaków z ciągu, `sz`, w buforze, `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 Pytanie jest: został ostatniego bajtu skopiowane bajtu? Następujące nie rozwiązuje problem, ponieważ potencjalnie może się przelewać buforu:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 `_mbccpy` Wywołania próbuje wykonać poprawną czynność — skopiować pełną znak, czy jest 1 lub 2 bajty. Ale nie przyjmuje pod uwagę, że ostatni znak skopiowane może się nie zmieścić buforu Jeśli znak jest 2 bajty szerokości. Właściwym rozwiązaniem jest:  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 Ten kod testów dla przepełnienie buforu możliwe w pętli przetestować, za pomocą `_mbclen` do testowania rozmiar bieżący znak wskazywana przez `sz`. Poprzez wywołanie `_mbsnbcpy` funkcji, można zastąpić kod w `while` pętli z jednego wiersza kodu. Na przykład:  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)