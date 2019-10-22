---
title: const_mem_fun_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: 5263612a26b2bcb606ad712a2a8e0a521ce9437a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688206"
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

@No__t_1 *PM*
Wskaźnik do funkcji członkowskiej klasy `Type` do przekonwertowania na obiekt funkcji.

*Pleft* \
Obiekt, na którym jest wywoływana funkcja członkowska *PM* .

## <a name="return-value"></a>Wartość zwracana

Dostosowywalna funkcja Jednoargumentowa.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *PM*, która musi być wskaźnikiem do funkcji członkowskiej klasy `Type`, w prywatnym obiekcie elementu członkowskiego. Definiuje jej funkcję członkowską `operator()` jako zwracającą (`Pleft` -> \* `Pm`) () **const**.

## <a name="example"></a>Przykład

Konstruktor `const_mem_fun_t` nie jest zazwyczaj używany bezpośrednio; funkcja pomocnika `mem_fun` jest używana do adaptacji funkcji Członkowskich. Zobacz [mem_fun](../standard-library/functional-functions.md#mem_fun) , aby zapoznać się z przykładem użycia adapterów funkcji składowych.
