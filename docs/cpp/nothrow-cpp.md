---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 88041b374cc48ac31c8990aa7f867ba25b33e1d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548138"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Microsoft Specific**

A **__declspec** atrybutów rozszerzonych, które mogą być używane w deklaracji funkcji.

## <a name="syntax"></a>Składnia

> *zwracany typ* __declspec(nothrow) [*konwencji wywołania*] *nazwy funkcji* ([*listy argumentów*])

## <a name="remarks"></a>Uwagi

Zalecane jest użycie wszystkich nowy kod [noexcept](noexcept-cpp.md) operator zamiast `__declspec(nothrow)`.

Ten atrybut informuje kompilator, że funkcja zadeklarowana i funkcji wywoływanych przez nią nigdy nie zgłasza wyjątku. Dyrektywa nie są jednak wymusić. Innymi słowy, nigdy nie powoduje [std::terminate](../standard-library/exception-functions.md#terminate) do wywołania, w odróżnieniu od `noexcept`, lub **STD: c ++ 17** trybu (Visual Studio 2017 w wersji 15.5 lub nowszej), `throw()`.

Z wyjątkiem synchroniczne obsługi modelu, a teraz domyślne, kompilator może wyeliminować mechanika śledzenia okresu istnienia niektórych odwracalnych obiektów w takich funkcji, a znacznie zmniejszyć rozmiar kodu. Biorąc pod uwagę następujące dyrektywy preprocesora, deklaracje funkcji trzy poniższe są równoważne w **/STD: c ++ 14** trybu:

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

W **/STD: c ++ 17** trybie `throw()` nie jest odpowiednikiem osobom, które używają `__declspec(nothrow)` ponieważ powoduje ona `std::terminate` do wywołania, jeśli wyjątek jest generowany przez funkcję.

`void __stdcall f3() throw();` Deklaracji używa składni zdefiniowanej przez C++ standard. W języku C ++ 17 `throw()` — słowo kluczowe została zakończona.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)