---
title: C3391 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3391
dev_langs:
- C++
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28615d85eca534966a4d8b90cef20ea577e0d592
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3391"></a>C3391 błąd kompilatora
"type_arg": nieprawidłowy typ argumentu dla parametru ogólnego "param" Ogólne "generic_type" musi być typem wartościowym niebędącym null  
  
Niepoprawnie wystąpienia typu ogólnego. Sprawdź definicję typu. Aby uzyskać więcej informacji, zobacz <xref:System.Nullable> i [ogólne](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
W poniższym przykładzie użyto C# do tworzenia składnika, który zawiera typu ogólnego, który ma pewne ograniczenia, które nie są obsługiwane podczas tworzenia typów ogólnych w języku C + +/ CLI. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
```cs  
// C3391.cs  
// Compile by using: csc /target:library C3391.cs  
// a C# program  
public class GR<N>  
where N : struct {}  
```  
  
Poniższy przykładowy składnik C3391.dll jest dostępny, generuje C3391.  
  
```cpp  
// C3391_b.cpp  
// Compile by using: cl /clr C3391_b.cpp  
#using <C3391.dll>  
using namespace System;  
value class VClass {};  
  
int main() {  
   GR< Nullable<VClass> >^ a =   
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable  
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK  
}  
```