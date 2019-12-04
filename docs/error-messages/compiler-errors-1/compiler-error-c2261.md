---
title: Błąd kompilatora C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: f23c2a38f8e4d6781af73fb70a25cf4737e2c4e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758778"
---
# <a name="compiler-error-c2261"></a>Błąd kompilatora C2261

"String": odwołanie do zestawu jest nieprawidłowe i nie można go rozpoznać

Wartość jest nieprawidłowa.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> jest używany do określania zaprzyjaźnionego zestawu. Na przykład jeśli. dll chce określić plik b. dll jako zestaw zaprzyjaźniony, należy określić (w bibliotece DLL): InternalsVisibleTo ("b"). Środowisko uruchomieniowe umożliwia następnie b. dll dostęp do wszystkich elementów w pliku. dll (z wyjątkiem typów prywatnych).

Aby uzyskać więcej informacji na temat poprawnej składni podczas określania zaprzyjaźnionych zestawów, zobacz [zaprzyjaźnione zestawyC++()](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C2261.

```cpp
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```
