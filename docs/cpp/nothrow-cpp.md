---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 8164f47190267627bdaf7c7ee2f03f22f65c8f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161064"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Specyficzne dla firmy Microsoft**

**__Declspec** rozszerzony atrybut, który może być używany w deklaracji funkcji.

## <a name="syntax"></a>Składnia

> *Typ zwracany* __declspec (nothrow) [*call-Convention*] *nazwa funkcji* ([*Lista argumentów*])

## <a name="remarks"></a>Uwagi

Zalecamy, aby cały nowy kod używał operatora [noexcept](noexcept-cpp.md) zamiast `__declspec(nothrow)`.

Ten atrybut informuje kompilator, że funkcja zadeklarowana i funkcje, które wywołuje, nigdy nie zgłasza wyjątku. Jednak nie wymusza zastosowania dyrektywy. Innymi słowy nigdy nie powoduje wywołania [std:: terminate](../standard-library/exception-functions.md#terminate) , w przeciwieństwie do `noexcept`lub w trybie **std: C++ 17** (Visual Studio 2017 wersja 15,5 i nowsze), `throw()`.

W modelu obsługi wyjątków synchronicznych, teraz, kompilator może wyeliminować Mechanics, aby śledzić okres istnienia niektórych niezawijanych obiektów w tej funkcji, i znacząco zmniejszyć rozmiar kodu. Zgodnie z poniższą dyrektywą preprocesora, trzy deklaracje funkcji są równoważne w trybie **/std: c++ 14** :

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

W **/std: tryb c++ 17** , `throw()` nie jest odpowiednikiem innych, które używają `__declspec(nothrow)` ponieważ powoduje wywoływanie `std::terminate`, jeśli wyjątek jest zgłaszany przez funkcję.

Deklaracja `void __stdcall f3() throw();` używa składni zdefiniowanej przez C++ Standard. W języku C++ 17 słowo kluczowe `throw()` było przestarzałe.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
