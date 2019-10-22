---
title: const_mem_fun1_ref_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 76fae1ce29cb4c47870e45e8f946f6ff1fea1885
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688173"
---
# <a name="const_mem_fun1_ref_t-class"></a>const_mem_fun1_ref_t — Klasa

Klasa adaptera, która umożliwia **stałemu** funkcji składowej, która przyjmuje pojedynczy argument jako obiekt funkcji binarnej po zainicjowaniu z argumentem Reference. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type, class Arg>
    class const_mem_fun1_ref_t
        : public binary_function<Type, Arg, Result>
{
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
};
```

### <a name="parameters"></a>Parametry

@No__t_1 *PM*
Wskaźnik do funkcji członkowskiej klasy `Type` do przekonwertowania na obiekt funkcji.

\ *lewo*
Obiekt **const** , dla którego jest wywoływana funkcja członkowska *PM* .

*prawa* \
Argument, który jest przypisywany do *PM*.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalna funkcja binarna.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *PM*, która musi być wskaźnikiem do funkcji członkowskiej klasy `Type`, w prywatnym obiekcie elementu członkowskiego. Definiuje jej funkcję członkowską `operator()` jako zwracającą (`left`. \* *PM*) (`right`) **const**.

## <a name="example"></a>Przykład

Konstruktor `const_mem_fun1_ref_t` nie jest zazwyczaj używany bezpośrednio; funkcja pomocnika `mem_fun_ref` jest używana do adaptacji funkcji Członkowskich. Zobacz [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) , aby poznać przykłady użycia adapterów funkcji składowych.
