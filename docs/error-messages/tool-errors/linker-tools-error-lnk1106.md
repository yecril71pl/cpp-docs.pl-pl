---
title: Błąd narzędzi konsolidatora LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 7551e2f3f1efc90913981feb674f48aadb9ace51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255322"
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