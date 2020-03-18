---
title: Niezawodność
ms.date: 11/04/2016
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 5e13152b2c31511cce4df9976d6c800960c099a5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444888"
---
# <a name="robustness"></a>Niezawodność

Użyj następujących funkcji biblioteki wykonawczej języka C, aby zwiększyć niezawodność programu.

## <a name="run-time-robustness-functions"></a>Funkcje niezawodności w czasie wykonywania

|Funkcja|Użycie|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Przenosi kontrolę do mechanizmu obsługi błędów, jeśli **Nowy** operator nie może przydzielić pamięci.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Obsługuje wyjątki Win32 (wyjątki strukturalne C) C++ jako wyjątki z określonym typem.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Instaluje własną funkcję zakończenia, która ma zostać wywołana przez [zakończenie](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instaluje własną funkcję zakończenia, która ma zostać wywołana przez [nieoczekiwane](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
