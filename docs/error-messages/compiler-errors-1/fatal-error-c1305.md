---
title: Błąd krytyczny C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 988842a0d5e8002ffd1478a2e10a8c88ee971911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397500"
---
# <a name="fatal-error-c1305"></a>Błąd krytyczny C1305

Baza danych profilu "pgd_file" jest przeznaczona dla innej architektury

Plik .pgd, który został wygenerowany przez operację pginstrument dla innej platformy został przekazany do [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optymalizacje sterowane profilem](../../build/profile-guided-optimizations.md) są dostępne dla x86 i x64 64. Jednak nie jest prawidłowy plik .pgd wygenerowany z operacją pginstrument na jednej platformie jako dane wejściowe /LTCG:PGOPTIMIZE dla różnych platform.

Aby rozwiązać ten problem, Przekaż tylko plik .pgd utworzone za pomocą pginstrument do /LTCG:PGOPTIMIZE na jednej platformie.