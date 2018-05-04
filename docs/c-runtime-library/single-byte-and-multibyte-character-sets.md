---
title: Jednobajtowe i wielobajtowe zestawów znaków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.character.multibyte
dev_langs:
- C++
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bc23f0be1f061e6bbad76d85706da5dc005db66
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="single-byte-and-multibyte-character-sets"></a>Obsługa zestawów znaków wielobajtowych i jednobajtowych

Zestaw znaków ASCII definiuje znaków z zakresu 0x00 - 0x7F. Istnieje wiele innych zestawów znaków, przede wszystkim Europejskiej definiujące znaków z zakresu 0x00 — 0x7F identycznie do znaków ASCII ustaw i również definiować rozszerzonego zestawu znaków z 0x80 - 0xFF. W związku z tym 8-bitową i pojedynczych bajtów znaków zestaw (SBCS) jest wystarczająca do reprezentowania zestawu znaków ASCII, a także zestawy znaków dla wielu języków europejskich. Jednak niektóre zestawy Nieeuropejskie znaków, takich jak japoński Kanji obejmują wiele więcej znaków niż mogą być reprezentowane w schemacie kodowania jednobajtowe i dlatego wymaga zestawu znaków wielobajtowych (MBCS) kodowania.

> [!NOTE]
> Wiele procedur SBCS biblioteki wykonawczej Microsoft obsługi wielobajtowe bajtów, znaków i ciągi zgodnie z potrzebami. Wiele zestawów znaków wielobajtowych Zdefiniuj zestaw jako podzbiór znaków ASCII. W wielu zestawów znaków wielobajtowych każdego znaku w zakresie 0x00 - 0x7F jest taki sam jak znak, który ma taką samą wartość zestawu znaków ASCII. Na przykład w ASCII i MBCS ciągi znaków jednobajtowych znak NULL ('\0') ma wartość 0x00 i wskazuje znak końcowy null.

Zestaw znaków wielobajtowych może zawierać zarówno jednobajtowych i dwubajtowych znaków. W związku z tym ciąg znaków wielobajtowych może zawierać znaki jednobajtowe i dwubajtowe. 2 bajtowych znaków wielobajtowych ma bajtu i bajt. W określonym zestawie znaków wielobajtowych bajtów realizacji mieścić się w pewnym, jak bajtów dziennik. Podczas nakładają się tych zakresów, może być konieczne do oceny określonego kontekstu do określenia, czy danego typu byte działa jako bajtu lub bajt.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
