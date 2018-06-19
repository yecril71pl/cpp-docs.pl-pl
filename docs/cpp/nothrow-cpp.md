---
title: nothrow (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/03/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nothrow_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69a706577cf112c3d8a3b7748f72679f7213936d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420660"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Microsoft Specific**

A `__declspec` rozszerzonych atrybutów, które mogą być używane w deklaracji funkcji.

## <a name="syntax"></a>Składnia  
  
> *zwracanego typu* __declspec(nothrow) [*konwencji wywołania*] *nazwy funkcji* ([*listy argumentów*])

## <a name="remarks"></a>Uwagi

Zalecane jest użycie wszystkich nowy kod [noexcept](noexcept-cpp.md) operator zamiast `__declspec(nothrow)`.

Ten atrybut informuje kompilator, że zadeklarowanej funkcji i funkcji wywoływanych przez nią nigdy nie zgłoszenia wyjątku. Jednak nie wymusza dyrektywy. Innymi słowy, nigdy nie powoduje [std::terminate](../standard-library/exception-functions.md#terminate) do wywołania, w odróżnieniu od `noexcept`, lub w **std:c ++ 17** trybu (Visual Studio 2017 wersji 15.5 i nowszych), `throw()`.

Z wyjątkiem synchroniczne obsługi modelu, a teraz domyślne, kompilator można wyeliminować mechanika śledzenia okres istnienia niektórych obiektów unwindable w tych funkcji i znacznie zmniejszyć rozmiar kodu. Biorąc pod uwagę następujące dyrektywy preprocesora, deklaracje funkcji trzy poniżej są równoważne w **/std:c ++ 14** tryb:

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

W **/std:c ++ 17** trybie `throw()` nie jest odpowiednikiem korzystających z innych `__declspec(nothrow)` ponieważ powoduje ona `std::terminate` do wywołania, jeśli funkcja jest zgłaszany wyjątek.

`void __stdcall f3() throw();` Deklaracji używa składni zdefiniowanych przez C++ standard. W języku C ++ 17 `throw()` — słowo kluczowe została uznana za przestarzałą.

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)  
[noexcept](noexcept-cpp.md)  
[Słowa kluczowe](../cpp/keywords-cpp.md)  
