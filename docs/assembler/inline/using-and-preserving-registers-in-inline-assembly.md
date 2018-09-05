---
title: Za pomocą rejestrów i zachowywanie ich w asemblerze wbudowanym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60506f53eb1933e5acbb03318edada82a8904386
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677021"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym

**Microsoft Specific**

Ogólnie rzecz biorąc, nie należy zakładać, że rejestr danej wartości podczas `__asm` rozpoczyna się w bloku. Wartości rejestru nie musi być zachowana w oddzielnych `__asm` bloków. Jeśli kończyć bloku kodu wbudowanego i rozpoczęcia następnego nie można polegać na rejestrów w drugim bloku do zachowują swoje wartości z pierwszego bloku. `__asm` Bloku dziedziczy zarejestrować niezależnie od wartości wyniku normalny przepływ sterowania.

Jeśli używasz `__fastcall` konwencji wywoływania, kompilator przekazuje argumenty funkcji w rejestrach, a nie na stosie. To może tworzyć problemy w funkcji z `__asm` blokuje, ponieważ funkcja nie ma możliwości powiedzieć, którym parametr znajduje się w której rejestruje. Jeśli funkcja stanie się pojawić parametr w EAX i natychmiast przechowuje czymś innym w EAX, oryginalnym parametr zostaną utracone. Ponadto należy zachować ECX, zarejestruj się w dowolnej funkcji zadeklarowanych za pomocą `__fastcall`.

Aby uniknąć konfliktów takich rejestru, nie należy używać `__fastcall` Konwencji dla funkcji, które zawierają `__asm` bloku. Jeśli określisz `__fastcall` Konwencja, za pomocą GR — opcja kompilatora zadeklarować, co funkcja zawierająca `__asm` blokowania z `__cdecl` lub `__stdcall`. ( `__cdecl` Atrybut informuje kompilator, aby używać konwencji wywoływania języka C dla tej funkcji.) Jeśli nie są kompilowane przy użyciu GR, należy unikać deklarowania funkcji o `__fastcall` atrybutu.

Korzystając z `__asm` pisanie języka zestawu w funkcji języka C/C++, nie trzeba zachować rejestrów EAX, EBX, ECX EDX, ESI lub EDI. Na przykład w POWER2. Przykład C w [pisanie funkcji w zestawie wbudowanym](../../assembler/inline/writing-functions-with-inline-assembly.md), `power2` funkcja nie zachowuje wartość w rejestrze EAX. Jednak przy użyciu tych rejestrów wpłynie na jakość kodu ponieważ alokatora rejestru nie można ich używać do przechowywania wartości między `__asm` bloków. Ponadto za pomocą EBX i ESI, EDI w wbudowany kod asemblera, możesz wymusić na kompilatorze do zapisywania i przywracania tych rejestrów w funkcji prologu i epilogu.

Należy zachować innych rejestrów użyć (np. usługi Katalogowej, SS, SP, najlepszych praktyk w zakresie i flagi rejestrów) do zakresu `__asm` bloku. Należy zachować rejestrów ESP i EBP, chyba że z jakiegoś powodu, aby zmienić ich (na przykład przełączyć stosów). Zobacz też [Optymalizacja wbudowanego asemblera](../../assembler/inline/optimizing-inline-assembly.md).

Niektóre typy SSE wymaga wyrównania stosu 8 bajtową wymuszanie kompilator będzie emitować Kod dynamiczne wyrównania stosu. Aby mieć możliwość dostępu do zmiennych lokalnych i parametrów funkcji po wyrównanie, kompilator obsługuje dwóch wskaźników ramek.  Kompilator wykonuje pominięcie wskaźnika ramki (ang.), zostanie użyty EBP i ESP.  Jeśli kompilator nie wykonuje FPO, użyje EBX i EBP. Aby upewnić się, kod działa poprawnie, nie należy modyfikować EBX w kodzie asm, jeśli funkcja wymaga wyrównania stosu dynamicznej można modyfikować, wskaźnik ramki. Przenieś typy wyrównany 8 bajtową z funkcji lub EBX należy unikać.

> [!NOTE]
>  Flaga kierunku, korzystając z instrukcji standardowe lub CLD zmiany kodu zestawu wbudowanego flagi należy przywrócić do oryginalnej wartości.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>