---
title: Typowe problemy przy migracji ARM Visual C++ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcc34d472fb6db02eb902001ad5aac77dea5baf0
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2018
---
# <a name="common-visual-c-arm-migration-issues"></a>Typowe problemy przy migracji Visual C++ ARM

Podczas korzystania z programu Microsoft Visual C++ (MSVC), ten sam kod źródłowy C++ może wygenerować różne wyniki na architekturze ARM, niż na x86 lub x64 architektury.

## <a name="sources-of-migration-issues"></a>Źródeł problemy przy migracji

Wiele problemów, które mogą wystąpić podczas migracji kodu z architektur x86 lub x64 do architektury ARM są związane z konstrukcji kodu źródłowego, które może wywołać zachowanie Niezdefiniowany, zdefiniowane w implementacji lub nieokreślona.

*Niezdefiniowane zachowanie* jest C++ standard nie definiuje zachowanie i który jest spowodowany przez operację, która nie ma żadnego wyniku uzasadnione: na przykład konwertowanie wartości zmiennoprzecinkowej na liczbę całkowitą bez znaku lub zmieni wartość przez liczbę pozycji który ma wartość ujemną lub przekracza liczbę bitów w jego typie awansowana.

*Zachowanie zdefiniowane w implementacji* jest zachowanie C++ standard wymaga dostawcą kompilatora, aby zdefiniować i zarządzania dokumentami. Program bezpiecznie może polegać na zachowanie zdefiniowane w implementacji, mimo że spowoduje to może nie być przenośne. Zachowanie zdefiniowane w implementacji przykładem wbudowanych typów danych i ich wymagania dotyczące wyrównywania. Przykład działania, które mogą wpłynąć na zachowanie zdefiniowane w implementacji uzyskuje dostęp do listy zmiennych argumentów.

*Nieokreślony zachowanie* jest zachowanie C++ standard pozostawia celowo deterministyczna. Mimo że zachowanie jest uważany za deterministyczna, wywołań określonego przez nieokreślony zachowanie są określane przez implementacja kompilatora. Jednak nie jest wymagane dla dostawcy kompilatora wstępnie określić wynik lub zagwarantowania spójności działania między porównywalne wywołań i nie jest wymagane dla dokumentacji. Przykład zachowania nieokreślony to kolejność, w jakiej są oceniane wyrażeń podrzędnych, których argumentów dla wywołania funkcji.

Inne problemy przy migracji może zostać przypisane do sprzętu różnice między ARM i x86 lub x64 architektury wchodzące w interakcje z C++ standard inaczej. Na przykład daje modelu pamięci silne architektury x86 i x64 `volatile`-kwalifikowana zmienne niektóre dodatkowe właściwości, które były używane do ułatwienia niektóre rodzaje komunikacji między wątku w przeszłości. Jednak model pamięci słabe architektury ARM nie obsługuje tego użycia ani C++ standard wymaga ona.

> [!IMPORTANT]
>  Mimo że `volatile` zyski niektóre właściwości, które mogą służyć do zaimplementowania formularze ograniczonej komunikacji między wątku na x86 i x64, te dodatkowe właściwości nie są wystarczające do implementowania ogólnie między wątku komunikacji. C++ standard zaleca wykonanie przez użycie zamiast niej elementy podstawowe synchronizacji odpowiednich taką komunikację.

Ponieważ różne platformy może express rodzaju zachowanie inaczej, eksportowanie oprogramowania między platformami może być trudne i usterki podatne jeśli zależy od zachowania określonej platformy. Mimo że wiele z tych rodzajów zachowanie można zaobserwować i może pojawić się stabilne polegania na ich jest co najmniej nieprzenośne, a w przypadku zachowania niezdefiniowane lub nieokreślona, jest również wystąpił błąd. Nawet zachowanie to wymienione w tym dokumencie nie powinno być stosowane na i może ulec zmianie w przyszłych kompilatory lub implementacji procesora CPU.

## <a name="example-migration-issues"></a>Przykład problemy przy migracji

Pozostała część tego dokumentu opisano, jak inaczej tych elementów języka C++ może spowodować uzyskanie innych wyników na różnych platformach.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Konwersja zmiennoprzecinkowych na liczbę całkowitą bez znaku

Konwersja wartości zmiennoprzecinkowej na 32-bitową liczbę całkowitą na architekturze ARM zmienia nasycenie do najbliższej wartości, mogącej reprezentować liczbę całkowitą, jeśli wartość zmiennoprzecinkowa jest poza zakresem, mogącej reprezentować liczbę całkowitą. Na architektur x86 i x64 konwersji zawija się wokół liczbę całkowitą nie jest podpisany, czy ustawiono -2147483648, jeśli liczba całkowita jest podpisana. Żadna z tych architektury bezpośrednio obsługuje konwersji wartości zmiennoprzecinkowych na mniejsze typy całkowite; Zamiast tego konwersje są wykonywane na 32-bitowy, a wyniki są obcinane mniejszy rozmiar.

Dla architektury ARM kombinację nasycenie i obcięcie oznacza, że konwersji na typy niepodpisane poprawnie zmienia nasycenie mniejsze typy bez znaku zmienia nasycenie 32-bitową liczbę całkowitą, ale powstaje skróconą wartości, które są większe niż mniejszy typ może reprezentować ale zbyt mała do nasycenia pełnej 32-bitową liczbę całkowitą. Konwersja również zmienia nasycenie poprawnie 32-bitowych liczb całkowitych ze znakiem, ale powoduje obcięcie nasycenia, podpisane liczby całkowite pozytywnie przepełniony wartości -1 i 0 dla wartości negatywnie przepełniony. Konwersja na mniejsze całkowita powstaje skróconą będzie nieprzewidywalny.

Dla architektury x86 i x64 kombinacja otoczone zachowanie w przypadku konwersji liczbę całkowitą bez znaku i wyceny jawnej konwersji liczbę całkowitą ze znakiem na przepełnienia, wraz z obcięcie, upewnij wyników dla zmian większości nieprzewidywalne, jeśli są one zbyt duży.

Tych platform różnią się również w sposób obsługują konwersja NaN (Not a Number) do typów całkowitych. Na ARM NaN konwertuje 0x00000000; na x86 i x64 są konwertowane na 0x80000000.

Konwersja typów zmiennoprzecinkowych tylko mogą polegać na, jeśli wiadomo, że wartość jest spoza zakresu typu Liczba całkowita, który jest przekształcany na.

### <a name="shift-operator---behavior"></a>Operator przesunięcia bitowego (\< \< >>) zachowanie

Na komputerze o architekturze ARM wartość można przesunięte lewej lub do prawej maksymalnie 255 bits przed rozpoczyna się ponownie. Na architektur x86 i x64 wzorzec jest powtarzany w każdej wielu 32 chyba, że źródło wzorzec jest zmienną 64-bitowy; w takim przypadku wzorzec jest powtarzany w każdej wielokrotnością 64 na x 64, a każda wielokrotność 256 na x86, gdzie jest zastosować implementacji oprogramowania. Na przykład dla zmiennej 32-bitowe o wartości 1 spowoduje przesunięcie od lewej 32 pozycji na ARM wynik wynosi 0, na x86 wynik jest 1 i na x64 wynik jest również 1. Jednak jeśli źródło wartości zmiennej 64-bitowych, wynik na wszystkich platformach trzy jest 4294967296, a wartość nie "otacza" do momentu jej spowoduje przesunięcie pozycji 64 na x64 lub 256 pozycji na ARM i x86.

Ponieważ zdefiniowano wynik operacji shift, który przekracza liczbę bitów dla typu źródłowego kompilator nie musi mieć zachowanie spójności we wszystkich sytuacjach. Na przykład jeśli obydwa argumenty operacji zmiany są znane w czasie kompilacji, kompilator może zoptymalizować program za pomocą wewnętrznej procedury precompute wynik zmiany, a następnie podstawiając wynik zamiast operacji przesunięcia. Jeśli liczba przesunięć jest za duży lub ujemne, wynik wewnętrznej procedury może być innego niż wynik tego samego wyrażenia shift, wykonywane przez procesor CPU.

### <a name="variable-arguments-varargs-behavior"></a>Zachowanie zmiennych argumentów (VARARG)

Na komputerze o architekturze ARM wyrównanie podlegają parametrów przy użyciu listy zmiennych argumentów, które są przekazywane na stosie. Na przykład parametr 64-bitowych jest wyrównany na granicy 64-bitowych. Na x86 i x64 argumenty, które są przekazywane na stosie nie podlegają wyrównanie i dodatkiem Service pack ściśle. Ta różnica może spowodować funkcję ze zmienną liczbą argumentów, takich jak `printf` do odczytania adresów pamięci, które miały jako dopełnienie ARM Jeśli oczekiwane układ listy zmiennych argumentów nie pasuje dokładnie, mimo że może działać dla podzbioru niektórych wartości na x86 lub x64 architektury. Rozważmy następujący przykład:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

W takim przypadku można naprawić ten błąd, upewniając się, czy specyfikacji poprawny format jest używany, aby uważanego wyrównanie argumentu. Ten kod jest poprawny:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Kolejność obliczania argumentów

Ponieważ ARM x 86 i x64 więc różne procesory, stanowią one różne wymagania dotyczące implementacji kompilatora, a także różne możliwości dla optymalizacji. W związku z tym razem z innych czynników, takich jak ustawienia Konwencja wywoływania i optymalizację, kompilatora może ocenić argumenty funkcji w innej kolejności na różnych architektur lub zmianie innych czynników. Może to spowodować zachowanie aplikacji, która zależy od kolejności oceny określonego, aby zmienić nieoczekiwanie.

Tego rodzaju błąd może wystąpić, gdy argumentów do funkcji ma efekty uboczne, które mają wpływ na inne argumenty funkcji w tym samym wywołaniu. Zazwyczaj jest łatwo uniknąć tego rodzaju zależności, ale może być zasłonięty czasami, zależności, które są trudne do wykrycia lub przeładowania operatora. Należy wziąć pod uwagę w tym przykładzie kodu:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Ta opcja dobrze zdefiniowany, ale jeśli `->` i `*` są przeciążone operatory, a następnie ten kod jest translacji podobny to:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

A jeśli istnieje zależność między `operator->(memory_handle)` i `operator*(p)`, kod może się opierać w kolejności określonej wersji ewaluacyjnej, nawet jeśli oryginalny kod wygląda jak jest nie możliwości zależności.

### <a name="volatile-keyword-default-behavior"></a>zachowanie domyślne volatile — słowo kluczowe

Kompilator MSVC obsługuje dwa różne interpretacji `volatile` kwalifikator magazynu, którą można określić za pomocą przełączniki kompilatora. [/Volatile:ms](../build/reference/volatile-volatile-keyword-interpretation.md) przełącznika wybiera przedłużony volatile semantyki gwarantuje kolejność silne został w przypadku tradycyjnych x86 i x64 z powodu modelu silne pamięci na tych architektur firmy Microsoft. [/Volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) przełącznika wybiera strict C++ standardowe volatile semantyki nie gwarantuje kolejność silne.

Na komputerze o architekturze ARM, wartość domyślna to **/volatile:iso** ponieważ procesorów ARM ma słabo uporządkowane modelu pamięci i ARM oprogramowania nie ma się z polegania na semantykę rozszerzonej **/volatile:ms**  i zwykle nie mają do interfejsu z oprogramowaniem, które wykonuje. Jednak jest nadal czasami wygodne lub nawet wymaganego do skompilowania programu ARM, korzysta z semantyki rozszerzonej. Na przykład może być zbyt kosztowne do portu program korzysta z semantyki ISO C++ lub sterownik może być konieczne stosować się do tradycyjnych semantyki do poprawnego działania. W takich przypadkach można użyć **/volatile:ms** przełącznik; Aby odtworzyć tradycyjnych semantyki volatile dla elementów docelowych ARM, kompilator należy wstawić bariery pamięci wokół każdego odczytu lub zapisu `volatile` zmiennej, aby wymusić silne porządkowania, która może mieć negatywny wpływ na wydajność.

W architekturze x86 i x64, wartość domyślna to **/volatile:ms** ponieważ większość oprogramowania, który został już utworzony dla tych architektur przy użyciu MSVC opiera się na nich. Podczas kompilowania x86 i x64 programy można określić **/volatile:iso** przełącznik, aby uniknąć niepotrzebnych zależność od tradycyjnego semantyki nietrwałe i wspierać mobilność.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie Visual C++ dla procesorów ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
