---
title: Błąd kompilatora C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: 2ec39768a88da049c6a31ca2a9de226e25479c99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571473"
---
# <a name="compiler-error-c2842"></a>Błąd kompilatora C2842

"class": zarządzanej lub typu WinRT nie musi definiować własnego "operator new" ani "operator delete"

Definiowanie swoich własnych ** nowy operator lub **operatora delete** Zarządzanie alokacji pamięci na natywnej stercie. Odwołanie do klasy nie można jednak zdefiniować te operatory, ponieważ są przydzielane tylko na stosie zarządzanym.

Aby uzyskać więcej informacji, zobacz [operatory zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2842.

```
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
