---
title: Definicje i deklaracje (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7391180ca83d40e6ec00688054223b2e9af48e4f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="definitions-and-declarations-c"></a>Definicje i deklaracje (C++)
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft
 Interfejsu biblioteki DLL odwołuje się do wszystkich elementów (funkcje i dane), które są znane do wyeksportowania przez program w systemie; oznacza to, że wszystkie elementy, które są zadeklarowane jako `dllimport` lub `dllexport`. Wszystkie deklaracje objęte interfejsu biblioteki DLL należy określić albo `dllimport` lub `dllexport` atrybutu. Jednak tylko określić definicję `dllexport` atrybutu. Na przykład następujące definicji funkcji generuje błąd kompilatora:

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;  
}
```

 Ten kod również generuje błąd:

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

 Jednak jest to prawidłowa składnia:

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

 Korzystanie z `dllexport` oznacza definicję, podczas gdy `dllimport` oznacza deklaracji. Należy użyć `extern` — słowo kluczowe z `dllexport` Aby wymusić deklarację; w przeciwnym razie jest domniemane definicji. W związku z tym następujące przykłady są prawidłowe:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

 Poniższe przykłady wyjaśnienia, poprzedni:

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

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz też
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)
