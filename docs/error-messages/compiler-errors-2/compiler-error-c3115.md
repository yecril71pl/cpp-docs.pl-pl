---
title: "C3115 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3115
dev_langs: C++
helpviewer_keywords: C3115
ms.assetid: 51726145-9782-4ec9-84b9-286f366d9cbd
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b50cf777b061f97e2243d32362c0c19247e2c97c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3115"></a>C3115 błąd kompilatora
"attribute": ten atrybut nie jest dozwolona w "konstrukcji"  
  
 Atrybut została zastosowana do konstrukcji, dla której po ewentualnym przypadkowym.  Zobacz [atrybuty w zależności od użycia](../../windows/attributes-by-usage.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3115.  
  
```  
// C3115.cpp  
// compile with: /c  
#include <unknwn.h>  
[module(name="xx")];  
  
[object, helpstringdll(xx.dll), uuid("00000000-0000-0000-0000-000000000001")]   // C3115  
// try the following line instead  
// [object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI {  
   HRESULT xx();  
};  
```