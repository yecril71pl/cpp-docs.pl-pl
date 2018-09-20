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
ms.openlocfilehash: 109719b437716e31fc5ebdcd43c02c55bfea997d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413487"
---
# <a name="buffer-overflow"></a>Przepełnienie buforu

Różne rozmiary znaków może powodować problemy, znaki są umieszczane w buforze. Należy wziąć pod uwagę następujący kod, który kopiuje znaków z ciągu, `sz`, do buforu `rgch`:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

Pytanie: był ostatni bajt skopiowane bajt wiodący? Następujące nie rozwiązuje problem, ponieważ go może potencjalnie przepełnienie buforu:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

`_mbccpy` Wywołanie podejmuje próbę wykonania czynności w prawidłowy sposób — kopiowanie znak pełne, czy jest to 1 lub 2 bajtów. Ale nie przyjmuje uwagę, że ostatni znak kopiowany może nie spełniać buforu, jeśli znak jest szeroki 2 bajty. Jakie rozwiązanie będzie odpowiednie jest:

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

Ten kod sprawdza przepełnienie buforu możliwe w pętli przetestować, za pomocą `_mbclen` rozmiar bieżący znak wskazywany przez `sz`. Poprzez wywołanie `_mbsnbcpy` funkcji, można zastąpić kod w **podczas** pętli za pomocą jednego wiersza kodu. Na przykład:

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>Zobacz też

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)