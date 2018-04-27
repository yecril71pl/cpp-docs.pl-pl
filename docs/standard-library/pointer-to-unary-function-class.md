---
title: pointer_to_unary_function — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xfunctional/std::pointer_to_unary
dev_langs:
- C++
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5cbcad162304a4eb7750c543deac5c8e00127b2a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function — Klasa

Konwertuje wskaźnik funkcji jednoargumentowy funkcja dostosowywalne jednoargumentowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
public:
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Parametry

`pfunc` Funkcja binarnej ma zostać przekonwertowany.

`left` Obiekt który  *\*pfunc* jest wywoływana na.

## <a name="return-value"></a>Wartość zwracana

Klasy szablonów przechowuje kopię **pfunc**. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie (\* **pfunc**) (_ *lewej*).

## <a name="remarks"></a>Uwagi

Jednoargumentowy wskaźnika funkcji jest obiektem funkcji i mogą być przekazywane do dowolnego algorytmu standardowa biblioteka C++, która oczekuje funkcji jednoargumentowy jako parametr, ale nie jest to dostosowywalne. Aby używać go z karty, takie jak powiązania wartości do niego lub użyciu negator, musi być zasilane zagnieżdżone typy **argument_type** i **result_type** który umożliwiają takie dostosowanie. Konwersja poprzez `pointer_to_unary_function` umożliwia adapterów funkcja do wykonania wskaźniki funkcji binarnego.

## <a name="example"></a>Przykład

Konstruktor obiektu `pointer_to_unary_function` jest rzadko używana bezpośrednio. Zobacz opis funkcji pomocnika [ptr_fun —](../standard-library/functional-functions.md#ptr_fun) przykład sposobu deklarowanie i użycie `pointer_to_unary_function` predykatu karty.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
