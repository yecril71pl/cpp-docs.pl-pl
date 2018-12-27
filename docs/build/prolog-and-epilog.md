---
title: x64 prologu i epilogu
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: b808703e9c89b8e455e9df2b5959a2f0dd10b939
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627231"
---
# <a name="x64-prolog-and-epilog"></a>x64 prologu i epilogu

Każdej funkcji, który przydziela miejsce w stosie wywołania innych funkcji, zapisuje rejestrów nieulotnej. natomiast przy użyciu obsługi wyjątków musi mieć prologu, na których limity adresów są opisane w dane odwinięcia skojarzone z wpisu tabeli odpowiednich funkcji. Aby uzyskać więcej informacji, zobacz [x64 wyjątków](../build/exception-handling-x64.md). Prologu zapisuje argument rejestrów w ich adresy domowe w razie potrzeby wypycha nieulotnej rejestrów na stosie, przydziela stałą częścią stosie dla zmiennych lokalnych i obiekty tymczasowe i opcjonalnie ustanawia wskaźnik ramki. Skojarzone dane operacji unwind muszą zawierać opis akcji prologu i podać informacje wymagane do cofnięcia efekt kodzie prologu.

Jeśli stały przydział w stosie jest więcej niż jedną stronę (czyli przekracza 4096 bajtów), jest możliwe, że alokacji stosu mogą obejmować więcej niż jednej strony pamięci wirtualnej i dlatego musi być zaznaczone alokacji przed jest on przydzielany. Specjalnej procedury, można wywołać za pomocą prologu i który nie niszczy znajdujących się w rejestrach argument znajduje się w tym celu.

Preferowaną metodą zapisywania nieulotnej rejestrów jest aby przenieść je na stosie przed alokacji stosu stały. Jeśli Alokacja stosu stałej jest wykonywana przed zapisaniem nieulotnej rejestrów, następnie prawdopodobnie przemieszczenia 32-bitowy jest wymagany do adresów obszar rejestru zapisane. (Powinno, wypchnięć rejestrów są tak szybko, jak przenosi i powinny pozostać tak w najbliższej przyszłości autora dorozumianych współzależności wypchnięć). Rejestry nieulotnej można zapisać w dowolnej kolejności. Jednak pierwszym użyciu nieulotnej Zarejestruj się w prologu należy go zapisać.

## <a name="prolog-code"></a>Kod prologu

Kod prologu typowe może być:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Ta prologu przechowuje rejestr argument RCX w jej lokalizacja główna, zapisuje nieulotnej rejestruje R13 R15 przydziela stałą częścią ramki stosu i ustanawia wskaźnik ramki, który wskazuje 128 bajtów do obszaru stały przydział. Zastosowanie przesunięcie daje więcej obszaru stały przydział adresowanie z przesunięciem jednobajtowych.

Jeśli rozmiar stały przydział jest mniejszy niż jedna strona pamięci, funkcji pomocnika, która musi zostać wywołany przed zmodyfikowaniem RSP. Tego pomocnika `__chkstk`, sondy zakresu stosu przydzielone być to aby upewnić się, że stos jest rozszerzany prawidłowo. W takim przypadku w poprzednim przykładzie prologu zamiast tego będzie:

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

`__chkstk` Pomocnika nie będą modyfikować żadnych rejestrów niż R10 R11 i kodów stanu. W szczególności go zwróci RAX bez zmian i pozostawić wszystkie nieulotnej rejestrów i przekazywania argumentów rejestrów w niezmienionej postaci.

## <a name="epilog-code"></a>Kod epilogu

Kod epilogu istnieje przy każdym wejściu do funkcji. Konieczne jest zwykle tylko jeden prologu, może być wiele epilogs. Kod epilogu przycina stosu rozmiar stały przydział (jeśli jest to konieczne), powoduje cofnięcie przydziału alokacji stosu stały, przywraca nieulotnej rejestrów przez usuwanie ich zapisane wartości ze stosu i zwraca.

Kod epilogu musi postępuj zgodnie z ograniczeniami zestaw reguł dla kodu unwind niezawodnie odwijanie wyjątków i przerwania. Te reguły zmniejszyć liczbę operacji unwind wymagane dane, ponieważ nie dodatkowe dane jest wymagane do opisania każdego epilogu. Zamiast tego kod unwind można określić, że epilogu jest wykonywana przez zeskanowanie do przodu, za pomocą strumienia kodu, aby zidentyfikować epilogu.

Brak wskaźnika ramki jest używany w funkcji, a następnie epilogu najpierw Cofnij Przydział stałą częścią stosu, nieulotnej rejestrów są zdjęte ze stosu i zwróceniem sterowania do funkcji wywołującej. Na przykład

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Jeśli wskaźnik ramki jest używany w funkcji, stos musi przycięta do jego stały przydział przed wykonaniem epilogu. Ta akcja jest technicznie nie jest częścią epilogu. Na przykład następujące epilogu może służyć do cofnięcia prologu wcześniej używano:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

W praktyce gdy jest używany wskaźnik ramki, nie ma dobrej dostosowania RSP w dwóch etapach, więc następujące epilogu będzie używana zamiast tego:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Te formularze są tylko prawidłowe dla epilogu. Musi zawierać albo `add RSP,constant` lub `lea RSP,constant[FPReg]`, a następnie szereg zero lub więcej zdejmowań 8-bajtowych register a `return` lub `jmp`. (Tylko podzbiór `jmp` instrukcje są dozwolone w epilogu. Podzbiór jest wyłącznie klasy `jmp` instrukcji za pomocą których wartość pola mod ModRM to 00 odwołania do pamięci ModRM. Korzystanie z `jmp` instrukcji w epilogu z ModRM wartość pola mod 01 lub 10 jest zabronione. Zobacz tabelę A-15 zbiorczo ręczne programisty architekturę x86 64 AMD 3: Ogólnego przeznaczenia i instrukcje systemu, aby uzyskać więcej informacji o dopuszczalny rozmiar odwołań ModRM.) Może się pojawić żadnego innego kodu. W szczególności nic nie można zaplanować w ramach epilogu, w tym ładowanie wartości zwracanej.

Gdy wskaźnik ramki nie jest używany, należy użyć epilogu `add RSP,constant` można cofnąć alokacji stałą część stosu. Nie można używać `lea RSP,constant[RSP]` zamiast tego. To ograniczenie istnieje, więc kod unwind ma mniejszą liczbę wzorców rozpoznawanie podczas szukania epilogs.

Następujących reguł umożliwia kodu odwijania, aby ustalić, czy jest aktualnie wykonywana epilogu i symulowanie wykonania pozostałej części epilogu, aby zezwolić na ponowne utworzenie kontekście funkcji wywołującej.

## <a name="see-also"></a>Zobacz też

[x64 konwencje kodowania](../build/x64-software-conventions.md)