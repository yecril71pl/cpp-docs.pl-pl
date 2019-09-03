---
title: setlocale, pragma
ms.date: 08/29/2019
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: 219354595e5c63b2f13211d43bfa517d97413251
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218178"
---
# <a name="setlocale-pragma"></a>setlocale, pragma

Definiuje *Ustawienia regionalne*, kraj, region i język, które mają być używane podczas tłumaczenia stałych znaków dwubajtowych i literałów ciągów.

## <a name="syntax"></a>Składnia

> **#pragma setlocaling ("** [ *Local-String* ] **")**

## <a name="remarks"></a>Uwagi

Ponieważ algorytm konwersji znaków wielobajtowych na znaki szerokie może różnić się w zależności od ustawień regionalnych lub kompilacja może odbywać się w różnych ustawieniach regionalnych z lokalizacji, w której zostanie uruchomiony plik wykonywalny, ta pragma zapewnia sposób określania docelowych ustawień regionalnych w czasie kompilacji. Gwarantuje on, że ciągi znaków dwubajtowych są przechowywane w prawidłowym formacie.

Domyślnym ustawieniem *Local-String* jest "".

Ustawienia regionalne "C" mapują każdy znak w ciągu na jego wartość jako **wchar_t**. Inne prawidłowe wartości dla `setlocale` to wpisy znalezione na liście [ciągów języka](../c-runtime-library/language-strings.md) . Na przykład można określić:

```cpp
#pragma setlocale("dutch")
```

Możliwość określenia ciągu języka zależy od strony kodowej i obsługi identyfikatora języka na komputerze.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
