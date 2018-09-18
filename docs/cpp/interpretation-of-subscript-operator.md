---
title: Interpretacja operatora indeksu dolnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1457744747ee3638d7f0b9485ac12af60e5cdd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058344"
---
# <a name="interpretation-of-subscript-operator"></a>Interpretacja operatora indeksu dolnego

Inne operatory operator indeksu dolnego, takich jak (**\[]**) mogą ponownie zdefiniowana przez użytkownika. Domyślne zachowanie operatora indeksu dolnego, jeżeli nie jest przeciążona, to aby połączyć nazwę tablicy i indeks dolny przy użyciu następującej metody:

\*((*nazwa macierzy*) + (*indeks dolny*))

Jak dodanie wszystkich obejmuje typy wskaźników skalowanie jest wykonywane automatycznie Aby dostosować rozmiar tego typu. W związku z tym, wynikowa wartość nie jest *indeks dolny* bajtów z pochodzenia *nazwa macierzy*; zamiast jest *indeks dolny*th elementu tablicy. (Aby uzyskać więcej informacji na temat tej konwersji, zobacz [operatory addytywne](../cpp/additive-operators-plus-and.md).)

Podobnie dla tablic wielowymiarowych adres jest tworzony przy użyciu następującej metody:

((*nazwa macierzy*) + (*indeks dolny*1 \* *max*2 \* *max*3 \* ... \* *max*n) + (*indeks dolny*2 \* *max*3 \* ... \* *max*n) +... + *indeks dolny*n))

## <a name="see-also"></a>Zobacz także

[Tablice](../cpp/arrays-cpp.md)<br/>
