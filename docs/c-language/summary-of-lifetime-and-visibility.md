---
title: Podsumowanie okresu istnienia i widoczności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcda68906e281bdf33ebe95a8019851bcb3cdb11
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752303"
---
# <a name="summary-of-lifetime-and-visibility"></a>Podsumowanie okresu istnienia i widoczności
Poniższa tabela znajduje się podsumowanie właściwości okresu istnienia i widoczności dla większości identyfikatorów. Pierwsze trzy kolumny zapewniają atrybutów, które definiują okres istnienia i widoczności. Identyfikator o atrybuty określone przez pierwsze trzy kolumny ma okres istnienia i widoczności wyświetlane w kolumnach czwarty i piąty. Jednak tabeli nie obejmują wszystkich możliwych przypadków. Zapoznaj się [klasy magazynu](../c-language/c-storage-classes.md) Aby uzyskać więcej informacji.  
  
### <a name="summary-of-lifetime-and-visibility"></a>Podsumowanie okresu istnienia i widoczności  
  
|Atrybuty:<br /><br /> Poziom|Element|Klasa magazynu<br /><br /> Specyfikator|Wynik:<br /><br /> Okres istnienia|Widoczność|  
|---------------------------|----------|----------------------------------|--------------------------|----------------|  
|Zakres pliku|Definicja zmiennej|**static**|Global|Pozostała część pliku źródłowego, w której występuje|  
||Deklaracja zmiennej|**extern**|Global|Pozostała część pliku źródłowego, w której występuje|  
||Prototyp funkcji lub definicja|**static**|Global|Plik źródłowy|  
||Prototyp funkcji|**extern**|Global|Pozostała część pliku źródłowego|  
|Zakres bloku|Deklaracja zmiennej|**extern**|Global|Blok|  
||Definicja zmiennej|**static**|Global|Blok|  
||Definicja zmiennej|**automatyczne** lub **zarejestrować**|Lokalny|Blok|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
W poniższym przykładzie pokazano bloki, zagnieżdżanie i widoczność zmiennych:  
  
### <a name="code"></a>Kod  
  
```  
// Lifetime_and_Visibility.c  
  
#include <stdio.h>  
  
int i = 1;  // i defined at external level  
  
int main()  // main function defined at external level  
{  
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)  
    {                                 // Begin first nested block  
        int i = 2, j = 3;          // i and j defined at internal level  
        printf_s( "%d %d\n", i, j );  // Prints 2, 3  
        {                             // Begin second nested block  
            int i = 0;                // i is redefined  
            printf_s( "%d %d\n", i, j ); // Prints 0, 3  
        }                             // End of second nested block  
        printf_s( "%d\n", i );        // Prints 2 (outer definition  
                                      //  restored)  
    }                                 // End of first nested block  
    printf_s( "%d\n", i );            // Prints 1 (external level  
                                      // definition restored)  
    return 0;  
}   
```  
  
### <a name="comments"></a>Komentarze  
W tym przykładzie istnieją cztery poziomy widoczności: poziomie zewnętrznym i blok trzy poziomy. Wartości są drukowane na ekranie, jak wspomniano w komentarzach po każdej instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
[Okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md)