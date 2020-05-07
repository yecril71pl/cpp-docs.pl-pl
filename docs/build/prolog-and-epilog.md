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

Każda funkcja, która przydziela miejsce na stosie, wywołuje inne funkcje, zapisuje niezalotne rejestry lub używa obsługi wyjątków, musi mieć Prolog, którego limity adresów są opisane w danych unwind skojarzonych z odpowiednim wpisem tabeli funkcji. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków x64](../build/exception-handling-x64.md). Prolog zapisuje w razie potrzeby rejestry argumentów w ich adresach domowych, wypychaje rejestry nietrwałe na stosie, przydzieli stałą część stosu dla zmiennych lokalnych i obiekty tymczasowe, a także opcjonalnie ustanowi wskaźnik ramki. Skojarzone dane odwinięcia muszą opisywać akcję prologu i muszą podawać informacje niezbędne do cofnięcia efektu kodu prologu.

Jeśli stała alokacja w stosie ma więcej niż jedną stronę (to znaczy więcej niż 4096 bajtów), możliwe jest, że Alokacja stosu może obejmować więcej niż jedną stronę pamięci wirtualnej, dlatego alokacja musi być sprawdzona przed przydzieleniem. Specjalna procedura, która jest wywoływana z prologu, która nie niszczy żadnego z rejestrów argumentów jest w tym celu dostępna.

Preferowaną metodą zapisywania nietrwałych rejestrów jest przeniesienie ich na stos przed stałym alokacją stosu. Jeśli alokacja stałego stosu jest wykonywana przed zapisaniem rejestrów nietrwałych, najprawdopodobniej jest wymagane przemieszczenie 32-bitowe w celu zaadresowania zapisanego obszaru rejestru. (Reportedly, wypchnięcia rejestrów odbywa się tak szybko, jak przesuwają się i powinny pozostać tak, jak w przyszłości, pomimo domniemanej zależności między wypchnięciami.) Rejestry nietrwałe można zapisać w dowolnej kolejności. Jednak pierwsze użycie nietrwałego rejestru w prologu musi mieć na celu jego zapisanie.

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

W tym prologu jest przechowywany argument Register RCX w lokalizacji głównej, zapisuje nietrwałe rejestry R13-R15, przydziela stałą część ramki stosu i ustanawia wskaźnik ramki, który wskazuje 128 bajtów do obszaru stałego przydziału. Użycie przesunięcia umożliwia rozliczenie większej części stałego obszaru alokacji z przesunięciami jednobajtowymi.

Jeśli ustalony rozmiar alokacji jest większy lub równy jednej stronie pamięci, należy wywołać funkcję pomocnika przed modyfikacją funkcji RSP. Ten pomocnik, `__chkstk`, sonduje przydzieloną zakres stosu, aby upewnić się, że stos jest prawidłowo rozszerzony. W takim przypadku poprzedni przykład prologu będzie:

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

`__chkstk` Pomocnik nie zmodyfikuje żadnych rejestrów, takich jak R10, R11 i kody warunków. W szczególności zwróci RAX bez zmian i opuszcza wszystkie nietrwałe rejestry i rejestry przekazywania argumentów niemodyfikowane.

## <a name="epilog-code"></a>Kod epilogu

Kod epilogu istnieje podczas każdego wyjścia do funkcji. Istnieje zwykle tylko jeden Prolog, ale może być wiele epilogs. Kod epilogu przycina stos do jego stałego rozmiaru alokacji (jeśli jest to konieczne), cofa alokację stałego przydziału stosu, przywraca rejestry nietrwałe przez usuwanie ich zapisane wartości ze stosu i zwraca.

Kod epilogu musi być zgodny z ścisłym zestawem reguł dla kodu unwind w celu niezawodnego wyłączania przez wyjątki i przerwania. Te reguły zmniejszają ilość wymaganych danych operacji unwind, ponieważ nie są potrzebne dodatkowe dane do opisania poszczególnych epilogu. Zamiast tego kod unwind może określić, że epilogu jest wykonywany przez skanowanie do przodu przez strumień kodu, aby zidentyfikować epilogu.

Jeśli w funkcji nie jest używany żaden wskaźnik ramki, epilogu musi najpierw cofnąć cofnięcie ustalonej części stosu, rejestry nietrwałe są zdjęte, a sterowanie jest zwracane do funkcji wywołującej. Na przykład:

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Jeśli wskaźnik ramki jest używany w funkcji, stos musi zostać przycięty do stałej alokacji przed wykonaniem epilogu. Ta akcja nie jest technicznie częścią epilogu. Na przykład następujące epilogu można użyć do cofnięcia wcześniej użytego prologu:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

W przypadku użycia wskaźnika ramki nie istnieje dobry powód, aby dostosować żądanie RSP w dwóch krokach, więc zamiast tego zostanie użyty następujący epilogu:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Te formularze są jedynymi prawami dla epilogu. Musi składać się `add RSP,constant` z lub `lea RSP,constant[FPReg]`, po którym następuje seria zero lub więcej 8-bajtowych punktów obecności rejestru i a `return` lub. `jmp` (Tylko podzestaw `jmp` instrukcji jest dozwolony w epilogu. Podzestaw jest wyłącznie klasą `jmp` instrukcji z odwołaniami do pamięci ModRM, gdzie wartość pola mod ModRM jest równa 00. Użycie `jmp` instrukcji w epilogu z ModRM mod o wartości pola "01 lub 10" jest zabronione. Aby uzyskać więcej informacji na temat dozwolonych ModRM odwołań, zobacz tabelę A-15 w woluminie AMD x86-64 Architecture Ogólnego przeznaczenia. Nie można wyświetlić żadnego innego kodu. W szczególności nic nie może być zaplanowane w ramach epilogu, łącznie z ładowaniem wartości zwracanej.

Gdy wskaźnik ramki nie jest używany, epilogu musi użyć `add RSP,constant` w celu cofnięcia alokacji ustalonej części stosu. Nie może być używana `lea RSP,constant[RSP]` zamiast. To ograniczenie istnieje, aby kod unwind ma mniejszą liczbę wzorców do rozpoznawania podczas wyszukiwania epilogs.

Zgodnie z tymi regułami kod unwind określa, że element epilogu jest aktualnie wykonywany i symuluje wykonywanie pozostałej części epilogu, aby umożliwić ponowne utworzenie kontekstu funkcji wywołującej.

## <a name="see-also"></a>Zobacz też

[Konwencje oprogramowania x64](x64-software-conventions.md)
