---
title: Przekazywanie argumentów i konwencje nazewnictwa
ms.date: 12/17/2018
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
ms.openlocfilehash: b6b65b4e0cc33ea384eff306952589a49e7ad41a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229236"
---
# <a name="argument-passing-and-naming-conventions"></a>Przekazywanie argumentów i konwencje nazewnictwa

**Specyficzne dla firmy Microsoft**

Kompilatory języka Microsoft C++ umożliwiają określenie Konwencji przekazywania argumentów i zwracania wartości między funkcjami i obiektami wywołującymi. Nie wszystkie konwencje są dostępne na wszystkich obsługiwanych platformach, a niektóre konwencje korzystają z implementacji specyficznych dla platformy. W większości przypadków słowa kluczowe lub przełączniki kompilatora, które określają nieobsługiwaną Konwencję na określonej platformie, są ignorowane, a używana jest Konwencja domyślna platformy.

W przypadku architektury x86 platformach wszystkie argumenty są rozszerzane do 32 bitów podczas przekazywania. Wartości zwracane są również rozszerzane do 32 bitów i zwracane w rejestrze EAX, z wyjątkiem struktur 8-bajtowych, które są zwracane w parze rejestru EDX: EAX. Większe struktury są zwracane w rejestrze EAX jako wskaźniki do ukrytych struktur powrotu. Parametry są wypychane na stosie od prawej do lewej. Struktury, które nie są, nie są zwracane w rejestrach.

Kompilator generuje kod prologu i epilogu w celu zapisania i przywrócenia rejestrów ESI, EDI, EBX i EBP, jeśli są one używane w funkcji.

> [!NOTE]
> Gdy struktura, Unia lub Klasa jest zwracana z funkcji przez wartość, wszystkie definicje tego typu muszą być takie same, w przeciwnym razie program może zakończyć się niepowodzeniem w czasie wykonywania.

Aby uzyskać informacje na temat sposobu definiowania własnego kodu prologu i epilogu, zobacz [wywołania funkcji](../cpp/naked-function-calls.md)bez użycia.

Aby uzyskać informacje na temat domyślnych konwencji wywoływania w kodzie, który jest przeznaczony dla platform x64, zobacz [konwencję wywoływania x64](../build/x64-calling-convention.md). Informacje o problemach z konwencją wywoływania w kodzie, który jest przeznaczony dla platform ARM, można znaleźć w temacie [typowe problemy dotyczące migracji do usługi arm Visual C++](../build/common-visual-cpp-arm-migration-issues.md)

Kompilator języka Visual C/C++ obsługuje następujące konwencje wywoływania.

|Słowo kluczowe|Czyszczenie stosu|Przekazywanie parametrów|
|-------------|-------------------|-----------------------|
|[__cdecl](../cpp/cdecl.md)|Obiekt wywołujący|Wypychanie parametrów na stosie w odwrotnej kolejności (od prawej do lewej)|
|[__clrcall](../cpp/clrcall.md)|nie dotyczy|Załaduj parametry na stos wyrażeń CLR w kolejności (od lewej do prawej).|
|[__stdcall](../cpp/stdcall.md)|Wywoływany|Wypychanie parametrów na stosie w odwrotnej kolejności (od prawej do lewej)|
|[__fastcall](../cpp/fastcall.md)|Wywoływany|Przechowywane w rejestrach, następnie wypychane na stosie|
|[__thiscall](../cpp/thiscall.md)|Wywoływany|Wypchnięcie na stosie; **`this`** wskaźnik przechowywany w ECX|
|[__vectorcall](../cpp/vectorcall.md)|Wywoływany|Przechowywane w rejestrach, następnie wypychane na stosie w odwrotnej kolejności (od prawej do lewej)|

Aby uzyskać powiązane informacje, zobacz [Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)
