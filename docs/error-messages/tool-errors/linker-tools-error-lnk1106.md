---
title: Błąd narzędzi konsolidatora LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 091d4e173bfb2eff8ffee2b5c30647f4d5e3bc04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195373"
---
# <a name="linker-tools-error-lnk1106"></a>Błąd narzędzi konsolidatora LNK1106

nieprawidłowy plik lub dysk: nie można przejść do lokalizacji

Narzędzie nie mogło odczytać lub zapisać w `location` w pliku mapowanym na pamięć.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Dysk jest zapełniony.

   Zwolnij trochę miejsca i Połącz ponownie.

1. Próba połączenia przez sieć.

   Niektóre sieci nie obsługują w pełni plików mapowanych na pamięć używanych przez konsolidator. Spróbuj połączyć się na dysku lokalnym.

1. Zły blok na dysku.

   Mimo że sprzęt systemu operacyjnego i dysku powinien wykryć taki błąd, można uruchomić program do sprawdzania dysku.

1. Za mało miejsca na stercie.

   Aby uzyskać więcej informacji, zobacz [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) .
