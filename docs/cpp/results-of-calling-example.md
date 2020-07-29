---
title: Wyniki przykładu wywołania
ms.date: 11/19/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: 1bf5fe62b8ef2b7a37bf72b7a40e5d47af3f3961
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225881"
---
# <a name="results-of-calling-example"></a>Wyniki przykładu wywołania

**Specyficzne dla firmy Microsoft**

## <a name="__cdecl"></a>__cdecl

Nazwa funkcji dekoracyjnej języka C to `_MyFunc` .

![Konwencja wywoływania CDECL](../cpp/media/vc37i01.gif "Konwencja wywoływania CDECL") <br/>
**`__cdecl`** Konwencja wywoływania

## <a name="__stdcall-and-thiscall"></a>__stdcall i thiscall

Nazwa dekoracyjna C ( **`__stdcall`** ) jest `_MyFunc@20` . Nazwa dekoracyjna języka C++ jest specyficzna dla implementacji.

![&#95;&#95;konwencje wywoływania StdCall i thiscall](../cpp/media/vc37i02.gif "&#95;&#95;konwencje wywoływania StdCall i thiscall") <br/>
Konwencje wywoływania __stdcall i thiscall

## <a name="__fastcall"></a>__fastcall

Nazwa dekoracyjna C ( **`__fastcall`** ) jest `@MyFunc@20` . Nazwa dekoracyjna języka C++ jest specyficzna dla implementacji.

![Konwencja wywoływania dla &#95;&#95;fastcall](../cpp/media/vc37i03.gif "Konwencja wywoływania dla &#95;&#95;fastcall") <br/>
Konwencja wywoływania __fastcall

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Przykład wywołania: prototyp funkcji i wywołanie](../cpp/calling-example-function-prototype-and-call.md)
