---
title: "Kompilatora (poziom 1) ostrzeżenie C4237 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4237
dev_langs: C++
helpviewer_keywords: C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2b4608309e10f9cd7256c20e3bdc5531a6121b60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4237"></a>Kompilator C4237 ostrzegawcze (poziom 1)
słowo kluczowe "— słowo kluczowe" jest nie jest jeszcze obsługiwane, ale zarezerwowane do użytku w przyszłości  
  
 Słowo kluczowe w specyfikacji języka C++ nie jest zaimplementowana w kompilatorze języka Visual C++, ale słowo kluczowe nie jest dostępna symbolu zdefiniowane przez użytkownika.  
  
 Poniższy przykład generuje C4237:  
  
```  
// C4237.cpp  
// compile with: /W1 /c  
int export;   // C4237  
```