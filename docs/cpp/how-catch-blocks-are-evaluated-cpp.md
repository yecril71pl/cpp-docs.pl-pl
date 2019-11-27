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
ms.openlocfilehash: 027dc87923a588ea891dbf6dd835e2baba75a1cb
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245855"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Sposób oceniania bloków Catch (C++)

C++ umożliwia wyrzucanie wyjątków dowolnego typu, jednak ogólnie zaleca się wyrzucanie typów, który pochodzą od std::exception. Wyjątek może być przechwytywany przez procedurę obsługi catch, która określa ten sam typ co zgłoszony wyjątek lub przez program obsługi, który może przechwytywać dowolny typ wyjątku. C++

Jeśli typ wyrzuconego wyjątku to klasa, która posiada również klasę bazową (lub klasy) wyjątek może zostać przechwycony przez program obsługi, który akceptuje klasy bazowe typu wyjątku, jak również odwołania do klasy bazowej typu wyjątku. Należy zauważyć, że gdy wyjątek zostaje przechwycony przez odwołanie, następuje jego powiązanie z rzeczywistym wyrzuconym obiektem wyjątku; w przeciwnym razie jest kopią (prawie tak samo jak argument do funkcji).

Gdy wyjątek jest zgłaszany, może być przechwycony przez następujące typy obsługi **catch** :

- Program obsługi, który może akceptować dowolny typ (przy użyciu składni wielokropka).

- Program obsługi, który akceptuje ten sam typ co obiekt wyjątku; ponieważ jest to kopia, Modyfikatory **const** i **volatile** są ignorowane.

- Program obsługi, który akceptuje odwołanie do tego samego typu co obiekt wyjątku.

- Program obsługi, który akceptuje odwołanie do formy **const** lub **volatile** tego samego typu co obiekt wyjątku.

- Program obsługi, który akceptuje klasę bazową tego samego typu co obiekt wyjątku; ponieważ jest to kopia, Modyfikatory **const** i **volatile** są ignorowane. Procedura obsługi **catch** dla klasy bazowej nie może poprzedzać obsługi **catch** dla klasy pochodnej.

- Program obsługi, który akceptuje odwołanie do klasy bazowej tego samego typu co obiekt wyjątku.

- Program obsługi, który akceptuje odwołanie do formy **const** lub **volatile** klasy bazowej tego samego typu co obiekt wyjątku.

- Program obsługi, który akceptuje wskaźnik, do którego można przekonwertować wyrzucony obiekt wskaźnika za pomocą standardowych reguł konwersji wskaźnika.

Kolejność, w jakiej są wyświetlane programy obsługi **catch** , jest istotna, ponieważ programy obsługi danego bloku **try** są badane w kolejności ich występowania. Na przykład, błędem jest umieszczenie programu obsługi dla klasy bazowej przed programem obsługi dla klasy pochodnej. Po znalezieniu pasującej obsługi **catch** nie są badane kolejne programy obsługi. W związku z tym program obsługi **catch** w postaci wielokropka musi być ostatnim programem obsługi dla jego bloku **try** . Na przykład:

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

W tym przykładzie procedura obsługi **catch** w postaci wielokropka jest jedyną zbadaną obsługą.

## <a name="see-also"></a>Zobacz także

[Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)