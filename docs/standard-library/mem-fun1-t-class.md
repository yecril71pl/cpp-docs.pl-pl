---
title: mem_fun1_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 822de97849750a72948137ba8fe23beab8554ff5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245095"
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

*_Pm*\
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

*_Pleft*\
Obiekt, *_Pm* wywoływana jest funkcja elementu członkowskiego.

*po prawej stronie*\
Argument, który jest umożliwiającej *_Pm*.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalne funkcja binarnego.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię *_Pm*, który musi być wskaźnikiem do funkcji składowej klasy `Type`, w obiekcie prywatnego elementu członkowskiego. Definiuje jej funkcji członkowskiej `operator()` powrotu ( **_Pleft** -> \* `_Pm`) (**prawo**).

## <a name="example"></a>Przykład

Konstruktor obiektu `mem_fun1_t` nie jest zazwyczaj używana bezpośrednio; funkcja Pomocnika `mem_fun` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun —](../standard-library/functional-functions.md#mem_fun) przykład sposobu użycia adapterów funkcja elementu członkowskiego.
