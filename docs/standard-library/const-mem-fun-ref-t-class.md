---
title: const_mem_fun_ref_t — Klasa
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::const_mem_fun_ref_t
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
ms.openlocfilehash: 3f0a87b71f39847590c5fbc4e94038b216ec4b1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515521"
---
# <a name="constmemfunreft-class"></a>const_mem_fun_ref_t — Klasa

Klasa adaptera, który umożliwia **const** funkcja elementu członkowskiego, która nie przyjmuje żadnych argumentów, które ma być wywoływana jako obiekt funkcji jednoargumentowe po zainicjowaniu z argumentem odwołania.

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

*PM*<br/>
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

*left*<br/>
Obiekt, *Pm* wywoływana jest funkcja elementu członkowskiego.

## <a name="return-value"></a>Wartość zwracana

Funkcję jednoargumentową dostosowywalne.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię *Pm*, który musi być wskaźnikiem do funkcji składowej klasy `Type`, w obiekcie prywatnego elementu członkowskiego. Definiuje jej funkcji członkowskiej `operator()` powrotu ( **po lewej stronie**.\* `Pm`) () **const**.

## <a name="example"></a>Przykład

Konstruktor obiektu `const_mem_fun_ref_t` nie jest zazwyczaj używana bezpośrednio; funkcja Pomocnika `mem_fun_ref` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun_ref —](../standard-library/functional-functions.md#mem_fun_ref) przykład sposobu użycia adapterów funkcja elementu członkowskiego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
