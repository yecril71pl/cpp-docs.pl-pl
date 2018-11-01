---
title: 'Porady: używanie typu natywnego w kompilacji / clr'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: 0079be21b474858684e1abaaeb363820764a701d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459959"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Porady: używanie typu natywnego w kompilacji /clr

Można zdefiniować typu natywnego w **/CLR** kompilacji i każde użycie tego typu natywnego z w obrębie zestawu jest nieprawidłowa. Jednak natywnych typów nie będzie dostępny do użytku z przywoływanych metadanych.

Każdy zestaw musi zawierać definicję każdego typu macierzystego, który będzie używany.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

W tym przykładzie tworzy składnik, który definiuje i korzysta z typu natywnego.

```
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

## <a name="example"></a>Przykład

W tym przykładzie definiuje klienta, który wykorzystuje składnika. Należy zauważyć, że jest błąd, aby uzyskiwać dostęp do natywnego typu, chyba że jest on zdefiniowany w compiland —.

```
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

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)