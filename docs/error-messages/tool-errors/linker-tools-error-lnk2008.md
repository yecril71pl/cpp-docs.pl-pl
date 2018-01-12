---
title: "Błąd narzędzi konsolidatora LNK2008 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2008
dev_langs: C++
helpviewer_keywords: LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a7c2fecff55677653c25c7d87fb22fa984526159
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2008"></a>Błąd narzędzi konsolidatora LNK2008
Cel naprawy nie jest wyrównany symbol_name  
  
 ŁĄCZE znaleziono cel naprawy w pliku obiektu, który nie został prawidłowo wyrównane.  
  
 Przyczyną tego błędu może być wyrównanie sekcji niestandardowe (na przykład #pragma [pakietu](../../preprocessor/pack.md)), [Dopasuj](../../cpp/align-cpp.md) modyfikator, lub za pomocą kodu języka zestawu, który modyfikuje wyrównanie sekcji.  
  
 Jeśli kod nie wykorzystuje dowolne z powyższych, może być spowodowane przez kompilator.