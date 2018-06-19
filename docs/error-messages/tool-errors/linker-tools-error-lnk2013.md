---
title: Błąd narzędzi konsolidatora LNK2013 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9320b9ead0276b6fb5e1b9773260049a01520e12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299854"
---
# <a name="linker-tools-error-lnk2013"></a>Błąd narzędzi konsolidatora LNK2013
przepełnienie naprawy typ naprawy. Docelowy "Nazwa symbolu" jest poza zakresem  
  
 Konsolidator przekroczenie limitu rozmiaru adresu niezbędne lub przesunięcie w danej instrukcji ponieważ symbolu docelowego jest zbyt daleko od lokalizacji tę instrukcję.  
  
 Ten problem można rozwiązać, tworząc wiele obrazów, lub za pomocą [/kolejność](../../build/reference/order-put-functions-in-order.md) opcja tak instrukcji i obiekt docelowy jest zmniejszany.  
  
 Gdy nazwa symbolu jest symbol zdefiniowany przez użytkownika (i nie symbol generowane przez kompilator), można użyć również następujące czynności, aby usunąć błąd:  
  
-   Zmień funkcję statyczną aby była niestatycznego.  
  
-   Zmień nazwę sekcji kodu zawierającego funkcję statyczną aby była taka sama jak obiekt wywołujący.  
  
 Użyj `DUMPBIN /SYMBOLS`, aby sprawdzić, czy funkcja jest statyczne.