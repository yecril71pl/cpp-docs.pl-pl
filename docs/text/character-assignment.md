---
title: Przypisanie znaku
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: 9099382a212f9f7bd6c071f4e4d9a0c2bc8887de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435377"
---
# <a name="character-assignment"></a>Przypisanie znaku

Rozważmy następujący przykład, w którym **podczas** pętli skanuje ciągu, kopiując wszystkie znaki z wyjątkiem "X" do innego ciągu:

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

Kod kopiuje bajt `sz2` w lokalizacji wskazywanej przez `sz1`, następnie zwiększa `sz1` do odbierania następny bajt. Ale jeśli następny znak w `sz2` jest znak dwubajtowy, przypisanie do `sz1` kopiuje tylko pierwszy bajt. W poniższym kodzie użyto funkcji przenośny, aby bezpiecznie skopiować znak i innej, aby zwiększyć `sz1` i `sz2` prawidłowo:

```cpp
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

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Porównywanie znaków](../text/character-comparison.md)