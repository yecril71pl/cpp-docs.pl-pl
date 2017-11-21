---
title: "C3247 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3247
dev_langs: C++
helpviewer_keywords: C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fc07da3d6fa994bfba9588b1169287da8c0d738b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3247"></a>C3247 błąd kompilatora
"class1": klasa coclass nie może dziedziczyć po innej klasie coclass "class2"  
  
 Klasy oznaczonej [coclass](../../windows/coclass.md) atrybutu nie może dziedziczyć po innej klasie oznaczonej przez `coclass` atrybutu.  
  
 Poniższy przykład generuje C3247:  
  
```  
// C3247.cpp  
[module(name="MyLib")];  
[coclass]  
class a {  
};  
  
[coclass]  
class b : public a {   // C3247  
};  
int main() {  
}  
```