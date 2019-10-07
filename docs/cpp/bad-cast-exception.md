---
title: bad_cast — Wyjątek
ms.date: 10/04/2019
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 7384394fb53c6aa4bc009a903ba0ed22bf0ed0d6
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998771"
---
# <a name="bad_cast-exception"></a>bad_cast — Wyjątek

Wyjątek **bad_cast** jest generowany przez operator **dynamic_cast** jako wynik nieudanego rzutowania na typ referencyjny.

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

Poniższy kod zawiera przykład błędu **dynamic_cast** , który zgłasza wyjątek **bad_cast** .

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo>
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

Wyjątek jest zgłaszany, ponieważ obiekt, który jest rzutowany (kształt) nie pochodzi od określonego typu rzutowania (koło). Aby uniknąć wyjątku, Dodaj następujące deklaracje do `main`:

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

Następnie Wycofaj sens rzutowania w bloku **try** w następujący sposób:

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[bad_cast](#bad_cast)|Konstruktor dla obiektów typu `bad_cast`.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[Whatman](#what)|TBD|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Operator przypisania, który przypisuje jeden obiekt `bad_cast` do innego.|

## <a name="bad_cast"></a>bad_cast

Konstruktor dla obiektów typu `bad_cast`.

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a>operator =

Operator przypisania, który przypisuje jeden obiekt `bad_cast` do innego.

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a>Whatman

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>Zobacz także

[operator dynamic_cast](../cpp/dynamic-cast-operator.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)\
[Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)
