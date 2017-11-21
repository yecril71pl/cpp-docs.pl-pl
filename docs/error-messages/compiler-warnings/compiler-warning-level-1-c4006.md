---
title: "Kompilatora (poziom 1) ostrzeżenie C4006 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4006
dev_langs: C++
helpviewer_keywords: C4006
ms.assetid: f1a59819-0fd2-4361-8e3a-99e4b514b8e1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d7c09f256223decda7d2a2e52cd6cb8c29f21b1b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4006"></a>Kompilator C4006 ostrzegawcze (poziom 1)
\#undef Oczekiwano identyfikatora  
  
 `#undef` Dyrektywy nie określa identyfikator, aby nie zdefiniowany. Dyrektywa jest ignorowana. Aby rozwiązać ostrzeżenia, należy określić identyfikator. Poniższy przykład generuje C4006:  
  
```  
// C4006.cpp  
// compile with: /W1  
#undef   // C4006  
  
// try..  
// #undef TEST  
  
int main() {  
}  
```