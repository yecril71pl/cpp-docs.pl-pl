---
title: pointer_to_binary_function — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::pointer_to_binary
dev_langs:
- C++
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b632fabe8f596d46a0423d670ff57bb12de93cd
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953459"
---
# <a name="pointertobinaryfunction-class"></a>pointer_to_binary_function — Klasa

Konwertuje wskaźnika funkcji binarne potężnej funkcja binarnego.

## <a name="syntax"></a>Składnia

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
public:
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>Parametry

*pfunc* binarnego funkcja ma zostać przekonwertowany.

*po lewej stronie* po lewej stronie obiektu, który  *\*pfunc* jest wywoływana w.

*prawy* po prawej stronie obiektu, który  *\*pfunc* jest wywoływana w.

## <a name="return-value"></a>Wartość zwracana

Klasa szablonu przechowuje kopię `pfunc`. Definiuje jej funkcji członkowskiej `operator()` powrotu (\* **pfunc**) (_ *po lewej stronie*, \_ *po prawej stronie*).

## <a name="remarks"></a>Uwagi

Wskaźnik binarny funkcji jest obiektem funkcji i może być przekazywany do dowolnego algorytmu biblioteki standardowej języka C++, który oczekuje binarnego funkcja jako parametr, ale nie jest dostosowana. Do korzystania z adaptera, takich jak powiązania wartości do niego lub użyciu negator, należy podać przy użyciu typów zagnieżdżonych `first_argument_type`, `second_argument_type`, i `result_type` , umożliwiają dostosowanie takie. Konwersja przez `pointer_to_binary_function` umożliwia adapterów funkcji do pracy z wskaźników funkcji binarnego.

## <a name="example"></a>Przykład

Konstruktor obiektu `pointer_to_binary_function` jest rzadko używana bezpośrednio. Zobacz opis funkcji pomocnika [ptr_fun —](../standard-library/functional-functions.md#ptr_fun) przykładowy sposób deklarowania i użyj `pointer_to_binary_function` predykatu adaptera.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
