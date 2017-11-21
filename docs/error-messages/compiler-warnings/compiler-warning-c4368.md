---
title: "C4368 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4368
dev_langs: C++
helpviewer_keywords: C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6fd66d8fb6d30a960c659345910242ec5a1a2e11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4368"></a>C4368 ostrzeżenia kompilatora
Nie można zdefiniować "członek" jako członka zarządzanego 'type': mieszane typy nie są obsługiwane.  
  
 Nie można osadzić elementu członkowskiego danych natywnych w typie CLR.  
  
 Można jednak zadeklarować wskaźnika do typu macierzystego i sterować jego okres istnienia w Konstruktor i destruktor finalizator klasy zarządzanej. Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 To zawsze ostrzeżenie jako błąd. Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma, aby wyłączyć C4368.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4368.  
  
```  
// C4368.cpp  
// compile with: /clr /c  
struct N {};  
ref struct O {};  
ref struct R {  
    R() : m_p( new N ) {}  
    ~R() { delete m_p; }  
  
   property N prop;   // C4368  
   int i[10];   // C4368  
  
   property O ^ prop2;   // OK  
   N * m_p;   // OK  
};  
```