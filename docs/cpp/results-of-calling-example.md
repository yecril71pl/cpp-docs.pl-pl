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
ms.openlocfilehash: dcd1f9002362b7726883c6ce4f74fda9ab593544
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175421"
---
# <a name="results-of-calling-example"></a>Wyniki przykładu wywołania

**Microsoft Specific**

## <a name="cdecl"></a>__cdecl

Nazwy ozdobione funkcji języka C jest `_MyFunc`.

![Konwencja wywoływania CDECL](../cpp/media/vc37i01.gif "CDECL konwencji wywoływania") <br/>
**__Cdecl** konwencji wywoływania

## <a name="stdcall-and-thiscall"></a>__stdcall i thiscall

Nazwy ozdobionej C (**__stdcall**) jest `_MyFunc@20`. Nazwy ozdobionej C++ jest specyficzne dla implementacji.

![&#95;&#95;STDCALL i Konwencje wywoływania thiscall](../cpp/media/vc37i02.gif "&#95;&#95;stdcall i Konwencje wywoływania thiscall") <br/>
__Stdcall i thiscall Konwencje wywoływania

## <a name="fastcall"></a>__fastcall

Nazwy ozdobionej C (**__fastcall**) jest `@MyFunc@20`. Nazwy ozdobionej C++ jest specyficzne dla implementacji.

![Konwencja wywoływania &#95; &#95;fastcall](../cpp/media/vc37i03.gif "konwencji wywoływania &#95; &#95;fastcall") <br/>
Konwencja wywoływania __fastcall

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Przykład wywołania: prototyp funkcji i wywołanie](../cpp/calling-example-function-prototype-and-call.md)