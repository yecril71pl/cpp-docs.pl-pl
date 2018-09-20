---
title: Tekst i ciągi w języku Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 555183de13728cc01509b87e8eca8c3340d2d68b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424063"
---
# <a name="text-and-strings-in-visual-c"></a>Tekst i ciągi w programie Visual C++

Ważnym aspektem projektowania aplikacji na rynki międzynarodowe jest odpowiednią reprezentację zestawy znaków lokalnych. Zestaw znaków ASCII definiuje znaki z zakresu od 0x00, 0x7F. Istnieją inne zestawy znaków Europejskiego przede wszystkim, zdefiniuj znaki w zakresie 0x00, 0x7F identycznie do zestawu znaków ASCII, który również zdefiniować znak rozszerzony ustawić od 0x80 do 0xFF. W związku z tym 8-bitową i pojedynczych bajtów znaków zestaw (SBCS) jest wystarczająca do reprezentowania zestawu znaków ASCII, a także zestawów znaków dla wielu języków Europejskiego. Jednak niektóre zestawy znaków Nieeuropejskie, takich jak japoński Kanji zawierają wiele więcej znaków niż schemat kodowania pojedynczych bajtów może reprezentować i dlatego wymaga zestawu znaków wielobajtowych (MBCS) kodowania.

## <a name="in-this-section"></a>W tej sekcji

[Unicode i MBCS](../text/unicode-and-mbcs.md)<br/>
W tym artykule omówiono obsługę języka Visual C++ do programowania Unicode i MBCS.

[Obsługa formatu Unicode](../text/support-for-unicode.md)<br/>
W tym artykule opisano Unicode, specyfikacji do obsługi wszystkich zestawów znaków, łącznie z zestawów znaków, które nie mogą być reprezentowane w jednobajtowych.

[Obsługa zestawów znaków wielobajtowych (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
W tym artykule omówiono MBCS, zamiast Unicode do obsługi zestawów znaków, takich jak japońskim i chińskim, który nie może być przedstawiony w jednobajtowych.

[Mapowania typ ogólny-tekst w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md)<br/>
Mapowania zwykłego tekstu specyficzne dla firmy Microsoft zawiera wiele typów danych, procedury i innych obiektów.

[Instrukcje: konwertowanie między rozmaitymi typami ciągów](../text/how-to-convert-between-various-string-types.md)<br/>
Pokazuje, jak konwertować różnych typów ciągu Visual C++ na inne ciągi.

## <a name="related-sections"></a>Sekcje pokrewne

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
W tym artykule omówiono Obsługa wymagań międzynarodowych w biblioteki wykonawczej C.

[Przykłady międzynarodowe](https://github.com/Microsoft/VCSamples)<br/>
Zawiera łącza do przykładów, demonstrując internacjonalizacji w programie Visual C++.

[Język i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
Udostępnia ciągów języka i kraju/regionu w biblioteki wykonawczej C.