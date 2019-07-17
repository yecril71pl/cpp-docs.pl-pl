---
title: const_mem_fun1_ref_t — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 59790b5791dc50d217053dc7a13856d436101020
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244539"
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t — Klasa

Klasa adaptera, który umożliwia **const** funkcja elementu członkowskiego, który przyjmuje jeden argument do wywoływania jako obiektu binarnego funkcja podczas inicjowania przy użyciu argument odwołania. Przestarzałe w C ++ 11, usunięte w języku C ++ 17.

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

*PM*\
Wskaźnik do funkcji składowej klasy typu `Type` do konwersji na obiekt funkcyjny.

*po lewej stronie*\
**Const** obiekt *Pm* wywoływana jest funkcja elementu członkowskiego.

*po prawej stronie*\
Argument, który jest umożliwiającej *Pm*.

## <a name="return-value"></a>Wartość zwracana

Dostosowywalne funkcja binarnego.

## <a name="remarks"></a>Uwagi

Klasa szablonu przechowuje kopię *Pm*, który musi być wskaźnikiem do funkcji składowej klasy `Type`, w obiekcie prywatnego elementu członkowskiego. Definiuje jej funkcji członkowskiej `operator()` powrotu (`left`.\* *PM*) (`right`) **const**.

## <a name="example"></a>Przykład

Konstruktor obiektu `const_mem_fun1_ref_t` nie jest zazwyczaj używana bezpośrednio; funkcja Pomocnika `mem_fun_ref` umożliwia dostosowanie funkcji elementów członkowskich. Zobacz [mem_fun_ref —](../standard-library/functional-functions.md#mem_fun_ref) przykłady sposobów użycia adapterów funkcja elementu członkowskiego.
