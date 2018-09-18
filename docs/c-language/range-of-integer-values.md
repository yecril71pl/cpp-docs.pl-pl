---
title: Zakres liczby całkowitej wartości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d940824e6bb1dc728cb999c1e820cb7adcedf8ce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092651"
---
# <a name="range-of-integer-values"></a>Zakres wartości całkowitych

**ANSI 3.1.2.5** oświadczenia i zestawy wartości różnych typów całkowitych

Liczby całkowite zawiera 32-bitowy (czterech bajtach). Oznaczone liczby całkowite są zapisywane w kodzie dopełnień do dwóch. Najbardziej znaczący bit utrzymuje znak: 1 dla wartości ujemnych, 0 dla wartości dodatnich i zera. Wartości są wymienione poniżej:

|Typ|Minimalne i maksymalne|
|----------|-------------------------|
|**short bez znaku**|od 0 do 65535|
|`signed short`|-32768 do 32767|
|`unsigned long`|0, 4294967295|
|**podpisana długo**|-2147483648 do 2147483647|

## <a name="see-also"></a>Zobacz też

[Liczby całkowite](../c-language/integers.md)