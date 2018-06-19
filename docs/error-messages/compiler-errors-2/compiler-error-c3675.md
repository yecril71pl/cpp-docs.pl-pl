---
title: C3675 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4aaa53ae1d92364fad143f127ee3e7b504acdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273647"
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