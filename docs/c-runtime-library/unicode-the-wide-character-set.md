---
title: 'Unicode: zestaw znaków dwubajtowych'
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 3a0c5698544c72e19feea8f35b7f5a516d95d561
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444489"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: zestaw znaków dwubajtowych

Znak dwubajtowy to kod 2-bitowy. Każdy znak używany w nowoczesnej skali na całym świecie, w tym symbole techniczne i znaki specjalne publikacji, można przedstawić na podstawie specyfikacji Unicode jako znaku dwubajtowego. Opracowane i utrzymywane przez duże konsorcjum, które obejmuje firmę Microsoft, standard Unicode jest teraz szeroko zaakceptowany.

Znak dwubajtowy jest typu **wchar_t**. Ciąg znaków dwubajtowych jest reprezentowany jako tablica **wchar_t []** i jest wskazywany przez wskaźnik `wchar_t*`. Można reprezentować dowolny znak ASCII jako znak dwubajtowy, tworząc prefiks litery **L** do znaku. Na przykład L ' \ 0 ' jest znakiem o zerowej szerokości (16-bitowym). Analogicznie, można reprezentować dowolny literał ciągu ASCII jako literał ciągu znaków dwubajtowych, tworząc prefiks litery L do literału ASCII (L "Hello").

Zwykle duże znaki zajmują więcej miejsca w pamięci niż znaki wielobajtowe, ale szybciej są przetwarzane. Ponadto w przypadku kodowania wielobajtowego można reprezentować tylko jedne ustawienia regionalne, natomiast wszystkie zestawy znaków na świecie są reprezentowane jednocześnie przez reprezentację Unicode.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
