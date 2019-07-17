---
title: pointer_to_binary_function — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: fcc643d7569bd4f71b11249babdb49ef1362dc8b
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240492"
---
# <a name="pointertobinaryfunction-class"></a>pointer_to_binary_function — Klasa

Konwertuje wskaźnika funkcji binarne potężnej funkcja binarnego. Przestarzałe w C ++ 11, usunięte w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>Parametry

*pfunc*\
Binarny funkcja, która ma zostać przekonwertowany.

*po lewej stronie*\
Po lewej stronie obiektu, który  *\*pfunc* jest wywoływana w.

*po prawej stronie*\
Po prawej stronie obiektu, który  *\*pfunc* jest wywoływana w.

## <a name="return-value"></a>Wartość zwracana

Klasa szablonu przechowuje kopię `pfunc`. Definiuje jej funkcji członkowskiej `operator()` powrotu `(* pfunc)(Left, right)`.

## <a name="remarks"></a>Uwagi

Wskaźnik binarny funkcji jest obiektem funkcji i może być przekazywany do dowolnego algorytmu biblioteki standardowej języka C++, który oczekuje binarnego funkcja jako parametr, ale nie jest dostosowana. Do korzystania z adaptera, takich jak powiązania wartości do niego lub użyciu negator, należy podać przy użyciu typów zagnieżdżonych `first_argument_type`, `second_argument_type`, i `result_type` , umożliwiają dostosowanie takie. Konwersja przez `pointer_to_binary_function` umożliwia adapterów funkcji do pracy z wskaźników funkcji binarnego.

## <a name="example"></a>Przykład

Konstruktor obiektu `pointer_to_binary_function` jest rzadko używana bezpośrednio. Zobacz opis funkcji pomocnika [ptr_fun —](../standard-library/functional-functions.md#ptr_fun) przykładowy sposób deklarowania i użyj `pointer_to_binary_function` predykatu adaptera.
