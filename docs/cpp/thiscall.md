---
title: Konwencja __thiscall | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4912628529ae0b47a5a5b938ab8e6d25a9099510
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704406"
---
# <a name="thiscall"></a>__thiscall

**Microsoft Specific**

`__thiscall` Konwencji wywoływania jest używana dla funkcji Członkowskich i konwencji wywoływania domyślne używane przez funkcji Członkowskich C++, które nie korzystają z argumentami zmiennych. W obszarze `__thiscall`, wywoływany czyści stosu, w którym nie ma możliwości `vararg` funkcji. Argumenty są przenoszone na stosie od prawej do lewej, z `this` wskaźnika przekazywany za pomocą rejestru ECX, a nie na stosie na x86 architektury.

Jedną z przyczyn do użycia `__thiscall` jest klas, w których element członkowski funkcji Użyj `__clrcall` domyślnie. W takim przypadku można użyć `__thiscall` dokonanie poszczególnych elementów członkowskich funkcji z kodu macierzystego.

Podczas kompilowania za pomocą [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), są wszystkie funkcje i wskaźniki funkcji `__clrcall` chyba że określono inaczej. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

W wersjach przed Visual C++ 2005 `__thiscall` konwencji wywoływania może nie być jawnie określona w programie, ponieważ `__thiscall` nie jest słowem kluczowym.

`vararg` Funkcje Członkowskie użyj `__cdecl` konwencji wywoływania. Wszystkie argumenty funkcji są przenoszone na stosie, z `this` wskaźnika ostatnio umieszczane na stosie

Konwencja wywoływania dotyczy tylko C++, nie istnieje żaden schemat decoration nazwa C.

Na ARM i x64 maszyny, `__thiscall` i akceptowany jest ignorowana przez kompilator.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji.

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

- [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)
