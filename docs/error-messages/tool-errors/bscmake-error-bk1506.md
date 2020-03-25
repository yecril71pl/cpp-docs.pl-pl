---
title: Błąd BSCMAKE BK1506
ms.date: 11/04/2016
f1_keywords:
- BK1506
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
ms.openlocfilehash: b272a12e1d729e33794b550c911fd2e56f1af006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197798"
---
# <a name="bscmake-error-bk1506"></a>Błąd BSCMAKE BK1506

nie można otworzyć pliku "filename" [: Przyczyna]

BSCMAKE nie może otworzyć pliku.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Plik zablokowany przez inny proces. Jeśli `reason` mówi **uprawnienia**, przeglądarka może korzystać z pliku. Zamknij okno przeglądania i ponów próbę kompilacji.

1. Pełny dysk.

1. Błąd sprzętowy.

1. Określony plik wyjściowy ma taką samą nazwę jak istniejący podkatalog.
