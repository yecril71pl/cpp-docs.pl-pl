---
title: Błąd kompilatora C2261 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed43dc43fb6ceaf514a8e7452b06eb7bdaf7362
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051649"
---
# <a name="compiler-error-c2261"></a>Błąd kompilatora C2261

"string": odwołanie do zestawu jest nieprawidłowa i nie można go rozpoznać

Wartość jest nieprawidłowa.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Służy do określania zestawu przyjaciela. Na przykład, jeśli a.dll chce określić b.dll jako zestaw przyjazny, należy określić (w a.dll): InternalsVisibleTo("b"). Środowisko uruchomieniowe pozwala następnie b.dll dostęp do wszystkiego w a.dll (z wyjątkiem typów prywatnych).

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