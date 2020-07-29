---
title: Niezawodność
ms.date: 11/04/2016
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 9de2611e29f5f9bfd08839517e873c3dda225af0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211596"
---
# <a name="robustness"></a>Niezawodność

Użyj następujących funkcji biblioteki wykonawczej języka C, aby zwiększyć niezawodność programu.

## <a name="run-time-robustness-functions"></a>Funkcje niezawodności w czasie wykonywania

|Funkcja|Zastosowanie|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Przenosi kontrolę do mechanizmu obsługi błędów, jeśli **`new`** nie można przydzielić pamięci przez operatora.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Obsługuje wyjątki Win32 (wyjątki strukturalne C) jako wyjątki z definicją języka C++.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Instaluje własną funkcję zakończenia, która ma zostać wywołana przez [zakończenie](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instaluje własną funkcję zakończenia, która ma zostać wywołana przez [nieoczekiwane](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Zobacz także

[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
