---
title: Błąd kompilatora C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: 2df788efd93fb531822d858ea5aee1722487db81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387048"
---
# <a name="compiler-error-c2261"></a>Błąd kompilatora C2261

"string": odwołanie do zestawu jest nieprawidłowa i nie można go rozpoznać

Wartość jest nieprawidłowa.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Służy do określania zestawu przyjaciela. Na przykład jeśli a.dll chce określić b.dll jako zestaw przyjazny, należy określić (w a.dll): InternalsVisibleTo("b"). Środowisko uruchomieniowe pozwala następnie b.dll dostęp do wszystkiego w a.dll (z wyjątkiem typów prywatnych).

Aby uzyskać więcej informacji o poprawnej składni podczas określania przyjaznych zestawów, zobacz [przyjazne zestawy (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2261.

```
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```