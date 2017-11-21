---
title: "Kompilatora (poziom 1) ostrzeżenie C4917 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4917
dev_langs: C++
helpviewer_keywords: C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a3b5d930b0c8a79542526adcd174a9ed6a0a8db4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4917"></a>Kompilator C4917 ostrzegawcze (poziom 1)
"deklarator": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzeni nazw  
  
Struktury zdefiniowane przez użytkownika innego niż [klasy](../../cpp/class-cpp.md), [interfejsu](../../cpp/interface.md), lub [przestrzeni nazw](../../cpp/namespaces-cpp.md) nie może mieć postać identyfikatora GUID.  
  
To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
Poniższy przykład kodu generuje C4917:  
  
```cpp  
// C4917.cpp  
// compile with: /W1  
#pragma warning(default : 4917)  
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S  
{  
} s;   // C4917, don't put uuid on a struct  
  
int main()  
{  
}  
```