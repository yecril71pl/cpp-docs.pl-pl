---
title: const_mem_fun_ref_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_ref_t
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
ms.openlocfilehash: 8ce29eb0d2122dbd95fea34fa59f3fa11b9b388e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689757"
---
# <a name="const_mem_fun_ref_t-class"></a>const_mem_fun_ref_t — Klasa

Klasa adaptera, która umożliwia **stałej** funkcji składowej, która nie przyjmuje argumentów, które mają być wywoływane jako jednoargumentowy obiekt funkcji po zainicjowaniu z argumentem Reference. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type>
    class const_mem_fun_ref_t
: public unary_function<Type, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type& left) const;
};
```

### <a name="parameters"></a>Parametry

@No__t_1 *PM*
Wskaźnik do funkcji członkowskiej klasy `Type` do przekonwertowania na obiekt funkcji.

\ *lewo*
Obiekt, na którym jest wywoływana funkcja członkowska *PM* .

## <a name="return-value"></a>Wartość zwracana

Dostosowywalna funkcja Jednoargumentowa.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *PM*, która musi być wskaźnikiem do funkcji członkowskiej klasy `Type`, w prywatnym obiekcie elementu członkowskiego. Definiuje jej funkcję członkowską `operator()` jako zwracającą (**Left**. \* `Pm`) () **const**.

## <a name="example"></a>Przykład

Konstruktor `const_mem_fun_ref_t` nie jest zazwyczaj używany bezpośrednio; funkcja pomocnika `mem_fun_ref` jest używana do adaptacji funkcji Członkowskich. Zobacz [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) , aby zapoznać się z przykładem użycia adapterów funkcji składowych.
