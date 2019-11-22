---
title: Obsługa wyjątku x64
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: eff4f1a22512b597b5479dbcaabcc9d5fc93c940
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303205"
---
# <a name="x64-exception-handling"></a>Obsługa wyjątku x64

Przegląd strukturalnej obsługi wyjątków oraz C++ konwencje kodowania i zachowanie obsługi wyjątków na platformie x64. Aby uzyskać ogólne informacje dotyczące obsługi wyjątków, zobacz [Obsługa wyjątków w C++wizualizacji ](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Dane operacji unwind dla obsługi wyjątków, obsługa debugera

Do obsługi wyjątków i obsługi debugowania są wymagane kilka struktur danych.

### <a name="struct-runtime_function"></a>struktura RUNTIME_FUNCTION

Obsługa wyjątków oparta na tabelach wymaga wpisu tabeli dla wszystkich funkcji, które przydzielą przestrzeń stosu lub wywołują inną funkcję (na przykład funkcje niebędące liśćmi). Wpisy tabeli funkcji mają format:

|||
|-|-|
|ULONG|Adres początkowy funkcji|
|ULONG|Adres końcowy funkcji|
|ULONG|Adres informacyjny operacji unwind|

Struktura RUNTIME_FUNCTION musi być wyrównana do wartości DWORD w pamięci. Wszystkie adresy są względne dla obrazu, czyli są 32-bitowe przesunięcia od adresu początkowego obrazu, który zawiera wpis w tabeli funkcji. Te wpisy są sortowane i umieszczane w sekcji. pdata w obrazie PE32 +. W przypadku funkcji generowanych dynamicznie [kompilatory JIT] środowisko uruchomieniowe do obsługi tych funkcji musi albo użyć RtlInstallFunctionTableCallback lub RtlAddFunctionTable, aby podać te informacje dla systemu operacyjnego. Niewykonanie tej czynności spowoduje niezawodną obsługę wyjątków i debugowanie procesów.

### <a name="struct-unwind_info"></a>struktura UNWIND_INFO

Struktura informacji o danych unwind służy do rejestrowania efektów funkcji na wskaźniku stosu i lokalizacji nietrwałych rejestrów na stosie:

|||
|-|-|
|UBYTE: 3|Wersja|
|UBYTE: 5|Flagi|
|UBYTE|Rozmiar prologu|
|UBYTE|Liczba kodów operacji unwind|
|UBYTE: 4|Rejestr ramek|
|UBYTE: 4|Przesunięcie rejestru ramek (skalowane)|
|USHORT \* n|Tablica kodów unwind|
|zmienna|Może mieć postać (1) lub (2) poniżej|

(1) procedura obsługi wyjątków

|||
|-|-|
|ULONG|Adres programu obsługi wyjątków|
|zmienna|Dane obsługi specyficzne dla języka (opcjonalnie)|

(2) powiązane z łańcuchem informacje o rozwinięcia

|||
|-|-|
|ULONG|Adres początkowy funkcji|
|ULONG|Adres końcowy funkcji|
|ULONG|Adres informacyjny operacji unwind|

Struktura UNWIND_INFO musi być wyrównana do wartości DWORD w pamięci. Oto co oznaczają każde pole:

- **Wersja**

   Numer wersji danych unwindy, obecnie 1.

- **Znaczników**

   Obecnie zdefiniowane są trzy flagi:

   |Flaga|Opis|
   |-|-|
   |`UNW_FLAG_EHANDLER`| Funkcja ma procedurę obsługi wyjątków, która powinna zostać wywołana podczas wyszukiwania funkcji, które muszą sprawdzać wyjątki.|
   |`UNW_FLAG_UHANDLER`| Funkcja ma procedurę obsługi zakończenia, która powinna zostać wywołana w przypadku odwinięcia wyjątku.|
   |`UNW_FLAG_CHAININFO`| Ta struktura informacji unwind nie jest podstawową procedurą dla procedury. Zamiast tego wpis informacje w łańcuchu unwindy jest zawartością poprzedniego wpisu RUNTIME_FUNCTION. Aby uzyskać więcej informacji, zobacz [struktury informacji o nieprzetworzonym procesie unwind](#chained-unwind-info-structures). Jeśli ta flaga jest ustawiona, UNW_FLAG_EHANDLER i UNW_FLAG_UHANDLER flagi muszą zostać wyczyszczone. Ponadto pola alokacji rejestru ramki i o stałym stosie muszą mieć takie same wartości jak w przypadku podstawowych informacji o rozwinięcia.|

- **Rozmiar prologu**

   Długość prologu funkcji w bajtach.

- **Liczba kodów operacji unwind**

   Liczba gniazd w tablicy kodów operacji unwind. Niektóre kody operacji unwind, na przykład UWOP_SAVE_NONVOL, wymagają więcej niż jednego gniazda w tablicy.

- **Rejestr ramek**

   Jeśli wartość jest różna od zera, funkcja używa wskaźnika ramki (FP), a to pole jest numerem nietrwałego rejestru używanym jako wskaźnik ramki, przy użyciu tego samego kodowania dla pola informacje o operacji UNWIND_CODE węzłów.

- **Przesunięcie rejestru ramek (skalowane)**

   Jeśli pole rejestr ramki ma wartość różną od zera, to pole jest przesunięte w poziomie na żądanie z usługi RSP, które jest stosowane do rejestru FP, gdy zostanie on ustanowiony. Rzeczywisty rejestr FP ma ustawioną wartość RSP + 16 \* tę liczbę, umożliwiając przesunięcia od 0 do 240. To przesunięcie zezwala na zarejestrowanie FP w środku alokacji lokalnego stosu dla dynamicznych ramek stosu, co zapewnia lepszą gęstość kodu przez krótsze instrukcje. (Oznacza to, że więcej instrukcji można użyć 8-bitowego podpisanego formularza przesunięcia).

- **Tablica kodów unwind**

   Tablica elementów, która objaśnia wpływ prologu na rejestry nielotne i żądanie RSP. Zapoznaj się z sekcją UNWIND_CODE na potrzeby znaczenia poszczególnych elementów. W celu wyrównania ta tablica zawsze ma parzystą liczbę wpisów, a ostatni wpis jest potencjalnie nieużywany. W takim przypadku tablica jest dłuższa niż określona przez liczbę pól unwind.

- **Adres programu obsługi wyjątków**

   Wskaźnik względny obrazu do procedury obsługi wyjątku lub zakończenia specyficznych dla funkcji, jeśli flaga UNW_FLAG_CHAININFO jest jasne i jedna z flag UNW_FLAG_EHANDLER lub UNW_FLAG_UHANDLER jest ustawiona.

- **Dane obsługi specyficzne dla języka**

   Dane programu obsługi wyjątków charakterystyczne dla języka funkcji. Format tych danych jest nieokreślony i całkowicie określany przez określoną obsługę wyjątków w użyciu.

- **Informacje o niezaszyfrowanym łańcuchu**

   Jeśli flaga UNW_FLAG_CHAININFO jest ustawiona, wówczas struktura UNWIND_INFO zostanie zakończona trzema UWORDs.  UWORDs te reprezentują informacje RUNTIME_FUNCTION dla funkcji łańcucha nieprzetworzonych danych.

### <a name="struct-unwind_code"></a>struktura UNWIND_CODE

Tablica kodu unwind służy do rejestrowania sekwencji operacji w prologu, która ma wpływ na rejestry nietrwałe i żądanie RSP. Każdy element kodu ma ten format:

|||
|-|-|
|UBYTE|Przesunięcie w prologu|
|UBYTE: 4|Kod operacji unwind|
|UBYTE: 4|Informacje o operacji|

Tablica jest sortowana według malejącej kolejności przesunięcia w prologu.

#### <a name="offset-in-prolog"></a>Przesunięcie w prologu

Przesunięcie (od początku prologu) zakończenia instrukcji, która wykonuje tę operację, oraz 1 (czyli przesunięcie początku następnej instrukcji).

#### <a name="unwind-operation-code"></a>Kod operacji unwind

Uwaga: Niektóre kody operacji wymagają przesunięcia bez znaku do wartości w lokalnej klatce stosu. To przesunięcie jest od początku, czyli najniższego adresu stałego przydziału stosu. Jeśli pole rejestru ramki w UNWIND_INFO wynosi zero, to przesunięcie jest z usługi RSP. Jeśli pole rejestr ramki ma wartość różną od zera, to przesunięcie pochodzi z lokalizacji, w której zarejestrowano żądanie RSP po ustanowieniu rejestru FP. Jest to zgodne z rejestrem FP pomniejszonym o przesunięcie rejestru FP (16 \* przesunięcie tabeli skalowanej ramki w UNWIND_INFO). Jeśli jest używany rejestr FP, każdy kod operacji unwind z przesunięciem musi być używany tylko po ustanowieniu rejestru FP w prologu.

W przypadku wszystkich kodów operacji, z wyjątkiem `UWOP_SAVE_XMM128` i `UWOP_SAVE_XMM128_FAR`, przesunięcie jest zawsze wielokrotnością 8, ponieważ wszystkie wartości stosu są przechowywane na 8-bajtowych granicach (sam stos jest zawsze wyrównany do 16 bajtów). W przypadku kodów operacji, które przyjmują krótkie przesunięcie (mniej niż 512K), końcowa USHORT w węzłach dla tego kodu przechowuje przesunięcie podzielone przez 8. W przypadku kodów operacji, które pobierają długie przesunięcie (512K < = offset < 4 GB), ostatnie dwa węzły USHORT dla tego kodu przechowują przesunięcie (w formacie little-endian).

W przypadku kodów operacji `UWOP_SAVE_XMM128` i `UWOP_SAVE_XMM128_FAR`przesunięcie jest zawsze wielokrotnością 16, ponieważ wszystkie 128-bitowe operacje XMM muszą wystąpić w pamięci podręcznej 16-bajtowej. W związku z tym, współczynnik skalowania 16 jest używany do `UWOP_SAVE_XMM128`, co pozwala na przesunięcie mniejsze niż 1M.

Kod operacji unwindy jest jedną z następujących wartości:

- `UWOP_PUSH_NONVOL` (0) 1 węzeł

  Wypchnij nietrwały rejestr liczb całkowitych, co zmniejsza żądanie RSP przez 8. Informacje o operacji są numerem rejestru. Ze względu na ograniczenia dotyczące epilogs `UWOP_PUSH_NONVOL`, kody unwind muszą pojawiać się najpierw w prologu i odpowiadające im ostatnio w tablicy kodu unwind. To względne Określanie kolejności ma zastosowanie do wszystkich innych kodów operacji unwind, z wyjątkiem `UWOP_PUSH_MACHFRAME`.

- `UWOP_ALLOC_LARGE` (1) 2 lub 3 węzły

  Przydziel obszar o dużym rozmiarze na stosie. Istnieją dwa formularze. Jeśli informacje o operacji są równe 0, rozmiar alokacji podzielony przez 8 jest rejestrowany w następnym miejscu, co pozwoli na alokację do 512K-8. Jeśli informacje o operacji są równe 1, wówczas rozmiar nieskalowanego przydziału jest rejestrowany w następnych dwóch gniazdach w formacie little-endian, co pozwala na przydzielanie do 4 GB-8.

- `UWOP_ALLOC_SMALL` (2) 1 węzeł

  Przydziel obszar o małym rozmiarze na stosie. Rozmiar alokacji to pole informacji o operacji \* 8 + 8, co umożliwia przydzielanie od 8 do 128 bajtów.

  Kod unwind dla alokacji stosu powinien zawsze używać najkrótszego możliwego kodowania:

  |**Rozmiar alokacji**|**Kod unwind**|
  |-|-|
  |od 8 do 128 bajtów|`UWOP_ALLOC_SMALL`|
  |136 do 512K – 8 bajtów|`UWOP_ALLOC_LARGE`, informacje o operacji = 0|
  |512K do 4G-8 bajtów|`UWOP_ALLOC_LARGE`, informacje o operacji = 1|

- `UWOP_SET_FPREG` (3) 1 węzeł

  Ustanów Rejestr wskaźnika ramki przez ustawienie w rejestrze określonego przesunięcia bieżącej wartości RSP. Przesunięcie jest równe polu Przesunięcie rejestru ramki (skalowane) w UNWIND_INFO \* 16, umożliwiając przesunięcia od 0 do 240. Użycie przesunięcia umożliwia ustanowienie wskaźnika ramki, który wskazuje na środek stałego przydziału stosu, co pomaga w rozwiązaniu kodu przez umożliwienie większej liczbie dostępu do korzystania z krótkich form instrukcji. Pole informacji o operacji jest zarezerwowane i nie powinno być używane.

- `UWOP_SAVE_NONVOL` (4) 2 węzły

  Zapisz nielotną liczbę całkowitą na stosie przy użyciu usługi MOV zamiast WYPYCHANia. Ten kod jest używany głównie do *zmniejszania liczby operacji zawijania*, w którym rejestr nietrwały jest zapisywany na stosie w pozycji, która została wcześniej przyznana. Informacje o operacji są numerem rejestru. Przesunięcie stosu skalowanego do 8 jest rejestrowane w następnym gnieździe kodu operacji unwind, zgodnie z opisem w powyższej uwadze.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 węzły

  Zapisz nielotną liczbę całkowitą na stosie z długim przesunięciem, używając w tym celu funkcji MOV zamiast WYPYCHANia. Ten kod jest używany głównie do *zmniejszania liczby operacji zawijania*, w którym rejestr nietrwały jest zapisywany na stosie w pozycji, która została wcześniej przyznana. Informacje o operacji są numerem rejestru. Przesunięcie stosu nieskalowanego jest rejestrowane w następnych dwóch gniazdach kodu operacji unwind, zgodnie z opisem w powyższej uwadze.

- `UWOP_SAVE_XMM128` (8) 2 węzłów

  Zapisz wszystkie 128 bity nietrwałego rejestru XMM na stosie. Informacje o operacji są numerem rejestru. Przesunięcie stosu skalowane przez 16 jest rejestrowane w następnym gnieździe.

- `UWOP_SAVE_XMM128_FAR` (9) 3 węzłów

  Zapisz wszystkie 128 bity nietrwałego rejestru XMM na stosie z długim przesunięciem. Informacje o operacji są numerem rejestru. Przesunięcie stosu nieskalowanego jest rejestrowane w następnych dwóch gniazdach.

- `UWOP_PUSH_MACHFRAME` (10) 1 węzeł

  Wypchnij ramkę maszyny.  Ten kod unwind służy do rejestrowania efektu przerwania lub wyjątku sprzętowego. Istnieją dwa formularze. Jeśli informacje o operacji są równe 0, jedna z tych ramek została wypchnięcia na stosie:

  |||
  |-|-|
  |RSP+32|SS|
  |RSP+24|Stary żądanie RSP|
  |RSP+16|EFLAGS|
  |RSP+8|Rejestr|
  |RSP|RPO|

  Jeśli informacje o operacji są równe 1, jedna z tych ramek została wypchnięte:

  |||
  |-|-|
  |RSP+40|SS|
  |RSP+32|Stary żądanie RSP|
  |RSP+24|EFLAGS|
  |RSP+16|Rejestr|
  |RSP+8|RPO|
  |RSP|Kod błędu:|

  Ten kod unwind zawsze pojawia się w postaci fikcyjnego prologu, który nigdy nie jest wykonywany, ale zamiast tego występuje przed rzeczywistym punktem wejścia procedury przerwania i istnieje tylko w celu zasymulowania wypychania ramki maszyny. `UWOP_PUSH_MACHFRAME` rejestruje tę symulację, co oznacza, że maszyna ma koncepcyjne działanie:

  1. Adres zwrotny protokołu RIP z góry stosu do *katalogu Temp*
  
  1. Wypchnięcie SS

  1. Wypychanie starego RSP

  1. Wypychanie EFLAGS

  1. Wypychanie CS

  1. Wypychanie — *temp*

  1. Kod błędu wypychania (Jeśli informacja o op jest równa 1)

  Symulowana operacja `UWOP_PUSH_MACHFRAME` zmniejsza żądanie RSP o 40 (informacja o op równa 0) lub 48 (informacja o op jest równa 1).

#### <a name="operation-info"></a>Informacje o operacji

Znaczenie informacji o operacji BITS zależy od kodu operacji. Aby zakodować rejestr ogólnego przeznaczenia (Integer), to mapowanie jest używane:

|||
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|od 8 do 15|R8 do R15|

### <a name="chained-unwind-info-structures"></a>Struktury informacji z łańcucha operacji unwind

Jeśli flaga UNW_FLAG_CHAININFO jest ustawiona, to struktura informacji o elemencie unwind jest pomocniczą, a pole udostępniony program obsługi wyjątków/połączone z informacjami zawiera podstawowe informacje o rozwinięcia. Ten przykładowy kod pobiera podstawowe informacje o rozwinięcia, przy założeniu, że `unwindInfo` jest strukturą, która ma ustawioną flagę UNW_FLAG_CHAININFO.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Informacje łańcuchowe są przydatne w dwóch sytuacjach. Po pierwsze, może być używany dla nieciągłych segmentów kodu. Korzystając z informacji łańcucha, można zmniejszyć rozmiar wymaganych informacji o rozwinięcia, ponieważ nie jest konieczne duplikowanie tablicy kodów operacji unwind z podstawowych informacji o stanie unwind.

Możesz również użyć łańcucha informacji do rejestrowania nietrwałej grupy. Kompilator może opóźnić zapisywanie niektórych nietrwałych rejestrów do momentu, gdy nie znajduje się poza funkcją prologu wejścia funkcji. Można je zarejestrować, mając podstawowe informacje o nieprzetworzonym fragmencie dla części funkcji przed zgrupowanym kodem, a następnie konfigurując informacje łańcucha z niezerowym rozmiarem prologu, gdzie kody unwind w łańcuchowych informacjach odzwierciedlają zapisywanie nietrwałych rejestrów. W takim przypadku kody unwind są wszystkie wystąpieniami UWOP_SAVE_NONVOL. Grupowanie, które zapisuje nietrwałe rejestry przy użyciu WYPYCHANia lub modyfikuje rejestr RSP przy użyciu dodatkowej alokacji o stałym stosie nie jest obsługiwane.

Element UNWIND_INFO, który ma zestaw UNW_FLAG_CHAININFO, może zawierać RUNTIME_FUNCTION wpis, którego element UNWIND_INFO ma również zestaw UNW_FLAG_CHAININFO, który jest czasami nazywany *wielokrotnym zawijaniem*. Ostatecznie wskaźniki informacji o nieprzetworzonym elemencie unwindy docierają do UNWIND_INFO elementu, który został UNW_FLAG_CHAININFO wyczyszczony. Ten element jest elementem głównym UNWIND_INFO, który wskazuje rzeczywisty punkt wejścia procedury.

## <a name="unwind-procedure"></a>Procedura unwind

Tablica kodu unwind jest posortowana w kolejności malejącej. Gdy wystąpi wyjątek, kompletny kontekst jest przechowywany przez system operacyjny w rekordzie kontekstu. Następnie wywoływana jest logika wysyłania wyjątku, która wielokrotnie wykonuje następujące kroki, aby znaleźć program obsługi wyjątków:

1. Użyj bieżącego protokołu RIP przechowywanego w rekordzie kontekstu, aby wyszukać RUNTIME_FUNCTION wpis w tabeli opisujący bieżącą funkcję (lub część funkcji dla wpisów z łańcuchem UNWIND_INFO).

1. Jeśli nie zostanie znaleziony żaden wpis tabeli funkcji, jest on w funkcji liścia, a żądanie RSP bezpośrednio odnosi się do zwracanego wskaźnika. Wskaźnik powrotu z [RSP] jest przechowywany w zaktualizowanym kontekście, symulowane żądanie RSP jest zwiększane o 8, a krok 1 jest powtarzany.

1. Jeśli zostanie znaleziony wpis tabeli funkcji, RIP może znajdować się w trzech regionach: a) w epilogu, b) w prologu lub c) w kodzie, który może być objęty programem obsługi wyjątków.

   - Przypadek a) Jeśli protokół RIP znajduje się w epilogu, a następnie kontrolka opuszcza funkcję, nie może istnieć procedura obsługi wyjątków skojarzona z tym wyjątkiem dla tej funkcji, a efekty epilogu muszą być kontynuowane w celu obliczenia kontekstu funkcji wywołującej. Aby określić, czy protokół RIP znajduje się w epilogu, badany jest strumień kodu z protokołu RIP z lewej. Jeśli strumień kodu można dopasować do końcowej części legalnej epilogu, to jest w epilogu, a pozostała część epilogu jest symulowana, a rekord kontekstu zaktualizowany w miarę przetwarzania każdej instrukcji. Po wykonaniu tego procesu krok 1 zostanie powtórzony.

   - Przypadek b) Jeśli protokół RIP znajduje się w prologu, a następnie kontrolka nie została wprowadzona do funkcji, nie może istnieć procedura obsługi wyjątków skojarzona z tym wyjątkiem dla tej funkcji, a efekty prologu muszą zostać cofnięte w celu obliczenia kontekstu funkcji wywołującej. Wartość RIP jest w prologu, jeśli odległość od funkcji zaczyna się na wartość RIP jest mniejsza niż lub równa rozmiarowi prologu zakodowanemu w informacjach o rozwinięcia. Efekty prologu są rozwiązane przez skanowanie w przód przez tablicę kodów unwind dla pierwszego wpisu z przesunięciem, które jest mniejsze niż lub równe przesunięciu protokołu RIP od początku funkcji, a następnie cofa efekt wszystkich pozostałych elementów w tablicy kodu unwind. Krok 1 jest następnie powtarzany.

   - Przypadek c) Jeśli protokół RIP nie znajduje się w prologu lub epilogu, a funkcja ma procedurę obsługi wyjątków (UNW_FLAG_EHANDLER jest ustawiona), to program obsługi specyficzny dla języka jest wywoływany. Program obsługi skanuje swoje dane i wywołuje odpowiednio funkcje filtrów. Program obsługi specyficzny dla języka może zwrócić, że wyjątek został obsłużony, lub że wyszukiwanie ma być kontynuowane. Może również inicjować odwinięcie bezpośrednio.

1. Jeśli program obsługi specyficzny dla języka zwraca stan obsłużony, wykonywanie jest kontynuowane przy użyciu oryginalnego rekordu kontekstu.

1. Jeśli nie ma procedury obsługi specyficznej dla języka lub procedura obsługi zwróci stan "Kontynuuj wyszukiwanie", rekord kontekstu musi być odwracany do stanu obiektu wywołującego. Jest to wykonywane przez przetwarzanie wszystkich elementów tablicy kodu unwind, cofając efekt każdego z nich. Krok 1 jest następnie powtarzany.

W przypadku powiązanych z nimi informacji o nieprzetworzonym czasie te podstawowe kroki są nadal wykonywane. Jedyną różnicą jest to, że podczas podzielenia tablicy kodu unwind w celu odwinięcia efektów prologu, po osiągnięciu końca tablicy, zostanie ona połączona z nadrzędnymi informacjami o oddziałach i zostanie wyświetlona cała tablica kodu operacji unwind. To łączenie jest kontynuowane, dopóki nie zostanie osiągnięta informacja o rozwinięcia bez flagi UNW_CHAINED_INFO, a następnie zostanie osiągnięta.

Najmniejszy zbiór danych unwindy to 8 bajtów. Może to oznaczać funkcję, która przydzieliła tylko 128 bajtów stosu lub mniej, i prawdopodobnie zapisała jeden nietrwały rejestr. Jest to również rozmiar połączonej struktury danych unwind dla prologu o zerowej długości bez kodów operacji unwind.

## <a name="language-specific-handler"></a>Obsługa specyficzna dla języka

Adres względny programu obsługi specyficzny dla języka znajduje się w UNWIND_INFO przy każdym ustawieniu flag UNW_FLAG_EHANDLER lub UNW_FLAG_UHANDLER. Zgodnie z opisem w poprzedniej sekcji program obsługi specyficzny dla języka jest wywoływany jako część wyszukiwania programu obsługi wyjątków lub jako część elementu unwind. Ma ten prototyp:

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** dostarcza wskaźnik do rekordu wyjątku, który ma standardową definicję Win64.

**EstablisherFrame** jest adresem podstawy stałego przydziału stosu dla tej funkcji.

**ContextRecord** wskazuje kontekst wyjątku w chwili, gdy wyjątek został zgłoszony (w przypadku obsługi wyjątku) lub bieżącego kontekstu "unwind" (w przypadku programu obsługi zakończenia).

**DispatcherContext** wskazuje kontekst dyspozytora dla tej funkcji. Ma tę definicję:

```cpp
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc** jest wartością protokołu RIP w tej funkcji. Ta wartość to adres wyjątku lub adres, pod którym formant opuścił funkcję ustanawiającą. Protokół RIP służy do określenia, czy formant znajduje się w pewnej chronionej konstrukcji wewnątrz tej funkcji, na przykład blok `__try` dla `__try`/`__except` lub `__try`/`__finally`.

**ImageBase** to podstawowy obraz (adres ładowania) modułu zawierającego tę funkcję, który ma zostać dodany do 32-bitowych przesunięć użytych we wpisie funkcji i w informacjach o rozwinięcia, aby zarejestrować adresy względne.

**FunctionEntry** dostarcza wskaźnik do wpisu funkcji RUNTIME_FUNCTION, w którym znajduje się funkcja i informacje o niezaszyfrowanym obrazie względnych adresów dla tej funkcji.

**EstablisherFrame** jest adresem podstawy stałego przydziału stosu dla tej funkcji.

**TargetIp** Dostarcza opcjonalne adresy instrukcji, które określają adres kontynuacji operacji unwind. Ten adres jest ignorowany, jeśli nie określono **EstablisherFrame** .

**ContextRecord** wskazuje kontekst wyjątku do użycia przez kod wysyłania/wywinięcia wyjątku systemu.

**LanguageHandler** wskazuje procedurę procedury obsługi języka specyficzną dla języka.

**HandlerData** wskazuje na dane obsługi dotyczące języka dla tej funkcji.

## <a name="unwind-helpers-for-masm"></a>Pomocnicy operacji unwind dla MASM

Aby można było napisać poprawne procedury asemblera, istnieje zestaw pseudo operacji, które mogą być używane równolegle z rzeczywistymi instrukcjami zestawu, aby utworzyć odpowiednie. pdata i. xdata. I istnieje zestaw makr, które zapewniają uproszczone korzystanie z pseudo operacji do najczęściej używanych.

### <a name="raw-pseudo-operations"></a>Nieprzetworzone operacje pseudoklasy

|Pseudo operacja|Opis|
|-|-|
|\[ramki procesu:*ehandler*]|Powoduje, że MASM wygenerował wpis tabeli funkcji w. pdata i informacje o rozwinięcia w. xdata dla zachowania funkcji unwind strukturalnych obsługującego wyjątek strukturalny.  Jeśli *ehandler* jest obecny, ten proces jest wprowadzany w. xdata jako program obsługi specyficzny dla języka.<br /><br /> Gdy atrybut FRAME jest używany, musi następować po nim. ENDPROLOG.  Jeśli funkcja jest funkcją liścia (zgodnie z definicją w [typach funkcji](../build/stack-usage.md#function-types)), atrybut ramki jest zbędny, co jest pozostałą częścią tych pseudo operacji.|
|. *Rejestr* PUSHREG|Generuje UWOP_PUSH_NONVOL wpis kodu unwind dla określonego numeru rejestru przy użyciu bieżącego przesunięcia w prologu.<br /><br /> Używać go tylko z rejestrami nietrwałych liczb całkowitych.  W przypadku wypchnięcia rejestrów nietrwałych należy użyć. ALLOCSTACK 8 zamiast tego|
|. SETFRAME — *rejestracja*, *przesunięcie*|Wypełnia pole rejestr ramki i przesunięcia w informacjach o rozwinięcia przy użyciu określonego rejestru i przesunięcia. Przesunięcie musi być wielokrotnością 16 i mniejszą lub równą 240. Ta dyrektywa generuje również UWOP_SET_FPREG wpis kodu unwind dla określonego rejestru przy użyciu bieżącego przesunięcia prologu.|
|. *Rozmiar* ALLOCSTACK|Generuje UWOP_ALLOC_SMALL lub UWOP_ALLOC_LARGE o określonym rozmiarze dla bieżącego przesunięcia w prologu.<br /><br /> Operand *rozmiaru* musi być wielokrotnością liczby 8.|
|. *Rejestr*SAVEREG, *przesunięcie*|Generuje UWOP_SAVE_NONVOL lub UWOP_SAVE_NONVOL_FAR wpis kodu unwind dla określonego rejestru i przesunięcia przy użyciu bieżącego przesunięcia prologu. MASM wybiera najbardziej wydajne kodowanie.<br /><br /> *przesunięcie* musi być dodatnie i wielokrotnością 8. *przesunięcie* jest względne względem podstawy ramki procedury, która zwykle znajduje się w RSP lub, jeśli jest używany wskaźnik ramki, wskaźnik nieskalowanej ramki.|
|. *Rejestr*SAVEXMM128, *przesunięcie*|Generuje UWOP_SAVE_XMM128 lub UWOP_SAVE_XMM128_FAR wpis kodu unwind dla określonego rejestru XMM i przesunięcia przy użyciu bieżącego przesunięcia prologu. MASM wybiera najbardziej wydajne kodowanie.<br /><br /> *przesunięcie* musi być dodatnie i wielokrotnością 16.  *przesunięcie* jest względne względem podstawy ramki procedury, która zwykle znajduje się w RSP lub, jeśli jest używany wskaźnik ramki, wskaźnik nieskalowanej ramki.|
|. PUSHFRAME \[*kod*]|Generuje wpis kodu unwind UWOP_PUSH_MACHFRAME. W przypadku określenia opcjonalnego *kodu* , wpis kodu unwind jest przyznany jako modyfikator 1. W przeciwnym razie modyfikator jest równy 0.|
|.ENDPROLOG|Sygnalizuje koniec deklaracji prologu.  Musi wystąpić w pierwszych 255 bajtach funkcji.|

Oto przykładowa funkcja prologu z prawidłowym użyciem większości kodów operacji:

```MASM
sample PROC FRAME
    db      048h; emit a REX prefix, to enable hot-patching
    push rbp
    .pushreg rbp
    sub rsp, 040h
    .allocstack 040h
    lea rbp, [rsp+020h]
    .setframe rbp, 020h
    movdqa [rbp], xmm7
    .savexmm128 xmm7, 020h ;the offset is from the base of the frame
                           ;not the scaled offset of the frame
    mov [rbp+018h], rsi
    .savereg rsi, 038h
    mov [rsp+010h], rdi
    .savereg rdi, 010h ; you can still use RSP as the base of the frame
                       ; or any other register you choose
    .endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn't have a frame pointer, this would be illegal
; if we didn't make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren't saved with a push
; this isn't part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here's the official epilog

    lea rsp, [rbp+020h] ; deallocate both fixed and dynamic portions of the frame
    pop rbp
    ret
sample ENDP
```

Aby uzyskać więcej informacji na temat przykładu epilogu, zobacz [epilogu Code](prolog-and-epilog.md#epilog-code) in [x64 Prolog i epilogu](prolog-and-epilog.md).

### <a name="masm-macros"></a>Makra MASM

Aby uprościć korzystanie z [nieprzetworzonych pseudo operacji](#raw-pseudo-operations), istnieje zestaw makr zdefiniowanych w ksamd64. Inc, który może służyć do tworzenia typowych procedur prologues i epilogues.

|Macro|Opis|
|-|-|
|alloc_stack (n)|Przypisuje ramkę stosu o n bajtach (przy użyciu `sub rsp, n`) i emituje odpowiednie informacje dotyczące operacji unwind (. ALLOCSTACK n)|
|save_reg *reg*, *Loc*|Zapisuje nietrwały rejestr *rejestru na stosie w witrynie* RSP offset *Loc*i emituje odpowiednie informacje o rozwinięcia. (. SAVEREG reg, Loc)|
|push_reg *reg*|Wypchnij nietrwały rejestr *rejestru na* stosie i emituje odpowiednie informacje o rozwinięcia. (. pushreg reg)|
|rex_push_reg *reg*|Zapisuje nietrwały rejestr na stosie przy użyciu wypychania 2-bajtowego i emituje odpowiednie informacje o rozwinięcia (. pushreg reg).  Użyj tego makra, jeśli wypychanie jest pierwszą instrukcją w funkcji, aby upewnić się, że funkcja jest w pełni funkcjonalna.|
|save_xmm128 *reg*, *Loc*|Zapisuje element *reg* unvolatile XMM Register na stosie w witrynie RSP offset *Loc*i emituje odpowiednie informacje dotyczące operacji unwind (. SAVEXMM128 reg, Loc)|
|set_frame *reg*, *przesunięcie*|Ustawia rejestr ramek *reg* w taki sposób, aby był to żądanie rsp + *offset* (przy użyciu `mov`lub `lea`) i emituje odpowiednie informacje o rozwinięcia (. set_frame reg, offset)|
|push_eflags|Wypchnięcie EFLAGS z instrukcją `pushfq` i emituje odpowiednie informacje o rozwinięcia (. alloc_stack 8)|

Oto przykładowa funkcja prologu z prawidłowym użyciem makr:

```MASM
sampleFrame struct
    Fill     dq ?; fill to 8 mod 16
    SavedRdi dq ?; Saved Register RDI
    SavedRsi dq ?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here's the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>Definicje danych unwind w języku C

Oto opis w języku C dla danych unwind:

```C
typedef enum _UNWIND_OP_CODES {
    UWOP_PUSH_NONVOL = 0, /* info == register number */
    UWOP_ALLOC_LARGE,     /* no info, alloc size in next 2 slots */
    UWOP_ALLOC_SMALL,     /* info == size of allocation / 8 - 1 */
    UWOP_SET_FPREG,       /* no info, FP = RSP + UNWIND_INFO.FPRegOffset*16 */
    UWOP_SAVE_NONVOL,     /* info == register number, offset in next slot */
    UWOP_SAVE_NONVOL_FAR, /* info == register number, offset in next 2 slots */
    UWOP_SAVE_XMM128 = 8, /* info == XMM reg number, offset in next slot */
    UWOP_SAVE_XMM128_FAR, /* info == XMM reg number, offset in next 2 slots */
    UWOP_PUSH_MACHFRAME   /* info == 0: no error-code, 1: error-code */
} UNWIND_CODE_OPS;

typedef union _UNWIND_CODE {
    struct {
        UBYTE CodeOffset;
        UBYTE UnwindOp : 4;
        UBYTE OpInfo   : 4;
    };
    USHORT FrameOffset;
} UNWIND_CODE, *PUNWIND_CODE;

#define UNW_FLAG_EHANDLER  0x01
#define UNW_FLAG_UHANDLER  0x02
#define UNW_FLAG_CHAININFO 0x04

typedef struct _UNWIND_INFO {
    UBYTE Version       : 3;
    UBYTE Flags         : 5;
    UBYTE SizeOfProlog;
    UBYTE CountOfCodes;
    UBYTE FrameRegister : 4;
    UBYTE FrameOffset   : 4;
    UNWIND_CODE UnwindCode[1];
/*  UNWIND_CODE MoreUnwindCode[((CountOfCodes + 1) & ~1) - 1];
*   union {
*       OPTIONAL ULONG ExceptionHandler;
*       OPTIONAL ULONG FunctionEntry;
*   };
*   OPTIONAL ULONG ExceptionData[]; */
} UNWIND_INFO, *PUNWIND_INFO;

typedef struct _RUNTIME_FUNCTION {
    ULONG BeginAddress;
    ULONG EndAddress;
    ULONG UnwindData;
} RUNTIME_FUNCTION, *PRUNTIME_FUNCTION;

#define GetUnwindCodeEntry(info, index) \
    ((info)->UnwindCode[index])

#define GetLanguageSpecificDataPtr(info) \
    ((PVOID)&GetUnwindCodeEntry((info),((info)->CountOfCodes + 1) & ~1))

#define GetExceptionHandler(base, info) \
    ((PEXCEPTION_HANDLER)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetChainedFunctionEntry(base, info) \
    ((PRUNTIME_FUNCTION)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetExceptionDataPtr(info) \
    ((PVOID)((PULONG)GetLanguageSpecificData(info) + 1)
```

## <a name="see-also"></a>Zobacz także

[Konwencje kodowania x64](../build/x64-software-conventions.md)
