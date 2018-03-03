---
title: Strony kodowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a0899f5f617fd28d121b85183280bd28fe91ee46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="code-pages"></a>Strony kodowe
A `code page` jest zestaw znaków, który może zawierać cyfry, znaki interpunkcyjne i inne znaki. Różnych języków i ustawień regionalnych może używać innej strony kodowe. Na przykład stronę kodową ANSI 1252 jest używana w języku angielskim i większości języków europejskich; Strona kodowa OEM 932 jest używana do japoński Kanji.  
  
 Strona kodowa może być reprezentowana w tabeli jako mapowanie znaki jednobajtowe wartości lub wartości wielobajtowe. Wiele stron kodowych udostępnianie zestaw znaków z zakresu 0x00 - 0x7F znaków ASCII.  
  
 Biblioteka wykonawcza Microsoft korzysta z następujących typów kodu stron:  
  
-   Domyślna systemowa strona kodowa ANSI. Domyślnie podczas uruchamiania systemu środowiska wykonawczego automatycznie ustawia strony kodowe wielobajtowe systemu domyślną stronę kodową ANSI, które są uzyskiwane z systemu operacyjnego. Wywołanie:  
  
    ```  
    setlocale ( LC_ALL, "" );  
    ```  
  
     Ustawia również ustawień regionalnych systemu domyślną stronę kodową ANSI.  
  
-   Strona kodowa ustawień lokalnych. Zachowanie liczba procedury czasu wykonywania jest zależna od bieżących ustawień regionalnych, który zawiera strona kodowa ustawień lokalnych. (Aby uzyskać więcej informacji, zobacz [procedury zależne od ustawień regionalnych](../c-runtime-library/locale.md).) Domyślnie wszystkie procedury zależne od ustawień regionalnych w bibliotece środowiska wykonawczego Microsoft używają stronę kodową, która odpowiada ustawień regionalnych "C". W czasie wykonywania można zmienić lub kwerendy strona kodowa ustawień lokalnych w użyciu, wywołanie [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
-   Strony kodowe wielobajtowe. Zachowanie większość procedur znaków wielobajtowych biblioteki wykonawczej zależy od bieżącego ustawienia strony kodowe wielobajtowe. Domyślnie te procedury używają systemu domyślną stronę kodową ANSI. W czasie wykonywania zapytań i zmienić strony kodowe wielobajtowe z [_getmbcp —](../c-runtime-library/reference/getmbcp.md) i [_setmbcp —](../c-runtime-library/reference/setmbcp.md)odpowiednio.  
  
-   Ustawienia regionalne "C" jest zdefiniowana przez ANSI na zgodne z ustawieniami regionalnymi, w którym tradycyjnie wykonali C — programy. Strona kodowa dla ustawień regionalnych "C" (strona kodowa "C") odnosi się do zestawu znaków ASCII. Na przykład w ustawieniach regionalnych "C" `islower` zwraca wartość true dla wartości 0x61 - tylko 0x7A. W innych regionalnych `islower` może zwracają wartość true dla tych, jak również inne wartości określonych ustawień regionalnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przystosowywanie do warunków międzynarodowych](../c-runtime-library/internationalization.md)   
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)