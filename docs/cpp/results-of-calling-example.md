---
title: Wyniki przykładu wywołania
ms.date: 09/05/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: 96582e48912bb591d869bbc4df179299e6459f1e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500944"
---
# <a name="results-of-calling-example"></a>Wyniki przykładu wywołania

**Microsoft Specific**

## <a name="cdecl"></a>__cdecl

Nazwy ozdobione funkcji języka C jest `_MyFunc`.

![Konwencja wywoływania CDECL](../cpp/media/vc37i01.gif "vc37I01") **__cdecl** konwencji wywoływania

## <a name="stdcall-and-thiscall"></a>__stdcall i thiscall

Nazwy ozdobionej C (**__stdcall**) jest `_MyFunc@20`. Nazwy ozdobionej C++ jest specyficzne dla implementacji.

![&#95;&#95;STDCALL i Konwencje wywoływania thiscall](../cpp/media/vc37i02.gif "vc37I02") __stdcall i thiscall Konwencje wywoływania

## <a name="fastcall"></a>__fastcall

Nazwy ozdobionej C (**__fastcall**) jest `@MyFunc@20`. Nazwy ozdobionej C++ jest specyficzne dla implementacji.

![Konwencja wywoływania &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03") Konwencję wywoływania __fastcall

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Przykład wywołania: prototyp funkcji i wywołanie](../cpp/calling-example-function-prototype-and-call.md)