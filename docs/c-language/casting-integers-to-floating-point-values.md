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

**ANSI 3.2.1.3** kierunek obcinania, gdy całkowite liczba jest konwertowana na liczbę zmiennoprzecinkową, która dokładnie nie może reprezentować wartość oryginalną

Gdy liczbą całkowitą jest rzutowany na wartość zmiennoprzecinkową, która dokładnie nie może reprezentować wartość, wartość jest zaokrąglana (górę lub w dół) do najbliższej odpowiednią wartość.

Na przykład rzutowanie **unsigned long** (z 32-bitowy precyzji) na **float** (których mantysy ma 23 bitów precyzji) Zaokrągla liczbę do najbliższej wielokrotności 256. **Długie** 4,294,966,913 do 4,294,967,167 wartości są zaokrąglane do **float** wartość 4,294,967,040.

## <a name="see-also"></a>Zobacz także

[Obliczenia matematyczne na liczbach zmiennoprzecinkowych](../c-language/floating-point-math.md)
