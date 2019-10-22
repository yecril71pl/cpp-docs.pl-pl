---
title: mem_fun1_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 00d9322a8f0530da2e48b3f16fb52c00f9d1b075
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687733"
---
# <a name="mem_fun1_t-class"></a>mem_fun1_t — Klasa

Klasa adaptera, która umożliwia `non_const` funkcję członkowską, która przyjmuje jeden argument jako obiekt funkcji binarnej, gdy zostanie zainicjowany przy użyciu argumentu wskaźnika. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm* \
Wskaźnik do funkcji członkowskiej klasy `Type` do przekonwertowania na obiekt funkcji.

*_Pleft* \
Obiekt, na którym jest wywoływana funkcja członkowska *_Pm* .

*prawa* \
Argument, który jest przyznawany *_Pm*.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalna funkcja binarna.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *_Pm*, która musi być wskaźnikiem do funkcji składowej klasy `Type`, w prywatnym obiekcie członkowskim. Definiuje jej funkcję członkowską `operator()` jako zwracającą ( **_Pleft** -> \* `_Pm`) (**prawo**).

## <a name="example"></a>Przykład

Konstruktor `mem_fun1_t` nie jest zazwyczaj używany bezpośrednio; funkcja pomocnika `mem_fun` jest używana do adaptacji funkcji Członkowskich. Zobacz [mem_fun](../standard-library/functional-functions.md#mem_fun) , aby zapoznać się z przykładem użycia adapterów funkcji składowych.
