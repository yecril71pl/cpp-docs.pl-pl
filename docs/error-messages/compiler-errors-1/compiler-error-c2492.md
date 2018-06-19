---
title: C2492 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68b3d769c5b86be172a0a27828fb1dc3905959d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197367"
---
# <a name="compiler-error-c2492"></a>C2492 błąd kompilatora
"*zmiennej*": dane z okresem magazynu wątku mogą nie mieć interfejsu biblioteki dll    
  
 Zmienna została zadeklarowana z [wątku](../../cpp/thread.md) atrybutu i z biblioteki DLL interfejsu. Adres `thread` zmienna nie jest znany do czasu wykonywania, więc nie można połączyć do biblioteki DLL importu lub eksportu.  
  
 Poniższy przykład generuje C2492:  
  
```  
// C2492.cpp  
// compile with: /c  
class C {  
public:  
   char   ch;  
};  
  
__declspec(dllexport) __declspec(thread) C c_1;   // C2492  
__declspec(thread) C c_1;   // OK  
```