---
title: const_mem_fun1_t — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81ee887e048e774cd8aafcfd59fe5d27338e2837
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t — Klasa

Klasa karty, który umożliwia **const** funkcji członkowskiej, która pobiera jeden argument ma być wywoływana jako obiektu binarnego funkcja po zainicjowaniu z argumentem wskaźnika.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t
 : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* _Pm)(Arg) const);
    Result operator()(const Type* _Pleft, Arg right) const;
 };
```

### <a name="parameters"></a>Parametry

`_Pm` Wskaźnik do funkcji członkowskiej klasy **typu** do przekonwertowania na obiekt funkcji.

`_Pleft` **Const** obiekt, który `_Pm` funkcja członkowska jest wywoływana na.

`right` Argument, który są przyznawane `_Pm`.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalne funkcja binarnej.

## <a name="remarks"></a>Uwagi

Klasy szablonów przechowuje kopię `_Pm`, która musi być wskaźnikiem do funkcji członkowskiej klasy **typu**, w obiekcie prywatnego elementu członkowskiego. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie ( **_Pleft** -> \* * Pm) (***prawej**) **const**.

## <a name="example"></a>Przykład

Konstruktor obiektu `const_mem_fun1_t` nie jest zwykle używana bezpośrednio; funkcja Pomocnika `mem_fun` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun —](../standard-library/functional-functions.md#mem_fun) przykład sposobu użycia karty funkcja elementu członkowskiego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
