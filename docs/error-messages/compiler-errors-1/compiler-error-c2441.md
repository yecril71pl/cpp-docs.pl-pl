---
title: "C2441 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2441
dev_langs: C++
helpviewer_keywords: C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6868feadda4c0c0f3d65a86c77a403b8965fded5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2441"></a>C2441 błąd kompilatora
"Zmienna": symbol zadeklarowany z __declspec(proces) musi być stały w/CLR: pure tryb czysty  
  
 **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 Domyślnie zmienne są właściwe dla domeny aplikacji w obszarze **/CLR: pure**. Oznaczone jako zmienną `__declspec(process)` w obszarze **/CLR: pure** jest podatne na błędy, jeśli zmodyfikowany w domenie jedną aplikację, a następnie odczytywane w innym.  
  
 W związku z tym kompilator wymusza na proces zmienne są `const` w obszarze **/CLR: pure**, wprowadzania je odczytać tylko we wszystkich domenach aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz [procesu](../../cpp/process.md) i [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2441.  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```