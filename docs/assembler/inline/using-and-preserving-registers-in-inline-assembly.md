---
title: Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 99ca0093bb27e859854dfd1ca64addea923e5a5c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191511"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym

**Specyficzne dla firmy Microsoft**

Ogólnie rzecz biorąc nie należy zakładać, że rejestr będzie miał daną wartość po **`__asm`** rozpoczęciu bloku. Wartości rejestru nie należy zachować w oddzielnym **`__asm`** bloku. Jeśli zakończysz blok kodu śródwierszowego i zaczniesz inny, nie możesz polegać na rejestrach w drugim bloku, aby zachować ich wartości z pierwszego bloku. **`__asm`** Blok dziedziczy wszelkie wartości rejestru wynik z normalnego przepływu sterowania.

Jeśli używasz **`__fastcall`** konwencji wywoływania, kompilator przekazuje argumenty funkcji w rejestrach zamiast na stosie. Może to spowodować problemy w funkcjach z **`__asm`** blokami, ponieważ funkcja nie ma sposobu na określenie, który parametr jest używany do rejestracji. Jeśli funkcja ma otrzymać parametr w EAX i natychmiast przechowuje coś innego w EAX, oryginalny parametr zostanie utracony. Ponadto należy zachować rejestr ECX w każdej funkcji zadeklarowanej za pomocą **`__fastcall`** .

Aby uniknąć takich konfliktów rejestrowania, nie należy używać **`__fastcall`** Konwencji dla funkcji, które zawierają **`__asm`** blok. W przypadku określenia **`__fastcall`** Konwencji globalnie przy użyciu opcji kompilatora/GR należy zadeklarować każdą funkcję zawierającą **`__asm`** blok z **`__cdecl`** lub **`__stdcall`** . ( **`__cdecl`** Atrybut nakazuje kompilatorowi użycie konwencji wywoływania języka C dla tej funkcji). Jeśli nie kompilujesz z/gr, unikaj deklarowania funkcji z **`__fastcall`** atrybutem.

W przypadku korzystania **`__asm`** z programu do pisania języka zestawu w funkcjach C/C++ nie trzeba zachować rejestrów EAX, EBX, ECX, EDX, ESI lub EDI. Na przykład w POWER2. Przykład w [przypadku funkcji pisania z wbudowanym zestawem](../../assembler/inline/writing-functions-with-inline-assembly.md) `power2` Funkcja nie zachowuje wartości w rejestrze EAX. Jednak użycie tych rejestrów wpłynie na jakość kodu, ponieważ Alokator rejestru nie może użyć ich do przechowywania wartości w **`__asm`** blokach. Ponadto przy użyciu EBX, ESI lub EDI w kodzie zestawu wbudowanego należy wymusić, aby kompilator zapisywał i przywrócił te rejestry w funkcji prologu i epilogu.

Należy zachować inne rejestry, z których korzystasz (na przykład rejestry DS, SS, SP, BP i flag) dla zakresu **`__asm`** bloku. Należy zachować rejestry ESP i EBP, chyba że istnieje jakiś powód, aby je zmienić (na przykład w celu przełączenia stosów). Zobacz też [Optymalizacja wbudowanego zestawu](../../assembler/inline/optimizing-inline-assembly.md).

Niektóre typy SSE wymagają 8-bajtowego wyrównania stosu, wymuszając kompilator do emitowania dynamicznego kodu wyrównania stosu. Aby można było uzyskać dostęp do zarówno zmiennych lokalnych, jak i parametrów funkcji po wyrównaniu, kompilator utrzymuje dwa wskaźniki ramek.  Jeśli kompilator wykonuje pominięcie wskaźnika ramki (FPO), będzie używać EBP i ESP.  Jeśli kompilator nie wykonuje FPO, będzie używać EBX i EBP. Aby upewnić się, że kod działa prawidłowo, nie należy modyfikować EBX w kodzie ASM, jeśli funkcja wymaga dynamicznego wyrównywania stosu, ponieważ może zmodyfikować wskaźnik ramki. Przenieś typy wyrównane przez osiem bajtów poza funkcję lub Unikaj używania EBX.

> [!NOTE]
> Jeśli wewnętrzny kod asemblera zmienia flagę kierunku przy użyciu instrukcji STD lub CLD, należy przywrócić flagę do oryginalnej wartości.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Asembler wbudowany](../../assembler/inline/inline-assembler.md)<br/>
