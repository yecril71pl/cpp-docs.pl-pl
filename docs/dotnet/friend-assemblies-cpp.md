---
title: Przyjazne zestawy (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
ms.openlocfilehash: a42caaf07f6ec0c71f63d6a0df8a79fff6f737e6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221448"
---
# <a name="friend-assemblies-c"></a>Przyjazne zestawy (C++)

W przypadku odpowiednich środowisk uruchomieniowych funkcja języka *zaprzyjaźnionych zestawów* tworzy typy, które są w zakresie przestrzeni nazw lub globalnym zakresie w składniku zestawu dostępnym dla jednego lub kilku zestawów klienta lub modułów.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

**Uwagi**

(Ta funkcja języka nie jest obsługiwana we wszystkich środowiskach uruchomieniowych).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

**Uwagi**

(Ta funkcja języka nie jest obsługiwana w środowisko wykonawcze systemu Windows).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: **/zw**

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

**Uwagi**

#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>Aby wprowadzić typy w zakresie przestrzeni nazw lub globalnym zakresie w składniku zestawu dostępnym dla zestawu klienta lub modułu.

1. W składniku Określ atrybut zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> i przekaż nazwę zestawu klienta lub moduł, który będzie miał dostęp do typów w zakresie przestrzeni nazw lub w zakresie globalnym w składniku.  Można określić wiele zestawów klienta lub modułów, określając dodatkowe atrybuty.

1. W zestawie klienta lub module, podczas odwoływania się do zestawu składników przy użyciu, należy `#using` przekazać **`as_friend`** atrybut.  Jeśli określisz **`as_friend`** atrybut zestawu, który nie `InternalsVisibleToAttribute` zostanie określony, zostanie wygenerowany wyjątek czasu wykonywania, jeśli spróbujesz uzyskać dostęp do typu w zakresie przestrzeni nazw lub zakresu globalnego w składniku.

Jeśli zestaw zawierający <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut nie ma silnej nazwy, ale zestaw klienta, który używa tego atrybutu, zostanie zwrócony błąd kompilacji **`as_friend`** .

Mimo że typy w zakresie przestrzeni nazw i zakres globalny mogą być znane w zestawie klienta lub module, ułatwienia dostępu członków nadal obowiązują.  Na przykład nie można uzyskać dostępu do prywatnego elementu członkowskiego.

Dostęp do wszystkich typów w zestawie musi być jawnie przyznany.  Na przykład zestaw C nie ma dostępu do wszystkich typów w zestawie A, jeśli zestaw C odwołuje się do zestawu B, a zestaw B ma dostęp do wszystkich typów w zestawie A.

Aby uzyskać informacje na temat sposobu podpisywania — to znaczy, jak nadać silną nazwę, zestawowi skompilowanemu przy użyciu kompilatora języka Microsoft C++, zobacz [zestawy silnej nazwy (podpisywanie zestawów) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Alternatywą dla korzystania z funkcji zaprzyjaźnionych zestawów jest możliwość <xref:System.Security.Permissions.StrongNameIdentityPermission> ograniczenia dostępu do poszczególnych typów.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: **/CLR**

### <a name="examples"></a>Przykłady

Poniższy przykład kodu definiuje składnik określający zestaw klienta, który ma dostęp do typów w składniku.

```cpp
// friend_assemblies.cpp
// compile by using: /clr /LD
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type
[assembly:InternalsVisibleTo("friend_assemblies_2")];

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Następny przykład kodu uzyskuje dostęp do typu prywatnego w składniku.

```cpp
// friend_assemblies_2.cpp
// compile by using: /clr
#using "friend_assemblies.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

Następny przykład kodu definiuje składnik, ale nie określa zestawu klienta, który będzie miał dostęp do typów w składniku.

Zwróć uwagę, że składnik jest połączony za pomocą **/OPT: NOREF**. Gwarantuje to, że typy prywatne są emitowane w metadanych składnika, co nie jest wymagane, gdy `InternalsVisibleTo` atrybut jest obecny. Aby uzyskać więcej informacji, zobacz [/opt (optymalizacje)](../build/reference/opt-optimizations.md).

```cpp
// friend_assemblies_3.cpp
// compile by using: /clr /LD /link /opt:noref
using namespace System;

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Poniższy przykład kodu definiuje klienta próbującego uzyskać dostęp do typu prywatnego w składniku, który nie zapewnia dostępu do jego typów prywatnych. W związku z zachowaniem środowiska uruchomieniowego, jeśli chcesz przechwytywać wyjątek, musisz próbować uzyskać dostęp do typu prywatnego w funkcji pomocnika.

```cpp
// friend_assemblies_4.cpp
// compile by using: /clr
#using "friend_assemblies_3.dll" as_friend
using namespace System;

void Test() {
   Class1 ^ a = gcnew Class1;
}

int main() {
   // to catch this kind of exception, use a helper function
   try {
      Test();
   }
   catch(MethodAccessException ^ e) {
      Console::WriteLine("caught an exception");
   }
}
```

```Output
caught an exception
```

Następny przykład kodu pokazuje, jak utworzyć składnik o silnej nazwie, który określa zestaw klienta, który będzie miał dostęp do typów w składniku.

```cpp
// friend_assemblies_5.cpp
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type

[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];

private ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Należy zauważyć, że składnik musi określić swój klucz publiczny. Sugerujemy uruchomienie następujących poleceń sekwencyjnie w wierszu polecenia, aby utworzyć parę kluczy i uzyskać klucz publiczny:

**SN-d friend_assemblies. snk**

**SN-k friend_assemblies. snk**

**SN-i friend_assemblies. snk friend_assemblies. snk**

**SN-PC friend_assemblies. snk Key. PublicKey**

**SN-TP Key. PublicKey**

Następny przykład kodu uzyskuje dostęp do typu prywatnego w składniku o silnej nazwie.

```cpp
// friend_assemblies_6.cpp
// compile by using: /clr /link /keyfile:friend_assemblies.snk
#using "friend_assemblies_5.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

## <a name="see-also"></a>Zobacz także

[Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md)
