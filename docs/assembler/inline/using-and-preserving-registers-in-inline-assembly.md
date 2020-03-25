---
title: Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 51147a217ec56c525fc01e1b36a9381b9356ba4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169158"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym

**Specyficzne dla firmy Microsoft**

Ogólnie rzecz biorąc nie należy zakładać, że rejestr będzie miał daną wartość, gdy zostanie rozpoczęty blok `__asm`. Wartości rejestru nie należy zachować w oddzielnym bloku `__asm`. Jeśli zakończysz blok kodu śródwierszowego i zaczniesz inny, nie możesz polegać na rejestrach w drugim bloku, aby zachować ich wartości z pierwszego bloku. Blok `__asm` dziedziczy wszelkie wartości rejestru wynik z normalnego przepływu sterowania.

Jeśli używasz konwencji wywoływania `__fastcall`, kompilator przekazuje argumenty funkcji w rejestrach zamiast na stosie. Może to spowodować problemy w funkcjach z blokami `__asm`, ponieważ funkcja nie ma żadnego sposobu, aby stwierdzić, który parametr jest używany do rejestracji. Jeśli funkcja ma otrzymać parametr w EAX i natychmiast przechowuje coś innego w EAX, oryginalny parametr zostanie utracony. Ponadto należy zachować rejestr ECX w każdej funkcji zadeklarowanej za pomocą `__fastcall`.

Aby uniknąć takich konfliktów rejestrowania, nie należy używać konwencji `__fastcall` dla funkcji, które zawierają blok `__asm`. W przypadku określenia `__fastcall` Konwencji globalnie przy użyciu opcji kompilatora/GR należy zadeklarować każdą funkcję zawierającą blok `__asm` z `__cdecl` lub `__stdcall`. (Atrybut `__cdecl` informuje kompilator, aby używał konwencji wywoływania C dla tej funkcji). Jeśli nie kompilujesz z/gr, unikaj deklarowania funkcji z atrybutem `__fastcall`.

W przypadku używania `__asm` do pisania języka zestawu w językuC++ C/Functions nie trzeba zachować rejestrów EAX, EBX, ECX, EDX, ESI lub EDI. Na przykład w POWER2. Przykład podczas [pisania funkcji z wbudowanym zestawem](../../assembler/inline/writing-functions-with-inline-assembly.md)funkcja `power2` nie zachowuje wartości w rejestrze EAX. Jednak użycie tych rejestrów wpłynie na jakość kodu, ponieważ Alokator rejestru nie może użyć ich do przechowywania wartości w blokach `__asm`. Ponadto przy użyciu EBX, ESI lub EDI w kodzie zestawu wbudowanego należy wymusić, aby kompilator zapisywał i przywrócił te rejestry w funkcji prologu i epilogu.

Należy zachować inne rejestry, z których korzystasz (na przykład rejestry DS, SS, SP, BP i flag) dla zakresu bloku `__asm`. Należy zachować rejestry ESP i EBP, chyba że istnieje jakiś powód, aby je zmienić (na przykład w celu przełączenia stosów). Zobacz też [Optymalizacja wbudowanego zestawu](../../assembler/inline/optimizing-inline-assembly.md).

Niektóre typy SSE wymagają 8-bajtowego wyrównania stosu, wymuszając kompilator do emitowania dynamicznego kodu wyrównania stosu. Aby można było uzyskać dostęp do zarówno zmiennych lokalnych, jak i parametrów funkcji po wyrównaniu, kompilator utrzymuje dwa wskaźniki ramek.  Jeśli kompilator wykonuje pominięcie wskaźnika ramki (FPO), będzie używać EBP i ESP.  Jeśli kompilator nie wykonuje FPO, będzie używać EBX i EBP. Aby upewnić się, że kod działa prawidłowo, nie należy modyfikować EBX w kodzie ASM, jeśli funkcja wymaga dynamicznego wyrównywania stosu, ponieważ może zmodyfikować wskaźnik ramki. Przenieś typy wyrównane przez osiem bajtów poza funkcję lub Unikaj używania EBX.

> [!NOTE]
>  Jeśli wewnętrzny kod asemblera zmienia flagę kierunku przy użyciu instrukcji STD lub CLD, należy przywrócić flagę do oryginalnej wartości.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
