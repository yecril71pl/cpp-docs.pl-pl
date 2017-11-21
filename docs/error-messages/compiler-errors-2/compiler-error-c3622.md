---
title: "C3622 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3622
dev_langs: C++
helpviewer_keywords: C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a5ebccc9fb6cc8c25a8a6b42ae3b99439b1f5d44
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3622"></a>C3622 błąd kompilatora
"class": klasy zadeklarowanej jako "— słowo kluczowe" nie można utworzyć wystąpienia  
  
Podjęto próbę utworzenia wystąpienia klasy oznaczonej jako [abstrakcyjny](../../windows/abstract-cpp-component-extensions.md). Klasa jest oznaczona jako `abstract` może być klasą podstawową, ale nie można utworzyć wystąpienia.  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C3622.  
  
```  
// C3622.cpp  
// compile with: /clr  
ref class a abstract {};  
  
int main() {  
   a aa;   // C3622  
}  
```  
