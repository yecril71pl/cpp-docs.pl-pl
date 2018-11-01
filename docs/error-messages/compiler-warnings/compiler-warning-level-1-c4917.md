---
title: Kompilator ostrzeżenie (poziom 1) C4917
ms.date: 11/04/2016
f1_keywords:
- C4917
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
ms.openlocfilehash: 97f6f0a08c8ef292d81471cb5d0d94e359466933
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466797"
---
# <a name="compiler-warning-level-1-c4917"></a>Kompilator ostrzeżenie (poziom 1) C4917

'deklarator': identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzeni nazw

Struktura zdefiniowanych przez użytkownika innego niż [klasy](../../cpp/class-cpp.md), [interfejsu](../../cpp/interface.md), lub [przestrzeni nazw](../../cpp/namespaces-cpp.md) nie może mieć postać identyfikatora GUID.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykładowy kod generuje C4917:

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