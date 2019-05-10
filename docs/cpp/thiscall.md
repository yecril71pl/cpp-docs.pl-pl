---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: e51879ae62b2881e0adadbe59859605f6cc58947
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221911"
---
# <a name="thiscall"></a>__thiscall

**Microsoft Specific**

**__Thiscall** konwencji wywoływania jest używany dla funkcji składowych i jest domyślnie używany Konwencja wywoływania C++ funkcji elementów członkowskich, które nie korzystają z zmiennych argumentów. W obszarze **__thiscall**, wywoływany obiekt czyści stos, który nie ma możliwości `vararg` funkcji. Argumenty są wypychane na stosie od prawej do lewej, za pomocą **to** wskaźnik przekazywany za pośrednictwem rejestru ECX, a nie na stosie, na x86 architektury.

Jednym z powodów używania **__thiscall** znajduje się w klasach funkcje Członkowskie, których korzystają `__clrcall` domyślnie. W takim przypadku można użyć **__thiscall** się poszczególnym członkom funkcji można wywołać za pomocą kodu natywnego.

Podczas kompilowania za pomocą [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), wszystkie funkcje i wskaźników do funkcji są `__clrcall` chyba że określono inaczej. **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

W wersjach przed Visual Studio 2005 **__thiscall** konwencji wywoływania nie można jawnie określić w programie, ponieważ **__thiscall** nie jest słowem kluczowym.

`vararg` Funkcje Członkowskie korzystają **__cdecl** konwencji wywoływania. Wszystkie argumenty funkcji są wypychane na stos, za pomocą **to** umieszczenie w stosie ostatniego wskaźnika

Ta konwencja wywołania ma zastosowanie wyłącznie do języka C++, nie istnieje żaden schemat dekorowania nazw języka C.

Na ARM i x64 maszyn, **__thiscall** jest akceptowane i ignorowane przez kompilator.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)