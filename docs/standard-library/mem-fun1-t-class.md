---
title: mem_fun1_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 42a6ee7c169d078e216b82365ab26d10838798c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412868"
---
# <a name="memfun1t-class"></a>mem_fun1_t — Klasa

Klasa adaptera, który umożliwia `non_const` funkcja elementu członkowskiego, który przyjmuje jeden argument do wywoływania jako obiektu binarnego funkcja podczas inicjowania przy użyciu argumentu będącego wskaźnikiem. Przestarzałe w C ++ 11, usunięte w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;

};
```

### <a name="parameters"></a>Parametry

*_Pm*<br/>
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

*_Pleft*<br/>
Obiekt, *_Pm* wywoływana jest funkcja elementu członkowskiego.

*right*<br/>
Argument, który jest umożliwiającej *_Pm*.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalne funkcja binarnego.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię *_Pm*, który musi być wskaźnikiem do funkcji składowej klasy `Type`, w obiekcie prywatnego elementu członkowskiego. Definiuje jej funkcji członkowskiej `operator()` powrotu ( **_Pleft** -> \* `_Pm`) ( **prawo**).

## <a name="example"></a>Przykład

Konstruktor obiektu `mem_fun1_t` nie jest zazwyczaj używana bezpośrednio; funkcja Pomocnika `mem_fun` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun —](../standard-library/functional-functions.md#mem_fun) przykład sposobu użycia adapterów funkcja elementu członkowskiego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
