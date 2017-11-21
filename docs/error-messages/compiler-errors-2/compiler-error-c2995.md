---
title: "C2995 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2995
dev_langs: C++
helpviewer_keywords: C2995
ms.assetid: a57cdfe0-b40b-4a67-a95c-1a49ace4842b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5c47d0930be7518dbef7cafd24e3767892f8f378
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2995"></a>C2995 błąd kompilatora
"Funkcja": szablon funkcji został już zdefiniowany.  
  
 Upewnij się, że istnieje tylko jedną definicję dla każdej funkcji członkowskiej klasy szablonu.  
  
 Poniższy przykład generuje C2995:  
  
```  
// C2995.cpp  
// compile with: /c  
template <class T>  
void Test(T x){}  
  
template <class T> void Test(T x){}   // C2995  
template <class T> void Test2(T x){}   // OK  
```