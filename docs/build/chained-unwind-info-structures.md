---
title: "Łańcuchowej Unwind struktury informacji o | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ac09c1f107b51542b7a17c8661eb784b4abf14a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="chained-unwind-info-structures"></a>Struktury informacji o operacji łańcuchowej unwind
Jeśli ustawiono flagi UNW_FLAG_CHAININFO, struktura informacji unwind ubocznym i pole udostępnionego adresu — program obsługi/łańcuchowej — informacje o wyjątku zawiera informacje unwind podstawowego. Następujące pobiera kod podstawowy unwind informacji, przy założeniu, że `unwindInfo` jest struktura, która ma UNW_FLAG_CHAININFO Flaga.  
  
```  
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);  
```  
  
 Informacje łańcuchowa jest przydatne w sytuacjach dwa. Po pierwsze może służyć segmentów nieciągłe kodu. Za pomocą łańcuchowa informacje, można zmniejszyć rozmiar unwind wymagane informacje, ponieważ nie masz mają zostać zduplikowane tablicy kody unwind z informacji unwind podstawowego.  
  
 Umożliwia także łańcuchowa informacji do grupowania zapisuje volatile rejestru. Kompilator może być opóźniona zapisywania niektórych volatile rejestrów momentu poza prologu wejścia funkcji. Można to zapisać dzięki użyciu informacji unwind głównej części funkcji przed grupowanych kodu, a następnie konfigurowania powiązane informacje o rozmiarze niezerowy prologu, gdzie kody unwind łańcuchowa informacji odzwierciedlają zapisuje nieulotnej rejestrów. W takim przypadku kody unwind są wszystkie wystąpienia UWOP_SAVE_NONVOL. Grupa, która zapisuje nieulotnej rejestrów za pomocą WYPYCHANIA lub modyfikuje rejestr źródło za pomocą alokacji stosu stałym dodatkowe nie jest obsługiwane.  
  
 Element UNWIND_INFO UNW_FLAG_CHAININFO ustawić może zawierać wpis RUNTIME_FUNCTION, którego element UNWIND_INFO ma również UNW_FLAG_CHAININFO Ustaw (shrink-wrapping wielu). Po pewnym czasie łańcuchowej unwind informacje może wskaźniki pojawią się na element UNWIND_INFO UNW_FLAG_CHAININFO wyczyszczone; jest to elementu UNWIND_INFO podstawowego wskazuje punktu wejścia procedury rzeczywistych.  
  
## <a name="see-also"></a>Zobacz też  
 [Dane operacji Unwind dla obsługi wyjątków, obsługa debugera](../build/unwind-data-for-exception-handling-debugger-support.md)