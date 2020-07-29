---
title: Przypisanie znaku
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: 0f627f88ca2b1d3533d3690cd0316ee047a327ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217314"
---
# <a name="character-assignment"></a>Przypisanie znaku

Rozważmy poniższy przykład, w którym **`while`** Pętla skanuje ciąg, kopiując wszystkie znaki z wyjątkiem "X" do innego ciągu:

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

Kod kopiuje bajt w `sz2` lokalizacji wskazywanej przez `sz1` , a następnie zwiększa `sz1` się do otrzymania następnego bajtu. Ale jeśli następny znak w `sz2` jest znakiem dwubajtowym, przypisanie do `sz1` kopiuje tylko pierwszy bajt. Poniższy kod używa funkcji przenośnej w celu bezpiecznego kopiowania znaku i kolejnego przyrostu `sz1` `sz2` :

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

## <a name="see-also"></a>Zobacz także

[Wskazówki dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Porównanie znaków](../text/character-comparison.md)
