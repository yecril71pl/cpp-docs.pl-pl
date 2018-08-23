---
title: Błąd krytyczny C1305 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90d73003d9f19eb41f9eb34cd47c7b90b1e6164f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465249"
---
# <a name="fatal-error-c1305"></a>Błąd krytyczny C1305
Baza danych profilu "pgd_file" jest przeznaczona dla innej architektury  
  
 Plik .pgd, który został wygenerowany przez operację pginstrument dla innej platformy został przekazany do [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md) są dostępne dla x86 i x64 64. Jednak nie jest prawidłowy plik .pgd wygenerowany z operacją pginstrument na jednej platformie jako dane wejściowe /LTCG:PGOPTIMIZE dla różnych platform.  
  
 Aby rozwiązać ten problem, Przekaż tylko plik .pgd utworzone za pomocą pginstrument do /LTCG:PGOPTIMIZE na jednej platformie.