---
title: mem_fun1_ref_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: d4f0f2064ac6771e2c351b70097137fed12c8262
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006698"
---
# <a name="memfun1reft-class"></a>mem_fun1_ref_t — Klasa

Klasa adaptera, który umożliwia `non_const` funkcja elementu członkowskiego, który przyjmuje jeden argument do wywoływania jako obiektu binarnego funkcja podczas inicjowania przy użyciu argument odwołania. Przestarzałe w C ++ 11, usunięte w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_ref_t : public binary_function<Type, Arg, Result> {
    explicit mem_fun1_ref_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type& left,
    Arg right) const;

};
```

### <a name="parameters"></a>Parametry

*_Pm*<br/>
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

*left*<br/>
Obiekt, *_Pm* wywoływana jest funkcja elementu członkowskiego.

*right*<br/>
Argument, który jest umożliwiającej *_Pm*.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalne funkcja binarnego.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię *_Pm*, który musi być wskaźnikiem do funkcji składowej klasy `Type`, w obiekcie prywatnego elementu członkowskiego. Definiuje jej funkcji członkowskiej `operator()` powrotu ( **po lewej stronie**.\* `_Pm`) ( **prawo**).

## <a name="example"></a>Przykład

Konstruktor obiektu `mem_fun1_ref_t` nie jest zazwyczaj używana bezpośrednio; funkcja Pomocnika `mem_fun_ref` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun_ref —](../standard-library/functional-functions.md#mem_fun_ref) przykład sposobu użycia adapterów funkcja elementu członkowskiego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
