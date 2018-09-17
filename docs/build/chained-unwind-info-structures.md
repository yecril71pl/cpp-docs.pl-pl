---
title: Łańcuchowej Unwind Info struktury | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6da09387595188026d855fb99a49b588e6f21aa3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715029"
---
# <a name="chained-unwind-info-structures"></a>Struktury informacji o operacji łańcuchowej unwind

Jeśli ustawiono flagę UNW_FLAG_CHAININFO, strukturę unwind info ubocznym i pole udostępnionego adresu — Obsługa/łańcuchowa — informacje o wyjątku zawiera informacje unwind podstawowego. Następujące pobiera kod podstawowy unwind informacji, przy założeniu, że `unwindInfo` to struktura, która ma UNW_FLAG_CHAININFO Flaga.

```
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Informacje łańcuchowych przydaje się w dwóch sytuacjach. Po pierwsze może służyć segmentów nieciągłego kodu. Za pomocą połączonych informacji, może zmniejszyć rozmiar informacji unwind wymagane, ponieważ nie masz zduplikowania tablica kody unwind info unwind podstawowego.

Informacje połączonych umożliwia również grupy zapisuje volatile rejestru. Kompilator może opóźnić zapisywania niektórych volatile rejestrów, dopóki nie znajduje się poza prologu wejścia funkcji. Można rejestrować to dzięki informacje unwind głównej części funkcji przed kodem pogrupowanych i konfigurując powiązane informacje o rozmiarze od zera prologu, gdzie kody łańcuchowych informacje z odwijania odzwierciedlają zapisuje nieulotnej rejestrów. W takim przypadku kody unwind są wszystkie wystąpienia elementu UWOP_SAVE_NONVOL. Grupa zapisuje nieulotnej rejestrów za pomocą instalacji WYPYCHANEJ lub modyfikuje rejestr RSP za pomocą alokacji dodatkowych, stałych stosu nie jest obsługiwane.

Element UNWIND_INFO UNW_FLAG_CHAININFO Ustaw może zawierać wpis RUNTIME_FUNCTION, którego element UNWIND_INFO ma również UNW_FLAG_CHAININFO Ustaw (shrink-wrapping wielu). Po pewnym czasie łańcuchowych elementu unwind info, wskaźniki zostanie wyświetlony element UNWIND_INFO UNW_FLAG_CHAININFO wyczyszczone; jest to główny element UNWIND_INFO wskazuje punkt wejścia procedury rzeczywistych.

## <a name="see-also"></a>Zobacz też

[Dane operacji Unwind dla obsługi wyjątków, obsługa debugera](../build/unwind-data-for-exception-handling-debugger-support.md)