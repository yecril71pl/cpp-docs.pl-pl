---
title: Przepełnienie buforu
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 7f9864e6b49446ea68d82e76e877ce9c677b893d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410762"
---
# <a name="buffer-overflow"></a>Przepełnienie buforu

Różne rozmiary znaków może powodować problemy, znaki są umieszczane w buforze. Należy wziąć pod uwagę następujący kod, który kopiuje znaków z ciągu, `sz`, do buforu `rgch`:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

Pytanie jest: Był ostatni bajt skopiowane bajt wiodący? Następujące nie rozwiązuje problem, ponieważ go może potencjalnie przepełnienie buforu:

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

## <a name="see-also"></a>Zobacz także

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)
