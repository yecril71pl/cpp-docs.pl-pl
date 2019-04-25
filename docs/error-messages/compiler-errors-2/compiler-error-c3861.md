---
title: Błąd kompilatora C3861
ms.date: 03/23/2018
f1_keywords:
- C3861
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
ms.openlocfilehash: 4ebfd3b0129e25cf543cac803a3b33fb074f3d70
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302415"
---
# <a name="compiler-error-c3861"></a>Błąd kompilatora C3861

> "*identyfikator*": nie odnaleziono identyfikatora

Kompilator nie był w stanie rozpoznać odwołania do identyfikatora, nawet za pomocą wyszukiwania zależnego od argumentów.

## <a name="remarks"></a>Uwagi

Aby naprawić ten błąd, porównaj użycie *identyfikator* do zgłoszenia identyfikator przypadku i sprawdzania pisowni. Upewnij się, że [zakres operatorów rozpoznawania](../../cpp/scope-resolution-operator.md) i przestrzeni nazw [dyrektywy using](../../cpp/namespaces-cpp.md#using_directives) są prawidłowo stosowane. Identyfikator jest zadeklarowana w pliku nagłówkowym, sprawdź, czy znajduje się nagłówek, aby odwoływać się do identyfikatora. Jeśli identyfikator ma być widoczne na zewnątrz, upewnij się, że zostanie ona zadeklarowana w dowolnym plikiem źródłowym, która go używa. Sprawdź również, że identyfikator deklaracji lub definicji nie jest wykluczone przez [dyrektywy kompilacji warunkowej](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

Zmiany do usuwania przestarzałych funkcji biblioteki środowiska uruchomieniowego języka C w programie Visual Studio 2015 może powodować C3861. Aby rozwiązać ten problem, usuń odwołania do tych funkcji, lub zastąp je ich bezpieczne rozwiązania alternatywne, jeśli istnieje. Aby uzyskać więcej informacji, zobacz [przestarzałe funkcje](../../c-runtime-library/obsolete-functions.md).

Jeśli błąd C3861 pojawia się po zakończeniu migracji projektów ze starszych wersji kompilatora, możesz mieć problemy związane z obsługiwanymi wersjami Windows. Visual C++ nie obsługuje już określania wartości docelowej Windows 95, Windows 98, Windows ME, Windows NT lub Windows 2000. Jeśli Twoje **WINVER** lub **_WIN32_WINNT** makra są przypisane do jednej z tych wersji systemu Windows, należy zmodyfikować makra. Aby uzyskać więcej informacji, zobacz [modyfikowanie WINVER i _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

## <a name="examples"></a>Przykłady

### <a name="undefined-identifier"></a>Niezdefiniowany identyfikator

Poniższy przykład generuje C3861, ponieważ nie zdefiniowano identyfikatora.

```cpp
// C3861.cpp
void f2(){}
int main() {
   f();    // C3861
   f2();   // OK
}
```

### <a name="identifier-not-in-scope"></a>Identyfikator nie znajduje się w zakresie

Poniższy przykład generuje C3861, ponieważ identyfikator tylko widoczne w zakresie pliku jego definicji, chyba że zostanie ona zadeklarowana w innych plikach źródłowych, które go używają.

```cpp
// C3861_a1.cpp
// Compile with: cl /EHsc /W4 C3861_a1.cpp C3861_a2.cpp
#include <iostream>
// Uncomment the following line to fix:
// int f();  // declaration makes external function visible
int main() {
   std::cout << f() << std::endl;    // C3861
}
```

```cpp
// C3861_a2.cpp
int f() {  // declared and defined here
   return 42;
}
```

### <a name="namespace-qualification-required"></a>Namespace kwalifikacyjnymi

Klasy wyjątków w standardowej bibliotece języka C++ wymagają `std` przestrzeni nazw.

```cpp
// C3861_b.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   try {
      throw exception("Exception");   // C3861
      // try the following line instead
      // throw std::exception("Exception");
   }
   catch (...) {
      std::cout << "caught an exception" << std::endl;
   }
}
```

### <a name="obsolete-function-called"></a>Wywołana funkcja przestarzała

Przestarzałe funkcje zostały usunięte z biblioteki CRT.

```cpp
// C3861_c.cpp
#include <stdio.h>
int main() {
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C3861
   // Use gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

### <a name="adl-and-friend-functions"></a>Funkcje usługi ADL i friend

Poniższy przykład generuje C3767, ponieważ kompilator nie może używać argumentów wyszukiwanie zależne `FriendFunc`:

```cpp
namespace N {
   class C {
      friend void FriendFunc() {}
      friend void AnotherFriendFunc(C* c) {}
   };
}

int main() {
   using namespace N;
   FriendFunc();   // C3861 error
   C* pC = new C();
   AnotherFriendFunc(pC);   // found via argument-dependent lookup
}
```

Aby naprawić błąd, Zadeklaruj friend w zakresie klasy i zdefiniuj go w zakresie przestrzeni nazw:

```cpp
class MyClass {
   int m_private;
   friend void func();
};

void func() {
   MyClass s;
   s.m_private = 0;
}

int main() {
   func();
}
```
