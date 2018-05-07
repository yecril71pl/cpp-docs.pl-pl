---
title: Kompilatora (poziom 3) ostrzeżenie C4398 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ace2df75b5d2579b66a4d3930470021726ba4c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4398"></a>Kompilator C4398 ostrzegawcze (poziom 3)
"Zmienna": globalny obiekt dla procesu może nie działać poprawnie z wieloma domenami aplikacji; należy wziąć pod uwagę użycie __declspec(appdomain)  
  
 Funkcję wirtualną z [__clrcall](../../cpp/clrcall.md) konwencji wywoływania w typie natywnym powoduje utworzenie na vtable domeny aplikacji. Przekazanie zmiennej nie może rozwiązać poprawnie, gdy jest używany w wielu domenach aplikacji.  
  
 To ostrzeżenie można rozwiązać przez oznaczenie jawnie zmiennej `__declspec(appdomain)`. W wersjach programu Visual Studio przed Visual Studio 2017 to ostrzeżenie można rozwiązać przez kompilowania przy użyciu **/CLR: pure**, co czyni domyślnie zmienne globalne dla domeny appdomain.  
  
 Aby uzyskać więcej informacji, zobacz [elementu appdomain](../../cpp/appdomain.md) i [i domen aplikacji Visual C++](../../dotnet/application-domains-and-visual-cpp.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4398.  
  
```  
// C4398.cpp  
// compile with: /clr /W3 /c  
struct S {  
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall  
};  
  
S glob_s;   // C4398  
__declspec(appdomain) S glob_s2;   // OK  
```