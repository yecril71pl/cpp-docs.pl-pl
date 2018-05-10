---
title: const_mem_fun1_ref_t — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun1_ref_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c465ce95ecbf2ecb50e79e6e4cbaafce8cf7a407
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t — Klasa

Klasa karty, który umożliwia **const** funkcji członkowskiej, która pobiera jeden argument ma być wywoływana jako obiektu binarnego funkcja po zainicjowaniu z argumentem odwołania.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_ref_t
 : public binary_function<Type, Arg, Result>
 {
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
 };
```

### <a name="parameters"></a>Parametry

`Pm` Wskaźnik do funkcji członkowskiej klasy **typu** do przekonwertowania na obiekt funkcji.

`left` **Const** obiekt, który `Pm` funkcja członkowska jest wywoływana na.

`right` Argument, który są przyznawane `Pm`.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalne funkcja binarnej.

## <a name="remarks"></a>Uwagi

Klasy szablonów przechowuje kopię `Pm`, która musi być wskaźnikiem do funkcji członkowskiej klasy **typu**, w obiekcie prywatnego elementu członkowskiego. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie ( `left`.\* *PM*) ( `right`) **const**.

## <a name="example"></a>Przykład

Konstruktor obiektu `const_mem_fun1_ref_t` nie jest zwykle używana bezpośrednio; funkcja Pomocnika `mem_fun_ref` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun_ref —](../standard-library/functional-functions.md#mem_fun_ref) przykłady dotyczące używania karty funkcja elementu członkowskiego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
