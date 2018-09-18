---
title: __thiscall | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __thiscall
- __thiscall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af20b6d406b0e2119df04d5348c554b3405e8597
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103376"
---
# <a name="thiscall"></a>__thiscall

**Microsoft Specific**

**__Thiscall** konwencja wywołania jest używany dla funkcji składowych i to domyślna konwencja wywołania posługują się funkcji składowych języka C++, które nie korzystają z zmiennych argumentów. W obszarze **__thiscall**, wywoływany obiekt czyści stos, który nie ma możliwości `vararg` funkcji. Argumenty są wypychane na stosie od prawej do lewej, za pomocą **to** wskaźnik przekazywany za pośrednictwem rejestru ECX, a nie na stosie, na x86 architektury.

Jednym z powodów używania **__thiscall** znajduje się w klasach funkcje Członkowskie, których korzystają `__clrcall` domyślnie. W takim przypadku można użyć **__thiscall** się poszczególnym członkom funkcji można wywołać za pomocą kodu natywnego.

Podczas kompilowania za pomocą [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), wszystkie funkcje i wskaźników do funkcji są `__clrcall` chyba że określono inaczej. **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

W wersjach przed Visual C++ 2005 **__thiscall** konwencji wywoływania nie można jawnie określić w programie, ponieważ **__thiscall** nie jest słowem kluczowym.

`vararg` Funkcje Członkowskie korzystają **__cdecl** konwencji wywoływania. Wszystkie argumenty funkcji są wypychane na stos, za pomocą **to** umieszczenie w stosie ostatniego wskaźnika

Ta konwencja wywołania ma zastosowanie wyłącznie do języka C++, nie istnieje żaden schemat dekorowania nazw języka C.

Na ARM i x64 maszyn, **__thiscall** jest akceptowane i ignorowane przez kompilator.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)