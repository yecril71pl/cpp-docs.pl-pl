---
title: Ostrzeżenie LNK4022 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4022
dev_langs:
- C++
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cffb9c4c67bc3003b8dcdda0ad3a2e8d55abe932
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300374"
---
# <a name="linker-tools-warning-lnk4022"></a>Ostrzeżenie LNK4022 narzędzi konsolidatora
Nie można znaleźć unikatowego dopasowania dla symbolu "symbol"  
  
 ŁĄCZE lub znaleziono wiele LIB odpowiada dla podanego symbolu bez i nie można rozpoznać niejednoznaczności. Nie pliku wyjściowego (.exe, .dll, .exp lub lib) jest tworzony. To ostrzeżenie występuje jeden ostrzeżenie [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) dla każdego zduplikowany symbol i na koniec następuje błąd krytyczny [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).  
  
 Aby uniknąć tego ostrzeżenia, należy określić symbol w postaci dekorowany. Uruchom [DUMPBIN](../../build/reference/dumpbin-options.md) na obiekcie, aby wyświetlić nazwy ozdobione.