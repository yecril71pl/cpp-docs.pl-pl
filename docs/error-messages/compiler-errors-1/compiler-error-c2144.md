---
title: C2144 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2144
dev_langs:
- C++
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60a6b0a6019ab6ddf1a403d2cbd4f6ef96b2a865
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171153"
---
# <a name="compiler-error-c2144"></a>C2144 błąd kompilatora

> Błąd składniowy: "*typu*"powinien być poprzedzony przez"*tokenu*"

Kompilator Oczekiwano *tokenu* i znaleźć *typu* zamiast tego.

Przyczyną tego błędu może być brak zamykającego nawiasu klamrowego, prawy nawias lub średnikami.

C2144 może również wystąpić podczas próby utworzenia makra ze słowem kluczowym CLR, która zawiera biały znak.

Może również zostać wyświetlony C2144 próbie przekazywanie dalej typu. Zobacz [przesyłania dalej typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md) Aby uzyskać więcej informacji.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2144 i przedstawia sposób, aby go rozwiązać:

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

Poniższy przykład generuje C2144 i przedstawia sposób, aby go rozwiązać:

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```