---
title: Przepełnienie buforu
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 71877ed770384190cb7f856567d9e7e845e3da19
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217327"
---
# <a name="buffer-overflow"></a>Przepełnienie buforu

Różne rozmiary znaków mogą spowodować problemy podczas umieszczania znaków w buforze. Rozważmy następujący kod, który kopiuje znaki z ciągu, `sz` w buforze `rgch` :

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

Pytanie: czy ostatni bajt skopiował bajt wiodący? Poniższe rozwiązanie nie rozwiązuje problemu, ponieważ może spowodować przepełnienie buforu:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

`_mbccpy`Wywołanie próbuje wykonać poprawną czynność — Skopiuj pełny znak, niezależnie od tego, czy jest to 1 czy 2 bajty. Ale nie przyjmuje się, że ostatni skopiowany znak może nie pasować do buforu, jeśli znak jest 2 b szerokości. Poprawne rozwiązanie to:

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

Ten kod sprawdza możliwy przepełnienie buforu w teście pętli, przy użyciu `_mbclen` do testowania rozmiaru bieżącego znaku wskazywanego przez `sz` . Wykonując wywołanie `_mbsnbcpy` funkcji, można zamienić kod w **`while`** pętli na pojedynczy wiersz kodu. Na przykład:

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>Zobacz także

[Wskazówki dotyczące programowania MBCS](../text/mbcs-programming-tips.md)
