---
title: Prolog i Epilog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2939293fe5fbdfd07cb12470790de5b064489d7f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372012"
---
# <a name="prolog-and-epilog"></a>Prolog i epilog
Każda funkcja przydziela miejsce na stosie, wywołania innych funkcji, zapisuje nieulotnej rejestrów lub korzysta z obsługi wyjątków muszą mieć prologu, w których limity adresu są opisane w skojarzonych z wpisu tabeli funkcji odpowiednich danych unwind (zobacz [(X64) obsługi wyjątków](../build/exception-handling-x64.md)). Prologu zapisuje argument rejestrów w ich adresy domowe w razie potrzeby wypchnięcia nieulotnej rejestrów na stosie, przydziela stała część stosu dla zmiennych lokalnych i obiekty tymczasowe i opcjonalnie ustanawia wskaźnika ramki. Skojarzone dane operacji unwind musi opisywać akcji prologu i podać informacje niezbędne do cofania efekt kod prologu.  
  
 Jeśli ustalonych alokacji w stosie jest więcej niż jedną stronę (oznacza to, większy niż 4096 bajtów), wówczas jest to możliwe, że alokacji stosu może obejmować więcej niż jedną stronę pamięci wirtualnej, i w związku z tym alokacji musi zostać sprawdzony przed faktycznie jest przydzielony. Specjalnej procedury można wywołać za pomocą prologu i które nie niszczy żadnego rejestrów argument jest dostępna dla tego celu.  
  
 Preferowaną metodą zapisywania nieulotnej rejestrów jest przenieś je na stosie przed alokacji stosu stałym. Jeśli alokacji stosu stałym były wykonywane przed nieulotnej rejestrów zostały zapisane, prawdopodobnie przemieszczenie 32-bitowe mogą być wymagane dla adresu, a następnie zapisanego zarejestrować obszarze (powinno, wypchnięć rejestrów są tak szybko jak przenosi, powinny pozostać tak dla najbliższej przyszłości mimo domniemanych zależność między wypchnięcia). Rejestruje nieulotnej mogą zostać zapisane w dowolnej kolejności. Jednak używany po raz pierwszy w prologu nieulotnej rejestru należy go zapisać.  
  
 Kod prologu typowe może być:  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
sub      RSP, fixed-allocation-size  
lea      R13, 128[RSP]  
...  
```  
  
 To prologu przechowuje rejestr argument RCX w domu lokalizacji, zapisuje nieulotnej rejestruje R13 R15, przydziela stała część ramki stosu i ustanawia wskaźnika ramki, wskazujące 128 bajtów do obszaru stałej alokacji. Za pomocą przesunięcia umożliwia więcej obszaru ustalonych alokacji mogą być adresowane z przesunięciem jednobajtowe.  
  
 Jeśli rozmiar alokacji stałej jest większa niż lub równa jeden strony pamięci, funkcja pomocnika musi zostać wywołany przed zmodyfikowaniem źródło. Tego pomocnika __chkstk, jest odpowiedzialny za sondowanie zakresu przydzielone być do stosu, aby upewnić się, czy stosu jest poprawnie rozszerzony. W takim przypadku poprzedni przykład prologu zamiast tego należy:  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
mov      RAX,  fixed-allocation-size  
call   __chkstk  
sub      RSP, RAX  
lea      R13, 128[RSP]  
...  
```  
  
 Pomocnik __chkstk nie zmodyfikuje rejestrów wszelkie inne niż R10, R11 i kodów stanu. W szczególności jego zwróci RAX bez zmian i pozostawić wszystkie nieulotnej rejestrów i rejestrów przekazywanie argumentów, które nie mają być modyfikowane.  
  
 Kod epilogu istnieje w każdym zakończenia w funkcji. Są zwykle tylko jeden prologu, może istnieć wiele epilogs. Kod epilogu przycina stosu alokacji stały rozmiar (w razie potrzeby), cofa alokację alokacji stosu stałym przywraca nieulotnej rejestrów przez wyświetlanie ich zapisanych wartości ze stosu i zwraca.  
  
 Kod epilogu obowiązek ścisłego przestrzegania reguł dla kodu unwind do niezawodnego unwind za pośrednictwem wyjątki i przerwania muszą być zgodne. Zmniejsza to ilość unwind dane wymagane, ponieważ nie dodatkowe dane nie jest konieczna opisano każdy epilogu. Zamiast tego kod unwind można określić, że epilogu jest wykonywana za pomocą skanowania do przodu, za pomocą strumienia kod, aby zidentyfikować epilogu.  
  
 Nie wskaźnika ramki jest używany w funkcji, a następnie epilogu najpierw cofnąć alokacji stałej części stosu, nieulotnej rejestrów są zdjęte ze stosu i zwróceniem sterowania do wywoływania funkcji. Na przykład  
  
```  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Użycie wskaźnika ramki w funkcji stosu musi zostać przycięty jego alokacji stałej, przed wykonaniem epilogu. Jest to technicznie nie jest częścią epilogu. Na przykład następujące epilogu mogła zostać użyta Aby cofnąć prologu korzystał już z:  
  
```  
lea      RSP, -128[R13]  
; epilogue proper starts here  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 W praktyce użycie wskaźnika ramki jest nie powód, aby dopasować źródło w dwóch krokach, więc będzie można zamiast tego użyć następujących epilogu:  
  
```  
lea      RSP, fixed-allocation-size - 128[R13]  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Są to jedyne formularzy dla epilogu. Musi zawierać albo `add RSP,constant` lub `lea RSP,constant[FPReg]`, a następnie według serią zero lub więcej zdejmowań 8-bajtowych rejestru i typ zwracany lub skok. (Tylko podzestaw skok instrukcje są dozwolone w epilogu. Są to wyłącznie klasy jmps z odwołaniami do pamięci ModRM gdzie ModRM mod pola wartość 00. Zabronione jest jmps w epilogu z wartości pola mod ModRM 01 lub 10. A-15 zobacz tabelę w 3 woluminu Podręcznik programisty architektura x86 64 AMD: ogólnego przeznaczenia i instrukcje systemu, aby uzyskać więcej informacji o dopuszczalny odwołań ModRM.). Brak innych kodu mogą być wyświetlane. W szczególności nic nie mogą być planowane w epilogu, w tym ładowania zwracanej wartości.  
  
 Należy pamiętać, że, gdy wskaźnik ramki nie jest używany, epilogu musi `add RSP,constant` można cofnąć alokacji stałej części stosu. Nie można używać `lea RSP,constant[RSP]` zamiast tego. To ograniczenie istnieje, więc kod unwind ma mniej wzorców do rozpoznania przy wyszukiwaniu epilogs.  
  
 Następujących reguł pozwala kod unwind, aby określić, czy jest obecnie wykonywana epilogu i symulowanie wykonywania w pozostałej części epilogu umożliwia odtworzenie kontekstu wywołania funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje kodowania x64](../build/x64-software-conventions.md)