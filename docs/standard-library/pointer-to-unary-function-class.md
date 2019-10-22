---
title: pointer_to_unary_function — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: 2b6bf82faa39e22c5af584a9fc3ebf68f5851463
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689139"
---
# <a name="pointer_to_unary_function-class"></a>pointer_to_unary_function — Klasa

Konwertuje wskaźnik jednoargumentowy funkcji na dostosowywalną funkcję jednoargumentową. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Parametry

*pfunc* \
Funkcja binarna do przekonwertowania.

\ *lewo*
Obiekt, na którym jest wywoływana *\*pfunc* .

## <a name="return-value"></a>Wartość zwracana

Szablon klasy przechowuje kopię `pfunc`. Definiuje swoją funkcję członkowską `operator()` jako zwracającą (\* **pFunc**) (_ *Left*).

## <a name="remarks"></a>Uwagi

Jednoargumentowy wskaźnik funkcji jest obiektem funkcji i może być przekazaniem do dowolnego C++ algorytmu biblioteki standardowej, który oczekuje jednoargumentowej funkcji jako parametru, ale nie jest możliwe do dostosowania. Aby można było użyć go z adapterem, takim jak powiązanie wartości lub użycie jej z negacją, musi być dostarczony z zagnieżdżonymi typami `argument_type` i `result_type`, które umożliwiają takie dostosowanie. Konwersja przez `pointer_to_unary_function` umożliwia adapterom funkcji współdziałanie ze wskaźnikami funkcji binarnych.

## <a name="example"></a>Przykład

Konstruktor `pointer_to_unary_function` jest rzadko używany bezpośrednio. Zapoznaj się z funkcją pomocnika [ptr_fun](../standard-library/functional-functions.md#ptr_fun) , aby zapoznać się z przykładem sposobu deklarowania i używania predykatu adaptera `pointer_to_unary_function`.
