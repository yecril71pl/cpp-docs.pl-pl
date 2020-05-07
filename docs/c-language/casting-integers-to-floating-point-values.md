---
title: Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: 8fa013668278fae82bcb2bb9eb1f2aec3cb61581
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312651"
---
# <a name="casting-integers-to-floating-point-values"></a>Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe

**3.2.1.3 ANSI** Kierunek obcinania, gdy numer całkowity jest konwertowany na liczbę zmiennoprzecinkową, która nie może dokładnie reprezentować pierwotnej wartości

Gdy całkowita liczba jest rzutowana na wartość zmiennoprzecinkową, która nie może dokładnie reprezentować wartości, wartość jest zaokrąglana (w górę lub w dół) do najbliższej odpowiedniej wartości.

Na przykład rzutowanie nieoznaczonej **długości** (o 32 bitów precyzji) do wartości **zmiennoprzecinkowej** (którego mantysy ma 23 bity precyzji) zaokrągla liczbę do najbliższej wielokrotności 256. Wartości **Long** od 4 294 966 913 do 4 294 967 167 są zaokrąglane do wartości **zmiennoprzecinkowej** 4 294 967 040.

## <a name="see-also"></a>Zobacz też

[Obliczenia matematyczne na liczbach zmiennoprzecinkowych](../c-language/floating-point-math.md)
