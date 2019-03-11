---
title: Niezawodność
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: c70c9a2bf0b95063fa3f679ca6c3053d2a4f2df5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744570"
---
# <a name="robustness"></a>Niezawodność

Użyj następujących funkcji biblioteki wykonawczej C do poprawy niezawodności programu.

## <a name="run-time-robustness-functions"></a>Funkcje środowiska wykonawczego niezawodności

|Funkcja|Zastosowanie|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Przekazuje sterowanie do Twojej mechanizm obsługi błędów, jeśli **nowe** operator nie może przydzielić pamięci.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Wyjątki Win32 dojścia (wyjątki strukturalne C), co kod C++ wpisane wyjątków.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Instaluje własną funkcję zakończenia ma zostać wywołana przez [zakończyć](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instaluje własną funkcję zakończenia ma zostać wywołana przez [nieoczekiwany](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](https://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)<br/>
