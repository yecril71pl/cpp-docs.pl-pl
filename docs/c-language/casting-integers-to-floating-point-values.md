---
title: Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a81b72a7dfedbc1d6033d53bde63be22943abb08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055224"
---
# <a name="casting-integers-to-floating-point-values"></a>Rzutowanie liczb całkowitych na wartości zmiennoprzecinkowe

**ANSI 3.2.1.3** kierunek obcinania, gdy całkowite liczba jest konwertowana na liczbę zmiennoprzecinkową, która dokładnie nie może reprezentować wartość oryginalną

Gdy liczbą całkowitą jest rzutowany na wartość zmiennoprzecinkową, która dokładnie nie może reprezentować wartość, wartość jest zaokrąglana (górę lub w dół) do najbliższej odpowiednią wartość.

Na przykład rzutowanie **unsigned long** (z 32-bitowy precyzji) na **float** (których mantysy ma 23 bitów precyzji) Zaokrągla liczbę do najbliższej wielokrotności 256. **Długie** 4,294,966,913 do 4,294,967,167 wartości są zaokrąglane do **float** wartość 4,294,967,040.

## <a name="see-also"></a>Zobacz też

[Obliczenia matematyczne na liczbach zmiennoprzecinkowych](../c-language/floating-point-math.md)