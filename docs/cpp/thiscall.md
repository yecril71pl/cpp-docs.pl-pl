---
title: __thiscall
ms.date: 05/22/2020
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: b9edc2cd8caa5fd5458f6a53c5fdb1f8a5e69914
ms.sourcegitcommit: 5bb421fdf61d290cac93a03e16a6a80959accf6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83854817"
---
# `__thiscall`

Konwencja wywoływania **specyficzna dla firmy Microsoft** **`__thiscall`** jest używana w funkcjach składowych klasy języka C++ w architekturze x86. Jest to domyślna konwencja wywoływania używana przez funkcje członkowskie, które nie używają argumentów zmiennych ( `vararg` Functions).

W obszarze **`__thiscall`** , wywoływany czyści stos, co jest niemożliwe dla `vararg` funkcji. Argumenty są wypychane na stosie od prawej do lewej. **`this`** Wskaźnik jest przesyłany za pośrednictwem rejestracji ECX, a nie na stosie.

Na komputerach ARM, ARM64 i x64 **`__thiscall`** jest akceptowane i ignorowane przez kompilator. Wynika to z tego, że domyślnie używają konwencji wywoływania opartej na rejestrze.

Jedną z przyczyn użycia **`__thiscall`** jest Klasa, której funkcje członkowskie **`__clrcall`** domyślnie używają. W takim przypadku można użyć, **`__thiscall`** Aby udostępnić poszczególne funkcje członkowskie z kodu natywnego.

Podczas kompilowania przy użyciu [**`/clr:pure`**](../build/reference/clr-common-language-runtime-compilation.md) , wszystkie funkcje i wskaźniki funkcji są, **`__clrcall`** chyba że określono inaczej. **`/clr:pure`** **`/clr:safe`** Opcje kompilatora i są przestarzałe w programie visual Studio 2015 i nie są obsługiwane w programie visual Studio 2017.

`vararg`funkcje członkowskie używają **`__cdecl`** konwencji wywoływania. Wszystkie argumenty funkcji są wypychane na stosie z **`this`** wskaźnikiem umieszczonym na stosie.

Ponieważ ta konwencja wywoływania ma zastosowanie tylko do języka C++, nie ma schematu dekoracji nazwy C.

Podczas definiowania niestatycznej funkcji składowej klasy, określ modyfikator konwencji wywoływania tylko w deklaracji. Nie musisz określać go ponownie w definicji poza wierszem. Kompilator używa konwencji wywoływania określonej podczas deklaracji w punkcie definicji.

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)
