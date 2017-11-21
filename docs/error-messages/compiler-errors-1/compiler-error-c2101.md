---
title: "C2101 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2101
dev_langs: C++
helpviewer_keywords: C2101
ms.assetid: 42f0136f-8cc1-4f2b-be1c-721ec9278e66
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 035b0d70a75652edb5ba01357076ba9942acdfae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2101"></a>C2101 błąd kompilatora
"&" dla stałej  
  
 Address-of — operator ( `&` ) musi mieć wartość l jako argument.  
  
 Poniższy przykład generuje C2101:  
  
```  
// C2101.cpp  
int main() {  
   char test;  
   test = &'a';   // C2101  
   test = 'a';   // OK  
}  
```