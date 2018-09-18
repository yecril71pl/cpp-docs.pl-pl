---
title: Błąd krytyczny C1092 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1092
dev_langs:
- C++
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9852b7b3d695d5414e52727ce672ee3258f6840b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077155"
---
# <a name="fatal-error-c1092"></a>Błąd krytyczny C1092

Edytuj i Kontynuuj nie obsługuje zmiany typów danych; Tworzenie wymagane

Zmienione lub dodane typu danych od czasu ostatniej zakończonej pomyślnie kompilacji.

- Edytuj i Kontynuuj nie obsługuje zmian do istniejących typów danych, w tym definicji klasy, struktury lub typu wyliczeniowego. Należy zatrzymać debugowanie i skompilować aplikację.

- Edytuj i Kontynuuj nie obsługuje dodawania nowych typów danych, jeśli plik bazy danych programu, takie jak vc*x*pdb 0 (gdzie *x* jest główną wersją Visual C++ w użyciu) jest tylko do odczytu. Aby dodać typy danych, kompilator należy otworzyć plik .pdb w trybie zapisu.

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Aby usunąć ten błąd nie kończy bieżącą sesję debugowania

1. Zmiana typu danych, wróć do stanu przed błędu.

1. Z **debugowania** menu, wybierz **zastosowanie zmian kodu**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Aby usunąć ten błąd bez wprowadzania zmian w kodzie źródłowym

1. Z **debugowania** menu, wybierz **Zatrzymaj debugowanie**.

1. Z **kompilacji** menu, wybierz **kompilacji**.

Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu](/visualstudio/debugger/supported-code-changes-cpp).