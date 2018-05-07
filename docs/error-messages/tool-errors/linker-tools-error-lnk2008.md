---
title: Błąd narzędzi konsolidatora LNK2008 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4ee6a8a4c4cc6d33f47d5335daa9fccd4e5fd99
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2008"></a>Błąd narzędzi konsolidatora LNK2008
Cel naprawy nie jest wyrównany symbol_name  
  
 ŁĄCZE znaleziono cel naprawy w pliku obiektu, który nie został prawidłowo wyrównane.  
  
 Przyczyną tego błędu może być wyrównanie sekcji niestandardowe (na przykład #pragma [pakietu](../../preprocessor/pack.md)), [Dopasuj](../../cpp/align-cpp.md) modyfikator, lub za pomocą kodu języka zestawu, który modyfikuje wyrównanie sekcji.  
  
 Jeśli kod nie wykorzystuje dowolne z powyższych, może być spowodowane przez kompilator.