---
title: Wpisz Conversions (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 606ff0197f73a697aa3dad3bea779de80b060705
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020839"
---
# <a name="type-conversions-c"></a>Konwersje typu (C)

Konwersje typów są zależne od określonego operatora i typu argumentu lub operatorów. Konwersje są wykonywane w następujących przypadkach:

- Wartości typu jeden jest przypisany do zmiennej innego typu lub operator konwertuje typ jej operand lub operandy przed wykonaniem operacji

- Kiedy wartości z jednego typu jest jawnie rzutowane na inny typ.

- Gdy wartość jest przekazywany jako argument do funkcji lub gdy typem jest zwracany przez funkcję

Znak, krótka liczba całkowita lub pola bitowe liczba całkowita, wszystkie podpisana lub nie, lub obiekt typu wyliczenia, może być używany w wyrażeniu, wszędzie tam, gdzie można użyć liczby całkowitej. Jeśli `int` może reprezentować wszystkie wartości oryginalnego typu, a następnie wartość jest konwertowana na `int`; w przeciwnym razie jest konwertowany na `unsigned int`. Ten proces jest nazywany "promocją typu całkowitego". Promocje typów całkowitych zachować wartość. Oznacza to, że wartość po promocji może być taka sama, jak na samym podwyższeniu. Zobacz [zwykle konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Wyrażenia i przydziały](../c-language/expressions-and-assignments.md)