---
title: Typowe problemy przy migracji Visual C++ ARM
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 78d87000240acd394edf823a778ae29060c6d09c
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220881"
---
# <a name="common-visual-c-arm-migration-issues"></a>Typowe problemy przy migracji Visual C++ ARM

Korzystając z programu Microsoft C++ kompilatora (MSVC), takie same C++ kod źródłowy może wygenerować różne wyniki w architekturze ARM, niż na x86 lub x64 architektury.

## <a name="sources-of-migration-issues"></a>Źródła problemy przy migracji

Wiele problemów, które można napotkać podczas migracji kodu z architektury x86 lub x64 do architektury ARM odnoszą się do konstrukcji kodu źródłowego, które może wywołać zachowanie niezdefiniowane, zdefiniowanych w implementacji lub nieokreślony.

*Niezdefiniowane zachowanie* jest zachowanie, C++ standard nie definiują i który jest spowodowany przez operację, która nie ma żadnego wyniku uzasadnione: na przykład konwertowanie bitoąa liczbę całkowitą bez znaku lub Przesunięcie wartość przez liczbę pozycji który jest ujemny lub przekracza liczbę bitów w jego typ o podwyższonym poziomie.

*Zachowanie zdefiniowane w implementacji* jest zachowanie, C++ standard wymaga dostawca kompilatora zdefiniować i zarządzania dokumentami. Program bezpiecznie może polegać na zachowanie zdefiniowane w implementacji, nawet jeśli wykonanie tej tak może nie być przenośnej. Zachowanie zdefiniowane w implementacji przykładem wbudowane typy danych i ich wymagania wyrównania. Przykład operacja, która może mieć wpływ zachowanie zdefiniowane w implementacji uzyskuje dostęp do listy zmiennych argumentów.

*Nieokreślone zachowanie* jest zachowanie, C++ standard, pozostawiając celowo deterministyczna. Chociaż zachowanie jest uznawany za deterministyczna, określonego wywołań nieokreślone zachowanie zależą od implementacji kompilatora. Jednak nie jest wymagane dla dostawcy kompilatora wstępnie określić wynik lub zagwarantować spójne zachowanie między porównywalne wywołań i nie jest wymagane dla dokumentacji. Przykładem nieokreślone zachowanie jest kolejność, w jakiej są oceniane wyrażeń podrzędnych obejmujących argumentów dla wywołania funkcji.

Inne problemy przy migracji można przypisać do sprzętu różnice między ARM i architektur x86 lub x64, współpracujących ze standardem C++ inaczej. Na przykład zapewnia silne pamięci model architektury x86 i x64 `volatile`-kwalifikowana zmienne niektóre dodatkowe właściwości, które zostały użyte w celu ułatwienia niektórych rodzajów komunikacji między wątku w przeszłości. Ale model pamięci słabe architektury ARM nie jest obsługiwane używanie tego, ani C++ standard wymaga on.

> [!IMPORTANT]
>  Mimo że `volatile` zyski niektóre właściwości, które mogą służyć do implementowania ograniczone rodzaje komunikacji między wątku na x86 i x64, te dodatkowe właściwości nie są wystarczające do zaimplementowania ogólnie rzecz biorąc transfer wątku komunikacji. C++ standard zaleca się wykonanie za pomocą elementów podstawowych synchronizacji odpowiednich zamiast tego powiadomienia.

Ponieważ różne platformy mogą express tego rodzaju zachowanie inaczej, przenoszenie oprogramowania między platformami może być trudne i podatne na usterki, jeśli jest to uzależnione od zachowania określonej platformy. Chociaż wiele z tych rodzajów zachowanie można zaobserwować i może pojawić się stabilne, opierając się na nich jest co najmniej nieprzenośne, a w przypadku zachowanie niezdefiniowane lub nieokreślony, również jest błąd. Nawet zachowanie, które są wymienione w tym dokumencie nie należy polegać i może ulec zmianie w przyszłych kompilatorów lub implementacji procesora CPU.

## <a name="example-migration-issues"></a>Przykładowe problemy przy migracji

W pozostałej części tego dokumentu opisano, jak odmienne zachowanie tych elementów języka C++ mogą wygenerować różne wyniki na różnych platformach.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Konwersja zmiennoprzecinkowych na liczbę całkowitą bez znaku

W architekturze ARM konwersja wartość zmiennoprzecinkowa do 32-bitową liczbę całkowitą zmienia nasycenie do najbliższej wartości, który może reprezentować liczbę całkowitą, jeśli wartość zmiennoprzecinkowa jest spoza zakresu, który może reprezentować liczbę całkowitą. W architekturach x86 i x64 konwersja zawija się wokół czy liczba całkowita jest podpisany, jest równa -2147483648, czy liczba całkowita jest podpisany. Żadna z tych architektur bezpośrednio obsługuje konwersji wartości zmiennoprzecinkowych do typów mniejszych liczba całkowita; Zamiast tego konwersje są wykonywane do 32 bitów, a wyniki są zaokrąglane do mniejszego rozmiaru.

Z architekturą ARM kombinacji nasycenia i obcięcie oznacza, że konwersja na typy bez znaku poprawnie zmienia nasycenie mniejsze typy bez znaku, gdy zmienia nasycenie 32-bitową liczbę całkowitą, ale daje wynik obcięty do wartości, które są większe niż mniejszych typów może reprezentować ale zbyt mała do nasycenia pełnej 32-bitową liczbę całkowitą. Konwersja również zmienia nasycenie poprawnie dla 32-bitowe podpisane liczby całkowite, ale powoduje obcięcie nasycony, podpisane liczby całkowite pozytywnie przepełniony wartości -1 i 0 dla wartości negatywny przepełniony. Konwersja na mniejsze liczba całkowita ze znakiem powstaje obcinania jest nieprzewidywalne.

Dla architektur x86 i x64, kombinacja otoczone zachowanie podczas konwersji liczb całkowitych bez znaku i jawne wartości dla liczby całkowitej ze znakiem konwersji przy przepełnieniu wraz z obcinania, sprawia, że wyniki dla większości przesunięcia nieprzewidywalne, jeśli są one zbyt duży.

Te platformy różnią się także w sposobu obsługi konwersji NaN (Not a Number) na typy liczb całkowitych. Na ARM NaN konwertuje 0x00000000; na x86 i x64 są konwertowane na 0x80000000.

Konwersja typów zmiennoprzecinkowych należy polegać tylko jeśli wiesz, że wartość znajduje się w zakresie typu Liczba całkowita, która jest konwertowana na.

### <a name="shift-operator---behavior"></a>Operator przesunięcia bitowego (\< \< >>) zachowanie

Na architekturze ARM wartość może być przesunięte do lewej lub prawej maksymalnie 255 bits przed rozpoczyna się powtórzyć. W architekturach x86 i x64 wzorzec jest powtarzany w każdym wielu 32, chyba że źródłem wzorzec jest zmienną 64-bitowy; w takim przypadku wzorzec jest powtarzany w każdym wielokrotnością 64 na x 64 i co wielu 256 na x86, gdzie jest zatrudniony implementacji oprogramowania. Na przykład dla zmiennej 32-bitowych, która ma wartość 1 przesunięte przez 32 pozycji, na ARM wynik jest równy 0, na x86 wynik wyniesie 1 i na x64 wynik jest również 1. Jednak jeśli źródło wartości jest zmienną 64-bitowych, wynik na wszystkich trzech platformach jest 4294967296 i wartości nie "otacza" do momentu jej spowoduje przesunięcie pozycji 64 x64 lub 256 pozycje na ARM i x86.

Ponieważ w wyniku operacji przesunięcia, który przekracza liczbę bitów w typ źródła jest niezdefiniowana, kompilator nie musi mieć spójne zachowanie we wszystkich sytuacjach. Na przykład jeśli oba operandy przesunięcia, są znane w czasie kompilacji, kompilator może zoptymalizować program za pomocą wewnętrznej procedury do precompute wynik przesunięcia, a następnie podstawianie wynik zamiast operacji przesunięcia. Jeśli liczba przesunięć jest za duży lub ujemne, wynikiem wewnętrznej procedury może być inny niż wynik wyrażenia przesunięcia wykonywane przez CPU.

### <a name="variable-arguments-varargs-behavior"></a>Zachowanie zmiennych argumentów (VARARG)

W architekturze ARM parametry, z listy argumentów zmiennych, które są przekazywane na stosie podlegają wyrównania. Na przykład parametr 64-bitowych jest wyrównana do granicy 64-bitowych. Na x86 i x64 argumenty, które są przekazywane na stosie nie podlegają wyrównanie i pakiet ściśle. Różnica ta może spowodować, że funkcja ze zmienną liczbą argumentów, takich jak `printf` odczytać adresów pamięci, które zostały przeznaczone dopełnienie ARM, jeśli oczekiwany układ listy zmiennych argumentów nie jest takie samo, mimo że może działać dla podzbioru niektóre wartości w x86 lub x64 architektury. Rozważmy następujący przykład:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

W tym przypadku można naprawić, upewniając się, że specyfikacji poprawny format jest używany tak, aby wyrównanie argumentu jest traktowane jako usterki. Ten kod jest poprawny:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Kolejność obliczania argumentu

Ponieważ ARM, x 86 i x64 więc różne procesory, stanowią one różne wymagania dotyczące implementacji kompilatora, a także różne możliwości optymalizacji. W związku z tym razem z innych czynników, takich jak ustawienia Konwencja wywoływania i Optymalizacja, kompilatora może ocenić argumentów funkcji w innej kolejności w różnych architektur lub zmianie innych czynników. Może to spowodować zachowanie aplikacji, która zależy od określonej wersji ewaluacyjnej aby ulegać nieoczekiwanym zmianom.

Tego rodzaju błąd może wystąpić, gdy argumenty do funkcji mają skutki uboczne, które mają wpływ na inne argumenty do funkcji w tym samym wywołaniu. Zazwyczaj jest łatwe uniknąć tego rodzaju zależności, ale może być zasłonięty czasami, zależności, które są trudne do wykrycia lub przeciążenia operatora. Rozważmy następujący przykład kodu:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Ta opcja ma nazwę dobrze zdefiniowanych, ale w tym przypadku `->` i `*` są przeciążone operatory, a następnie ten kod jest tłumaczona na coś, co jest podobny do tego:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

A jeśli istnieje zależność między `operator->(memory_handle)` i `operator*(p)`, kod może się opierać w kolejności określonej wersji ewaluacyjnej, nawet jeśli oryginalny kod wygląda to niezależne możliwe.

### <a name="volatile-keyword-default-behavior"></a>zachowanie domyślne volatile — słowo kluczowe

Kompilator MSVC obsługuje dwa różne interpretacji `volatile` kwalifikatora magazynu można określić za pomocą przełączników kompilatora. [/Volatile:ms](reference/volatile-volatile-keyword-interpretation.md) przełącznika wybiera Microsoft rozszerzone volatile semantykę, która gwarantuje kolejności silne, ponieważ została w przypadku tradycyjnych x86 i x64 ze względu na modelu silnej pamięci na tych architektur. [/Volatile:iso](reference/volatile-volatile-keyword-interpretation.md) przełącznika wybiera strict C++ standard volatile semantykę, która nie gwarantuje kolejności silne.

W architekturze ARM, wartość domyślna to **/volatile:iso** ponieważ procesorów ARM mają słabo uporządkowane model pamięci, a oprogramowanie ARM nie ma się z polegania na rozszerzoną semantykę **/volatile:ms**  i zazwyczaj nie ma do interfejsu z oprogramowaniem, które ma. Będzie jednak nadal czasami wygodne lub nawet wymagane do kompilowania programu ARM, korzysta z semantyki rozszerzonej. Na przykład może być zbyt kosztowne do portu program korzysta z semantyki ISO C++ lub sterownik może mieć stosować się do tradycyjnych semantyki do poprawnego działania. W takich przypadkach można użyć **/volatile:ms** przełącznik; jednak odtworzyć tradycyjnych semantyki volatile dla elementów docelowych ARM, kompilator należy wstawić barier pamięci wokół każdej Odczyt lub zapis `volatile` zmiennej do wymuszania silne kolejność, która może mieć negatywny wpływ na wydajność.

W architekturach x86 i x64, wartość domyślna to **/volatile:ms** ponieważ większość oprogramowania, który został już utworzony dla tych architektur przy użyciu MSVC opiera się na nich. Podczas kompilowania programów x86 i x64 można określić **/volatile:iso** przełącznika, aby uniknąć niepotrzebnych poleganie na tradycyjnych semantyki volatile i wspierać mobilność.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie Visual C++ dla procesorów ARM](configuring-programs-for-arm-processors-visual-cpp.md)
