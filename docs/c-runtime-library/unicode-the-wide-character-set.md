---
title: 'Unicode: Zestaw znaków dwubajtowych'
ms.date: 11/04/2016
f1_keywords:
- c.international
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: dc9028be85870766af0274ede091d74a9b4d5130
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304205"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: Zestaw znaków dwubajtowych

Znak dwubajtowy jest kod znaku wielojęzyczny 2-bajtowych. Dowolny znak używany w nowoczesnych przetwarzania danych na całym świecie, w tym techniczne symboli i publikowania znaków specjalnych, może być reprezentowany zgodnie ze specyfikacją Unicode jako znak dwubajtowy. Rozwinięte i utrzymywane przez konsorcjum dużych, obejmującą firmy Microsoft, w standardzie Unicode teraz jest powszechnie akceptowane.

Znak dwubajtowy jest typu **wchar_t**. Ciąg znaków dwubajtowych jest reprezentowany jako **[] wchar_t** macierz, a następnie jest wskazywany przez `wchar_t*` wskaźnika. Użytkownik oświadcza dowolnego znaku ASCII jako znak dwubajtowy, przez dodanie przedrostka literę **L** do znaku. Na przykład L '\0' jest kończącego znaku null całej (16-bitowe). Podobnie może reprezentować dowolny ciąg ASCII literału jako literał ciągu znaków dwubajtowych, po prostu przez dodanie przedrostka litera L na literał ASCII (L "Witaj,").

Ogólnie rzecz biorąc znaki dwubajtowe zajmują więcej miejsca w pamięci niż znaki wielobajtowe, ale są szybsze do procesu. Ponadto tylko jeden ustawienia regionalne mogą być reprezentowane w czasie wielobajtowego kodowania, natomiast zestawy wszystkich znaków na świecie są jednocześnie reprezentowane przez reprezentację Unicode.

## <a name="see-also"></a>Zobacz także

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
