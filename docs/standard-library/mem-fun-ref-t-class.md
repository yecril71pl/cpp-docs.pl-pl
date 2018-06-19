---
title: mem_fun_ref_t — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::mem_fun_ref_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 029fba9cc5a13569df8cc1e2e11b639e65ea24c9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863907"
---
# <a name="memfunreft-class"></a>mem_fun_ref_t — Klasa

Klasa karty, który umożliwia **non_const** funkcji członkowskiej, która nie przyjmuje żadnych argumentów do wywołania jako obiekt funkcja jednoargumentowy po zainicjowaniu z argumentem odwołania.

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

`_Pm` Wskaźnik do funkcji członkowskiej klasy **typu** do przekonwertowania na obiekt funkcji.

`left` Obiekt który `_Pm` funkcja członkowska jest wywoływana na.

## <a name="return-value"></a>Wartość zwracana

Funkcja dostosowywalne jednoargumentowy.

## <a name="remarks"></a>Uwagi

Klasy szablonów przechowuje kopię `_Pm`, która musi być wskaźnikiem do funkcji członkowskiej klasy **typu**, w obiekcie prywatnego elementu członkowskiego. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie ( **po lewej stronie**. * `_Pm`) ().

## <a name="example"></a>Przykład

Konstruktor obiektu `mem_fun_ref_t` nie jest zwykle używana bezpośrednio; funkcja Pomocnika `mem_fun_ref` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun_ref —](../standard-library/functional-functions.md#mem_fun_ref) przykład sposobu użycia karty funkcja elementu członkowskiego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
