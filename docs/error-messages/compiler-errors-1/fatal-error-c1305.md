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
ms.openlocfilehash: 3cb1cf19d0fc4152fbb458d684972bb5a4418f37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227150"
---
# <a name="fatal-error-c1305"></a>Błąd krytyczny C1305
Baza danych profilów "pgd_file" jest przeznaczony dla innej architektury  
  
 Plik .pgd, który został wygenerowany przez operację /LTCG:PGINSTRUMENT dla innej platformy został przekazany do [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md) są dostępne dla x86 i [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platform. Jednak nie jest prawidłowy plik .pgd wygenerowane z operacją /LTCG:PGINSTRUMENT dla jednej platformie jako dane wejściowe /LTCG:PGOPTIMIZE dla różnych platform.  
  
 Aby rozwiązać ten problem, należy przekazać tylko plik .pgd, który jest tworzony z /LTCG:PGINSTRUMENT do /LTCG:PGOPTIMIZE na tej samej platformy.