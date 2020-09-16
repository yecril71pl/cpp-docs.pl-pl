---
title: Zalecenia dotyczące wybierania pomiędzy funkcjami i makrami
description: Wyjaśnia różnice między używaniem makr a funkcjami w bibliotece środowiska uruchomieniowego Microsoft C (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.functions
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
ms.openlocfilehash: 8c47bf1924aeb94e2e4c9ee9358627cafcf90cba
ms.sourcegitcommit: a6b97f5d78299ad93675de2fe0f0561f528d26c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2020
ms.locfileid: "90569536"
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>Zalecenia dotyczące wybierania pomiędzy funkcjami i makrami

Większość procedur biblioteki wykonawczej firmy Microsoft jest skompilowanych lub zmontowanych funkcji, ale niektóre procedury są implementowane jako makra. Gdy plik nagłówkowy deklaruje zarówno funkcję, jak i wersję makro procedury, ma pierwszeństwo definicja makra, ponieważ zawsze jest wyświetlana po deklaracji funkcji. Po wywołaniu procedury, która jest zaimplementowana jako funkcja i makro, można wymusić użycie przez kompilator wersji funkcji na dwa sposoby:

- Ujmij nazwę procedury w nawiasy.

    ```C
    #include <ctype.h>
    a = _toupper(a);    // Use macro version of toupper.
    a = (_toupper)(a);  // Force compiler to use
                        // function version of toupper.
    ```

- "Usuń definicję" definicji makra z `#undef` dyrektywą:

    ```C
    #include <ctype.h>
    #undef _toupper
    ```

Jeśli konieczne jest wybranie między funkcją a implementacją makra procedury biblioteki, należy wziąć pod uwagę następujące zalety:

- **Szybkość w porównaniu z rozmiarem** Główną zaletą korzystania z makr jest szybszy czas wykonywania. Podczas przetwarzania wstępnego makro jest rozwinięte (zastąpione przez jego definicję) przy każdym użyciu. Definicja funkcji występuje tylko raz, niezależnie od tego, ile razy jest wywoływana. Makra mogą zwiększyć rozmiar kodu, ale nie mają obciążenia związanego z wywołaniami funkcji.

- **Obliczanie funkcji** Funkcja daje w wyniku adres; makro nie jest. Z tego względu nie można użyć nazwy makra w kontekstach wymagających wskaźnika. Na przykład można zadeklarować wskaźnik do funkcji, ale nie wskaźnik do makra.

- **Sprawdzanie typu** Kiedy deklarujesz funkcję, kompilator może sprawdzić typy argumentów. Ponieważ nie można zadeklarować makra, kompilator nie może sprawdzić typów argumentów makra; Chociaż można sprawdzić liczbę argumentów, które są przekazywane do makra.

## <a name="see-also"></a>Zobacz także

[Typ-ogólne matematyczne](tgmath.md)\
[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)