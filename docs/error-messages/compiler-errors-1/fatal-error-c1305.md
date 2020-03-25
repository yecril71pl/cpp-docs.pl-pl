---
title: Błąd krytyczny C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 6ad00eb3d95e9f09d4f84daefb7e2a87fd1a3abf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203362"
---
# <a name="fatal-error-c1305"></a>Błąd krytyczny C1305

Baza danych profilów "pgd_file" jest dla innej architektury

Plik. PGD wygenerowany z/LTCG: PGINSTRUMENT operacji dla innej platformy został przekazano do [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optymalizacje oparte na profilach](../../build/profile-guided-optimizations.md) są dostępne dla platform x86 i x64. Jednak plik. PGD wygenerowany przy użyciu operacji/LTCG: PGINSTRUMENT dla jednej platformy nie jest prawidłowy jako dane wejściowe do/LTCG: PGOPTIMIZE dla innej platformy.

Aby rozwiązać ten problem, należy przekazać plik. pgd, który został utworzony za pomocą/LTCG: PGINSTRUMENT do/LTCG: PGOPTIMIZE na tej samej platformie.
