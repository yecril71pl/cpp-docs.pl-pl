---
title: 'Unicode: Zestaw znaków dwubajtowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fcd1c874c1701f471026deec73ab596971d3ad4
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450800"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: zestaw znaków dwubajtowych

Znaków dwubajtowych jest kodem 2-bajtowych wartości znakowych wielu języków. Dowolny znak używany w przypadku nowoczesnych komputerów na całym świecie, tym techniczne symboli i znaków specjalnych publikowania, może być reprezentowany według specyfikacji Unicode jako znaków dwubajtowych. Opracowany i aktualizowany przez dużych konsorcjum zawierającą firmy Microsoft, standardu Unicode teraz jest powszechnie zaakceptowany.

Typ jest znaków dwubajtowych **wchar_t**. Ciąg znaków dwubajtowych jest reprezentowany jako **[wchar_t]** tablicy i jest wskazywana przez `wchar_t*` wskaźnika. Jako znaków dwubajtowych może reprezentować znaków ASCII, dodając literę **L** do znaku. Na przykład L '\0' jest znak końcowy null całej (16-bitowe). Podobnie może reprezentować dowolny ciąg ASCII literałów jako literału ciągu znaków dwubajtowych po prostu dodając litera na literał ASCII (L "Hello").

Ogólnie rzecz biorąc znaki dwubajtowe zajmują więcej miejsca w pamięci niż znaków wielobajtowych, ale są szybsze do procesu. Ponadto tylko jeden ustawień regionalnych może być reprezentowany w czasie w kodowaniu wielobajtowe, natomiast zestawy wszystkich znaków w świecie są jednocześnie reprezentowane przez reprezentacja Unicode.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
