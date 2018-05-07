---
title: C2441 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6557e913f2bd34fda9d435d44020697a925af4e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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