---
title: Tekst i ciągi w programie Visual C++ | Dokumentacja firmy Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e16c44993f3cd9598bc42f9151264e09ac3b7a53
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856036"
---
# <a name="text-and-strings-in-visual-c"></a>Tekst i ciągi w programie Visual C++
Ważnym aspektem opracowywanie aplikacji dla międzynarodową jest odpowiednią reprezentację zestawy znaków lokalnych. Zestaw znaków ASCII definiuje znaków z zakresu 0x00 do 0x7F. Brak innych zestawów znaków, przede wszystkim Europejskiej, zdefiniuj znaków z zakresu 0x00 do 0x7F identycznie do zestawu znaków ASCII, który również definiować rozszerzonego zestawu z 0x80 do 0xFF znaków. W związku z tym 8-bitową i pojedynczych bajtów znaków zestaw (SBCS) jest wystarczająca do reprezentowania zestawu znaków ASCII, a także zestawy znaków dla wielu języków europejskich. Jednak niektóre zestawy Nieeuropejskie znaków, takich jak japoński Kanji obejmują wiele więcej znaków niż schemat kodowania jednobajtowe reprezentują i dlatego wymaga zestawu znaków wielobajtowych (MBCS) kodowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Unicode i MBCS](../text/unicode-and-mbcs.md)  
 W tym artykule omówiono Obsługa programowania Unicode i MBCS w języku Visual C++.  
  
 [Obsługa formatu Unicode](../text/support-for-unicode.md)  
 W tym artykule opisano Unicode, specyfikacja do obsługi wszystkich zestawów znaków, w tym zestawów znaków, które nie mogą być reprezentowane w pojedynczy bajt.  
  
 [Obsługa zestawów znaków wielobajtowych (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)  
 W tym artykule omówiono MBCS, zamiast Unicode do obsługi zestawów znaków, takich jak japoński i chiński, której nie można przedstawić w pojedynczy bajt.  
  
 [Mapowania typ ogólny-tekst w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md)  
 Mapowania zwykłego tekstu specyficzne dla firmy Microsoft zawiera wiele typów danych, procedury i innych obiektów.  
  
 [Instrukcje: konwertowanie między rozmaitymi typami ciągów](../text/how-to-convert-between-various-string-types.md)  
 Pokazuje, jak przekonwertować rozmaitymi typami ciągów Visual C++ na innych ciągów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Internacjonalizacja](../c-runtime-library/internationalization.md)  
 W tym artykule omówiono obsługi międzynarodowej biblioteki wykonawcze języka C.  
  
 [Międzynarodowe przykłady](http://msdn.microsoft.com/en-us/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 Zawiera łącza do prezentacja przystosowywanie do warunków międzynarodowych w programie Visual C++ — przykłady.  
  
 [Język i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 Zawiera ciągi kraj/region i język biblioteki wykonawcze języka C.