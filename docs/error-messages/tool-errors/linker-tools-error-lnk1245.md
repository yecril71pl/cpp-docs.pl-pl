---
title: "Błąd narzędzi konsolidatora LNK1245 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1245
dev_langs: C++
helpviewer_keywords: LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e937962fc71b0767dce94614f0505c2d30e915bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1245"></a>Błąd narzędzi konsolidatora LNK1245
Nieprawidłowy podsystem "podsystemu" określono; / SUBSYSTEM musi być systemu WINDOWS, WINDOWSCE lub CONSOLE  
  
 [/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) była używana do kompilowania obiektu i odnosi się jeden z następujących warunków:  
  
-   Punkt wejścia niestandardowych został zdefiniowany ([/Entry](../../build/reference/entry-entry-point-symbol.md)), w taki sposób, że konsolidator nie można wywnioskować podsystemu.  
  
-   Wartość został przekazany do [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opcji konsolidatora, która jest nieprawidłowa dla obiektów w/CLR.  
  
 Dla obu sytuacjach rozdzielczość jest Określ prawidłową wartość do/Subsystem — opcja konsolidatora.