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

C++ umożliwia wyrzucanie wyjątków dowolnego typu, jednak ogólnie zaleca się wyrzucanie typów, który pochodzą od std::exception. A C++ exception can be caught by a **catch** handler that specifies the same type as the thrown exception, or by a handler that can catch any type of exception.

Jeśli typ wyrzuconego wyjątku to klasa, która posiada również klasę bazową (lub klasy) wyjątek może zostać przechwycony przez program obsługi, który akceptuje klasy bazowe typu wyjątku, jak również odwołania do klasy bazowej typu wyjątku. Należy zauważyć, że gdy wyjątek zostaje przechwycony przez odwołanie, następuje jego powiązanie z rzeczywistym wyrzuconym obiektem wyjątku; w przeciwnym razie jest kopią (prawie tak samo jak argument do funkcji).

When an exception is thrown, it may be caught by the following types of **catch** handlers:

- Program obsługi, który może akceptować dowolny typ (przy użyciu składni wielokropka).

- A handler that accepts the same type as the exception object; because it is a copy, **const** and **volatile** modifiers are ignored.

- Program obsługi, który akceptuje odwołanie do tego samego typu co obiekt wyjątku.

- A handler that accepts a reference to a **const** or **volatile** form of the same type as the exception object.

- A handler that accepts a base class of the same type as the exception object; since it is a copy, **const** and **volatile** modifiers are ignored. The **catch** handler for a base class must not precede the **catch** handler for the derived class.

- Program obsługi, który akceptuje odwołanie do klasy bazowej tego samego typu co obiekt wyjątku.

- A handler that accepts a reference to a **const** or **volatile** form of a base class of the same type as the exception object.

- Program obsługi, który akceptuje wskaźnik, do którego można przekonwertować wyrzucony obiekt wskaźnika za pomocą standardowych reguł konwersji wskaźnika.

The order in which **catch** handlers appear is significant, because handlers for a given **try** block are examined in order of their appearance. Na przykład, błędem jest umieszczenie programu obsługi dla klasy bazowej przed programem obsługi dla klasy pochodnej. After a matching **catch** handler is found, subsequent handlers are not examined. As a result, an ellipsis **catch** handler must be the last handler for its **try** block. Na przykład:

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

In this example, the ellipsis **catch** handler is the only handler that is examined.

## <a name="see-also"></a>Zobacz także

[Modern C++ best practices for exceptions and error handling](../cpp/errors-and-exception-handling-modern-cpp.md)