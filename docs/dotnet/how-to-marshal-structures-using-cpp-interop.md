---
title: 'Porady: przeprowadzanie marshalingu struktur za pomocą międzyoperacyjności języka C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
ms.openlocfilehash: 8ca53761647c1f3d5ea059ddf381cb334cd2a993
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413843"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>Porady: przeprowadzanie marshalingu struktur za pomocą międzyoperacyjności języka C++

W tym temacie przedstawiono jeden aspekt współdziałania Visual C++. Aby uzyskać więcej informacji, zobacz [using C++ Interop (niejawne PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

W poniższych przykładach kodu użyto [zarządzanych, niezarządzanych](../preprocessor/managed-unmanaged.md) #pragma dyrektyw, aby zaimplementować funkcje zarządzane i niezarządzane w tym samym pliku, ale te funkcje współdziałają w taki sam sposób, jeśli zostały zdefiniowane w oddzielnych plikach. Pliki zawierające tylko funkcje niezarządzane nie muszą być kompilowane z [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example-pass-structure-from-managed-to-unmanaged-function"></a>Przykład: Przekaż strukturę z zarządzanej do niezarządzanej funkcji

Poniższy przykład demonstruje przekazywanie struktury z zarządzanej do niezarządzanej funkcji, zarówno przez wartość, jak i przez odwołanie. Ze względu na to, że struktura w tym przykładzie zawiera tylko proste, wewnętrzne typy danych (zobacz [danych kopiowalnych i typy inne niż danych kopiowalnych](/dotnet/framework/interop/blittable-and-non-blittable-types)), nie jest wymagane żadne specjalne kierowanie. Aby zorganizować struktury inne niż danych kopiowalnych, takie jak te, które zawierają wskaźniki, zobacz [How to: Marshaling Embedded Reports using C++ Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```cpp
// PassStruct1.cpp
// compile with: /clr

#include <stdio.h>
#include <math.h>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

struct Location {
   int x;
   int y;
};

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}

#pragma managed

int main() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   Location loc3;
   InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

## <a name="example-pass-structure-from-unmanaged-to-managed-function"></a>Przykład: Przekaż strukturę z niezarządzanej do funkcji zarządzanej

Poniższy przykład demonstruje przekazywanie struktury z niezarządzanej do funkcji zarządzanej, zarówno przez wartość, jak i przez odwołanie. Ze względu na to, że struktura w tym przykładzie zawiera tylko proste, wewnętrzne typy danych (zobacz [danych kopiowalnych i typy inne niż danych kopiowalnych](/dotnet/framework/interop/blittable-and-non-blittable-types)), nie jest wymagane żadne specjalne kierowanie. Aby zorganizować struktury inne niż danych kopiowalnych, takie jak te, które zawierają wskaźniki, zobacz [How to: Marshaling Embedded Reports using C++ Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```cpp
// PassStruct2.cpp
// compile with: /clr
#include <stdio.h>
#include <math.h>
using namespace System;

// native structure definition
struct Location {
   int x;
   int y;
};

#pragma managed

double GetDistance(Location loc1, Location loc2) {
   Console::Write("[managed] got loc1({0},{1})", loc1.x, loc1.y);
   Console::WriteLine(" loc2({0},{1})", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   Console::WriteLine("[managed] Initializing location...");
   lp->x = 50;
   lp->y = 50;
}

#pragma unmanaged

int UnmanagedFunc() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   printf_s("(unmanaged) loc1=(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2=(%d,%d)\n", loc2.x, loc2.y);

   double dist = GetDistance(loc1, loc2);
   printf_s("[unmanaged] distance = %f\n", dist);

   Location loc3;
   InitLocation(&loc3);
   printf_s("[unmanaged] got x=%d y=%d\n", loc3.x, loc3.y);

    return 0;
}

#pragma managed

int main() {
   UnmanagedFunc();
}
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawne PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
