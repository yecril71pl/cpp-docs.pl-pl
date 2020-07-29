---
title: Zakres wartości char
ms.date: 11/04/2016
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
ms.openlocfilehash: 085f7a319cb193f9d9d744d6e896062e550404cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227806"
---
# <a name="range-of-char-values"></a>Zakres wartości char

**3.2.1.1 ANSI** Czy "zwykły" **`char`** ma taki sam zakres wartości jak **`signed char`** lub**`unsigned char`**

Wszystkie podpisane wartości znakowe mieszczą się w zakresie od-128 do 127. Wszystkie wartości znaku bez znaku mieszczą się w zakresie od 0 do 255.

[`/J`](../build/reference/j-default-char-type-is-unsigned.md)Opcja kompilatora zmienia domyślny typ dla **`char`** z **`signed char`** na **`unsigned char`** .

## <a name="see-also"></a>Zobacz także

[Znaki](../c-language/characters.md)
