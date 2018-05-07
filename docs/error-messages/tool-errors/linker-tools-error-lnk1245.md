---
title: Błąd narzędzi konsolidatora LNK1245 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47a1c2e5f7bf66946dcc5816d7a20fd485b59b45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1245"></a>Błąd narzędzi konsolidatora LNK1245
Nieprawidłowy podsystem "podsystemu" określono; / SUBSYSTEM musi być systemu WINDOWS, WINDOWSCE lub CONSOLE  
  
 [/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) była używana do kompilowania obiektu i odnosi się jeden z następujących warunków:  
  
-   Punkt wejścia niestandardowych został zdefiniowany ([/Entry](../../build/reference/entry-entry-point-symbol.md)), w taki sposób, że konsolidator nie można wywnioskować podsystemu.  
  
-   Wartość został przekazany do [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opcji konsolidatora, która jest nieprawidłowa dla obiektów w/CLR.  
  
 Dla obu sytuacjach rozdzielczość jest Określ prawidłową wartość do/Subsystem — opcja konsolidatora.