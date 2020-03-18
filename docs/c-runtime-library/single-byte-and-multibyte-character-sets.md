---
title: Obsługa zestawów znaków wielobajtowych i jednobajtowych
ms.date: 11/04/2016
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
ms.openlocfilehash: a6a0f3aaaa463297b7c51b035acc7b2f4a40b6cf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444646"
---
# <a name="single-byte-and-multibyte-character-sets"></a>Obsługa zestawów znaków wielobajtowych i jednobajtowych

Zestaw znaków ASCII definiuje znaki w zakresie 0x00-0x7F. Istnieje wiele innych zestawów znaków, głównie europejskich, które definiują znaki w zakresie 0x00-0x7F identycznie z zestawem znaków ASCII, a także definiują rozszerzony zestaw znaków z 0x80-0xFF. W ten sposób 8-bitowy, jednobajtowy zestaw znaków (SBCS) jest wystarczający do reprezentowania zestawu znaków ASCII, a także zestawów znaków dla wielu języków europejskich. Jednak niektóre nieeuropejskie zestawy znaków, takie jak japoński Kanji, zawierają wiele więcej znaków niż może być reprezentowane w schemacie kodowania jednobajtowego i dlatego wymagają kodowania zestawu znaków wielobajtowych (MBCS).

> [!NOTE]
> Wiele procedur SBCS w bibliotece Microsoft Run-Time obsługuje bajty wielobajtowe, znaki i ciągi odpowiednio do potrzeb. Wiele zestawów znaków wielobajtowych definiuje zestaw znaków ASCII jako podzestaw. W wielu zestawach znaków wielobajtowych każdy znak w zakresie 0x00-0x7F jest identyczny ze znakiem, który ma taką samą wartość w zestawie znaków ASCII. Na przykład w przypadku ciągów znaków ASCII i MBCS, jednobajtowy znak null (' \ 0 ') ma wartość 0x00 i wskazuje kończący znak null.

Zestaw znaków wielobajtowych może zawierać zarówno znaki jednobajtowe, jak i dwubajtowe. W ten sposób ciąg znaków wielobajtowych może zawierać kombinację znaków jednobajtowych i dwubajtowych. Dwubajtowy znak wielostronicowy ma bajt wiodący i końcowy. W konkretnym zestawie znaków wielobajtowych potencjalni klienci mieszczą się w określonym zakresie, tak jak w przypadku bajtów końcowych. Gdy te zakresy nakładają się na siebie, może być konieczne oszacowanie określonego kontekstu, aby określić, czy dany bajt działa jako bajt wiodący czy bajt końcowy.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
