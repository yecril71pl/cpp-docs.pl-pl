---
title: Strony kodowe | Dokumentacja firmy Microsoft
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
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 203467eea055927ac7eb8d5ccf8a90242c62d33a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="code-pages"></a>Strony kodowe

A *strona kodowa* jest zestaw znaków, który może zawierać cyfry, znaki interpunkcyjne i inne znaki. Różnych języków i ustawień regionalnych może używać innej strony kodowe. Na przykład stronę kodową ANSI 1252 jest używana w języku angielskim i większości języków europejskich; Strona kodowa OEM 932 jest używana do japoński Kanji.

 Strona kodowa może być reprezentowana w tabeli jako mapowanie znaki jednobajtowe wartości lub wartości wielobajtowe. Wiele stron kodowych udostępnianie zestaw znaków z zakresu 0x00 - 0x7F znaków ASCII.

 Biblioteka wykonawcza Microsoft korzysta z następujących typów kodu stron:

- Domyślna systemowa strona kodowa ANSI. Domyślnie podczas uruchamiania systemu środowiska wykonawczego automatycznie ustawia strony kodowe wielobajtowe systemu domyślną stronę kodową ANSI, które są uzyskiwane z systemu operacyjnego. Wywołanie:

    ```C
    setlocale ( LC_ALL, "" );
    ```

     Ustawia również ustawień regionalnych systemu domyślną stronę kodową ANSI.

- Strona kodowa ustawień lokalnych. Zachowanie liczba procedury czasu wykonywania jest zależna od bieżących ustawień regionalnych, który zawiera strona kodowa ustawień lokalnych. (Aby uzyskać więcej informacji, zobacz [procedury zależne od ustawień regionalnych](../c-runtime-library/locale.md).) Domyślnie wszystkie procedury zależne od ustawień regionalnych w bibliotece środowiska wykonawczego Microsoft używają stronę kodową, która odpowiada ustawień regionalnych "C". W czasie wykonywania można zmienić lub kwerendy strona kodowa ustawień lokalnych w użyciu, wywołanie [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

- Strony kodowe wielobajtowe. Zachowanie większość procedur znaków wielobajtowych biblioteki wykonawczej zależy od bieżącego ustawienia strony kodowe wielobajtowe. Domyślnie te procedury używają systemu domyślną stronę kodową ANSI. W czasie wykonywania zapytań i zmienić strony kodowe wielobajtowe z [_getmbcp —](../c-runtime-library/reference/getmbcp.md) i [_setmbcp —](../c-runtime-library/reference/setmbcp.md)odpowiednio.

- Ustawienia regionalne "C" jest zdefiniowana przez ANSI na zgodne z ustawieniami regionalnymi, w którym tradycyjnie wykonali C — programy. Strona kodowa dla ustawień regionalnych "C" (strona kodowa "C") odnosi się do zestawu znaków ASCII. Na przykład w ustawieniach regionalnych "C" **islower —** zwraca wartość true dla wartości 0x61 - tylko 0x7A. W innych regionalnych **islower —** może zwracają wartość true dla tych, jak również inne wartości określonych ustawień regionalnych.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
 [Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>