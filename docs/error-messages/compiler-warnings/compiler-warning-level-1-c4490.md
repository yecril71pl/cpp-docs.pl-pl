---
title: "Kompilatora (poziom 1) ostrzeżenie C4490 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4490
dev_langs: C++
helpviewer_keywords: C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 544c02ab08d18cf1596f588439183bba8a6edc57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4490"></a>Kompilator C4490 ostrzegawcze (poziom 1)
"override": nieprawidłowe użycie specyfikatora override; "Funkcja" jest niezgodny z metody podstawowej klasy referencyjnej  
  
 Specyfikator przesłonięcia zostało niepoprawnie użyte. Na przykład nie zastępuje funkcję interfejsu, go zaimplementować.  
  
 Aby uzyskać więcej informacji, zobacz [specyfikatory Override](../../windows/override-specifiers-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4490.  
  
```  
// C4490.cpp  
// compile with: /clr /c /W1  
  
interface struct IFace {  
   void Test();  
};  
  
ref struct Class1 : public IFace {  
   virtual void Test() override {}   // C4490  
   // try the following line instead  
   // virtual void Test() {}  
};  
```