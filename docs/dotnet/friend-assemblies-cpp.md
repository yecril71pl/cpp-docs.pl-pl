---
title: Przyjazne zestawy (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
ms.openlocfilehash: e469556a773ffcdbf50e53d94022c0b6b7abf869
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404432"
---
# <a name="friend-assemblies-c"></a>Przyjazne zestawy (C++)

Aby uzyskać odpowiednie środowiska uruchomieniowe *przyjaznych zestawów* funkcja językowa sprawia, że typy, które są w zakresie przestrzeni nazw lub zakresie globalnym w dostępna dla zestawów klientów lub modułów .netmodule składnika zestawu.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

**Uwagi**

(Ta funkcja język nie jest obsługiwana w wszystkie środowiska uruchomieniowe).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

**Uwagi**

(Ta funkcja języka nie jest obsługiwana w środowisku uruchomieniowym Windows).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: **/ZW**

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

**Uwagi**

#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>Aby udostępnić typów w zakresie przestrzeni nazw lub zasięgu globalnym w składniku zestawu do klienta, zestaw lub moduł .netmodule

1. W składniku, określ atrybut zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>i przekazywać nazwę jednostki zestaw klienta lub moduł .netmodule, który będzie uzyskiwać dostęp do typów w zakresie przestrzeni nazw lub zakresie globalnym w składniku.  Można określić wiele zestawów klientów lub modułów .netmodule przez określenie dodatkowych atrybutów.

1. W zestawie klienta lub .netmodule, gdy odwołujesz się zestaw składników za pomocą `#using`, przekazać `as_friend` atrybutu.  Jeśli określisz `as_friend` atrybutu dla zestawu, który nie określa `InternalsVisibleToAttribute`, jeśli zostanie podjęta próba dostęp do typu w zakresie przestrzeni nazw lub zakresie globalnym w składniku zostanie zgłoszony wyjątek czasu wykonywania.

Spowoduje to błąd kompilacji, jeśli zestaw zawiera <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut nie ma silnej nazwy, ale zestaw klienta, który używa `as_friend` atrybut zapewnia.

Mimo że typów w zakresie przestrzeni nazw i zakresu globalnego może być znane klienta zestaw lub moduł .netmodule, dostępność składowej jest nadal obowiązują.  Na przykład nie można uzyskać dostępu od prywatnej składowej.

Dostęp do wszystkich typów w zestawie, muszą zostać przyznane jawnie.  Na przykład zestaw C nie ma dostępu do wszystkich typów w zestawie, A Jeśli zestaw B odwołuje się do zestawu języka C, a zestaw B ma dostęp do wszystkich typów w zestawie A.

Aby uzyskać informacje dotyczące sposobu podpisywania — czyli udzielanie silnej nazwy do — zestawu, który jest zbudowany za pomocą wizualizacji C++ kompilatora, zobacz [zestawy o silnej nazwach (podpisywanie zestawów) (C++sposób niezamierzony)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Alternatywa przy użyciu funkcji zestawów friend, można użyć <xref:System.Security.Permissions.StrongNameIdentityPermission> ograniczyć dostęp do poszczególnych typów.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora:   **/CLR**

### <a name="examples"></a>Przykłady

Poniższy przykład kodu określa składnik, który określa zestaw klienta, który ma dostęp do typów w składniku.

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

W kolejnym przykładzie kod uzyskuje dostęp do prywatnej typu składnika.

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

Następny przykład kodu definiuje składnika, ale nie określa zestawu klienta, który będzie miał dostęp do typów w składniku.

Należy zauważyć, że składnik jest połączony za pomocą **/ opt: noref**. Daje to gwarancję, że prywatnej typy są emitowane w metadanych składnika, który nie jest wymagane podczas `InternalsVisibleTo` atrybut był obecny. Aby uzyskać więcej informacji, zobacz [od (optymalizacje)](../build/reference/opt-optimizations.md).

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

Poniższy kod definiuje klienta, który próbuje uzyskać dostęp prywatny typ składnika, który nie daje dostęp do swojej prywatnej typów. Ze względu na zachowanie aparatu plików wykonywalnych Jeśli chcesz przechwytywać wyjątek, musi próbie uzyskania dostępu prywatny typ w funkcji pomocnika.

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

Następny przykład kodu pokazuje, jak utworzyć składnika silnej nazwy, który określa zestaw klienta, który będzie miał dostęp do typów w składniku.

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

Należy zauważyć, że składnika należy określić swojego klucza publicznego. Sugerujemy, uruchom następujące polecenia sekwencyjnie w wierszu polecenia, aby utworzyć parę kluczy i uzyskać klucz publiczny:

**sn -d friend_assemblies.snk**

**sn -k friend_assemblies.snk**

**sn -i friend_assemblies.snk friend_assemblies.snk**

**sn -pc friend_assemblies.snk key.publickey**

**key.publickey - tp SN**

W kolejnym przykładzie kod uzyskuje dostęp do prywatnej typu w składniku silnej nazwy.

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
