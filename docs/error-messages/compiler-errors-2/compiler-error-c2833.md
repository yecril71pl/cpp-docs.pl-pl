---
title: C2833 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff066510292690bc940f18ab8d63605eb8627308
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244113"
---
# <a name="compiler-error-c2833"></a>C2833 błąd kompilatora
"operator operator" nie jest rozpoznany jako operator lub typ  
  
 Wyraz `operator` musi występować operator, który chcesz zmienić lub typu, który chcesz przekonwertować.  
  
 Aby uzyskać listę operatory, które można zdefiniować typu zarządzanego, zobacz [operatory zdefiniowane przez użytkownika](../../dotnet/user-defined-operators-cpp-cli.md).  
  
 Poniższy przykład generuje C2833:  
  
```  
// C2833.cpp  
// compile with: /c  
class A {};  
  
void operator ::* ();   // C2833  
void operator :: ();   // OK  
```