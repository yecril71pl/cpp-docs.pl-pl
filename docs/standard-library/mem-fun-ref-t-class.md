---
title: mem_fun_ref_t — Klasa
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::mem_fun_ref_t
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
ms.openlocfilehash: 752b3aeb4126ba41b7a0741ed9de68db018dd6c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488039"
---
# <a name="memfunreft-class"></a>mem_fun_ref_t — Klasa

Klasa adaptera, który umożliwia `non_const` funkcja elementu członkowskiego, która nie przyjmuje żadnych argumentów, które ma być wywoływana jako obiekt funkcji jednoargumentowe po zainicjowaniu z argumentem odwołania.

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

*_Pm*<br/>
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

*left*<br/>
Obiekt, *_Pm* wywoływana jest funkcja elementu członkowskiego.

## <a name="return-value"></a>Wartość zwracana

Funkcję jednoargumentową dostosowywalne.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię *_Pm*, który musi być wskaźnikiem do funkcji składowej klasy `Type`, w obiekcie prywatnego elementu członkowskiego. Definiuje jej funkcji członkowskiej `operator()` powrotu ( **po lewej stronie**. * `_Pm`) ().

## <a name="example"></a>Przykład

Konstruktor obiektu `mem_fun_ref_t` nie jest zazwyczaj używana bezpośrednio; funkcja Pomocnika `mem_fun_ref` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun_ref —](../standard-library/functional-functions.md#mem_fun_ref) przykład sposobu użycia adapterów funkcja elementu członkowskiego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
