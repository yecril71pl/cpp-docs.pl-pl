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
ms.openlocfilehash: b40f64671e7c259b7dc04b31a11d20d0fc76c5c4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68242396"
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
class bad_cast : public exception
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

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[bad_cast —](#bad_cast)|Konstruktor dla obiektów typu `bad_cast`.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[Co to](#what)|TBD|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Operator przypisania, który przypisuje jeden `bad_cast` obiektu do drugiego.|

## <a name="bad_cast"></a> bad_cast —

Konstruktor dla obiektów typu `bad_cast`.

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a> operator =

Operator przypisania, który przypisuje jeden `bad_cast` obiektu do drugiego.

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a> Co to

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>Zobacz także

[Operator dynamic_cast](../cpp/dynamic-cast-operator.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)