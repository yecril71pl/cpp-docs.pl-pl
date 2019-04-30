---
title: Kompilator ostrzeżenie (poziom 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 66b8d42b63bcbf328703523c4eeda7a047f4643c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374576"
---
# <a name="compiler-warning-level-1-c4677"></a>Kompilator ostrzeżenie (poziom 1) C4677

'Funkcja': podpis z nieprywatnej składowej zawiera prywatny typ zestawu "private_type"

Typ, który ma dostęp publiczny spoza zestawu, używa typ, który ma dostęp prywatny spoza zestawu. Składnik, który odwołuje się do typu publicznego zestawu nie będzie używać składowej typu lub elementów członkowskich, które odwołują się prywatny typ zestawu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4677.

```
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```