---
title: mem_fun_ref_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_ref_t
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
ms.openlocfilehash: d8f5ef05d1bdeec694cdf22d7e7a163478127dfc
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687760"
---
# <a name="mem_fun_ref_t-class"></a>mem_fun_ref_t — Klasa

Klasa adaptera, która umożliwia `non_const` funkcji członkowskiej, która nie przyjmuje argumentów do wywołania jednoargumentowego obiektu, gdy zostanie zainicjowany z argumentem odwołania. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type>
class mem_fun_ref_t : public unary_function<Type, Result> {
    explicit mem_fun_ref_t(
    Result (Type::* _Pm)());

    Result operator()(Type& left) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm* \
Wskaźnik do funkcji członkowskiej klasy `Type` do przekonwertowania na obiekt funkcji.

\ *lewo*
Obiekt, na którym jest wywoływana funkcja członkowska *_Pm* .

## <a name="return-value"></a>Wartość zwracana

Dostosowywalna funkcja Jednoargumentowa.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *_Pm*, która musi być wskaźnikiem do funkcji składowej klasy `Type`, w prywatnym obiekcie członkowskim. Definiuje jej funkcję członkowską `operator()` jako zwracającą (**Left**. * `_Pm`) ().

## <a name="example"></a>Przykład

Konstruktor `mem_fun_ref_t` nie jest zazwyczaj używany bezpośrednio; funkcja pomocnika `mem_fun_ref` jest używana do adaptacji funkcji Członkowskich. Zobacz [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) , aby zapoznać się z przykładem użycia adapterów funkcji składowych.
