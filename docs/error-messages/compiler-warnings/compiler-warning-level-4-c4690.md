---
title: "Kompilatora (poziom 4) ostrzeżenie C4690 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4690
dev_langs: C++
helpviewer_keywords: C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e1307a571e38cf7e4ef81f7c9c08a07bf5c833c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4690"></a>Kompilator C4690 ostrzegawcze (poziom 4)
[ emitidl( pop ) ] : więcej zdejmowań niż włożeń  
  
 [Emitidl](../../windows/emitidl.md) atrybut został zdjęte ze stosu jeszcze raz, który został naciśnięty go.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4690.  
  
```  
// C4690.cpp  
// compile with: /c /W4  
[emitidl(pop)];   // C4690  
class x {};  
```