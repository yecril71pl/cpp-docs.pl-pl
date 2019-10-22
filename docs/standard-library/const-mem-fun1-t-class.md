---
title: const_mem_fun1_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 1af44635400037c6359b13c4f2925c3ac7f2d9d5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689747"
---
# <a name="const_mem_fun1_t-class"></a>const_mem_fun1_t — Klasa

Klasa adaptera, która umożliwia **stałemu** funkcji składowej, która przyjmuje pojedynczy argument jako obiekt funkcji binarnej, gdy zostanie zainicjowany przy użyciu argumentu wskaźnika. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* member_ptr)(Arg) const);
    Result operator()(const Type* left, Arg right) const;
};
```

### <a name="parameters"></a>Parametry

*member_ptr* \
Wskaźnik do funkcji członkowskiej klasy `Type` do przekonwertowania na obiekt funkcji.

\ *lewo*
Obiekt **const** , dla którego jest wywoływana funkcja członkowska *member_ptr* .

*prawa* \
Argument, który jest przyznawany *member_ptr*.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalna funkcja binarna.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *member_ptr*, która musi być wskaźnikiem do funkcji składowej klasy `Type`, w prywatnym obiekcie członkowskim. Definiuje jej funkcję członkowską `operator()` jako zwracającą `(left->member_ptr)(right) const`.

## <a name="example"></a>Przykład

Konstruktor `const_mem_fun1_t` jest rzadko używany bezpośrednio. `mem_fn` służy do adaptacji funkcji Członkowskich. Zobacz [mem_fn](../standard-library/functional-functions.md#mem_fn) , aby zapoznać się z przykładem użycia adapterów funkcji składowych.
