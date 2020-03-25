---
title: Ostrzeżenie kompilatora (poziom 1) C4917
ms.date: 11/04/2016
f1_keywords:
- C4917
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
ms.openlocfilehash: c7a2d72b429f762e476286093c7f273a9a546cb6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174677"
---
# <a name="compiler-warning-level-1-c4917"></a>Ostrzeżenie kompilatora (poziom 1) C4917

"deklarator": identyfikator GUID może być skojarzony tylko z klasą, interfejsem lub przestrzenią nazw

Zdefiniowana przez użytkownika struktura inna niż [Klasa](../../cpp/class-cpp.md), [interfejs](../../cpp/interface.md)lub [przestrzeń nazw](../../cpp/namespaces-cpp.md) nie może mieć identyfikatora GUID.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

## <a name="example"></a>Przykład

Następujący przykładowy kod generuje C4917:

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
