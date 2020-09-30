---
title: Obsługa zestawów znaków wielobajtowych i jednobajtowych
description: Wprowadzenie do pojedynczego i wielobajtowego zestawu znaków w bibliotece środowiska uruchomieniowego firmy Microsoft.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
ms.openlocfilehash: 6668285915ab9f1939c1baf8a2d3da2d00543528
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590176"
---
# <a name="single-byte-and-multibyte-character-sets"></a>Obsługa zestawów znaków wielobajtowych i jednobajtowych

Zestaw znaków ASCII definiuje znaki w zakresie 0x00-0x7F. Istnieje wiele innych zestawów znaków, głównie europejskich, które definiują znaki w zakresie 0x00-0x7F identycznie z zestawem znaków ASCII, a także definiują rozszerzony zestaw znaków z 0x80-0xFF.  8-bitowy zestaw znaków jednobajtowych (SBCS) jest wystarczający do reprezentowania zestawu znaków ASCII oraz zestawów znaków dla wielu języków europejskich. Jednak niektóre nieeuropejskie zestawy znaków, takie jak japoński Kanji, zawierają wiele więcej znaków niż może być reprezentowane w schemacie kodowania jednobajtowego i dlatego wymagają kodowania zestawu znaków wielobajtowych (MBCS).

> [!NOTE]
> Wiele procedur SBCS w bibliotece Microsoft Run-Time obsługuje bajty wielobajtowe, znaki i ciągi odpowiednio do potrzeb. Wiele zestawów znaków wielobajtowych definiuje zestaw znaków ASCII jako podzestaw. W wielu zestawach znaków wielobajtowych każdy znak w zakresie 0x00-0x7F jest identyczny ze znakiem, który ma taką samą wartość w zestawie znaków ASCII. Na przykład w przypadku ciągów znaków ASCII i MBCS, jednobajtowy znak null (' \ 0 ') ma wartość 0x00 i wskazuje kończący znak null.

Zestaw znaków wielobajtowych może zawierać zarówno znaki jednobajtowe, jak i dwubajtowe. Ciąg znaków wielobajtowych może zawierać kombinację znaków jednobajtowych i dwubajtowych. Dwubajtowy znak wielostronicowy ma bajt wiodący i końcowy. W konkretnym zestawie znaków wielobajtowych potencjalni klienci mieszczą się w określonym zakresie, tak jak w przypadku bajtów końcowych. Gdy te zakresy nakładają się na siebie, może być konieczne oszacowanie kontekstu, aby określić, czy dany bajt działa jako bajt wiodący czy bajt końcowy.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
