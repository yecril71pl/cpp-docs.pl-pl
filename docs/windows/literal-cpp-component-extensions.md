---
title: "literał (C++ Component Extensions) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- literal
- literal_cpp
dev_langs: C++
helpviewer_keywords: literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f858e94bf916c2d441cee607739bb9e08da09b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="literal-c-component-extensions"></a>literal (C++ Component Extensions)
Zmienna (elementu członkowskiego danych) jest oznaczony jako `literal` w **/CLR** kompilacji jest odpowiednikiem natywnego `static const` zmiennej.  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 **Uwagi**  
  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych.)  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 **Uwagi**  
  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do środowiska uruchomieniowego systemu Windows.)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
  
## <a name="remarks"></a>Uwagi  
 Element członkowski danych jest oznaczona jako `literal` musi zostać zainicjowany po zadeklarowaniu i wartość musi być stałą typu całkowitego, wyliczeniowego lub typu string. Konwersja z typu wyrażenia inicjowania na typ statyczny const — element członkowski danych nie może wymagać konwersji zdefiniowanej przez użytkownika.  
  
 Brak pamięci zarezerwowanej dla pola literal w czasie wykonywania; tylko zostanie wstawiona wartość metadanych dla tej klasy.  
  
 Oznaczone jako zmienną `static const` nie będą dostępne w metadanych do inne kompilatory.  
  
 Aby uzyskać więcej informacji, zobacz [statycznych](../cpp/storage-classes-cpp.md) i [const](../cpp/const-cpp.md).  
  
 `literal`jest słowem kluczowym kontekstowa. Zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, że `literal` zmienna oznacza `static`.  
  
```  
// mcppv2_literal.cpp  
// compile with: /clr  
ref struct X {  
   literal int i = 4;  
};  
  
int main() {  
   int value = X::i;  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje wpływ literał w metadanych:  
  
```  
// mcppv2_literal2.cpp  
// compile with: /clr /LD  
public ref struct A {  
   literal int lit = 0;  
   static const int sc = 1;  
};  
```  
  
 Należy zauważyć różnicę w metadanych dla `sc` i `lit`: `modopt` dyrektywa jest stosowana do `sc`, czyli może być ignorowane przez inne kompilatory.  
  
```  
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```  
  
```  
.field public static literal int32 lit = int32(0x0000000A)  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład utworzone w języku C#, odwołuje się do metadanych utworzony w poprzednim przykładzie i pokazuje wpływ `literal` i `static const` zmiennych:  
  
```  
// mcppv2_literal3.cs  
// compile with: /reference:mcppv2_literal2.dll  
// A C# program  
class B {  
   public static void Main() {  
      // OK  
      System.Console.WriteLine(A.lit);  
      System.Console.WriteLine(A.sc);  
  
      // C# does not enforce C++ const  
      A.sc = 9;  
      System.Console.WriteLine(A.sc);  
  
      // C# enforces const for a literal  
      A.lit = 9;   // CS0131  
  
      // you can assign a C++ literal variable to a C# const variable  
      const int i = A.lit;  
      System.Console.WriteLine(i);  
  
      // but you cannot assign a C++ static const variable  
      // to a C# const variable  
      const int j = A.sc;   // CS0133  
      System.Console.WriteLine(j);  
   }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)