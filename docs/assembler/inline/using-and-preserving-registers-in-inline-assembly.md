---
title: "Przy użyciu rejestrów i zachowanie ich w zestawie wbudowanym | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bc9b874535e2169a1ca16bb934fb4d13029c46e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Korzystanie z rejestrów i zachowywanie ich w asemblerze wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Ogólnie rzecz biorąc, nie należy zakładać, że rejestr podanej wartości podczas `__asm` rozpoczyna bloku. Wartości rejestru nie ma gwarancji mają być zachowane w oddzielnym `__asm` bloków. Jeśli kończyć bloku kodu wbudowanego i rozpoczęcia następnego nie zależne rejestrów w bloku drugi do zachowania ich wartości z pierwszej bloku. `__asm` Bloku dziedziczy zarejestrować niezależnie od wartości w wyniku normalnej przepływu sterowania.  
  
 Jeśli używasz `__fastcall` konwencji wywoływania, kompilator przekazuje argumenty funkcji w rejestrach zamiast na stosie. To tworzyć problemy w funkcji z `__asm` blokuje, ponieważ funkcja nie ma możliwości stwierdzić, którego parametr jest które rejestru. Jeśli funkcja stanie się otrzymywanie parametr EAX i natychmiast przechowuje inny w EAX, pierwotny parametr zostaną utracone. Ponadto muszą zachować rejestru ECX w dowolnym funkcja zadeklarowana ze `__fastcall`.  
  
 Aby uniknąć konfliktów takie rejestru, nie używaj `__fastcall` Konwencji dla funkcji, które zawierają `__asm` bloku. Jeśli określisz `__fastcall` Konwencji globalnie z/GR — opcja kompilatora deklarować co funkcja zawierająca `__asm` zablokować z `__cdecl` lub `__stdcall`. ( `__cdecl` Atrybut informuje kompilator, aby używać konwencji wywołania C dla tej funkcji.) Jeśli nie kompilacja z/GR, należy unikać deklarowania funkcji z `__fastcall` atrybutu.  
  
 Korzystając z `__asm` zapisu języka zestawu w funkcji języka C/C++, nie trzeba zachować EAX, element EBX, ECX, EDX, ESI lub EDI rejestrów. Na przykład w POWER2. Przykład C w [pisanie funkcji w zestawie wbudowanym](../../assembler/inline/writing-functions-with-inline-assembly.md), `power2` funkcja nie zachowuje wartość rejestru EAX. Jednak przy użyciu tych rejestrów będzie miało wpływ na jakości kodu ponieważ alokatora rejestru nie można ich używać do przechowywania wartości między `__asm` bloków. Ponadto za pomocą element EBX, ESI lub EDI w kodu zestawu wbudowanego, możesz wymusić kompilatora do zapisywania i przywracania tych rejestrów w prologu funkcji i epilogu.  
  
 Należy zachować innych rejestrów użyć (np. DS, SS SP, BP i rejestruje flagi) dla zakresu `__asm` bloku. Powinien zachować rejestrów ESP i EBP, chyba że niektóre przyczyny, aby zmienić ich (na przykład przełącznika stosy,). Zobacz też [Optymalizowanie zestawu wbudowanego](../../assembler/inline/optimizing-inline-assembly.md).  
  
 Niektóre typy SSE wymagają wyrównania stosu 8 bajtowych, wymuszanie kompilatora można wyemitować kodu dynamiczne wyrównania stosu. Aby mieć możliwość dostępu zarówno zmiennych lokalnych, jak i parametry funkcji po wyrównanie, kompilator obsługuje dwa wskaźniki ramek.  Jeśli kompilator przeprowadza pominięcie wskaźnika ramki (FPO), zostanie użyty EBP i ESP.  Kompilator nie przeprowadza FPO, zostanie użyty element EBX i EBP. Aby upewnić się, kod działa poprawnie, nie należy modyfikować element EBX w kodzie asm Jeśli funkcja wymaga dynamicznej stos wyrównania, jak można zmodyfikować wskaźnika ramki. Przenieś wyrównane typy ośmiu bajtów poza funkcji lub element EBX należy unikać.  
  
> [!NOTE]
>  Jeśli kod zestawu wbudowanego Flaga kierunku, korzystając z instrukcji STD lub CLD, należy przywrócić flagę oryginalnej wartości.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Asembler wbudowany](../../assembler/inline/inline-assembler.md)