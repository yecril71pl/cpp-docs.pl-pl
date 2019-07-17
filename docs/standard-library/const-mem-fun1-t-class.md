---
title: const_mem_fun1_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 8ccd9d7e58b9cadec83b64df5553564db20a5745
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244527"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t — Klasa

Klasa adaptera, który umożliwia **const** funkcja elementu członkowskiego, który przyjmuje jeden argument do wywoływania jako obiektu binarnego funkcja podczas inicjowania przy użyciu argumentu będącego wskaźnikiem. Przestarzałe w C ++ 11, usunięte w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* member_ptr)(Arg) const);
    Result operator()(const Type* left, Arg right) const;
};
```

### <a name="parameters"></a>Parametry

*member_ptr*\
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

*po lewej stronie*\
**Const** obiekt *member_ptr* wywoływana jest funkcja elementu członkowskiego.

*po prawej stronie*\
Argument, który jest umożliwiającej *member_ptr*.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalne funkcja binarnego.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię *member_ptr*, który musi być wskaźnikiem do funkcji składowej klasy `Type`, w obiekcie prywatnego elementu członkowskiego. Definiuje jej funkcji członkowskiej `operator()` powrotu `(left->member_ptr)(right) const`.

## <a name="example"></a>Przykład

Konstruktor obiektu `const_mem_fun1_t` jest rzadko używana bezpośrednio. `mem_fn` Umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fn —](../standard-library/functional-functions.md#mem_fn) przykład sposobu użycia adapterów funkcja elementu członkowskiego.
