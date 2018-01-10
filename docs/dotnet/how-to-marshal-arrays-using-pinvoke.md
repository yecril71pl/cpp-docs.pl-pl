---
title: "Porady: kierowanie tablic za pomocą funkcji PInvoke | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3694d6628005c49cc824e52d710e64e060822f96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>Porady: przeprowadzanie marshalingu tablic za pomocą funkcji PInvoke
W tym temacie opisano sposób natywny funkcje, których ciągów w stylu języka C można wywołać przy użyciu typu ciąg CLR <xref:System.String> przy użyciu wywołania platformy Framework .NET pomocy technicznej. Visual C++ programistów są zachęcani do zamiast tego użyj funkcji międzyoperacyjności języka C++ (jeśli jest to możliwe), ponieważ zapewnia P/Invoke małego błąd kompilacji raportowania, nie jest bezpieczne i może być niewygodne wdrożenia. Jeśli niezarządzanego API jest dostarczana jako biblioteki DLL i kod źródłowy jest niedostępny, P/Invoke jest jedyną opcją (w przeciwnym razie zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)).  
  
## <a name="example"></a>Przykład  
 Ponieważ natywnych i zarządzanych tablic są wyświetlane inaczej w pamięci, przekazywanie ich pomyślnie granicy zarządzanych/niezarządzanych wymaga konwersji lub przekazywanie. W tym temacie przedstawiono sposób tablicę elementów proste (blitable) mogą zostać przekazane do funkcji natywnych z kodu zarządzanego.  
  
 Podobnie jak zarządzanych/niezarządzanych danych marshalingu ogólnie rzecz biorąc, <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut służy do tworzenia zarządzany punkt wejścia dla każdej funkcji macierzystego, który będzie używany. W przypadku funkcji, które przyjmują tablic jako argumenty <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut musi być również używany do określenia w kompilatorze, jak będą przekazywane dane. W poniższym przykładzie <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenie jest używany do określania, czy tablicy zarządzanej będą przekazywane jako tablica stylu języka C.  
  
 Poniższy kod składa się z modułu zarządzanych i niezarządzanych. Niezarządzane modułu jest bibliotekę DLL, która definiuje funkcję, która akceptuje tablica liczb całkowitych. Drugi moduł jest zarządzanej aplikacji wiersza polecenia, który importuje tej funkcji, ale definiuje ją w postaci tablicy i używa <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić, że tablica powinny być konwertowane do tablicy natywnej po wywołaniu.  
  
 Moduł zarządzany została skompilowana z/CLR, ale/CLR: pure działa również. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
```cpp  
// TraditionalDll4.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);  
}  
  
void TakesAnArray(int len, int a[]) {  
   printf_s("[unmanaged]\n");  
   for (int i=0; i<len; i++)  
      printf("%d = %d\n", i, a[i]);  
}  
```  
  
```cpp  
// MarshalBlitArray.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL {  
   [DllImport("TraditionalDLL4.dll")]  
   static public void TakesAnArray(  
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);  
};  
  
int main() {  
   array<int>^ b = gcnew array<int>(3);  
   b[0] = 11;  
   b[1] = 33;  
   b[2] = 55;  
   TraditionalDLL::TakesAnArray(3, b);  
  
   Console::WriteLine("[managed]");  
   for (int i=0; i<3; i++)  
      Console::WriteLine("{0} = {1}", i, b[i]);  
}  
```  
  
 Należy pamiętać, że żadna jego część biblioteki DLL jest narażony na kodu zarządzanego za pośrednictwem tradycyjnych # dyrektywy include. W rzeczywistości, ponieważ plik DLL, który jest dostępny tylko w czasie wykonywania, problemy z funkcjami są importowane z <xref:System.Runtime.InteropServices.DllImportAttribute> nie zostanie wykryty w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)