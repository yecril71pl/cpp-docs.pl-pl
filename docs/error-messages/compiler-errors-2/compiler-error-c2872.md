---
title: C2872 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2872
dev_langs:
- C++
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 636f263382c41806e04c50c0770340305a3013ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2872"></a>C2872 błąd kompilatora
"*symbol*": niejednoznaczny symbol  
  
Kompilator nie może określić symbol, którego odnosi się do. Więcej niż jeden symbol o określonej nazwie znajduje się w zakresie. Zobacz uwagi następujący komunikat o błędzie dla lokalizacji plików i deklaracje kompilatora znaleziono niejednoznaczny symbol. Aby rozwiązać ten problem, można pełnej kwalifikacji niejednoznaczny symbol przy użyciu ich nazw, na przykład `std::byte` lub `::byte`. Można również użyć [alias przestrzeni nazw](../../cpp/namespaces-cpp.md#namespace_aliases) umożliwiają nazw uwzględnione wygodny krótka nazwa do użycia podczas usuwania niejednoznaczności w nazwach symbole w kodzie źródłowym.  
  
C2872 może wystąpić, jeśli plik nagłówka zawiera [dyrektywa using](../../cpp/namespaces-cpp.md#using_directives), i jest zawarty w pliku nagłówka kolejnych zawierający typ, który jest również w przestrzeni nazw określonej w `using` dyrektywy. Określ `using` dyrektywy tylko po wszystkie pliki nagłówka są określane za pomocą `#include`.  
  
 Aby uzyskać więcej informacji na temat C2872, zobacz artykuły wiedzy [PRB: kompilatora błędy przy użyciu #import XML w Visual C++ .NET](http://support.microsoft.com/kb/316317) i ["C2872 błąd:"Platformy": niejednoznaczny symbol" komunikat o błędzie, korzystając z Przestrzeń nazw Windows::Foundation::METADATA w programie Visual Studio 2013](https://support.microsoft.com/kb/2890859).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2872, ponieważ jest niejednoznaczne odwołanie do zmiennej o nazwie `i`; dwie zmienne o takiej samej nazwie znajdują się w zakresie:  
  
```cpp  
// C2872.cpp  
// compile with: cl /EHsc C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok, uses i from global namespace  
   A::i++;   // ok, uses i from namespace A  
   i++;   // C2872 ambiguous: ::i or A::i? 
   // To fix this issue, use the fully qualified name
   // for the intended variable. 
}  
```