---
title: Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 97db09ac7652c00e9599a6938f4114de080906c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318028"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym

**Specyficzne dla firmy Microsoft**

Ogólnie rzecz biorąc nie należy zakładać, że rejestr `__asm` będzie miał daną wartość po rozpoczęciu bloku. Wartości rejestru nie są gwarantowane `__asm` do zachowania w oddzielnych blokach. Jeśli zakończysz blok kodu wbudowanego i rozpoczniesz inny, nie można polegać na rejestrach w drugim bloku, aby zachować ich wartości z pierwszego bloku. Blok `__asm` dziedziczy niezależnie od wartości rejestru wynik z normalnego przepływu kontroli.

Jeśli używasz `__fastcall` konwencji wywołującej kompilator przekazuje argumenty funkcji w rejestrach, a nie na stosie. Może to spowodować problemy `__asm` w funkcjach z blokami, ponieważ funkcja nie ma sposobu, aby stwierdzić, który parametr jest w którym rejestrze. Jeśli funkcja otrzyma parametr w EAX i natychmiast przechowuje coś innego w EAX, oryginalny parametr zostanie utracony. Ponadto należy zachować rejestr ECX w dowolnej `__fastcall`funkcji zadeklarowanej za pomocą .

Aby uniknąć takich konfliktów rejestru, `__fastcall` nie należy używać `__asm` konwencji dla funkcji, które zawierają blok. Jeśli konwencja `__fastcall` zostanie określona globalnie za pomocą opcji kompilatora /Gr, zadeklaruj każdą funkcję zawierającą `__asm` blok z `__cdecl` lub `__stdcall`. (Atrybut `__cdecl` informuje kompilatora do używania konwencji wywoływania języka C dla tej funkcji.) Jeśli nie kompilujesz z /Gr, należy unikać `__fastcall` deklarowania funkcji z atrybutem.

Podczas `__asm` pisania języka zestawu w funkcjach C/C++ nie trzeba zachowywać rejestrów EAX, EBX, ECX, EDX, ESI lub EDI. Na przykład w power2. C przykład w pisanie funkcji z `power2` zestawu [wbudowanego](../../assembler/inline/writing-functions-with-inline-assembly.md), funkcja nie zachowuje wartość w rejestrze EAX. Jednak przy użyciu tych rejestrów wpłynie na jakość kodu, ponieważ alokator rejestru nie można ich używać do przechowywania wartości w blokach. `__asm` Ponadto za pomocą EBX, ESI lub EDI w wbudowanym kodzie zestawu, można wymusić kompilator, aby zapisać i przywrócić te rejestry w prologu funkcji i epilogu.

Należy zachować inne rejestry, których używasz (takich jak DS, SS, SP, `__asm` BP i flagi rejestrów) dla zakresu bloku. Należy zachować rejestry ESP i EBP, chyba że masz jakiś powód, aby je zmienić (na przykład, aby przełączyć stosy). Zobacz [też: Optymalizacja zestawu wbudowanego](../../assembler/inline/optimizing-inline-assembly.md).

Niektóre typy SSE wymagają wyrównania stosu ośmio bajtów, zmuszając kompilator do emitowania dynamicznego kodu wyrównania stosu. Aby uzyskać dostęp zarówno do zmiennych lokalnych, jak i parametrów funkcji po wyrównaniu, kompilator przechowuje dwa wskaźniki ramki.  Jeśli kompilator wykonuje pominięcie wskaźnika ramki (FPO), użyje EBP i ESP.  Jeśli kompilator nie wykonuje FPO, użyje EBX i EBP. Aby upewnić się, że kod działa poprawnie, nie należy modyfikować EBX w asm kod, jeśli funkcja wymaga wyrównania stosu dynamicznego, ponieważ może zmodyfikować wskaźnik ramki. Albo przenieść osiem bajtów wyrównane typy z funkcji lub uniknąć używania EBX.

> [!NOTE]
> Jeśli wbudowany kod zestawu zmienia flagę kierunku przy użyciu instrukcji STD lub CLD, należy przywrócić flagę do jej pierwotnej wartości.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Asembler wbudowany](../../assembler/inline/inline-assembler.md)<br/>
