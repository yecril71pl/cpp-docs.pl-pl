---
title: 'Porady: kierowanie ciągów za pomocą funkcji PInvoke | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a377e7074e72693a1a63e392c64a6d60c5995b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Porady: przeprowadzanie marshalingu ciągów za pomocą funkcji PInvoke
W tym temacie opisano sposób natywny funkcje, których ciągów w stylu języka C można wywołać przy użyciu ciągu CLR typu System::String przy użyciu wywołania platformy Framework .NET pomocy technicznej. Visual C++ programistów są zachęcani do zamiast tego użyj funkcji międzyoperacyjności języka C++ (jeśli jest to możliwe), ponieważ zapewnia P/Invoke małego błąd kompilacji raportowania, nie jest bezpieczne i może być niewygodne wdrożenia. Jeśli niezarządzanego API jest dostarczana jako biblioteki DLL i kod źródłowy jest niedostępny, następnie P/Invoke jest jedyną opcją, ale w przeciwnym razie zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
 Ciągi zarządzane i niezarządzane są wyświetlane inaczej w pamięci, dlatego przekazywanie ciągów z zarządzanych do niezarządzanych funkcji wymaga <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu nakazać kompilatora, aby wstawić mechanizmy konwersji wymagane przekazywanie danych ciągu poprawnie i bezpiecznie.  
  
 Podobnie jak w przypadku funkcji używanego tylko typy danych wewnętrznych, <xref:System.Runtime.InteropServices.DllImportAttribute> służy do deklarowania punkty wejścia zarządzanych w funkcjach natywnych, ale — może być przekazywany ciągów — zamiast definiować te punkty wejścia jako ciągi w stylu języka C, dojścia do wykonywania <xref:System.String> typu można zamiast tego. Powoduje wyświetlenie monitu o kompilatora, aby wstawić kod, który wykonuje konwersję wymagane. Dla każdego argumentu funkcji w funkcji niezarządzanej ciąg znaków <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut powinien być używany w celu wskazania, że z obiektem ciągu powinny być przekazywane do funkcji macierzystej jako ciągu w stylu języka C.  
  
## <a name="example"></a>Przykład  
 Poniższy kod składa się z modułu zarządzanych i niezarządzanych. Moduł niezarządzanym jest bibliotekę DLL, która definiuje funkcji o nazwie TakesAString, który akceptuje ANSI C-style ciąg w formie char *. Moduł zarządzany jest aplikacją wiersza polecenia, która importuje funkcja TakesAString, ale definiuje ją jako biorąc zarządzanego typu System.String zamiast znaków\*. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut używany do określenia, jak należy zorganizować zarządzanych ciąg wywołanego TakesAString.  
  
```  
// TraditionalDll2.cpp  
// compile with: /LD /EHsc  
#include <windows.h>  
#include <stdio.h>  
#include <iostream>  
  
using namespace std;  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAString(char*);  
}  
  
void TakesAString(char* p) {  
   printf_s("[unmanaged] %s\n", p);  
}  
```  
  
```  
// MarshalString.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL  
{  
   [DllImport("TraditionalDLL2.dll")]  
      static public void   
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);  
};  
  
int main() {  
   String^ s = gcnew String("sample string");  
    Console::WriteLine("[managed] passing managed string to unmanaged function...");  
   TraditionalDLL::TakesAString(s);  
   Console::WriteLine("[managed] {0}", s);  
}  
```  
  
 Ta metoda powoduje, że kopia ciąg, który można skonstruować na stercie niezarządzane, więc zmiany wprowadzone do ciągu w funkcji natywnej nie zostaną odzwierciedlone w zarządzanej kopii ciągu.  
  
 Należy pamiętać, że żadna jego część biblioteki DLL jest narażony na kodu zarządzanego za pośrednictwem tradycyjnych # dyrektywy include. W rzeczywistości biblioteki DLL jest dostępny w czasie wykonywania, więc problemy z funkcjami zaimportowane z `DllImport` nie zostanie wykryty w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)