---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: 8772159dca71bb7605af5e5919425065423d503d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188158"
---
# <a name="__thiscall"></a>__thiscall

**Specyficzne dla firmy Microsoft**

Konwencja wywoływania **__thiscall** jest używana w funkcjach składowych i jest domyślną konwencją wywoływania używaną przez C++ funkcje członkowskie, które nie używają argumentów zmiennych. W obszarze **__thiscall**wywoływany czyści stos, co jest niemożliwe dla `vararg` funkcji. Argumenty są wypychane na stosie od prawej do lewej, z **tym** wskaźnikiem, który jest przesyłany za pośrednictwem rejestracji ECX, a nie na stosie, na architekturze x86.

Jedną z przyczyn użycia **__thiscall** jest Klasa, której funkcje członkowskie domyślnie używają `__clrcall`. W takim przypadku można użyć **__thiscall** , aby umożliwić każdemu elementowi członkowskiemu wywoływanie z kodu natywnego.

Podczas kompilowania z [/CLR: Pure](../build/reference/clr-common-language-runtime-compilation.md), wszystkie funkcje i wskaźniki funkcji są `__clrcall`, chyba że określono inaczej. **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

W wersjach przed programem Visual Studio 2005 nie można jawnie określić konwencji wywoływania **__thiscall** w programie, ponieważ **__thiscall** nie jest słowem kluczowym.

`vararg` funkcje członkowskie używają konwencji wywoływania **__cdecl** . Wszystkie argumenty funkcji są wypychane na stosie, z **tym** wskaźnikiem umieszczonym na stosie.

Ponieważ ta konwencja wywoływania ma zastosowanie tylko C++do, nie istnieje schemat dekoracji nazwy języka C.

Na komputerach z architekturą ARM i x64 **__thiscall** jest akceptowana i ignorowana przez kompilator.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)
