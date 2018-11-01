---
title: 'Porady: przeprowadzanie marshalingu struktur za pomocą funkcji PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: e79eb343f81cf2d66e394be7561d2c9727c4c9ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429114"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Porady: przeprowadzanie marshalingu struktur za pomocą funkcji PInvoke

W tym dokumencie wyjaśniono, jak natywne funkcje, których struktury stylu C może być wywoływana z funkcji zarządzanej przez przy użyciu metody P/Invoke. Mimo że zaleca się, że korzystasz z funkcji międzyoperacyjności języka C++, a nie P/Invoke ponieważ P/Invoke zapewnia nieco błąd kompilacji, raportowanie, nie jest bezpieczny i może być uciążliwe zaimplementować, jeśli niezarządzanego interfejsu API jest spakowany jako biblioteki DLL i kod źródłowy jest dostępne metody P/Invoke jest jedyną opcją. W przeciwnym razie można znaleźć w następujących dokumentach:

- [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Instrukcje: przeprowadzanie marshalingu ciągów za pomocą funkcji PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

Domyślnie struktur natywnych i zarządzanych są wyświetlane inaczej w pamięci, dlatego pomyślnie przekazywanie struktury przez granicę zarządzanych/niezarządzanych wymaga wykonania dodatkowych czynności w celu zachowania integralności danych.

W tym dokumencie opisano kroki wymagane do zdefiniowania zarządzanych odpowiedników funkcji natywnej struktury i jak wynikowy struktury mogą być przekazywane do funkcji niezarządzanych. W tym dokumencie założono, że prosty struktur — te, które nie zawierają ciągi lub wskaźniki — są używane. Aby uzyskać informacje o współdziałaniu niekopiowalnych, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md). Zwracana wartość metody P/Invoke nie może być typów niekopiowalnych. Typy Kopiowalne mają tę samą reprezentację w kodzie zarządzanym i niezarządzanym. Aby uzyskać więcej informacji, zobacz [Kopiowalne i typy danych Kopiowalnych inne niż](/dotnet/framework/interop/blittable-and-non-blittable-types).

Marshaling prosty, struktur danych kopiowalnych granicę zarządzanych/niezarządzanych najpierw wymaga zdefiniowania zarządzanej wersji natywnej struktury. Te struktury mogą mieć dowolną nazwę prawne; nie ma relacji między wersjami natywnych i zarządzanych dwie struktury inne niż ich układ danych. Dlatego jest istotne, że zarządzanej wersji zawiera pola, które są takie same, rozmiar i w tej samej kolejności, jak natywnej wersji. (Nie ma mechanizmu za zapewnienie, że zarządzanego i natywnego wersje struktury są równoważne, więc niezgodności nie staną się widoczne do czasu wykonywania. Jest odpowiedzialny za programisty, aby upewnić się, że dwie struktury mają taki sam układ danych).

Ponieważ członkowie struktury zarządzane są czasami zostaną przestawione do celów wydajności, należy go używać <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu, aby wskazać, że struktura są ułożone w sekwencyjnie. Jest również dobrym pomysłem jest jawnie ustawione strukturze, pakowania ustawienie, aby być taka sama, jak te stosowane w natywnej struktury. (Mimo że domyślnie Visual C++ używa struktury 8-bajtowych pakowania dla obu kodu zarządzanego).

1. Następnie użyj <xref:System.Runtime.InteropServices.DllImportAttribute> zadeklarować punktów wejścia, które odnoszą się do funkcji niezarządzanych, które akceptują strukturę, ale korzystać z zarządzanej wersji struktury w sygnatur funkcji, która jest punktem moot, jeśli użyjesz tej samej nazwy dla obu wersji systemu Struktura.

1. Teraz kod zarządzany można przekazać zarządzanej wersji struktury z funkcjami niezarządzanymi tak, jakby są faktycznie zarządzanej funkcji. Te struktury mogą być przekazywane przez wartość lub przez odwołanie, jak pokazano w poniższym przykładzie.

## <a name="example"></a>Przykład

Poniższy kod składa się z modułu zarządzanego i niezarządzanego. Moduł niezarządzane to biblioteki DLL, który definiuje strukturę o nazwie lokalizacji i funkcji o nazwie GetDistance, który akceptuje dwa wystąpienia struktury lokalizacji. Drugi moduł jest zarządzanej aplikacji wiersza polecenia, która importuje funkcja GetDistance, ale definiuje go pod kątem zarządzanych wielokrotność struktury lokalizacji MLocation. W praktyce takiej samej nazwie prawdopodobnie będzie używana dla obu wersji struktury; jednak innej nazwy służy tutaj do pokazują, że prototyp DllImport jest zdefiniowany w zarządzanej wersji.

Należy pamiętać, że części biblioteki DLL jest uwidaczniany związane z kodem zarządzanym przy użyciu tradycyjnych # dyrektywy include. W rzeczywistości biblioteki DLL jest dostępny tylko w czasie wykonywania, dzięki czemu problemy z funkcjami zaimportowane wraz z DllImport nie zostanie wykryty w czasie kompilacji.

```
// TraditionalDll3.cpp
// compile with: /LD /EHsc
#include <iostream>
#include <stdio.h>
#include <math.h>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
   #define TRADITIONALDLL_API __declspec(dllexport)
#else
   #define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct Location {
   int x;
   int y;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API double GetDistance(Location, Location);
   TRADITIONALDLL_API void InitLocation(Location*);
}

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
```

## <a name="example"></a>Przykład

```
// MarshalStruct_pi.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MLocation {
   int x;
   int y;
};

value struct TraditionalDLL {
   [DllImport("TraditionalDLL3.dll")]
   static public double GetDistance(MLocation, MLocation);
   [DllImport("TraditionalDLL3.dll")]
   static public double InitLocation(MLocation*);
};

int main() {
   MLocation loc1;
   loc1.x = 0;
   loc1.y = 0;

   MLocation loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = TraditionalDLL::GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   MLocation loc3;
   TraditionalDLL::InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

```Output
[unmanaged] loc1(0,0) loc2(100,100)
[managed] distance = 141.42135623731
[unmanaged] Initializing location...
[managed] x=50 y=50
```

## <a name="see-also"></a>Zobacz też

[Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
