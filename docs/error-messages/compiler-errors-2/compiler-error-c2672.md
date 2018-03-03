---
title: "C2672 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.date: 10/24/2017
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C2672
dev_langs:
- C++
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52663aed470aff254d07cba6a65f484269d8703d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2672"></a>C2672 błąd kompilatora

> "*funkcja*": nie zgodnej przeciążonej funkcji znaleziono

Kompilator nie może odnaleźć przeciążonej funkcji odpowiadający określonej funkcji. Nie znaleziono czy zajmuje zgodnych parametrów lub brak pasującego funkcji ma wymagany ułatwień dostępu w kontekście.

W przypadku niektórych kontenery biblioteki standardowej lub algorytmów z typów podać dostępnych elementach członkowskich lub zaprzyjaźnionych funkcji, które spełniają wymagania algorytm lub kontenera. Na przykład swój iteratora typ powinien pochodzić od `std::iterator<>`. Typ uważane za po lewej stronie i prawostronny operand może wymagać operacji porównywania lub użycie innych działających na typy elementów kontenera. Użycie typu prawostronny operand mogą wymagać wykonania operator jako funkcję niebędący elementem członkowskim typu.

## <a name="example"></a>Przykład

Wersje kompilatora przed Visual Studio 2017 nie wykonał dostępu sprawdzanie na nazwy kwalifikowane w niektórych kontekstach szablonu. Może to utrudniać oczekiwane zachowanie techniki SFINAE, których można oczekiwać podstawienie się niepowodzeniem z powodu inaccessibility nazwy. To może potencjalnie spowodował awarię lub nieoczekiwanego zachowania w czasie wykonywania z powodu kompilatora niepoprawnie wywoływania niewłaściwy przeciążenia operatora. W programie Visual Studio 2017 r wystąpi błąd kompilatora jest wywoływane.

W tym przykładzie kompiluje w programie Visual Studio 2015, ale zgłasza błąd w programie Visual Studio 2017 r. Aby rozwiązać ten problem, upewnij elementu członkowskiego parametru szablonu, które są dostępne w którym jest oceniana.

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```