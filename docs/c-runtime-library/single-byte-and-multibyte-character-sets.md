---
title: Obsługa zestawów znaków wielobajtowych i jednobajtowych
ms.date: 11/04/2016
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
ms.openlocfilehash: 1870fed732e5b940edb7690f9c3b58bb39c24572
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645386"
---
# <a name="single-byte-and-multibyte-character-sets"></a>Obsługa zestawów znaków wielobajtowych i jednobajtowych

Zestaw znaków ASCII definiuje znaki z zakresu od 0x00 - 0x7F. Istnieje kilka innych zestawów znaków, przede wszystkim Europejskiej, które definiują znaki w zakresie 0x00 — 0x7F identycznie do znaku ASCII zestawu, a także definiować rozszerzonego zestawu znaków od 0x80 - 0xFF. Związku z tym 8-bitową i pojedynczych bajtów znaków zestaw (SBCS) jest wystarczająca do reprezentowania zestawu znaków ASCII, a także zestawów znaków dla wielu języków europejskich. Jednak niektóre zestawy znaków Nieeuropejskie, takich jak japoński Kanji zawierają wiele więcej znaków niż mogą być reprezentowane w schemacie kodowania pojedynczych bajtów i dlatego wymaga zestawu znaków wielobajtowych (MBCS) kodowania.

> [!NOTE]
> Wiele procedur SBCS w bibliotece wykonawczej Microsoft obsługują wielobajtowych bajtów, znaki oraz ciągi zgodnie z potrzebami. Wiele zestawów znaków wielobajtowych definiują zestaw stanowią podzestaw znaków ASCII. W wielu zestawów znaków wielobajtowych każdy znak w zakresie 0x00 - 0x7F jest taka sama jak znak, który ma taką samą wartość w zestawie znaków ASCII. Na przykład w ciągach znaków ASCII i znaków MBCS, jednobajtowych znakiem null (\0) ma wartość 0x00 i wskazuje kończącego znaku null.

Zestaw znaków wielobajtowych może zawierać znaków jednobajtowych i dwubajtowych. Ten sposób ciąg znaków wielobajtowych może zawierać kombinację znaków jednobajtowych i dwubajtowych. Znak wielobajtowy dwubajtowy ma bajt wiodący i bajt. W określonym zestawie znaków wielobajtowych wiodące bajty mieszczą się w pewnym zakresie, tak jak bajtów dziennika. Gdy te zakresy zachodziły na siebie, może być konieczne do oceny w szczególnym kontekście do określenia, czy danego typu byte działa jako bajt wiodący lub bajt.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
