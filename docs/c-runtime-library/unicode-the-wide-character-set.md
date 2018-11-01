---
title: 'Unicode: zestaw znaków dwubajtowych'
ms.date: 11/04/2016
f1_keywords:
- c.international
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 0432de1203d595947eb958a032870a929f00aeb0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618299"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: zestaw znaków dwubajtowych

Znak dwubajtowy jest kod znaku wielojęzyczny 2-bajtowych. Dowolny znak używany w nowoczesnych przetwarzania danych na całym świecie, w tym techniczne symboli i publikowania znaków specjalnych, może być reprezentowany zgodnie ze specyfikacją Unicode jako znak dwubajtowy. Rozwinięte i utrzymywane przez konsorcjum dużych, obejmującą firmy Microsoft, w standardzie Unicode teraz jest powszechnie akceptowane.

Znak dwubajtowy jest typu **wchar_t**. Ciąg znaków dwubajtowych jest reprezentowany jako **[] wchar_t** macierz, a następnie jest wskazywany przez `wchar_t*` wskaźnika. Użytkownik oświadcza dowolnego znaku ASCII jako znak dwubajtowy, przez dodanie przedrostka literę **L** do znaku. Na przykład L '\0' jest kończącego znaku null całej (16-bitowe). Podobnie może reprezentować dowolny ciąg ASCII literału jako literał ciągu znaków dwubajtowych, po prostu przez dodanie przedrostka litera L na literał ASCII (L "Witaj,").

Ogólnie rzecz biorąc znaki dwubajtowe zajmują więcej miejsca w pamięci niż znaki wielobajtowe, ale są szybsze do procesu. Ponadto tylko jeden ustawienia regionalne mogą być reprezentowane w czasie wielobajtowego kodowania, natomiast zestawy wszystkich znaków na świecie są jednocześnie reprezentowane przez reprezentację Unicode.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
