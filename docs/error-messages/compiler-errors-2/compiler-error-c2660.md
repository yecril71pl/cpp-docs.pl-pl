---
title: "C2660 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2660
dev_langs: C++
helpviewer_keywords: C2660
ms.assetid: 2e01a1db-4f00-4df6-a04d-cb6f70a6922b
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a7c9237cf8d2bce08861cc5c225617c60966d83e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2660"></a>C2660 błąd kompilatora
"Funkcja": funkcja nie przyjmuje liczba parametrów  
  
 Funkcja jest wywoływana z nieprawidłową liczbą parametrów.  
  
 C2660 może wystąpić, jeśli przypadkowo wywołania funkcji API systemu Windows, a nie funkcja członkowska MFC o takiej samej nazwie. Aby rozwiązać ten problem:  
  
-   Dostosuj wywołanie funkcji, aby był zgodny z formatem wywołanie funkcji Członkowskich.  
  
-   Operator rozpoznawania zakresów Użyj (`::`) do nakazuje kompilatorowi do wyszukania nazwy funkcji w obszarze nazw globalnych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2660.  
  
```  
// C2660.cpp  
void func( int, int ) {}  
  
int main() {  
   func( 1 );   // C2660 func( int ) not declared  
   func( 1, 0 );   // OK  
}  
```  
  
## <a name="example"></a>Przykład  
 C2660 może również wystąpić, jeśli użytkownik spróbuje bezpośrednio wywoływać metodę Dispose typu zarządzanego. Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers). Poniższy przykład generuje C2660.  
  
```  
// C2660_a.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Threading;  
  
void CheckStatus( Object^ stateInfo ) {}  
  
int main() {  
   ManualResetEvent^ event = gcnew ManualResetEvent( false );     
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );  
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );  
  
   stateTimer->Dispose();   // C2660  
   stateTimer->~Timer();   // OK  
}  
```  
  
## <a name="example"></a>Przykład  
 C2660 zostanie przeprowadzona, jeśli Klasa pochodna ukrywa funkcji.  
  
```  
// C2660b.cpp  
// C2660 expected  
#include <stdio.h>  
  
class f {  
public:  
   void bar() {  
      printf_s("in f::bar\n");  
    }  
};  
  
class f2 : public f {  
public:  
   void bar(int i){printf("in f2::bar\n");}  
   // Uncomment the following line to resolve.  
   // using f::bar;   // - using declaration added  
   // or  
   // void bar(){__super::bar();}  
};  
  
int main() {  
   f2 fObject;  
   fObject.bar();  
}  
```  
  
## <a name="example"></a>Przykład  
 C2660 może wystąpić, jeśli wywołanie z właściwości indeksowanej.  
  
```  
// C2660c.cpp  
// compile with: /clr  
ref class X {  
   double d;  
public:  
   X() : d(1.9) {}  
   property double MyProp[] {  
      double get(int i) {  
         return d;  
      }  
   }   // end MyProp definition  
};  
  
int main() {  
   X ^ MyX = gcnew X();  
   System::Console::WriteLine(MyX->MyProp(1));   // C2660  
   System::Console::WriteLine(MyX->MyProp[1]);   // OK  
}  
```  
  
## <a name="example"></a>Przykład  
 C2660 może wystąpić, jeśli wywołanie z właściwości indeksowanej.  
  
```  
// C2660d.cpp  
// compile with: /clr  
ref class A{  
public:  
   property int default[int,int] {  
      int get(int a, int b) {  
         return a + b;  
      }  
   }  
};  
  
int main() {  
   A^ a = gcnew A;  
   int x = a[3][5];   // C2660  
   int x2 = a[3,5];   // OK  
}  
```  
  
## <a name="example"></a>Przykład  
 C2660 może wystąpić w przypadku definiowania klasy szablonu operatora new, ale operatora new tworzy obiekt, którego typ jest inny niż typ otaczający.  
  
```  
// C2660e.cpp  
// compile with: /c  
#include <malloc.h>  
  
template <class T> class CA {  
private:  
    static T** line;  
   void* operator new (size_t, int i) {   
      return 0;  
   }  
   void operator delete(void* pMem, int i) {  
      free(pMem);  
   }  
  
public:  
   CA () { new (1) T(); }   // C2660  
   // try the following line instead  
   // CA () { new (1) CA<int>(); }  
};  
  
typedef CA <int> int_CA;  
  
void AAA() {  
   int_CA  list;  
}  
```