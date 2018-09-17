---
title: Definicje i deklaracje (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54754e465f3a153b769b7619ff2bfb70a1872907
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699618"
---
# <a name="definitions-and-declarations-c"></a>Definicje i deklaracje (C++)
**Microsoft Specific**

 Interfejsu biblioteki DLL, który odwołuje się do wszystkich elementów (funkcje i dane), które są znane mają zostać wyeksportowane przez program w systemie; oznacza to, że wszystkie elementy, które są zadeklarowane jako **dllimport** lub **dllexport**. Należy określić wszystkie deklaracje objęte interfejsu biblioteki DLL **dllimport** lub **dllexport** atrybutu. Jednak tylko określić definicję **dllexport** atrybutu. Na przykład następująca definicja funkcji generuje błąd kompilatora:

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;  
}
```

 Ten kod jest również generuje błąd:

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

 Jednak jest to prawidłowa składnia:

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

 Korzystanie z **dllexport** oznacza definicję, podczas gdy **dllimport** zakłada deklarację. Należy użyć **extern** — słowo kluczowe z **dllexport** Aby wymusić deklarację; w przeciwnym razie jest implikowane definicję. W tym samym poniższe przykłady są prawidłowe:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

 Poniższe przykłady wyjaśnienia kroku:

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)