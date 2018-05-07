---
title: Przyjazne zestawy (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cc39fa66a73f16f800f0c7f0e4bbc49730d4b9c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="friend-assemblies-c"></a>Przyjazne zestawy (C++)
Dla odpowiednich runtimes *przyjazne zestawy* typy, które są w zakresie przestrzeni nazw lub zakresie globalnym w składniku zestawu dostępne zestawy klienta lub modułów .netmodule dzięki funkcji języka.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 **Uwagi**  
  
 (Ta funkcja językowa nie jest obsługiwana w środowiskach uruchomieniowych wszystkie).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 **Uwagi**  
  
 (Ta funkcja językowa nie jest obsługiwana w środowisku wykonawczym systemu Windows).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>Aby udostępnić typów w zakresie przestrzeni nazw lub zakresie globalnym w składniku zestawu do klienta zestawu lub moduł .netmodule  
  
1.  W składniku należy określić atrybut zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>i podaj nazwę klienta zestawu lub modułu .netmodule, które będą uzyskiwać dostęp do typów w zakresie przestrzeni nazw lub zakresie globalnym w składniku.  Można określić wiele zestawów klientów lub modułów .netmodule przez określenie dodatkowych atrybutów.  
  
2.  Klient zestawu lub modułu .netmodule podczas odwoływania się zestaw składników przy użyciu `#using`, Przekaż `as_friend` atrybutu.  Jeśli określisz `as_friend` atrybutu dla zestawu, który nie został określony `InternalsVisibleToAttribute`, wyjątek czasu wykonywania zostanie zgłoszony, Jeśli spróbujesz uzyskać dostępu do typu w zakresie przestrzeni nazw lub zakresie globalnym w składniku.  
  
 Spowoduje to błąd kompilacji, jeśli zestaw, który zawiera <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut nie ma silnej nazwy, ale zestaw klienta, który używa `as_friend` atrybut zapewnia.  
  
 Mimo że typy w przestrzeni nazw i zakres globalny może być znane klienta zestawu lub moduł .netmodule, dostępność elementu członkowskiego jest nadal obowiązują.  Na przykład nie można uzyskać dostępu do prywatnego elementu członkowskiego.  
  
 Należy jawnie udzielić dostępu do wszystkich typów w zestawie.  Na przykład zestaw C nie ma dostępu do wszystkich typów w zestawie, A Jeśli zestawu C odwołuje się do zestawu B i zestawu B ma dostęp do wszystkich typów w zestawie A.  
  
 Aby uzyskać informacje dotyczące sposobu podpisywania — oznacza to, jak zapewnić silnej nazwy do — zestawu, który jest utworzony przy użyciu kompilatora Visual C++, zobacz [silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
 Alternatywą dla funkcji zestawy friend służy <xref:System.Security.Permissions.StrongNameIdentityPermission> ograniczyć dostęp do poszczególnych typów.  
  
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
  
 W następnym przykładzie kodu uzyskuje dostęp do prywatnego typu składnika.  
  
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
  
 W następnym przykładzie kodu definiuje składnik, ale nie określa zestawu klienta, który będzie miał dostęp do typów w składniku.  
  
 Należy zauważyć, że składnik jest połączony za pomocą **/ opt: noref**. Dzięki temu emisję prywatnych typów w metadanych składnika, który nie jest wymagana podczas `InternalsVisibleTo` obecny jest atrybut. Aby uzyskać więcej informacji, zobacz [od (optymalizacje)](../build/reference/opt-optimizations.md).  
  
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
  
 Poniższy przykładowy kod definiuje klienta, który próbuje uzyskać dostęp prywatny typ składnika, który nie zapewnia dostępu do swoich prywatnych typów. Ze względu na zachowanie środowiska uruchomieniowego jeśli ma zostać przechwycony wyjątek, użytkownik musi próba uzyskania dostępu do prywatny typ w funkcji pomocnika.  
  
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
  
 W następnym przykładzie kodu pokazano, jak można utworzyć składnika silnej nazwy, który określa zestaw klienta, który będzie miał dostęp do typów w składniku.  
  
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
  
 Zwróć uwagę, że składnika należy określić swojego klucza publicznego. Sugerujemy, uruchom następujące polecenia sekwencyjnie w wierszu polecenia, aby utworzyć pary kluczy i uzyskać klucz publiczny:  
  
 **-d friend_assemblies.snk SN**  
  
 **SN -k friend_assemblies.snk**  
  
 **SN -i friend_assemblies.snk friend_assemblies.snk**  
  
 **SN -pc friend_assemblies.snk key.publickey**  
  
 **key.publickey - tp SN**  
  
 W następnym przykładzie kod uzyskuje dostęp do prywatnego typu w składniku silnej nazwy.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)