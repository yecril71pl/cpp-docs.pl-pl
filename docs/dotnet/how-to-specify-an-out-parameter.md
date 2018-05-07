---
title: 'Porady: Określanie poza parametr | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: adc56a65829064376d2472206f916d32d369cb01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-an-out-parameter"></a>Porady: określanie parametru wyjściowego
W tym przykładzie pokazano sposób wywołania tej funkcji z programu C# oraz jak określić, że parametr funkcji jest parametrem wyjściowym.  
  
 Parametr wyjściowy jest określony w programie Visual C++ z <xref:System.Runtime.InteropServices.OutAttribute> .  
  
## <a name="example"></a>Przykład  
 Pierwsza część w tym przykładzie jest plikiem Visual C++ z typu, który zawiera funkcji z parametrem out.  
  
```  
// cpp_out_param.cpp  
// compile with: /LD /clr:safe  
using namespace System;  
public value struct TestStruct {  
   static void Test([Runtime::InteropServices::Out] String^ %s) {  
      s = "a string";  
   }  
};  
```  
  
## <a name="example"></a>Przykład  
 Jest to klienta C#, który używa składnika Visual C++ utworzony w poprzednim przykładzie.  
  
```  
// cpp_out_param_2.cs  
// compile with: /reference:cpp_out_param.dll  
using System;  
class TestClass {  
   public static void Main() {  
      String t;  
      TestStruct.Test(out t);  
      System.Console.WriteLine(t);  
   }  
}  
```  
  
```Output  
a string  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)