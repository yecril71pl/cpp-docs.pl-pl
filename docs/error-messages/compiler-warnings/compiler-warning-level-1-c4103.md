---
title: "Kompilatora (poziom 1) ostrzeżenie C4103 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4103
dev_langs:
- C++
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 115c88a43f38065541fe925b023d61679c06be53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4103"></a>Kompilator C4103 ostrzegawcze (poziom 1)
"filename": wyrównanie zmieniono po dołączeniu nagłówka, może być spowodowany brakiem elementu #pragma pack(pop)  
  
 Pakowanie ma wpływ na układ klasy, a często, jeśli pakowania zmian przez pliki nagłówkowe, mogą być problemy.  
  
 Użyj #pragma [pakietu](../../preprocessor/pack.md)(pop) przed zamknięciem pliku nagłówka do rozwiązania to ostrzeżenie.  
  
 Poniższy przykład generuje C4103:  
  
```  
// C4103.h  
#pragma pack(push, 4)  
  
// defintions and declarations  
  
// uncomment the following line to resolve  
// #pragma pack(pop)  
```  
  
 a następnie  
  
```  
// C4103.cpp  
// compile with: /LD /W1  
#include "c4103.h"   // C4103  
```