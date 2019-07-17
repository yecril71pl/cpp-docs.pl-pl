---
title: pointer_to_unary_function — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: cff84f1f15eea34c60162f702dfe05350d1383d1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240469"
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function — Klasa

Konwertuje funkcję jednoargumentową potężnej jednoargumentowe wskaźnika funkcji. Przestarzałe w C ++ 11, usunięte w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Parametry

*pfunc*\
Binarny funkcja, która ma zostać przekonwertowany.

*po lewej stronie*\
Obiekt,  *\*pfunc* jest wywoływana w.

## <a name="return-value"></a>Wartość zwracana

Klasa szablonu przechowuje kopię `pfunc`. Definiuje jej funkcji członkowskiej `operator()` powrotu (\* **pfunc**) (_ *po lewej stronie*).

## <a name="remarks"></a>Uwagi

Jednoargumentowy wskaźnika funkcji jest obiektem funkcji i może być przekazywany do dowolnego algorytmu biblioteki standardowej języka C++, który oczekuje funkcję jednoargumentową jako parametru, ale nie jest dostosowana. Do korzystania z adaptera, takich jak powiązania wartości do niego lub użyciu negator, należy podać przy użyciu typów zagnieżdżonych `argument_type` i `result_type` , umożliwiają dostosowanie takie. Konwersja przez `pointer_to_unary_function` umożliwia adapterów funkcji do pracy z wskaźników funkcji binarnego.

## <a name="example"></a>Przykład

Konstruktor obiektu `pointer_to_unary_function` jest rzadko używana bezpośrednio. Zobacz opis funkcji pomocnika [ptr_fun —](../standard-library/functional-functions.md#ptr_fun) przykładowy sposób deklarowania i użyj `pointer_to_unary_function` predykatu adaptera.
