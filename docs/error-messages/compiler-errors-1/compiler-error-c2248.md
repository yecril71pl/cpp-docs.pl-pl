---
title: Błąd kompilatora C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: d9b9a6c04e7e9a5d88df516125280b6b23894a01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558200"
---
# <a name="compiler-error-c2248"></a>Błąd kompilatora C2248

"*elementu członkowskiego*": nie można uzyskać dostępu "*access_level*"składowa zadeklarowana w klasie"*klasy*"

Elementy członkowskie klasy pochodnej nie może uzyskać dostępu `private` członków klasy podstawowej. Nie można uzyskać dostępu `private` lub `protected` składowych wystąpienia klasy.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2248 podczas prywatnych lub chronionych składowych klasy są dostępne z poza klasy. Aby rozwiązać ten problem, nie ma dostępu te elementy członkowskie bezpośrednio poza klasą. Użyj publicznego elementu członkowskiego danych i elementów członkowskich do interakcji z klasą.

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

Inny problem zgodności, który udostępnia C2248 polega na użyciu zaprzyjaźnione i specjalizacji. Aby rozwiązać ten problem, deklarowanie przyjaznych funkcje szablonu za pomocą pusty szablon parametru listy <> lub parametry określonego szablonu.

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

Inny problem zgodności, który udostępnia C2248 jest przy próbie deklarować elementu przyjaznego klasy i klasa nie jest widoczny dla deklaracją elementu zaprzyjaźnionego w zakresie klasy. Aby rozwiązać ten problem, należy udzielić przyjaźni do klasy otaczającej.

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