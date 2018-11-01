---
title: Strony kodowe
ms.date: 11/04/2016
f1_keywords:
- c.international
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
ms.openlocfilehash: 707aec51b0a244fe305205b9b098f3f67a90de1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521066"
---
# <a name="code-pages"></a>Strony kodowe

A *strony kodowej* jest zestaw znaków, który może zawierać liczby, znaki interpunkcyjne i symbole inne. Różne języki i ustawienia regionalne może używać różne strony kodowe. Na przykład strona kodowa ANSI 1252 jest używana w języku angielskim i najbardziej języka Europejskiego; Strona kodowa OEM 932 jest używana do japoński Kanji.

Strona kodowa może być reprezentowany w tabeli jako mapowanie znaków wielobajtowych wartości lub wartości jednobajtowych. Wiele stron kodowych udostępnić zestaw znaków z zakresu od 0x00 - 0x7F znaków ASCII.

Biblioteki wykonawczej firmy Microsoft korzysta z następujących typów stron kodowych:

- Domyślna systemowa strona kodowa ANSI. Domyślnie podczas uruchamiania systemu środowiska wykonawczego automatycznie ustawia stronę kodu wielobajtowego stronę kodową ANSI systemu domyślnego, uzyskany od systemu operacyjnego. Wywołanie:

    ```C
    setlocale ( LC_ALL, "" );
    ```

   Ponadto Ustawia ustawienia regionalne na stronę kodową ANSI systemu domyślnego.

- Strona kodowa ustawień lokalnych. Zachowanie numer procedury czasu wykonywania zależy od bieżących ustawień regionalnych, który zawiera strona kodowa ustawień lokalnych. (Aby uzyskać więcej informacji, zobacz [procedury zależne od ustawień regionalnych](../c-runtime-library/locale.md).) Domyślnie wszystkie procedury zależne od ustawień regionalnych w bibliotece wykonawczej programu Microsoft używają stronę kodową, która odnosi się do ustawień regionalnych "C". W czasie wykonywania można zmienić lub zbadać strona kodowa ustawień regionalnych używany z wywołaniem [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

- Strony kodowe wielobajtowe. Zachowanie większość obsługi znaków wielobajtowych w bibliotece wykonawczej zależy od bieżącego ustawienia strony kodowe wielobajtowe. Domyślnie te procedury używają stronę kodową ANSI systemu domyślnego. W czasie wykonywania można wykonywać zapytania i zmienić stronę kodu wielobajtowego, za pomocą [_getmbcp](../c-runtime-library/reference/getmbcp.md) i [_setmbcp](../c-runtime-library/reference/setmbcp.md), odpowiednio.

- Ustawienia regionalne "C" jest zdefiniowany przez ANSI odpowiadające im ustawienia regionalne, w którym tradycyjnie wykonali programów C. Strona kodowa dla ustawień regionalnych "C" (strona kodowa "C") odnosi się do zestawu znaków ASCII. Na przykład w ustawieniach regionalnych "języka C" **islower** zwraca wartość true, wartości 0x61 - 0x7A tylko. W innej wersji regionalnej **islower** może zwracają wartość true dla je, a także inne wartości, zgodnie z definicją danego ustawienia regionalnego.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>