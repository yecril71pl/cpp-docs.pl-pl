---
title: "C4936 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4936
dev_langs: C++
helpviewer_keywords: C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a4342c749c5db4d66f206209a146ad7d7aef7041
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4936"></a>C4936 ostrzeżenia kompilatora
Ta deklaracja __declspec jest obsługiwana tylko w przypadku, gdy skompilowano z opcją/CLR lub/CLR: pure  
  
 **/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015.  
  
 A `__declspec` modyfikator użyto ale `__declspec` modyfikator obowiązuje tylko, gdy skompilowano z jednym z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opcje.  
  
 Aby uzyskać więcej informacji, zobacz [elementu appdomain](../../cpp/appdomain.md) i [procesu](../../cpp/process.md).  
  
 C4936 jest zawsze wystawione jako błąd.  Możesz wyłączyć C4936 z [ostrzeżenie](../../preprocessor/warning.md) pragma.  
  
 Poniższy przykład generuje C4936:  
  
```  
// C4936.cpp  
// compile with: /c  
// #pragma warning (disable : 4936)  
__declspec(process) int i;   // C4936  
__declspec(appdomain) int j;   // C4936  
```