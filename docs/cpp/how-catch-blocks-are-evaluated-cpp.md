---
title: Sposób oceniania bloków Catch (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
ms.openlocfilehash: 21d68b25fa3695a9b5637dcace081424f99911d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188105"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Sposób oceniania bloków Catch (C++)

C++ umożliwia wyrzucanie wyjątków dowolnego typu, jednak ogólnie zaleca się wyrzucanie typów, który pochodzą od std::exception. Wyjątek języka C++ może zostać przechwycony przez **`catch`** procedurę obsługi, która określa ten sam typ co zgłoszony wyjątek lub przez program obsługi, który może przechwytywać dowolny typ wyjątku.

Jeśli typ wyrzuconego wyjątku to klasa, która posiada również klasę bazową (lub klasy) wyjątek może zostać przechwycony przez program obsługi, który akceptuje klasy bazowe typu wyjątku, jak również odwołania do klasy bazowej typu wyjątku. Należy zauważyć, że gdy wyjątek zostaje przechwycony przez odwołanie, następuje jego powiązanie z rzeczywistym wyrzuconym obiektem wyjątku; w przeciwnym razie jest kopią (prawie tak samo jak argument do funkcji).

Gdy wyjątek jest zgłaszany, może być przechwycony przez następujące typy **`catch`** obsługi:

- Program obsługi, który może akceptować dowolny typ (przy użyciu składni wielokropka).

- Program obsługi, który akceptuje ten sam typ co obiekt wyjątku; ponieważ jest to kopia, **`const`** a **`volatile`** Modyfikatory są ignorowane.

- Program obsługi, który akceptuje odwołanie do tego samego typu co obiekt wyjątku.

- Program obsługi, który akceptuje odwołanie do **`const`** formularza lub tego **`volatile`** samego typu co obiekt wyjątku.

- Program obsługi, który akceptuje klasę bazową tego samego typu co obiekt wyjątku; ponieważ jest to kopia, **`const`** a **`volatile`** Modyfikatory są ignorowane. **`catch`** Procedura obsługi dla klasy bazowej nie może poprzedzać **`catch`** procedury obsługi dla klasy pochodnej.

- Program obsługi, który akceptuje odwołanie do klasy bazowej tego samego typu co obiekt wyjątku.

- Program obsługi, który akceptuje odwołanie do **`const`** lub **`volatile`** postać klasy bazowej tego samego typu co obiekt wyjątku.

- Program obsługi, który akceptuje wskaźnik, do którego można przekonwertować wyrzucony obiekt wskaźnika za pomocą standardowych reguł konwersji wskaźnika.

Kolejność, w której **`catch`** pojawiają się programy obsługi, jest istotna, ponieważ programy obsługi dla danego **`try`** bloku są badane w kolejności ich występowania. Na przykład, błędem jest umieszczenie programu obsługi dla klasy bazowej przed programem obsługi dla klasy pochodnej. Po **`catch`** znalezieniu zgodnej procedury obsługi nie są badane kolejne programy obsługi. W związku z tym program obsługi wielokropka **`catch`** musi być ostatnim programem obsługi dla jego **`try`** bloku. Na przykład:

```cpp
// ...
try
{
    // ...
}
catch( ... )
{
    // Handle exception here.
}
// Error: the next two handlers are never examined.
catch( const char * str )
{
    cout << "Caught exception: " << str << endl;
}
catch( CExcptClass E )
{
    // Handle CExcptClass exception here.
}
```

W tym przykładzie procedura obsługi wielokropka **`catch`** jest jedyną zbadaną obsługą.

## <a name="see-also"></a>Zobacz także

[Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)
