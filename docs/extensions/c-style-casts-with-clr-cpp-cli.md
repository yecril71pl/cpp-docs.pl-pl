---
title: Rzutowania w stylu języka C na polecenie-CLR (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
ms.openlocfilehash: daaf92e36550c5479903dec4869b1cb116c0a65a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219797"
---
# <a name="c-style-casts-with-clr-ccli"></a>Rzutowania w stylu C i kompilator /clr (C++/CLI)

Poniższy temat dotyczy tylko środowiska uruchomieniowego języka wspólnego.

W przypadku użycia z typami CLR kompilator próbuje zmapować rzutowania w stylu C do jednego z rzutów wymienionych poniżej, w następującej kolejności:

1. const_cast

2. safe_cast

3. safe_cast Plus const_cast

4. static_cast

5. static_cast Plus const_cast

Jeśli żaden z wymienionych powyżej elementów rzutowania nie jest prawidłowy, a jeśli typem wyrażenia i typem docelowym są typy odwołań CLR, Rzutowanie w stylu języka C mapuje do sprawdzenia w czasie wykonywania (Castclass instrukcji MSIL). W przeciwnym razie Rzutowanie w stylu języka C jest traktowane jako nieprawidłowe i kompilator wygeneruje błąd.

## <a name="remarks"></a>Uwagi

Nie zaleca się rzutowania w stylu języka C. Podczas kompilowania z [opcją/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md)Użyj [safe_cast](safe-cast-cpp-component-extensions.md).

Poniższy przykład pokazuje Rzutowanie w stylu C, które jest mapowane na **`const_cast`** .

```cpp
// cstyle_casts_1.cpp
// compile with: /clr
using namespace System;

ref struct R {};
int main() {
   const R^ constrefR = gcnew R();
   R^ nonconstR = (R^)(constrefR);
}
```

Poniższy przykład pokazuje Rzutowanie w stylu C, który jest mapowany na **safe_cast**.

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

Poniższy przykład pokazuje Rzutowanie w stylu C, który jest mapowany do **safe_cast** Plus **`const_cast`** .

```cpp
// cstyle_casts_3.cpp
// compile with: /clr
using namespace System;

ref struct R {};
ref struct R2 : public R {};

int main() {
   const R^ constR2 = gcnew R2();
   try {
   R2^ b2DR = (R2^)(constR2);
   }
   catch(InvalidCastException^ e) {
      System::Console::WriteLine("Invalid Exception");
   }
}
```

Poniższy przykład pokazuje Rzutowanie w stylu C, które jest mapowane na **`static_cast`** .

```cpp
// cstyle_casts_4.cpp
// compile with: /clr
using namespace System;

struct N1 {};
struct N2 {
   operator N1() {
      return N1();
   }
};

int main() {
   N2 n2;
   N1 n1 ;
   n1 = (N1)n2;
}
```

Poniższy przykład pokazuje Rzutowanie w stylu C, który jest mapowany na **`static_cast`** znak plus **`const_cast`** .

```cpp
// cstyle_casts_5.cpp
// compile with: /clr
using namespace System;
struct N1 {};

struct N2 {
   operator const N1*() {
      static const N1 n1;
      return &n1;
   }
};

int main() {
   N2 n2;
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast
}
```

Poniższy przykład pokazuje Rzutowanie w stylu C, który jest mapowany do sprawdzenia w czasie wykonywania.

```cpp
// cstyle_casts_6.cpp
// compile with: /clr
using namespace System;

ref class R1 {};
ref class R2 {};

int main() {
   R1^ r  = gcnew R1();
   try {
      R2^ rr = ( R2^)(r);
   }
   catch(System::InvalidCastException^ e) {
      Console::WriteLine("Caught expected exception");
   }
}
```

Poniższy przykład pokazuje nieprawidłowe Rzutowanie w stylu C, co powoduje, że kompilator wystawia błąd.

```cpp
// cstyle_casts_7.cpp
// compile with: /clr
using namespace System;
int main() {
   String^s = S"hello";
   int i = (int)s;   // C2440
}
```

## <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)
