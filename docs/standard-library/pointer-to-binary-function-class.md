---
title: pointer_to_binary_function — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 890ebb7d4c2b8fbd51a4460e21efba3e763ead7e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687193"
---
# <a name="pointer_to_binary_function-class"></a>pointer_to_binary_function — Klasa

Konwertuje wskaźnik funkcji binarnej na dostosowywalną funkcję binarną. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>Parametry

*pfunc* \
Funkcja binarna do przekonwertowania.

\ *lewo*
Lewy obiekt, na którym jest wywoływana *\*pfunc* .

*prawa* \
Prawidłowy obiekt, w którym jest wywoływana *\*pfunc* .

## <a name="return-value"></a>Wartość zwracana

Szablon klasy przechowuje kopię `pfunc`. Definiuje jej funkcję członkowską `operator()` jako zwracającą `(* pfunc)(Left, right)`.

## <a name="remarks"></a>Uwagi

Wskaźnik funkcji binarnej jest obiektem funkcji i może być przesłany do C++ dowolnego algorytmu biblioteki standardowej, który oczekuje funkcji binarnej jako parametru, ale nie można go dostosować. Aby można było użyć go z adapterem, takim jak powiązanie wartości lub użycie jej z negacją, musi być dostarczana z zagnieżdżonymi typami `first_argument_type`, `second_argument_type` i `result_type`, które umożliwiają takie dostosowanie. Konwersja przez `pointer_to_binary_function` umożliwia adapterom funkcji współdziałanie ze wskaźnikami funkcji binarnych.

## <a name="example"></a>Przykład

Konstruktor `pointer_to_binary_function` jest rzadko używany bezpośrednio. Zapoznaj się z funkcją pomocnika [ptr_fun](../standard-library/functional-functions.md#ptr_fun) , aby zapoznać się z przykładem sposobu deklarowania i używania predykatu adaptera `pointer_to_binary_function`.
