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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11a3da883dae4d292a55eb2537fd98609404b5a9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609515"
---
# <a name="buffer-overflow"></a>Przepełnienie buforu
Różne rozmiary znaków może powodować problemy, znaki są umieszczane w buforze. Należy wziąć pod uwagę następujący kod, który kopiuje znaków z ciągu, `sz`, do buforu `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 Pytanie: był ostatni bajt skopiowane bajt wiodący? Następujące nie rozwiązuje problem, ponieważ go może potencjalnie przepełnienie buforu:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 `_mbccpy` Wywołanie podejmuje próbę wykonania czynności w prawidłowy sposób — kopiowanie znak pełne, czy jest to 1 lub 2 bajtów. Ale nie przyjmuje uwagę, że ostatni znak kopiowany może nie spełniać buforu, jeśli znak jest szeroki 2 bajty. Jakie rozwiązanie będzie odpowiednie jest:  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 Ten kod sprawdza przepełnienie buforu możliwe w pętli przetestować, za pomocą `_mbclen` rozmiar bieżący znak wskazywany przez `sz`. Poprzez wywołanie `_mbsnbcpy` funkcji, można zastąpić kod w **podczas** pętli za pomocą jednego wiersza kodu. Na przykład:  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)