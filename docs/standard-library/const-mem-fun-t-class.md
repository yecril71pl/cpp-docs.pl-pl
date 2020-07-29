---
title: const_mem_fun_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: 6b34fb6b20b2aaf2f18fbe8d937e50bdbaa3bdff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228352"
---
# <a name="const_mem_fun_t-class"></a>const_mem_fun_t — Klasa

Klasa adaptera, która umożliwia stałej funkcji składowej, która nie przyjmuje argumentów, które mają być wywoływane jako jednoargumentowy obiekt funkcji po zainicjowaniu z argumentem Reference. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
};
```

### <a name="parameters"></a>Parametry

*23:59:59*\
Wskaźnik do funkcji składowej klasy `Type` , która ma zostać przekonwertowana na obiekt funkcji.

*Pleft*\
Obiekt, na którym jest wywoływana funkcja członkowska *PM* .

## <a name="return-value"></a>Wartość zwracana

Dostosowywalna funkcja Jednoargumentowa.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *PM*, która musi być wskaźnikiem do funkcji składowej klasy `Type` , w prywatnym obiekcie składowej. Definiuje swoją funkcję członkowską `operator()` jako zwracaną ( `Pleft` -> \* `Pm` ) () **`const`** .

## <a name="example"></a>Przykład

Konstruktor `const_mem_fun_t` nie jest zazwyczaj używany bezpośrednio; funkcja pomocnika `mem_fun` służy do adaptacji funkcji Członkowskich. Zobacz [mem_fun](../standard-library/functional-functions.md#mem_fun) , aby zapoznać się z przykładem użycia adapterów funkcji składowych.
