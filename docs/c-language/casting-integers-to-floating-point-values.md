---
title: Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: b3c65beee0cef4eb74d1bad3c03e5a9c11efae27
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227923"
---
# <a name="casting-integers-to-floating-point-values"></a>Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe

**3.2.1.3 ANSI** Kierunek obcinania, gdy numer całkowity jest konwertowany na liczbę zmiennoprzecinkową, która nie może dokładnie reprezentować pierwotnej wartości

Gdy całkowita liczba jest rzutowana na wartość zmiennoprzecinkową, która nie może dokładnie reprezentować wartości, wartość jest zaokrąglana (w górę lub w dół) do najbliższej odpowiedniej wartości.

Na przykład rzutowanie **`unsigned long`** (o 32 bitów precyzji) do **`float`** (którego mantysy ma 23 bitów precyzji) zaokrągla liczbę do najbliższej wielokrotności 256. **`long`** Wartości od 4 294 966 913 do 4 294 967 167 są zaokrąglane do **`float`** wartości 4 294 967 040.

## <a name="see-also"></a>Zobacz także

[Obliczenia matematyczne zmiennoprzecinkowe](../c-language/floating-point-math.md)
