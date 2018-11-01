---
title: Kompilator ostrzeżenie (poziom 1) C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: aff78dbed217a6d9c5bc2a315ef12a33fe6caf0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514858"
---
# <a name="compiler-warning-level-1-c4655"></a>Kompilator ostrzeżenie (poziom 1) C4655

> "*symbol*": typ zmiennej jest nowy od czasu ostatniej kompilacji lub zdefiniowanej w różny sposób w innym miejscu

## <a name="remarks"></a>Uwagi

Zmienić lub dodać nowy typ danych od czasu ostatniej zakończonej pomyślnie kompilacji. Edytuj i Kontynuuj nie obsługuje zmian do istniejących typów danych.

To ostrzeżenie jest poprzedzony [krytyczny C1092 błąd](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Aby usunąć to ostrzeżenie, bez przerywania bieżącej sesji debugowania

1. Zmiana typu danych, wróć do stanu przed błędu.

2. Z **debugowania** menu, wybierz **zastosowanie zmian kodu**.

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Aby usunąć to ostrzeżenie bez wprowadzania zmian w kodzie źródłowym

1. Z **debugowania** menu, wybierz **Zatrzymaj debugowanie**.

2. Z **kompilacji** menu, wybierz **kompilacji**.