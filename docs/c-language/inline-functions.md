---
title: Funkcje śródwierszowe
ms.date: 10/16/2017
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
ms.openlocfilehash: ebe0fd3d785903c149999bd4ec8de9eabeabdb05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325549"
---
# <a name="inline-functions"></a>Funkcje śródwierszowe

**Specyficzne dla firmy Microsoft**

`__inline` Słowo kluczowe instruuje kompilator w celu zastąpienia kodu w definicji funkcji dla każdego wystąpienia wywołania funkcji. Jednak podstawianie następuje tylko według uznania kompilatora. Na przykład kompilator nie tworzy wbudowanej funkcji, jeśli jej adres jest zajęty lub jest zbyt duży do inline.

Aby funkcja była brana pod uwagę jako kandydat do tworzenia konspektu, musi używać definicji funkcji New-Style.

Użyj tego formularza, aby określić wbudowaną funkcję:

> **__inline** *Typ*__inline funkcja<sub>opt</sub> *-Definicja*

Użycie funkcji wbudowanych generuje szybszy kod i czasami może generować mniejszy kod niż odpowiednik wywołania funkcji generowane z następujących powodów:

- Zapisuje czas wymagany do wykonania wywołań funkcji.

- Małe wbudowane funkcje, które mogą być trzy lub mniej, tworzą mniej kodu niż równoważne wywołanie funkcji, ponieważ kompilator nie generuje kodu do obsługi argumentów i wartości zwracanej.

- Funkcje wygenerowane wewnętrznie są uzależnione od optymalizacji kodu, które nie są dostępne dla normalnych funkcji, ponieważ kompilator nie wykonuje optymalizacji międzyproceduralnej.

Funkcji using `__inline` nie należy mylić z wbudowanym kodem asemblera. Aby uzyskać więcej informacji, zobacz [asembler wbudowany](../c-language/inline-assembler-c.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[inline, __inline \_, _forceinline](../cpp/inline-functions-cpp.md)
