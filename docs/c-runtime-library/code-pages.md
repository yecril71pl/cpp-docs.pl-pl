---
title: Strony kodowe
description: Opis obsługi strony kodowej w środowisku uruchomieniowym języka Microsoft C.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
ms.openlocfilehash: 1f9d311ec714d2043e072cbbfbac505d3f804294
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590072"
---
# <a name="code-pages"></a>Strony kodowe

*Strona kodowa* jest zestawem znaków, który może zawierać cyfry, znaki interpunkcyjne i inne glify. Różne języki i ustawienia regionalne mogą korzystać z różnych stron kodowych. Na przykład strona kodowa ANSI 1252 jest używana w języku angielskim i większości języków europejskich. Strona kodowa OEM 932 jest używana dla japońskiego Kanji.

Strona kodowa może być przedstawiona w tabeli jako mapowanie znaków na wartości jednobajtowe lub wielostronicowe. Wiele stron kodowych współużytkuje zestaw znaków ASCII dla znaków w zakresie 0x00-0x7F.

Biblioteka środowiska uruchomieniowego Microsoft używa następujących typów stron kodowych:

- Domyślna strona kodowa ANSI systemu. Domyślnie podczas uruchamiania system środowiska uruchomieniowego automatycznie ustawia stronę kodową wielobajtową na domyślną stronę kodową ANSI systemu, która jest uzyskiwana z systemu operacyjnego. Wywołanie:

    ```C
    setlocale ( LC_ALL, "" );
    ```

   ustawia również ustawienia regionalne na stronę kodową ANSI systemu domyślnego.

- Strona kodowa ustawień regionalnych. Zachowanie wielu procedur czasu wykonywania zależy od bieżących ustawień regionalnych, które obejmują stronę kodową ustawienia regionalne. (Aby uzyskać więcej informacji, zobacz [procedury zależne od ustawień regionalnych](../c-runtime-library/locale.md)). Domyślnie wszystkie procedury zależne od ustawień regionalnych w bibliotece wykonawczej Microsoft używają strony kodowej, która odpowiada ustawieniom regionalnym "C". W czasie wykonywania można zmienić lub zbadać stronę kodową ustawień regionalnych, która jest używana z wywołaniem metody [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

- Wielobajtowa strona kodowa. Zachowanie większości procedur znaków wielobajtowych w bibliotece wykonawczej zależy od bieżącego ustawienia strony kodowej wielobajtowego. Domyślnie te procedury korzystają z domyślnej strony kodowej ANSI w systemie. W czasie wykonywania można wykonywać zapytania i zmieniać stronę kodową wielobajtowego odpowiednio do [_getmbcp](../c-runtime-library/reference/getmbcp.md) i [_setmbcp](../c-runtime-library/reference/setmbcp.md).

- Ustawienia regionalne "C" są definiowane przez ANSI, aby odpowiadały ustawieniom regionalnym, w których programy języka C są tradycyjnie wykonywane. Strona kodowa dla ustawień regionalnych "C" (strona kodowa "C") odnosi się do zestawu znaków ASCII. Na przykład w ustawieniach regionalnych "C" **IsLower** zwraca wartość true dla wartości 0X61-0x7a. W przypadku innych ustawień regionalnych, **IsLower** może zwrócić `true` do tych i innych wartości, zgodnie z definicją w ustawieniach regionalnych.

## <a name="see-also"></a>Zobacz też

[Międzynarodowe](../c-runtime-library/internationalization.md)\
[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
