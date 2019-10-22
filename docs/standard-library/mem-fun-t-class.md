---
title: mem_fun_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: 3c6606fe4d2df3b6068c3bb8194dc380344f7d97
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689381"
---
# <a name="mem_fun_t-class"></a>mem_fun_t — Klasa

Klasa adaptera, która umożliwia `non_const` funkcji członkowskiej, która nie przyjmuje argumentów do wywołania jednoargumentowego obiektu funkcyjnego, gdy zostanie zainicjowany przy użyciu argumentu wskaźnika. Przestarzałe w języku C++ 11, usunięte w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm* \
Wskaźnik do funkcji członkowskiej klasy `Type` do przekonwertowania na obiekt funkcji.

*_Pleft* \
Obiekt, na którym jest wywoływana funkcja członkowska *_Pm* .

## <a name="return-value"></a>Wartość zwracana

Dostosowywalna funkcja Jednoargumentowa.

## <a name="remarks"></a>Uwagi

Szablon klasy przechowuje kopię *_Pm*, która musi być wskaźnikiem do funkcji składowej klasy `Type`, w prywatnym obiekcie członkowskim. Definiuje jej funkcję członkowską `operator()` jako zwracającą (`_Pleft` ->*  `_Pm`) ().

## <a name="example"></a>Przykład

Konstruktor `mem_fun_t` nie jest zazwyczaj używany bezpośrednio; funkcja pomocnika `mem_fun` jest używana do adaptacji funkcji Członkowskich. Zobacz [mem_fun](../standard-library/functional-functions.md#mem_fun) , aby zapoznać się z przykładem użycia adapterów funkcji składowych.
