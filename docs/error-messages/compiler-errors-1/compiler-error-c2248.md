---
title: C2248 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2248
dev_langs:
- C++
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e48da84824b2069216c2ab3aca82ea9528251638
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172135"
---
# <a name="compiler-error-c2248"></a>C2248 błąd kompilatora
"*elementu członkowskiego*": nie można uzyskać dostępu "*access_level*"element członkowski zadeklarowany w klasie"*klasy*"  
  
Nie ma dostępu do elementów członkowskich klasy pochodnej `private` elementów członkowskich klasy podstawowej. Nie można uzyskać dostępu `private` lub `protected` członków wystąpień klas.  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład powoduje C2248 podczas prywatnych lub chronionych elementów członkowskich klasy są dostępne spoza tej klasy. Aby rozwiązać ten problem, Brak dostępu do tych elementów członkowskich bezpośrednio poza klasą. Użyj publicznego elementu członkowskiego danych i funkcji elementów członkowskich do interakcji z klasą.  
  
```cpp  
// C2248_access.cpp 
// compile with: cl /EHsc /W4 C2248_access.cpp 
#include <stdio.h>  

class X {  
public:  
    int  m_publicMember;  
    void setPrivateMember( int i ) {  
        m_privateMember = i;  
        printf_s("\n%d", m_privateMember);  
    }  
protected:  
    int  m_protectedMember;  
  
private:  
    int  m_privateMember;  
} x;  
  
int main() {  
    x.m_publicMember = 4;  
    printf_s("\n%d", x.m_publicMember);  
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected  
    x.m_privateMember = 3;   // C2248  m_privMemb is private  
    x.setPrivateMember(0);   // OK uses public access function  
}  
```  
  
Inny problem zgodności, który udostępnia C2248 jest używana i specjalizacja szablonu znajomych. Aby rozwiązać ten problem, zadeklarować friend szablonu funkcji przy użyciu pustego szablonu parametru listy <> lub parametry określonego szablonu.  
  
```cpp  
// C2248_template.cpp 
// compile with: cl /EHsc /W4 C2248_template.cpp 
template<class T>  
void f(T t) {  
    t.i;   // C2248  
}  
  
struct S {  
private:  
    int i;  
  
public:  
    S() {}  
    friend void f(S);   // refer to the non-template function void f(S)  
    // To fix, comment out the previous line and
    // uncomment the following line.  
    // friend void f<S>(S);  
};  
  
int main() {  
    S s;  
    f<S>(s);  
}  
```  
  
Inny problem zgodności, który udostępnia C2248 jest przy próbie deklarować elementu przyjaznego klasa i klasy nie jest widoczny dla deklaracji friend w zakresie klasy. Aby rozwiązać ten problem, należy przyznać przyjaźni do klasy otaczającej.  
  
```cpp  
// C2248_enclose.cpp  
// compile with: cl /W4 /c C2248_enclose.cpp  
class T {  
    class S {  
        class E {};  
    };  
    friend class S::E;   // C2248  
};  
  
class A {  
    class S {  
        class E {};  
        friend class A;  // grant friendship to enclosing class  
    };  
    friend class S::E;   // OK  
};  
```