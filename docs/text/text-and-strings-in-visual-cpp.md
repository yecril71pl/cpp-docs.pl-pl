---
title: Tekst i ciągi w programie Visual C++
ms.date: 11/04/2016
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
ms.openlocfilehash: c6083fcf9db8236df15d1cb5e7de4cc15fe5916e
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626724"
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

[Mapowania typ ogólny tekst w pliku tchar.h](../text/generic-text-mappings-in-tchar-h.md)<br/>
Mapowania zwykłego tekstu specyficzne dla firmy Microsoft zawiera wiele typów danych, procedury i innych obiektów.

[Instrukcje: Konwertowanie między rozmaitymi typami ciągów](../text/how-to-convert-between-various-string-types.md)<br/>
Pokazuje, jak konwertować różnych typów ciągu Visual C++ na inne ciągi.

## <a name="related-sections"></a>Sekcje pokrewne

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
W tym artykule omówiono Obsługa wymagań międzynarodowych w biblioteki wykonawczej C.

[Przykłady międzynarodowe](https://github.com/Microsoft/VCSamples)<br/>
Zawiera łącza do przykładów, demonstrując internacjonalizacji w programie Visual C++.

[Język i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
Udostępnia ciągów języka i kraju/regionu w biblioteki wykonawczej C.
