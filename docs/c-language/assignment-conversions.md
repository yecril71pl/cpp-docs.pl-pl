---
title: Konwersje przypisań
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: cc75bdd8227c09247f6d4270f1fc21235de2eb05
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211843"
---
# <a name="assignment-conversions"></a>Konwersje przypisań

W operacjach przypisywania typ przypisanej wartości jest konwertowany na typ zmiennej, która otrzymuje przypisanie. Język C umożliwia konwersje przez przypisanie między typami całkowitymi i zmiennoprzecinkowymi, nawet jeśli informacje zostaną utracone podczas konwersji. Używana metoda konwersji zależy od typów należących do przypisania, zgodnie z opisem w [zwykłych konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) i w następujących sekcjach:

- [Konwersje z podpisanych typów całkowitych](../c-language/conversions-from-signed-integral-types.md)

- [Konwersje z niepodpisanych typów całkowitych](../c-language/conversions-from-unsigned-integral-types.md)

- [Konwersje z typów zmiennoprzecinkowych](../c-language/conversions-from-floating-point-types.md)

- [Konwersje do i z typów wskaźnika](../c-language/conversions-to-and-from-pointer-types.md)

- [Konwersje z innych typów](../c-language/conversions-from-other-types.md)

Kwalifikatory typu nie wpływają na dopuszczanie konwersji, chociaż **`const`** nie można użyć wartości l po lewej stronie przypisania.

## <a name="see-also"></a>Zobacz także

[Konwersje typu](../c-language/type-conversions-c.md)
