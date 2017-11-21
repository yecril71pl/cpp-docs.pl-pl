---
title: "C2371 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2371
dev_langs: C++
helpviewer_keywords: C2371
ms.assetid: d383993d-05ef-4e35-8129-3b58a6f7b7b7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 01753e3b14df40592acba8979a85a727ddc34dd2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2371"></a>C2371 błąd kompilatora
"identyfikator": zmiana definicji; różne typy podstawowe  
  
 Identyfikator jest już zadeklarowany.  
  
 Poniższy przykład generuje C2371:  
  
```  
// C2371.cpp  
int main() {  
   int i;  
   float i;   // C2371, redefinition  
   float f;   // OK  
}  
```