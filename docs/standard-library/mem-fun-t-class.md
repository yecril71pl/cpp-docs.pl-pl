---
title: mem_fun_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: 19ccd4835c4257a7f409bcf0f7bda1a898567458
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245083"
---
# <a name="memfunt-class"></a>mem_fun_t — Klasa

Klasa adaptera, który umożliwia `non_const` funkcja elementu członkowskiego, która nie przyjmuje żadnych argumentów, które ma być wywoływana jako obiektu funkcyjnego jednoargumentowe podczas inicjowania przy użyciu argumentu będącego wskaźnikiem. Przestarzałe w C ++ 11, usunięte w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;
};
```

### <a name="parameters"></a>Parametry

*_Pm*\
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

*_Pleft*\
Obiekt, *_Pm* wywoływana jest funkcja elementu członkowskiego.

## <a name="return-value"></a>Wartość zwracana

Funkcję jednoargumentową dostosowywalne.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię *_Pm*, który musi być wskaźnikiem do funkcji składowej klasy `Type`, w obiekcie prywatnego elementu członkowskiego. Definiuje jej funkcji członkowskiej `operator()` powrotu (`_Pleft`->* `_Pm`) ().

## <a name="example"></a>Przykład

Konstruktor obiektu `mem_fun_t` nie jest zazwyczaj używana bezpośrednio; funkcja Pomocnika `mem_fun` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun —](../standard-library/functional-functions.md#mem_fun) przykład sposobu użycia adapterów funkcja elementu członkowskiego.
