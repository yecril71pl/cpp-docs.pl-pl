---
title: Niezawodność | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 235eafb6fefb644ce5097b07b6cd55d91adf31aa
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="robustness"></a>Niezawodność

Użyj następujących funkcji biblioteki wykonawczej języka C do poprawy niezawodności programu.

## <a name="run-time-robustness-functions"></a>Funkcje niezawodności środowiska wykonawczego

|Funkcja|Zastosowanie|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Przekazuje sterowanie z mechanizmu obsługi błędów, jeśli **nowe** operator nie może przydzielić pamięci.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Uchwyty Win32 wyjątków (C strukturalnych wyjątkami) jako C++ wpisana wyjątków.|
|[set_terminate —](../c-runtime-library/reference/set-terminate-crt.md)|Instaluje własnej funkcji zakończenia ma zostać wywołana przez [przerwanie](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instaluje własnej funkcji zakończenia ma zostać wywołana przez [nieoczekiwany](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Zobacz też

[Universal C procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)<br/>
