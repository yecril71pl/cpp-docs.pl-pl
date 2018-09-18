---
title: Rozwiązywanie niejednoznacznych deklaracji (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1e55d5afc3cc95dbfd61bead30cdb2d686f7f30
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066645"
---
# <a name="resolving-ambiguous-declarations-c"></a>Rozwiązywanie niejednoznacznych deklaracji (C++)

Aby wykonywania jawnych konwersji z jednego typu na inny, należy użyć rzutowania, określający nazwę żądanego typu. Wynik rzutowania niektóre wpisz składni niejednoznaczności. Następujące rzutowanie typu w stylu funkcji jest niejednoznaczny:

```cpp
char *aName( String( s ) );
```

Nie wiadomo, czy jest deklaracja funkcji lub deklaracja obiektu za pomocą funkcji rzutowania w stylu jako inicjator: można zadeklarować, funkcja zwracająca typ `char *` przyjmującą jeden argument typu `String`, lub można je zadeklarować obiekt `aName` i zainicjuj ją z wartością `s` Rzutowanie na typ `String`.

Jeśli deklaracja jest uznawana za deklaracji prawidłową funkcją, jest ona traktowana jako takie. Tylko wtedy, gdy jest to prawdopodobnie nie może być deklaracji funkcji — to znaczy, jeśli będzie składniowo niepoprawny — jest badany instrukcję, aby sprawdzić, czy jest rzutowanie typu stylu funkcji. W związku z tym, kompilator traktuje instrukcji jako deklaracja funkcji i ignoruje nawiasów wokół identyfikator `s`. Z drugiej strony, instrukcji:

```cpp
char *aName( (String)s );
```

and

```cpp
char *aName = String( s );
```

są wyraźnie deklaracje obiektów i zdefiniowana przez użytkownika konwersja z typu `String` na typ `char *` wywoływana w celu wykonania inicjowanie `aName`.