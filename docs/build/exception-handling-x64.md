---
title: x64 obsługi wyjątków
ms.date: 12/17/2018
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 33206dfb885239839c3a64436b6b540fc7d4e6e5
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627543"
---
# <a name="x64-exception-handling"></a>x64 obsługi wyjątków

Omówienie obsługi wyjątków strukturalnych i obsługa wyjątków języka C++, Konwencji i zachowanie w x64 kodowania. Aby uzyskać ogólne informacje na temat obsługi wyjątków, zobacz [obsługi wyjątków w języku Visual C++](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Operacja unwind dane dotyczące obsługi wyjątków, obsługa debugera

Kilka struktury danych są wymagane dla wyjątków, obsługa i obsługi debugowania.

### <a name="struct-runtimefunction"></a>struktura RUNTIME_FUNCTION

Obsługa wyjątków na podstawie tabeli wymaga wpisu tabeli dla wszystkich funkcji, które alokacji stosu lub wywołać inną funkcję (na przykład funkcje niebędącym elementem typu liść). Funkcja wpisów tabeli mają format:

|||
|-|-|
|ULONG|Adres początkowy — funkcja|
|ULONG|Adres końcowy — funkcja|
|ULONG|Operacja unwind info adresu|

Struktura RUNTIME_FUNCTION muszą być wyrównane w pamięci typu DWORD. Wszystkie adresy są względne obrazu, oznacza to, że są one 32-bitowe przesunięcia od adres początkowy obrazu, który zawiera wpis tabeli funkcji. Te wpisy są sortowane i umieścić w sekcji .pdata obrazu je typu PE32 +. Dla funkcji dynamicznie generowanym [JIT kompilatory] środowisko uruchomieniowe do obsługi tych funkcji, należy użyć RtlInstallFunctionTableCallback lub RtlAddFunctionTable może przekazać tę informację do systemu operacyjnego. Niewykonanie tej czynności spowoduje zawodnych wyjątków, obsługa i debugowanie procesów.

### <a name="struct-unwindinfo"></a>struktura UNWIND_INFO

Struktury informacji o danych unwind jest używana do rejestrowania efekty, które funkcja ma na wskaźnik stosu i gdzie nieulotnej rejestrów są zapisywane na stos:

|||
|-|-|
|UBYTE: 3|Wersja|
|UBYTE: 5|Flagi|
|UBYTE|Rozmiar prologu|
|UBYTE|Liczba kodów unwind|
|UBYTE: 4|Zarejestruj się ramki|
|UBYTE: 4|Przesunięcie rejestru ramki (skalowanie)|
|USHORT \* n|Operacja unwind kody tablicy|
|zmienna|Formularz (1) lub (2) poniżej albo być|

(1) Obsługa wyjątków

|||
|-|-|
|ULONG|Adres obsługi wyjątków|
|zmienna|Obsługa określonego języka danych (opcjonalnie)|

(2) łańcuchowej Unwind Info

|||
|-|-|
|ULONG|Adres początkowy — funkcja|
|ULONG|Adres końcowy — funkcja|
|ULONG|Operacja unwind info adresu|

Struktura UNWIND_INFO muszą być wyrównane w pamięci typu DWORD. Oto, co oznacza każdego pola:

- **Wersja**

   Numer wersji dane odwinięcia aktualnie 1.

- **flagi**

   Trzy flagi są obecnie zdefiniowane:

   |Flaga|Opis|
   |-|-|
   |`UNW_FLAG_EHANDLER`| Funkcja ma obsługi wyjątków, która powinna być wywoływana podczas wyszukiwania dla funkcji, które są konieczne przeanalizowanie wyjątków.|
   |`UNW_FLAG_UHANDLER`| Funkcja ma powinna być wywoływana, gdy odwijanie wyjątków programu obsługi zakończenia.|
   |`UNW_FLAG_CHAININFO`| To unwind info, że struktura nie jest to podstawowy dla procedury. Zamiast tego łańcuchowych elementu unwind info wpis jest zawartość poprzedniego zapisu RUNTIME_FUNCTION. Aby uzyskać informacje, zobacz [Chained unwind info struktury](#chained-unwind-info-structures). Jeśli ta flaga jest ustawiona, flagi UNW_FLAG_EHANDLER i UNW_FLAG_UHANDLER muszą zostać wyczyszczone. Ponadto ramki rejestr stosu stałej alokacji pola i musi mieć takie same wartości jak podstawowego elementu unwind info.|

- **Rozmiar prologu**

   Długość prologu funkcji w bajtach.

- **Liczba kodów unwind**

   Liczba miejsc, w tablicy kody unwind. Niektóre kodów, na przykład UWOP_SAVE_NONVOL odwinięcia wymagają więcej niż jednego miejsca, w tablicy.

- **Zarejestruj się ramki**

   Jeśli wartość jest niezerowa, następnie funkcja używa wskaźnik ramki (FP), a to pole jest to liczba nieulotnej rejestru używana jako wskaźnik ramki, przy użyciu tego samego kodowania dla pola informacje o operacji UNWIND_CODE węzłów.

- **Ramka zarejestrować przesunięcie (skalowanie)**

   Jeśli pole rejestru ramki jest różna od zera, to pole jest skalowany przesunięcie od RSP, która jest stosowana do FP zarejestrować po jego nawiązaniu. Rzeczywiste rejestr FP ustawiono RSP + 16 \* tę liczbę, dzięki czemu przesunięcia z zakresu od 0 do 240. Zezwala na to przesunięcie, wskazując rejestr FP do środka alokacji stosu lokalnego ramek stosu dynamiczne, umożliwiając lepsze gęstość kodu za pomocą krótszy instrukcje (więcej instrukcji użyć formularz przesunięcia podpisany 8-bitowa).

- **Operacja unwind kody tablicy**

   Tablica elementów opisano wpływ prologu nieulotnej rejestrów i RSP. Zobacz sekcję dotyczącą UNWIND_CODE na znaczenie wybranych elementów. Ze względów wyrównanie Ta tablica ma zawsze parzystą liczbą wpisów i końcowe wejścia jest potencjalnie nieużywane. W takim przypadku tablica jest jeden dłużej niż wskazywanym przez liczbę unwind kodów pola.

- **Adres obsługi wyjątków**

   Wskaźnik względem obrazu do funkcji wyjątków specyficzne dla języka lub UNW_FLAG_CHAININFO flaga jest wyczyszczona, jeśli ustawiono jeden flagi UNW_FLAG_EHANDLER lub UNW_FLAG_UHANDLER obsługi zakończenia.

- **Dane specyficzne dla języka programu obsługi**

   Funkcji specyficznych dla języka programu obsługi wyjątku. Format danych nie zostanie podany, całkowicie jest określana przez program obsługi określonego wyjątku w użyciu.

- **Łańcuchowej Unwind Info**

   Jeśli jest ustawiona flaga UNW_FLAG_CHAININFO struktura UNWIND_INFO kończy się z trzech UWORDs.  Te UWORDs reprezentują informacje RUNTIME_FUNCTION funkcji łańcuchowej unwind.

### <a name="struct-unwindcode"></a>struktura UNWIND_CODE

Tablica kodu odwijania jest używana do rejestrowania sekwencji operacji w prologu, na które wpływają na nieulotnej rejestrów i RSP. Każdy element kodu ma następujący format:

|||
|-|-|
|UBYTE|Przesunięcie w prologu|
|UBYTE: 4|Kod operacji unwind|
|UBYTE: 4|Informacje o operacji|

Tablica jest posortowana według malejącej przesunięcie w prologu.

#### <a name="offset-in-prolog"></a>Przesunięcie w prologu

Przesunięcie od początku prologu końca instrukcji, która wykonuje tę operację powiększoną o 1 (czyli Przesunięcie początku następnej instrukcji).

#### <a name="unwind-operation-code"></a>Kod operacji unwind

Uwaga: Niektóre kody operacji wymagają niepodpisane przesunięcie wartości w ramce stosu lokalnego. Jest to przesunięcie od początku, czyli najniższym adresem alokacji stosu stały. Jeśli pole zarejestrować ramki UNWIND_INFO wynosi zero, to przesunięcie pochodzi z RSP. Jeśli pole zarejestrować ramki jest różna od zera, to przesunięcie, z którym RSP znajdował się w przypadku rejestr FP zostało ustanowione. To jest równe rejestr FP minus przesunięcie rejestr FP (16 \* skalowanych ramki zarejestrować przesunięcie w UNWIND_INFO). Jeśli rejestr FP jest używany, następnie jakiegokolwiek kodu unwind biorąc przesunięcia może być używana tylko po nawiązaniu rejestr FP w prologu.

Dla wszystkich rozkazów z wyjątkiem `UWOP_SAVE_XMM128` i `UWOP_SAVE_XMM128_FAR`, przesunięcie jest zawsze wielokrotnością liczby 8, ponieważ wszystkie stosu interesujących wartości są przechowywane na 8-bajtowych granicach (stosu, sam jest zawsze 16-bajtowy wyrównane). Kody operacji, które przyjmują krótki przesunięcie (mniej niż 512K) końcowy USHORT w węzłach dla tego kodu przechowuje przesunięcie podzielić przez 8. Dla kodów operacji, które przyjmują długie przesunięcie (512 KB < = przesunięcie < 4GB), końcowy dwa węzły USHORT ten kod przechowywania przesunięcie (w formacie little-endian).

Aby uzyskać rozkazów `UWOP_SAVE_XMM128` i `UWOP_SAVE_XMM128_FAR`, przesunięcie jest zawsze wielokrotnością liczby 16, ponieważ wszystkie operacje XMM 128-bitowego musi przypadać na 16-bajtowy wyrównanej pamięci. W związku z tym, współczynnik skali 16 służy do `UWOP_SAVE_XMM128`, pozwalające przesunięcia mniej niż 1 mln.

Kod operacji odwijania jest jedną z następujących wartości:

- `UWOP_PUSH_NONVOL` (0) 1 węzeł

  Wypchnij nieulotnej całkowitoliczbowym, zmniejszanie RSP przez 8. Informacje o operacji są numer rejestru. Ze względu na ograniczenia dotyczące epilogs `UWOP_PUSH_NONVOL` kodów unwind musi występować jako pierwszy w prologu i odpowiednio ostatni w tablicy kodu unwind. Względne uporządkowanie ma zastosowanie do wszystkich innych kodów odwijania, z wyjątkiem `UWOP_PUSH_MACHFRAME`.

- `UWOP_ALLOC_LARGE` (1) 2 lub 3 węzłów

  Przydziel obszar o dużych rozmiarach na stosie. Istnieją dwie formy. Jeśli informacje o operacji jest równa 0, a następnie rozmiar alokacji podzielona przez 8 są rejestrowane w następnym gniazda, umożliwiając alokacji maksymalnie 512 K - 8. Jeśli informacje o operacji jest równa 1, a następnie nieskalowanego rozmiar alokacji jest rejestrowana w następnych dwóch miejsc w formacie little-endian, dzięki czemu alokacji do 4GB - 8.

- `UWOP_ALLOC_SMALL` (2) 1 węzeł

  Przydziel obszar małe na stosie. Rozmiar alokacji to pola informacje o operacji \* 8 + 8, dzięki czemu alokacje od 8 do 128.

  Kod unwind alokacji stosu zawsze należy używać w możliwie najkrótszym możliwe kodowanie:

  |**Rozmiar alokacji**|**Kodzie operacji unwind**|
  |-|-|
  |8 do 128 bajtów|`UWOP_ALLOC_SMALL`|
  |136 do 512-8 kilobajtów|`UWOP_ALLOC_LARGE`, informacje o operacji = 0|
  |512 KB do 4G - 8 bajtów|`UWOP_ALLOC_LARGE`, informacje o operacji = 1|

- `UWOP_SET_FPREG` (3) 1 węzeł

  Przez ustawienie rejestru na niektórych przesunięcie bieżącego RSP, należy ustanowić rejestr wskaźnika ramki. Przesunięcie jest równa zarejestrować ramki (skalowanych) pole przesunięcia UNWIND_INFO \* 16, dzięki czemu przesunięcia z zakresu od 0 do 240. Zezwala na użycie przesunięcie, ustanawiania wskaźnik ramki, który wskazuje na środku alokacji stosu stały, pomagając gęstość kodu, umożliwiając więcej uzyskuje dostęp do używania formularzy krótkich instrukcji. Pola informacje o operacji jest zarezerwowana i nie powinna być używana.

- `UWOP_SAVE_NONVOL` (4) 2 węzły

  Zapisz nieulotnej całkowitoliczbowym na stosie przy użyciu MOV zamiast powiadomienie WYPYCHANE. Ten kod jest używany głównie dla *shrink-wrapping*, gdzie nieulotnej rejestru są zapisywane na stos w stanie, która była przydzielona wcześniej. Informacje o operacji są numer rejestru. Przesunięcie skalowany przy 8 stosu są zapisywane w następnej operacji unwind miejsca kod operacji zgodnie z opisem w powyższej Uwaga.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 węzły

  Zapisz nieulotnej całkowitoliczbowym na stosie z przesunięciem długie, użycie MOV zamiast powiadomienie WYPYCHANE. Ten kod jest używany głównie dla *shrink-wrapping*, gdzie nieulotnej rejestru są zapisywane na stos w stanie, która była przydzielona wcześniej. Informacje o operacji są numer rejestru. Przesunięcie nieskalowanego stosu jest rejestrowana w ciągu następnych dwóch miejsc kod operacji unwind zgodnie z opisem w powyższej Uwaga.

- `UWOP_SAVE_XMM128` (8) węzłów 2

  Zapisz wszystkie 128 bitów nieulotnej, zarejestruj XMM na stosie. Informacje o operacji są numer rejestru. Przesunięcie stosu skalowany przy 16 są rejestrowane w gnieździe dalej.

- `UWOP_SAVE_XMM128_FAR` (9) 3 węzły

  Zapisz wszystkie 128 bitów nieulotnej, zarejestruj XMM na stosie z przesunięciem długie. Informacje o operacji są numer rejestru. Przesunięcie nieskalowanego stosu jest rejestrowana w dwóch następnych miejsc.

- `UWOP_PUSH_MACHFRAME` (10) 1 węzeł

  Wypchnij ramki maszyny.  Służy do rejestrowania efekt sprzętu, przerwania lub wyjątku. Istnieją dwie formy. Jeśli informacje o operacji jest równa 0, zostało wypchnięte jeden z tych ramek na stosie:

  |||
  |-|-|
  |RSP + 32|SS|
  |RSP + 24|Stary RSP|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|PROTOKÓŁ RIP|

  Jeśli informacje o operacji jest równa 1, następnie jedną z tych ramki zostało wypchnięte:

  |||
  |-|-|
  |RSP + 40|SS|
  |RSP + 32|Stary RSP|
  |RSP + 24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|PROTOKÓŁ RIP|
  |RSP|Kod błędu|

  Ten kod odwijania jest zawsze wyświetlany w prologu fikcyjnego z rolą, która faktycznie nigdy nie jest wykonywane, ale zamiast tego jest umieszczany przed punktu wejścia rzeczywistych procedury przerwań i istnieje tylko po to, aby zapewnić miejsce, aby zasymulować wypychania ramki maszyny. `UWOP_PUSH_MACHFRAME` rejestruje symulacji i wskazuje, że komputer ma pod względem koncepcyjnym przeprowadzane tej operacji:

  1. Adres zwrotny RIP z góry stosu do POP *Temp*
  
  1. Wypychanie SS

  1. Stary RSP wypychania

  1. Wypychanie EFLAGS

  1. CS wypychania

  1. Wypychanie *Temp*

  1. Wypychanie kodu błędu (Jeśli informacje o operacji jest równa 1)

  Symulowane `UWOP_PUSH_MACHFRAME` operacji zmniejsza RSP przez 40 (op informacji jest równa 0) lub 48 (op informacji jest równa 1).

#### <a name="operation-info"></a>Informacje o operacji

Znaczenie bitów informacje o operacji zależy od kodu operacji. Do zakodowania rejestru ogólnego przeznaczenia (liczba całkowita), to mapowanie jest używany:

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
|8-15|R8 do R15|

### <a name="chained-unwind-info-structures"></a>Łańcuchowej unwind info struktury

Jeśli ustawiono flagę UNW_FLAG_CHAININFO, strukturę unwind info ubocznym i pole udostępnionego adresu — Obsługa/łańcuchowa — informacje o wyjątku zawiera informacje unwind podstawowego. Ten przykładowy kod pobiera podstawowy unwind informacji, przy założeniu, że `unwindInfo` to struktura, która ma UNW_FLAG_CHAININFO Flaga.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Informacje łańcuchowych przydaje się w dwóch sytuacjach. Po pierwsze może służyć segmentów nieciągłego kodu. Za pomocą połączonych informacji, może zmniejszyć rozmiar informacji unwind wymagane, ponieważ nie masz zduplikowania tablica kody unwind info unwind podstawowego.

Informacje połączonych umożliwia również grupy zapisuje volatile rejestru. Kompilator może opóźnić zapisywania niektórych volatile rejestrów, dopóki nie znajduje się poza prologu wejścia funkcji. Można rejestrować to dzięki informacje unwind głównej części funkcji przed kodem pogrupowanych i konfigurując powiązane informacje o rozmiarze od zera prologu, gdzie kody łańcuchowych informacje z odwijania odzwierciedlają zapisuje nieulotnej rejestrów. W takim przypadku kody unwind są wszystkie wystąpienia elementu UWOP_SAVE_NONVOL. Grupa zapisuje nieulotnej rejestrów za pomocą instalacji WYPYCHANEJ lub modyfikuje rejestr RSP za pomocą alokacji dodatkowych, stałych stosu nie jest obsługiwane.

Element UNWIND_INFO UNW_FLAG_CHAININFO zestaw może zawierać wpis RUNTIME_FUNCTION, którego element UNWIND_INFO ma również UNW_FLAG_CHAININFO ustawiona, czasami nazywane *wielu shrink-wrapping*. Po pewnym czasie łańcuchowych elementu unwind info, wskaźniki przyjeździe do biura element UNWIND_INFO UNW_FLAG_CHAININFO wyczyszczone; jest to główny element UNWIND_INFO wskazuje punkt wejścia procedury rzeczywistych.

## <a name="unwind-procedure"></a>Procedura unwind

Tablica kodu odwijania jest posortowana w kolejności malejącej. Gdy wystąpi wyjątek, pełnego kontekstu są przechowywane przez system operacyjny w rekordu kontekstu. Następnie wywoływana jest logiki wysyłania wyjątków, które regularnie wykonuje następujące kroki, aby znaleźć obsługi wyjątków:

1. Użyj bieżącego RIP, przechowywane w rekordu kontekstu, aby wyszukać RUNTIME_FUNCTION wpis tabeli, który opisuje bieżącą funkcję (lub część funkcji, łańcuchowych wpisy UNWIND_INFO).

1. Jeśli zostanie znaleziony żaden wpis tabeli funkcji, będzie ona wówczas w funkcji liścia i RSP zwracany wskaźnik jest ukierunkowane bezpośrednio. Zwracany wskaźnik u [RSP] jest przechowywana w kontekście zaktualizowane symulowane RSP jest zwiększany o 8 i jest powtarzany w kroku 1.

1. Jeżeli wpis tabeli funkcji zostanie znaleziony, RIP może znajdować się w trzech regionach: () w epilogu, (b) w prologu lub c) w kodzie, który może być objętych przez program obsługi wyjątku.

   - Wielkości liter) czy RPO w ramach epilogu, a następnie sterowania opuszcza funkcji, może być nie skojarzonych z tym wyjątkiem, dla tej funkcji program obsługi wyjątków, a skutki epilogu musi być kontynuowana do obliczenia kontekście wywołujący funkcję. Aby określić, jeśli protokół RIP mieści się w epilogu strumienia kodu z RIP na jest sprawdzany pod. Jeśli tego strumienia kodu można dopasować do końcowej części epilogu uzasadnione, to znajduje się w epilogu i pozostałej części epilogu jest symulowane, przy użyciu rekordu kontekstu aktualizować wraz z każdą instrukcję przetwarzania. Po tym kroku 1 jest powtarzany.

   - Przypadku b) Jeśli RPO znajduje się w prologu, wówczas formantu nie wprowadzono funkcji, może być nie skojarzonych z tym wyjątkiem, dla tej funkcji program obsługi wyjątków, a skutki prologu muszą zostać cofnięte do obliczenia kontekście wywołujący funkcję. Protokół RIP znajduje się w prologu, jeśli odległość od początku funkcji RPO jest mniejsza niż lub równy rozmiarowi prologu zakodowane w informacji unwind. Efekty prologu są odwinięty do przodu skanowania przez tablicę kody unwind do pierwszej pozycji z przesunięciem mniejsze niż lub równe przesunięcia RPO od początku funkcji, a następnie cofnięcie efekt wszystkie pozostałe elementy w tablicy kodu unwind. Krok 1 jest następnie powtarzany.

   - Wielkość c), jeśli RPO nie znajduje się w prologu i epilogu i funkcji ma program obsługi wyjątku (UNW_FLAG_EHANDLER jest ustawiona), a następnie jest wywoływana procedura obsługi określonego języka. Program obsługi skanuje dane i wywołania filtrowania funkcji zgodnie z potrzebami. Obsługa określonego języka może zwrócić obsługiwania wyjątku lub wyszukiwanie jest kontynuowane. Go może również inicjować unwind bezpośrednio.

1. Jeśli program obsługi określonego języka zwraca obsługiwane stan, a następnie wykonywanie jest kontynuowane przy użyciu oryginalnego rekordu kontekstu.

1. Jeśli nie istnieje żadna procedura obsługi określonego języka lub program obsługi zwraca stan "Kontynuuj wyszukiwanie", rekordu kontekstu musi być rozwinięty do stanu obiektu wywołującego. Jest to realizowane przez wszystkie elementy tablicy unwind kodu, cofnięcie efektu każdej przetwarzanie. Krok 1 jest następnie powtarzany.

Gdy łańcuchowej unwind uczestniczy info, te proste kroki, nadal po nim. Jedyną różnicą jest to, że, gdy zalet tablicy kodu unwind na odpoczynek efekty prologu, po osiągnięciu końca tablicy, jego jest następnie łączony z informacji unwind nadrzędnego i zostaje przeprowadzony unwind całej tablicy kodu znalezione. To połączenie jest kontynuowany aż do otrzymywanych unwind info, bez flagi UNW_CHAINED_INFO, a następnie kończy zalet jego tablica kodu unwind.

Dane operacji unwind najmniejszy zestaw jest 8 bajtów. To reprezentuje funkcję, która tylko przydzielone 128 bajtów stosu lub mniej, a prawdopodobnie zapisywane jeden rejestr nieulotnej. Jest to również rozmiar łańcuchowych unwind info struktury prologu o zerowej długości z żadnych kodów unwind.

## <a name="language-specific-handler"></a>Obsługa określonego języka

Adres względny obsługi określonego języka jest obecny w UNWIND_INFO, zawsze wtedy, gdy ustawiono flagi UNW_FLAG_EHANDLER lub UNW_FLAG_UHANDLER. Zgodnie z opisem w poprzedniej sekcji, obsługi określonego języka jest wywoływana w ramach wyszukiwania dla obsługi wyjątków lub jako część unwind. Ma to prototypu:

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** dostarcza wskaźnik do rekordu wyjątku, który standardowej definicji Win64.

**EstablisherFrame** to adres podstawowy alokacji stosu stałą dla tej funkcji.

**ContextRecord** wskazuje kontekst wyjątku na czas (w przypadku obsługi wyjątku) został zgłoszony wyjątek lub bieżącego "Odwiń" kontekstu (w przypadku programu obsługi zakończenia).

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

**ControlPc** jest wartością RIP w ramach tej funkcji. Ta wartość jest adresem wyjątek lub adres, w którym formant pozostanie ustanowienia — funkcja. Protokół RIP służy do określenia, czy formant jest w ramach niektórych chroniona konstrukcja wewnątrz tej funkcji, na przykład `__try` zablokować na `__try` / `__except` lub `__try` / `__finally`.

**Dla właściwości ImageBase** jest obraz podstawowy (adres obciążenia) moduł zawierający tę funkcję, dodany do przesunięcia 32-bitowe używane we wpisie funkcji do elementu unwind info, aby zarejestrować względnych adresów.

**FunctionEntry** dostarcza wskaźnik RUNTIME_FUNCTION działać wpisu zawierający funkcję, a operacja unwind info obraz podstawowy względnych adresów dla tej funkcji.

**EstablisherFrame** to adres podstawowy alokacji stosu stałą dla tej funkcji.

**TargetIp** dostarcza adres instrukcji opcjonalne, który określa adres kontynuacji unwind. Ten adres jest ignorowana, jeśli **EstablisherFrame** nie zostanie określony.

**ContextRecord** wskazuje kontekst wyjątku, do użytku przez kod operacji unwind/wysyłania wyjątku systemu.

**LanguageHandler** wskazuje procedury obsługi języka specyficznego dla języka, które są wywoływane.

**HandlerData** punktów danych specyficznych dla języka programu obsługi dla tej funkcji.

## <a name="unwind-helpers-for-masm"></a>Pomocnicy operacji unwind dla MASM

Do napisania procedury prawidłowego zestawu ustawiono pseudo-operacje, które można równolegle z instrukcje montażu rzeczywiste tworzenie odpowiednich .pdata i .xdata. Istnieje również zestaw makra, które udostępniają uproszczone użycie pseudo-operacjami dotyczącymi ich najbardziej typowych zastosowań.

### <a name="raw-pseudo-operations"></a>Pierwotne operacje pseudo

|Operacja pseudo|Opis|
|-|-|
|RAMKA PROC \[:*ehandler*]|Powoduje, że MASM, można wygenerować funkcji tabeli wpis .pdata i unwind informacje zawarte w .xdata dla funkcji w strukturze wyjątków unwind zachowanie.  Jeśli *ehandler* jest obecny, ten proces został wprowadzony w .xdata jako procedura obsługi określonego języka.<br /><br /> Gdy atrybut ramki jest używany, należy wprowadzić znak. Dyrektywa ENDPROLOG.  Jeśli funkcja jest funkcją typu liść (zgodnie z definicją w [funkcji typy](../build/stack-usage.md#function-types)) atrybut ramki jest zbędne, ponieważ są w pozostałej części te pseudo operacje.|
|. PUSHREG *zarejestrować*|Generuje wpis UWOP_PUSH_NONVOL unwind kodu dla określonego rejestru numeru przy użyciu bieżącego przesunięcie w prologu.<br /><br /> Powinno to można używać tylko z rejestrów nieulotnej liczby całkowitej.  Wypchnięć volatile rejestrów, należy użyć. ALLOCSTACK 8, zamiast tego|
|. SETFRAME *zarejestrować*, *przesunięcia*|Wypełnienia w klatce zarejestrować pola i przesunięcie unwind informacje przy użyciu określonego rejestru i przesunięcia. Przesunięcie musi być wielokrotnością liczby 16 i mniejsza niż 240. Ta dyrektywa generuje również nazwę UWOP_SET_FPREG unwind kodu dla określonego rejestru za pomocą bieżące przesunięcie prologu.|
|. ALLOCSTACK *rozmiar*|Generuje UWOP_ALLOC_SMALL lub UWOP_ALLOC_LARGE o określonym rozmiarze, aby uzyskać bieżące przesunięcie w prologu.<br /><br /> *Rozmiar* operand musi być wielokrotnością liczby 8.|
|. SAVEREG *zarejestrować*, *przesunięcia*|Generuje UWOP_SAVE_NONVOL lub wpis UWOP_SAVE_NONVOL_FAR unwind kodu dla określonego rejestru i przesunięcia za pomocą bieżące przesunięcie prologu. MASM wybiera najbardziej efektywny sposób kodowania.<br /><br /> *Przesunięcie* musi być dodatnia i wielokrotność liczby 8. *Przesunięcie* względem base ramki procedury, która jest zwykle w RSP, lub, jeśli za pomocą wskaźnika ramki, wskaźnik ramki nieskalowanego.|
|. SAVEXMM128 *zarejestrować*, *przesunięcia*|Generuje UWOP_SAVE_XMM128 lub wpis UWOP_SAVE_XMM128_FAR unwind kodu dla określonego rejestru XMM i przesunięcia za pomocą bieżące przesunięcie prologu. MASM wybiera najbardziej efektywny sposób kodowania.<br /><br /> *Przesunięcie* musi być dodatnia i wielokrotnością liczby 16.  *Przesunięcie* względem base ramki procedury, która jest zwykle w RSP, lub, jeśli za pomocą wskaźnika ramki, wskaźnik ramki nieskalowanego.|
|. PUSHFRAME \[ *kodu*]|Generuje wpis UWOP_PUSH_MACHFRAME unwind kodu. Jeśli opcjonalny *kodu* zostanie określony, wpis kodu unwind modyfikujący 1. W przeciwnym razie modyfikator wynosi 0.|
|.ENDPROLOG|Sygnalizuje koniec deklaracje prologu.  Musi przypadać w pierwsze bajty 255 funkcji.|

Poniżej przedstawiono przykładowe prologu funkcji, z użyciem odpowiednich większości rozkazów:

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
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here’s the official epilog

    lea rsp, [rbp-020h]
    pop rbp
    ret
sample ENDP
```

### <a name="masm-macros"></a>Makra MASM

Aby uprościć używanie [pierwotne pseudo-operacje](#raw-pseudo-operations), ustawiono makra, zdefiniowane w ksamd64.inc, która może służyć do tworzenia Typowa procedura prologues i epilogues.

|Macro|Opis|
|-|-|
|alloc_stack(n)|Przydziela ramkę stosu w bajtach n (przy użyciu `sub rsp, n`) i emituje odpowiednie unwind informacji (.allocstack — n)|
|save_reg *reg*, *lokalizacja*|Zapisuje nieulotnej rejestru *reg* na stosie na RSP przesunięcie *loc*i emituje odpowiednie informacje o operacji unwind. (reg .savereg — lokalizacja)|
|push_reg *reg.*|Wypycha nieulotnej rejestru *reg* na stosie i emituje odpowiednie informacje o operacji unwind. (.pushreg — reg)|
|rex_push_reg *reg.*|Zapisz nieulotnej rejestru na stosie, za pomocą wypychania 2 bajtów, a następnie emituje odpowiednie informacje (.pushreg — reg), ta powinna być używana w przypadku wypychania pierwsza instrukcja w funkcji do upewnij się, że funkcja hot-patchable operacji unwind.|
|save_xmm128 *reg*, *lokalizacja*|Zapisuje nieulotnej rejestru XMM *reg* na stosie na RSP przesunięcie *loc*i emituje odpowiednie unwind informacji (reg .savexmm128 —, lokalizacja)|
|set_frame *reg*, *przesunięcia*|Ustawia rejestr ramki *reg* jako RSP + *przesunięcie* (przy użyciu `mov`, lub `lea`) i emituje odpowiednie unwind informacji (.set_frame reg, przesunięcie)|
|push_eflags|Wypycha eflags z `pushfq` instrukcji i emituje odpowiednie unwind informacji (.alloc_stack 8)|

Poniżej przedstawiono przykładowe prologu funkcji, z użyciem odpowiednich makr:

```MASM
SkFrame struct
    Fill    dq ?; fill to 8 mod 16
    SavedRdi dq ?; saved register RDI
    SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
    Filldq?; fill to 8 mod 16
    SavedRdidq?; Saved Register RDI
    SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>Definicje danych unwind w języku C

Poniżej przedstawiono opis C dane odwinięcia:

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

## <a name="see-also"></a>Zobacz też

[x64 konwencje kodowania](../build/x64-software-conventions.md)