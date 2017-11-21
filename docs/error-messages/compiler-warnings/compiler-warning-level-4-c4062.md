---
title: "Kompilatora (poziom 4) ostrzeżenie C4062 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4062
dev_langs: C++
helpviewer_keywords: C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8e37e750ef3eabc3f48814e589113d4c63aa0dcb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4062"></a>Kompilator C4062 ostrzegawcze (poziom 4)
Moduł wyliczający "identyfikator" przełącznika wyliczenia 'wyliczenia' nie jest obsługiwany.  
  
 Wyliczenia nie ma żadnych skojarzony program obsługi w `switch` instrukcji i ma nie **domyślne** etykiety.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4062:  
  
```  
// C4062.cpp  
// compile with: /W4  
#pragma warning(default : 4062)  
enum E { a, b, c };  
void func ( E e ) {  
   switch(e) {  
      case a:  
      case b:  
      break;   // no default label  
   }   // C4062, enumerate 'c' not handled  
}  
  
int main() {  
}  
```