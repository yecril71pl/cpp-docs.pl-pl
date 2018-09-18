---
title: Kompilator ostrzeżenie (poziom 1) C4656 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4656
dev_langs:
- C++
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3334b9448dd6e9d47ed0b3ee3e4dfb9dfc57b57f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032416"
---
# <a name="compiler-warning-level-1-c4656"></a>Kompilator ostrzeżenie (poziom 1) C4656

'symbol': typ danych nowego została zmieniona od czasu ostatniej kompilacji lub zdefiniowanej w różny sposób w innym miejscu

Możesz dodać lub zmienić typu danych, dzięki czemu nowe do kodu źródłowego od czasu ostatniej zakończonej pomyślnie kompilacji. Edytuj i Kontynuuj nie obsługuje zmian do istniejących typów danych.

To ostrzeżenie będzie zawsze występować [krytyczny C1092 błąd](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Aby usunąć to ostrzeżenie, bez przerywania bieżącej sesji debugowania

1. Zmiana typu danych, wróć do stanu przed błędu.

1. Z **debugowania** menu, wybierz **zastosowanie zmian kodu**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Aby usunąć ten błąd bez wprowadzania zmian w kodzie źródłowym

1. Z **debugowania** menu, wybierz **Zatrzymaj debugowanie**.

1. Z **kompilacji** menu, wybierz **kompilacji**.