---
title: Magazynowanie literałów ciągu
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: 0d505479f0844122826a2f07b57eaa69f33932e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157867"
---
# <a name="storage-of-string-literals"></a>Magazynowanie literałów ciągu

Znaki ciągu literału są przechowywane w kolejności w ciągłej lokalizacji pamięci. Sekwencja ucieczki (taka jak ** \\ ** lub ** \\"**) w literale ciągu liczy jako pojedynczy znak. Znak null (reprezentowany przez sekwencję ucieczki **\ 0** ) jest automatycznie dołączany do i oznacza koniec każdego literału ciągu. (Dzieje się to w [fazie translacji](../preprocessor/phases-of-translation.md) 7). Należy zauważyć, że kompilator może nie przechowywać dwóch identycznych ciągów przy użyciu dwóch różnych adresów. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) wymusza, aby kompilator umieszczał pojedynczą kopię identycznych ciągów w pliku wykonywalnym.

## <a name="remarks"></a>Uwagi

**Specyficzne dla firmy Microsoft**

Ciągi mają statyczny czas przechowywania. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) , aby uzyskać informacje o czasie trwania magazynu.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Literały ciągu języka C](../c-language/c-string-literals.md)
