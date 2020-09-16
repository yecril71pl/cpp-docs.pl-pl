---
title: 'Instrukcje: korzystanie z typu natywnego w kompilacji środowiska CLR'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: 88a678a19043d3229218dd69afbf8548348817df
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683965"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Porady: używanie typu natywnego w kompilacji /clr

Można zdefiniować typ natywny w kompilacji **/CLR** i każde użycie tego typu natywnego z zestawu jest prawidłowe. Jednak typy natywne nie będą dostępne do użycia z metadanych, do których się odwołuje.

Każdy zestaw musi zawierać definicję każdego typu natywnego, który będzie używany.

Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="examples"></a>Przykłady

Ten przykład tworzy składnik, który definiuje i używa typu natywnego.

```cpp
// use_native_type_in_clr.cpp
// compile with: /clr /LD
public struct NativeClass {
   static int Test() { return 98; }
};

public ref struct ManagedClass {
   static int i = NativeClass::Test();
   void Test() {
      System::Console::WriteLine(i);
   }
};
```

Ten przykład definiuje klienta, który zużywa składnik. Zwróć uwagę, że jest to błąd w celu uzyskania dostępu do typu natywnego, chyba że jest on zdefiniowany w jednostka kompilacji.

```cpp
// use_native_type_in_clr_2.cpp
// compile with: /clr
#using "use_native_type_in_clr.dll"
// Uncomment the following 3 lines to resolve.
// public struct NativeClass {
//    static int Test() { return 98; }
// };

int main() {
   ManagedClass x;
   x.Test();

   System::Console::WriteLine(NativeClass::Test());   // C2653
}
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawne PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
