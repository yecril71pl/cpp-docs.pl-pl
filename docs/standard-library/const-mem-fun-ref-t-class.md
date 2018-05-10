---
title: const_mem_fun_ref_t — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun_ref_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29c86f71912c5fe4cf3f5d2fc0df37c8530a8517
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="constmemfunreft-class"></a>const_mem_fun_ref_t — Klasa

Klasa karty, który umożliwia **const** funkcji członkowskiej, która nie przyjmuje żadnych argumentów do wywołania jako obiekt funkcja jednoargumentowy po zainicjowaniu z argumentem odwołania.

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

`Pm` Wskaźnik do funkcji członkowskiej klasy **typu** do przekonwertowania na obiekt funkcji.

`left` Obiekt który `Pm` funkcja członkowska jest wywoływana na.

## <a name="return-value"></a>Wartość zwracana

Funkcja dostosowywalne jednoargumentowy.

## <a name="remarks"></a>Uwagi

Klasy szablonów przechowuje kopię `Pm`, która musi być wskaźnikiem do funkcji członkowskiej klasy **typu**, w obiekcie prywatnego elementu członkowskiego. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie ( **po lewej stronie**.\* `Pm`) () **const**.

## <a name="example"></a>Przykład

Konstruktor obiektu `const_mem_fun_ref_t` nie jest zwykle używana bezpośrednio; funkcja Pomocnika `mem_fun_ref` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun_ref —](../standard-library/functional-functions.md#mem_fun_ref) przykład sposobu użycia karty funkcja elementu członkowskiego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
