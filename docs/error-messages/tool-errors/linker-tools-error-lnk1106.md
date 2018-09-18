---
title: Błąd narzędzi konsolidatora LNK1106 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1106
dev_langs:
- C++
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 719ff1a87f3f1afc19cf38736c0059c46a8a9bdc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110877"
---
# <a name="linker-tools-error-lnk1106"></a>Błąd narzędzi konsolidatora LNK1106

Nieprawidłowy plik lub dysk jest pełny: nie można przejść do lokalizacji

Narzędzie nie można odczytać lub zapisać `location` w pliku mapowanych na pamięć.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Dysk jest zapełniony.

     Zwolnij trochę miejsca i połącz ponownie.

1. Podjęto próbę połączenia za pośrednictwem sieci.

     Niektóre sieci nie obsługują w pełni pliki mapowane w pamięci używane przez konsolidator. Spróbuj konsolidacji na dysku lokalnym.

1. Nieprawidłowy blok na dysku.

     Mimo że system operacyjny i sprzęt dysku powinien mieć wykryte takiego komunikatu o błędzie, możesz uruchomić program sprawdzania dysku.

1. Brak miejsca na stosie.

     Zobacz [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) Aby uzyskać więcej informacji.