---
title: "C2523 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2523
dev_langs: C++
helpviewer_keywords: C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d9ec6a9196498f210e680acf17efd34ac84faf77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2523"></a>C2523 błąd kompilatora
"klasy:: ~ identyfikator": niezgodność tagu destruktora/finalizatora  
  
 Nazwa destruktora musi być nazwą klasy poprzedzone tyldy (`~`). Konstruktor i destruktor są tylko elementy członkowskie, które mają taką samą nazwę jak klasa.  
  
 Poniższy przykład generuje C2523:  
  
```  
// C2523.cpp  
// compile with: /c  
class A {  
   ~B();    // C2523  
   ~A();   // OK  
};  
```