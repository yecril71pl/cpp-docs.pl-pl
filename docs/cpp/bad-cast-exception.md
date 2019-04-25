---
title: bad_cast — Wyjątek
ms.date: 11/04/2016
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 028fa8cc90b33aca6a37fb3b7f58b8c5fad81bd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284776"
---
# <a name="badcast-exception"></a>bad_cast — Wyjątek

**Bad_cast** wyjątek jest generowany przez **dynamic_cast** operatora w wyniku zakończone niepowodzeniem Rzutowanie na typ odwołania.

## <a name="syntax"></a>Składnia

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>Uwagi

Interfejs **bad_cast** jest:

```cpp
class bad_cast : public exception {
public:
   bad_cast(const char * _Message = "bad cast");
   bad_cast(const bad_cast &);
   virtual ~bad_cast();
};
```

Poniższy kod zawiera przykład niepowodzenia **dynamic_cast** która zgłasza **bad_cast** wyjątku.

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo.h>
#include <iostream>

class Shape {
public:
   virtual void virtualfunc() const {}
};

class Circle: public Shape {
public:
   virtual void virtualfunc() const {}
};

using namespace std;
int main() {
   Shape shape_instance;
   Shape& ref_shape = shape_instance;
   try {
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);
   }
   catch (bad_cast b) {
      cout << "Caught: " << b.what();
   }
}
```

Wyjątek jest zgłaszany, ponieważ obiekt rzutowany (kształt) nie pochodzi od typu określone rzutowanie (Circle). Aby uniknąć wyjątek, należy dodać te deklaracje `main`:

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

Wycofać poczucie rzutowanie w **spróbuj** blokowania w następujący sposób:

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="see-also"></a>Zobacz także

[Operator dynamic_cast](../cpp/dynamic-cast-operator.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)