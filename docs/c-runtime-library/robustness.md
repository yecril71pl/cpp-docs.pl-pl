---
title: "Niezawodność | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.runtime
dev_langs: C++
helpviewer_keywords: robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fb071b615d87ab1b605c78e5ba0645be139fba1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="robustness"></a>Niezawodność
Użyj następujących funkcji biblioteki wykonawczej języka C do poprawy niezawodności programu.  
  
### <a name="run-time-robustness-functions"></a>Funkcje niezawodności środowiska wykonawczego  
  
|Funkcja|Zastosowanie|  
|--------------|---------|  
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Przekazuje sterowanie z mechanizmu obsługi błędów, jeśli `new` operator nie może przydzielić pamięci.|  
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Uchwyty Win32 wyjątków (C strukturalnych wyjątkami) jako C++ wpisana wyjątków.|  
|[set_terminate —](../c-runtime-library/reference/set-terminate-crt.md)|Instaluje własnej funkcji zakończenia ma zostać wywołana przez [przerwanie](../c-runtime-library/reference/terminate-crt.md).|  
|[set_unexpected —](../c-runtime-library/reference/set-unexpected-crt.md)|Instaluje własnej funkcji zakończenia ma zostać wywołana przez [nieoczekiwany](../c-runtime-library/reference/unexpected-crt.md).|  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)   
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)