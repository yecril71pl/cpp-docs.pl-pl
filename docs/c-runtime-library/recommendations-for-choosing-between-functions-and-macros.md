---
title: Zalecenia dotyczące wybierania pomiędzy funkcjami i makrami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.functions
dev_langs:
- C++
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e347da977b58621529564f6e6d8646bd72063a0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023270"
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>Zalecenia dotyczące wybierania pomiędzy funkcjami i makrami

Większość procedur biblioteki wykonawczej firmy Microsoft są kompilowane lub złożonego funkcji, ale niektóre procedury są implementowane jako makra. Gdy plik nagłówkowy deklaruje zarówno funkcja i makra wersję procedury, definicji makra, pierwszeństwo, ponieważ zawsze pojawia się po deklaracji funkcji. Gdy wywołujesz procedurę, która jest implementowana jako funkcja i makra, możesz wymusić na kompilatorze używać wersji funkcji na dwa sposoby:

- Rutynowe nazwę należy ująć w nawiasy.

    ```C
    #include <ctype.h>
    a = _toupper(a);    // Use macro version of toupper.
    a = (_toupper)(a);  // Force compiler to use
                        // function version of toupper.
    ```

- "Usuń" definicji makra z `#undef` dyrektywy:

    ```C
    #include <ctype.h>
    #undef _toupper
    ```

Jeśli musisz wybierać między funkcja i makra stosowania procedury biblioteki należy wziąć pod uwagę następujące wad i zalet:

- **Szybkości i rozmiaru** główną zaletą korzystania z makr jest krótszy czas wykonywania. Podczas wstępnego przetwarzania, makra podzielonego (zastąpione przez jego definicję) wbudowane zawsze jest używany. Jest wywoływana tylko raz, niezależnie od tego, ile razy występuje definicji funkcji. Makra może zwiększyć rozmiar kodu, ale nie mają zapas skojarzony z wywołania funkcji.

- **Obliczanie funkcji** funkcji obliczane jako adres; makra nie. Dlatego nie można użyć nazwę makra w kontekstach wymagające wskaźnik. Na przykład można zadeklarować wskaźnik do funkcji, ale nie wskaźnik do makra.

- **Kontrola typów** kiedy Deklarujesz funkcję, kompilator można sprawdzić typy argumentów. Ponieważ nie można zadeklarować makra, kompilator nie można sprawdzić typy argumentów makra; Mimo że można sprawdzić, liczba argumentów są przekazywane do makra.

## <a name="see-also"></a>Zobacz też

[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)