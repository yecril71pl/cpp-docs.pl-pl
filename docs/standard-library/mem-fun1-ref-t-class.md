---
title: mem_fun1_ref_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 238d6147b2afa5ca3e143bc57aa4892e17d2c869
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687753"
---
# <a name="mem_fun1_ref_t-class"></a>mem_fun1_ref_t — Klasa

Klasa adaptera, która umożliwia `non_const` funkcję członkowską, która przyjmuje jeden argument jako obiekt funkcji binarnej po zainicjowaniu z argumentem odwołania. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_ref_t : public binary_function<Type, Arg, Result> {
    explicit mem_fun1_ref_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type& left,
    Arg right) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm* \
Wskaźnik do funkcji członkowskiej klasy `Type` do przekonwertowania na obiekt funkcji.

\ *lewo*
Obiekt, na którym jest wywoływana funkcja członkowska *_Pm* .

*prawa* \
Argument, który jest przyznawany *_Pm*.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalna funkcja binarna.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *_Pm*, która musi być wskaźnikiem do funkcji składowej klasy `Type`, w prywatnym obiekcie członkowskim. Definiuje jej funkcję członkowską `operator()` jako zwracającą (**Left**. \* `_Pm`) (**prawo**).

## <a name="example"></a>Przykład

Konstruktor `mem_fun1_ref_t` nie jest zazwyczaj używany bezpośrednio; funkcja pomocnika `mem_fun_ref` jest używana do adaptacji funkcji Członkowskich. Zobacz [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) , aby zapoznać się z przykładem użycia adapterów funkcji składowych.
