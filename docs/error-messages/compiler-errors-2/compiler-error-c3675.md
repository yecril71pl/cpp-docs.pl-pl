---
title: "C3675 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3675
dev_langs: C++
helpviewer_keywords: C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6545b7cfa8232ba8b48df104ce848eb34c0e108c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3675"></a>C3675 błąd kompilatora
"Funkcja": jest zarezerwowana, ponieważ zdefiniowano "property"  
  
 Deklaracja właściwości prostej kompilator generuje get i metody dostępu set i tych nazw znajdują się w zakresie programu.  Generowane przez kompilator nazwy są tworzone przez poprzedzenie jej get_ i set_ nazwę właściwości.  W związku z tym nie można zadeklarować funkcji z taką samą nazwę jak metodach dostępu generowanych przez kompilator.  
  
 Zobacz [właściwości](../../windows/property-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3675.  
  
```  
// C3675.cpp  
// compile with: /clr /c  
ref struct C {  
public:  
   property int Size;  
   int get_Size() { return 0; }   // C3675  
};  
```