---
title: "Ostrzeżenie LNK4022 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4022
dev_langs: C++
helpviewer_keywords: LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7bd9553f158a64960a068942fcb25d3d9019f7bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4022"></a>Ostrzeżenie LNK4022 narzędzi konsolidatora
Nie można znaleźć unikatowego dopasowania dla symbolu "symbol"  
  
 ŁĄCZE lub znaleziono wiele LIB odpowiada dla podanego symbolu bez i nie można rozpoznać niejednoznaczności. Nie pliku wyjściowego (.exe, .dll, .exp lub lib) jest tworzony. To ostrzeżenie występuje jeden ostrzeżenie [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) dla każdego zduplikowany symbol i na koniec następuje błąd krytyczny [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).  
  
 Aby uniknąć tego ostrzeżenia, należy określić symbol w postaci dekorowany. Uruchom [DUMPBIN](../../build/reference/dumpbin-options.md) na obiekcie, aby wyświetlić nazwy ozdobione.