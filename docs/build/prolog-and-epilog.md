---
title: Prolog i epilog x64
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328432"
---
# <a name="x64-prolog-and-epilog"></a>Prolog i epilog x64

Każda funkcja, która przydziela miejsce na stosie, wywołuje inne funkcje, zapisuje rejestry nieulotne lub używa obsługi wyjątków musi mieć prolog, którego limity adresów są opisane w danych unwind skojarzonych z odpowiednim wpisem tabeli funkcji. Aby uzyskać więcej informacji, zobacz [obsługę wyjątków x64](../build/exception-handling-x64.md). Prolog zapisuje rejestry argumentów w swoich adresach domowych, jeśli to konieczne, wypycha rejestry nieulotne na stosie, przydziela stałą część stosu dla mieszkańców i tymczasowo i opcjonalnie ustanawia wskaźnik ramki. Skojarzone dane unwind musi opisywać działanie prologu i musi dostarczyć informacji niezbędnych do cofnięcia efektu kodu prologu.

Jeśli stała alokacja w stosie jest więcej niż jedna strona (czyli większa niż 4096 bajtów), to jest możliwe, że alokacja stosu może obejmować więcej niż jedną stronę pamięci wirtualnej i w związku z tym alokacji należy sprawdzić przed jej przydzieleniem. Specjalna procedura, która jest wywoływana z prologu i która nie niszczy żadnego z rejestrów argumentów, jest w tym celu dostępna.

Preferowaną metodą zapisywania rejestrów nieulotnych jest przeniesienie ich na stos przed alokacją stosu stałego. Jeśli alokacja stałego stosu jest wykonywana przed zapisaniem rejestrów nieulotnych, najprawdopodobniej do rozwiązania zapisanego obszaru rejestru wymagane jest przemieszczenie 32-bitowe. (Podobno, wypychacze rejestrów są tak szybko, jak ruchy i powinny pozostać tak w dającej się przewidzieć przyszłości, pomimo dorozumianej zależności między wypychaniem.) Rejestry nieulotne można zapisać w dowolnej kolejności. Jednak pierwszym użyciem rejestru nieulotnego w prologu musi być jego zapisanie.

## <a name="prolog-code"></a>Kod prologu

Kod typowego prologu może być:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Ten prolog przechowuje rejestr argumentów RCX w lokalizacji głównej, zapisuje rejestry nieulotne R13-R15, przydziela stałą część ramki stosu i ustanawia wskaźnik ramki, który wskazuje 128 bajtów do stałego obszaru alokacji. Użycie przesunięcia umożliwia zajmącej więcej stałych obszarów alokacji za pomocą przesunięć jedno bajtowych.

Jeśli stały rozmiar alokacji jest większy lub równy jednej stronie pamięci, należy wywołać funkcję pomocnika przed zmodyfikowaniem RSP. Ten pomocnik, `__chkstk`sonduje zakres stosu, który ma być przydzielony, aby upewnić się, że stos jest prawidłowo rozbudowyowany. W takim przypadku poprzedni przykład prologu będzie zamiast tego:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    mov    RAX,  fixed-allocation-size
    call   __chkstk
    sub    RSP, RAX
    lea    R13, 128[RSP]
    ...
```

Pomocnik `__chkstk` nie zmodyfikuje żadnych rejestrów innych niż R10, R11 i kody warunków. W szczególności zwróci RAX bez zmian i pozostawi wszystkie rejestry nieulotne i rejestry kłótliwe bez zmian.

## <a name="epilog-code"></a>Kod epilogu

Kod Epilogu istnieje przy każdym wyjściu z funkcji. Podczas gdy zwykle istnieje tylko jeden prolog, może być wiele epilogów. Kod Epilog przycina stos do jego stałego rozmiaru alokacji (jeśli to konieczne), rozdziela alokację stałego stosu, przywraca rejestry nieulotne, wyskakujący ich zapisane wartości ze stosu i zwraca.

Kod epilogu musi być zgodny ze ścisłym zestawem reguł dla kodu unwind, aby niezawodnie odwinąć za pomocą wyjątków i przerwań. Te reguły zmniejszyć ilość danych unwind wymagane, ponieważ nie dodatkowe dane są potrzebne do opisania każdego epilogu. Zamiast tego kod unwind można określić, że epilog jest wykonywany przez skanowanie do przodu za pośrednictwem strumienia kodu w celu zidentyfikowania epilogu.

Jeśli wskaźnik ramki nie jest używany w funkcji, epilog musi najpierw zdobędyć stałą część stosu, rejestry nieulotne są pojawiały się i kontroli jest zwracany do funkcji wywołującej. Na przykład:

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Jeśli wskaźnik ramki jest używany w funkcji, stos musi być przycięty do jego stałej alokacji przed wykonaniem epilogu. Ta akcja technicznie nie jest częścią epilogu. Na przykład następujące epilog może służyć do cofania prologu wcześniej używane:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

W praktyce, gdy wskaźnik ramki jest używany, nie ma powodu, aby dostosować RSP w dwóch krokach, więc zamiast tego zostanie użyty następujący epilog:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Te formy są jedynymi legalne dla epilogu. Musi składać się z `add RSP,constant` `lea RSP,constant[FPReg]`lub , po którym następuje seria zero lub więcej `return` 8-bajtowy rejestr pops i lub `jmp`. (Tylko podzbiór `jmp` instrukcji są dozwolone w epilogu. Podzbiór jest wyłącznie `jmp` klasą instrukcji z odwołaniami do pamięci ModRM, gdzie wartość pola mod ModRM wynosi 00. Użycie `jmp` instrukcji w epilogu o wartości pola mod ModRM 01 lub 10 jest zabronione. Aby uzyskać więcej informacji na temat dopuszczalnych odniesień do modrm, zobacz tabela A-15 w ręcznym tomie 3 programu architektury AMD x86-64: Ogólne przeznaczenie i instrukcje systemowe). Nie może pojawić się żaden inny kod. W szczególności nic nie można zaplanować w epilogu, w tym ładowania wartości zwracanej.

Gdy wskaźnik ramki nie jest używany, `add RSP,constant` epilog musi służyć do cofniętego alokacji stałej części stosu. Nie może `lea RSP,constant[RSP]` używać zamiast tego. To ograniczenie istnieje, więc kod unwind ma mniej wzorców do rozpoznania podczas wyszukiwania epilogów.

Po tych regułach umożliwia unwind kodu, aby ustalić, że epilog jest obecnie wykonywany i symulować wykonanie pozostałej części epilogu, aby umożliwić odtworzenie kontekstu funkcji wywołującej.

## <a name="see-also"></a>Zobacz też

[Konwencje dotyczące oprogramowania x64](x64-software-conventions.md)
