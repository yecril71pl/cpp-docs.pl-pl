---
title: Niezawodność
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 108b4c9dde08adf1a3c54c810f68be69bf150472
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739601"
---
# <a name="robustness"></a>Niezawodność

Użyj następujących funkcji biblioteki wykonawczej języka C, aby zwiększyć niezawodność programu.

## <a name="run-time-robustness-functions"></a>Funkcje niezawodności w czasie wykonywania

|Funkcja|Zastosowanie|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Przenosi kontrolę do mechanizmu obsługi błędów, jeśli **Nowy** operator nie może przydzielić pamięci.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Obsługuje wyjątki Win32 (wyjątki strukturalne C) C++ jako wyjątki z określonym typem.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Instaluje własną funkcję zakończenia, która ma zostać wywołana przez [zakończenie](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instaluje własną funkcję zakończenia, która ma zostać wywołana przez [nieoczekiwane](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
