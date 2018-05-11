---
title: Wskazówki dla deweloperów języka C++ rozważana kanałów po stronie wykonywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/03/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
author: mamillmsft
ms.author: mikeblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a7e7ddb51f07f7fe6be1da017d8feae9cc4919e
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Wskazówki dla deweloperów języka C++ rozważana kanałów po stronie wykonywania

Ten artykuł zawiera wskazówki dla deweloperów, co ułatwi zidentyfikowanie i zmniejszenia rozważana wykonywania po stronie kanał sprzętu luki w zabezpieczeniach oprogramowania C++. Te luki w zabezpieczeniach może ujawnić poufne informacje w granicach zaufania i może mieć wpływ na oprogramowanie, które działa na procesorów, które obsługują rozważana, poza kolejnością wykonywania instrukcji. Ta klasa luk w zabezpieczeniach pierwszy opisanego w styczniu, 2018 oraz dodatkowe i wskazówki można znaleźć w [biuletyn zabezpieczeń firmy Microsoft](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002).

Wskazówki podane w tym artykule jest powiązane z klasą luk w zabezpieczeniach reprezentowany przez CVE-2017-5753, znanej także jako wariant Spectre 1. Ta klasa luki w zabezpieczeniach sprzętu jest powiązany z kanałów po stronie, które mogą wystąpić z powodu wykonywania rozważana, który występuje w wyniku misprediction gałąź warunkowa. Kompilator Visual C++ w programie Visual Studio 2017 r (począwszy od wersji 15.5.5) obejmuje obsługę `/Qspectre` przełącznik udostępnia środki zaradcze kompilacji dla ograniczony zestaw wzorców kodowania potencjalnie narażone związane z CVE-2017-5753. W dokumentacji [/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) flagi zawiera więcej informacji na jego skutków i użycia. 

Dostępny wprowadzenie do wykonywania rozważana po stronie kanał luk w zabezpieczeniach znajdują się w prezentacji zatytułowany [przypadku Spectre i Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) przez jeden z zespołów badawczych, które wykryte tych problemów.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>Co to są luk w zabezpieczeniach sprzętu kanału po stronie wykonywania Speculative?

Nowoczesne procesory zapewniają wyższy stopień wydajności poprzez użycie rozważana i poza kolejnością wykonywania instrukcji. Na przykład często odbywa się przez element docelowy gałęzi (warunkowe i indrect), dzięki czemu może rozpocząć speculatively wykonywania instrukcji w celu przewidywane gałęzi, co umożliwia uniknięcie wstrzymania, aż do rzeczywistego gałęzi docelowej rozwiązane. W przypadku, gdy Procesor później wykryje, że misprediction wystąpił, wszystkie stan komputera, który został obliczony speculatively zostaną odrzucone. Dzięki temu, że nie ma żadnych skutków pod względem architektury widoczne przewidzianych spekulacji.

Podczas wykonywania rozważana nie ma wpływu na architecturaly widoczności, jego pozostaw śladów w stanie architektury, takich jak różnych pamięci podręcznych, które są używane przez procesor CPU. Jest tych śladów rozważana wykonywania, który może powodować powstanie luk w zabezpieczeniach kanału po stronie. Aby lepiej zrozumieć to, należy wziąć pod uwagę następującego fragmentu kodu, który stanowi przykład CVE 2017 5753 (granice Sprawdź obejście):

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

W tym przykładzie `ReadByte` jest buforu, rozmiar buforu i Indeks został dostarczony do tego buforu. Parametr indeks określony przez `untrusted_index`, jest dostarczana przez mniej uprzywilejowane kontekstu, takie jak proces innych niż administracyjne. Jeśli `untrusted_index` jest mniejsza niż `buffer_size`, a następnie znak w pozycji tego indeksu są odczytywane z `buffer` i używany do indeksu w udostępniony region pamięci odwołuje się `shared_buffer`.

Względem architektury, ta sekwencja kodu jest idealnie bezpieczne, ponieważ będzie gwarancji, że `untrusted_index` zawsze będzie mniejsza niż `buffer_size`. Jednak obecności rozważana wykonywania jest możliwe, że Procesor będzie mispredict gałąź warunkowa i wykonać treści, jeśli instrukcja nawet wtedy, gdy `untrusted_index` jest większa niż lub równa `buffer_size`. W wyniku tego Procesora może speculatively Odczytaj bajt from beyond granice `buffer` (która może być klucz tajny), a następnie użyj tej wartości bajtu do obliczenia adresu kolejnych obciążenia za pośrednictwem `shared_buffer`. 

Gdy Procesor wykryje ostatecznie to misprediction, pozostałe efekty uboczne może pozostać w pamięci podręcznej Procesora, które ujawnić informacje o wartości bajtów odczytanych poza granicami z `buffer`. Te efekty uboczne mogą być wykryte przez mniej uprzywilejowane kontekstu uruchomiona w systemie przez sondowanie jak szybko każda usługa pamięć podręczna wiersz w `shared_buffer` jest dostępny. Dostępne są następujące kroki, które można podjąć w tym celu:

1. **Wywołanie `ReadByte` wiele razy przy użyciu `untrusted_index` jest mniejsza niż `buffer_size`** . Kontekst zaatakowanego może spowodować kontekstu ofiara do wywołania `ReadByte` (np. za pomocą RPC) tak, by predykcyjne gałęzi jest uczenia się nie wykonywanej na `untrusted_index` jest mniejsza niż `buffer_size`.

2. **Flush wszystkie wiersze w pamięci podręcznej w `shared_buffer`** . Kontekst zaatakowanego musi opróżnienia wszystkich wierszy pamięci podręcznej w regionie udostępnionej pamięci odwołuje się `shared_buffer`. Ponieważ obszar pamięci jest udostępniony, jest proste, można wykonywać przy użyciu funkcji wewnętrznych, takich jak `_mm_clflush`.

3. **Wywołanie `ReadByte` z `untrusted_index` jest większa niż `buffer_size`** . Kontekst zaatakowanego powoduje, że kontekst ofiara do wywołania `ReadByte` tak, aby niepoprawnie prognozuje gałąź nie zostaną wykonane. Ta powoduje, że procesor speculatively wykonać treści, jeśli zablokowanie z `untrusted_index` jest większa niż `buffer_size`, w związku z tym prowadzących do liczbach odczytu z `buffer`. W rezultacie `shared_buffer` jest indeksowana przy użyciu potencjalnie poufną wartość, która została odczytana liczbach, powodując wiersza pamięci podręcznej odpowiednich być załadowana przez Procesor.

4. **Każdy wiersz pamięci podręcznej odczytu `shared_buffer` aby zobaczyć, która jest uzyskiwany dostęp do najbardziej szybko**. Kontekst zaatakowanego może odczytywać każdego wiersza pamięci podręcznej w `shared_buffer` i wykrywać wiersza pamięci podręcznej, który ładuje znacznie szybciej niż pozostałych. Jest to wiersza pamięci podręcznej, który może być wprowadzone kroku 3. Ponieważ między wartość i pamięci podręcznej wierszem bajtów w tym przykładzie relację 1:1, umożliwia osobie atakującej na wnioskowanie rzeczywistej wartości bajtów, który został odczytany liczbach.

Powyższe kroki podać przykład przy użyciu techniki nazywanej OPRÓŻNIANIA + ponownego ZAŁADOWANIA w połączeniu z wystąpienia CVE-2017-5753 wykorzystania.

## <a name="what-software-scenarios-can-be-impacted"></a>Może mieć wpływ na jakie scenariuszach oprogramowania?

Tworzenie bezpiecznego oprogramowania przy użyciu procedury jak [cyklu programistycznym zabezpieczeń](https://www.microsoft.com/en-us/sdl/) (SDL) wymaga zwykle deweloperzy do identyfikowania granice zaufania, które istnieją w aplikacjach. Granice zaufania istnieje w miejscach, w których aplikacja może współpracować z danymi dostarczonymi przez kontekst niższym poziomie zaufania, takich jak inny proces na komputerze lub proces użytkownika niebędącego administratorem tryb w przypadku sterownik urządzenia trybu jądra. Nowa klasa luk w zabezpieczeniach dotyczące wykonywania rozważana kanały po stronie ma zastosowanie do wielu granic zaufania w istniejących modeli zabezpieczeń oprogramowania, które izolować kodu i danych na urządzeniu.

Poniższa tabela zawiera podsumowanie modele zabezpieczeń oprogramowania, których deweloperzy musi zwracać uwagę na wystąpienia te luki w zabezpieczeniach:

|Granic zaufania|Opis|
|----------------|----------------|
|Granic maszyny wirtualnej|Aplikacje, które izolują obciążenia w oddzielnych maszyn wirtualnych, które odbieranie niezaufanych danych z innej maszyny wirtualnej może być zablokowana.|
|Granic jądra|Sterownika urządzenia trybu jądra, który odbiera dane niezaufane z procesem trybu użytkownika niebędącego administratorem może być zablokowana.|
|Granica procesu|Aplikacja odbiera niezaufanych danych z innego procesu uruchomionego na komputerze lokalnym za pomocą zdalnego wywoływania procedur (RPC), pamięci współużytkowanej lub innych komunikacji między procesem (IPC) mechanizmów może być zablokowana.|
|Enklawę granic|Aplikacja wykonuje w ramach bezpiecznego enklawę (na przykład Intel SGX), który recieves niezaufanych danych poza enklawę może być zagrożone.|
|Język granic|Aplikacja, która interpretuje lub just in Time (JIT) kompiluje i wykonuje niezaufany kod napisany w języku wyższego poziomu może być zablokowana.|

Aplikacje, które mają ataku widoczne dla każdego z powyższych ufać granic należy przejrzeć kod na powierzchni ataku na identyfikowanie i usuwanie wystąpień możliwych luk w zabezpieczeniach kanału rozważana wykonywania po stronie. Należy zauważyć, że granice zaufania na powierzchni ataku zdalnego, takich jak zdalny protokołów sieciowych, nie została uruchomiona zagrożenie do wykonywania rozważana po stronie kanał luk w zabezpieczeniach.

## <a name="potentially-vulnerable-coding-patterns"></a>Potencjalnie narażone wzorce programowania

Luki kanału po stronie rozważana wykonywania może wystąpić w wyniku wielu wzorców kodowania. Ta sekcja zawiera opis potencjalnie narażone wzorce programowania oraz przykłady dla każdego, ale uznaje, że zmiany w tych obszarach mogą istnieć. Tak deweloperzy zalecana do wykonania tych wzorców jako przykłady, a nie stanowi wyczerpującej listy wszystkich wzorców kodowania potencjalnie narażone.

Ogólnie rzecz biorąc misprediction związanych z warunkowych gałęzi kanały po stronie rozważana wykonywania może wystąpić, gdy wyrażenie warunkowe działa na danych, które mogą być kontrolowane lub wpływu na niższym poziomie zaufania kontekst. Na przykład może to obejmować wyrażenia warunkowe używane w `if`, `for`, `while`, `switch`, lub trójargumentowy instrukcje. Dla każdego z tych instrukcji kompilator może wygenerować gałąź warunkowa, który Procesor może następnie prognozowania obiektu docelowego gałęzi w czasie wykonywania.

W każdym przykładzie komentarz z frazy "SPEKULACJI bariery" zostanie wstawiony, gdzie deweloper może wprowadzić bariery jako środki zaradcze. Jest to omówiono bardziej szczegółowo w sekcji środki zaradcze.

### <a name="speculative-out-of-bounds-load"></a>Zdalne rozważana obciążenia

Ta kategoria kodowania wzorce obejmuje misprediction gałąź warunkowa, który prowadzi do rozważana liczbach dostęp do pamięci.

#### <a name="array-out-of-bounds-load-feeding-a-load"></a>Tablica liczbach załadować zasilania obciążenia

Ten wzorzec kodowania jest pierwotnie opisano narażone wzorzec kodowania CVE 2017 5753 (granice Sprawdź obejście). Tło części w tym artykule opisano tego wzorca szczegółowo.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

Podobnie tablicy liczbach obciążenia może wystąpić w połączeniu z pętli, która przekracza jego zakończenie warunku z powodu misprediction. W tym przykładzie gałąź warunkowa skojarzone z `x < buffer_size` wyrażenie może mispredict i speculatively wykonania treści `for` pętli, kiedy `x` jest większa niż lub równa `buffer_size`, w związku z tym rozważana co zdalne obciążenia.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

#### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Tablica liczbach obciążenia zasilania pośrednie gałęzi

Ten wzorzec kodowania obejmuje przypadek, w którym misprediction gałąź warunkowa może prowadzić do liczbach dostępu do tablicy wskaźników funkcji, które następnie prowadzi do pośredniego gałęzi do obiektu docelowego adresów, które zostały odczytane poza granicami. Poniższy fragment kodu zawiera przykład przedstawiający to. 

W tym przykładzie identyfikator wiadomości niezaufanych został dostarczony do DispatchMessage za pośrednictwem `untrusted_message_id` parametru. Jeśli `untrusted_message_id` jest mniejsza niż `MAX_MESSAGE_ID`, zostanie użyty do indeksowanie tablicy wskaźników funkcji i gałęzi do odpowiednie miejsce docelowe gałęzi. Ten kod jest bezpieczne pod względem architektury, ale jeśli Procesora źle przewidzianych gałęzi warunkowej, może spowodować `DispatchTable` indeksowany przez `untrusted_message_id` , gdy jego wartość jest większa niż lub równa `MAX_MESSAGE_ID`, w związku z tym prowadzących do liczbach dostępu. Może to spowodować wykonanie rozważana z adresu docelowego gałęzi pochodnego poza granice tablicy, która może spowodować ujawnienie informacji, w zależności od kodu, który jest wykonywany speculatively.

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    if (untrusted_message_id < MAX_MESSAGE_ID) {
        // SPECULATION BARRIER
        DispatchTable[untrusted_message_id](buffer, buffer_size);
    }
}
```

Zgodnie z przypadkiem tablicy liczbach załadować zasilania inny obciążenia, warunek ten również mogą powstać w połączeniu z pętli, która przekracza stanu zakończenia z powodu misprediction.

### <a name="speculative-type-confusion"></a>Typ rozważana pomyłek

Ta kategoria kodowania wzorce obejmuje misprediction gałąź warunkowa, który prowadzi do pomyłek rozważana typu. Wzorce programowania, w tej sekcji dotyczą zostanie przykładowy kod poniżej.

```cpp
enum TypeName {
    Type1,
    Type2
};

class CBaseType {
public:
    CBaseType(TypeName type) : type(type) {}
    TypeName type;
};

class CType1 : public CBaseType {
public:
    CType1() : CBaseType(Type1) {}
    char field1[256];
    unsigned char field2;
};

class CType2 : public CBaseType {
public:
    CType2() : CBaseType(Type2) {}
    void (*dispatch_routine)();
    unsigned char field2;
};

// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ProcessType(CBaseType *obj)
{
    if (obj->type == Type1) {
        // SPECULATION BARRIER
        CType1 *obj1 = static_cast<CType1 *>(obj);

        unsigned char value = obj1->field2;

        return shared_buffer[value * 4096];
    }
    else if (obj->type == Type2) {
        // SPECULATION BARRIER
        CType2 *obj2 = static_cast<CType2 *>(obj);

        obj2->dispatch_routine();

        return obj2->field2;
    }
}
```

#### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Rozważana typu pomyłek, co może prowadzić do liczbach obciążenia

Ten wzorzec kodowania obejmuje przypadek, w którym pomyłek rozważana typu może spowodować zdalne lub dostępu do pola pomylić typu, gdzie wartość załadować źródła adres kolejnych obciążenia. Jest to podobne do wzorca liczbach kodowania tablicy, ale jest on dyskowe widoczne za pośrednictwem zamiast kodowania sekwencji, jak pokazano powyżej. W tym przykładzie zaatakowanego kontekstu może spowodować ofiara Kontekst wykonywania `ProcessType` wiele razy przy użyciu typu obiektu `CType1` (`type` pole jest równa `Type1`). Ma to wpływu szkolenia gałąź warunkowa w pierwszym `if` instrukcji do prognozowania nie podjęte. Kontekst zaatakowanego następnie może spowodować ofiara Kontekst wykonywania `ProcessType` z obiektem typu `CType2`. Może to spowodować pomyłek rozważana typu Jeśli warunkowe gałęzi w pierwszym `if` instrukcji źle przewidzianych i wykonuje treści `if` instrukcji, w związku z tym rzutowanie obiektu typu `CType2` do `CType1`. Ponieważ `CType2` jest mniejszy niż `CType1`, dostęp do pamięci, aby `CType1::field2` spowodować rozważana liczbach załaduje danych, które mogą być tajny. Ta wartość jest następnie używana w przypadku obciążenia z `shard_buffer` której można utworzyć zauważalne efekty uboczne, podobnie jak w przypadku tablicy liczbach przykład opisanych powyżej.

#### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Typ rozważana pomyłek prowadzące do pośredniego gałęzi

Ta wzorce programowania obejmuje przypadek, w którym pomyłek rozważana typu może spowodować niebezpieczne gałęzi pośrednie podczas wykonywania rozważana. W tym przykładzie zaatakowanego kontekstu może spowodować ofiara Kontekst wykonywania `ProcessType` wiele razy przy użyciu typu obiektu `CType2` (`type` pole jest równa `Type2`). Ma to wpływu szkolenia gałąź warunkowa w pierwszym `if` instrukcji podejmowanych i `else if` instrukcji nie można zwrócić. Kontekst zaatakowanego następnie może spowodować ofiara Kontekst wykonywania `ProcessType` z obiektem typu `CType1`. Może to spowodować pomyłek rozważana typu Jeśli warunkowe gałęzi w pierwszym `if` prognozuje instrukcji podjęte i `else if` instrukcji prognozuje nie podejmowanych w związku z tym wykonywania treści `else if` i rzutowanie obiektu typu `CType1` do `CType2`. Ponieważ `CType2::dispatch_routine` nakłada się na pola `char` tablicy `CType1::field1`, może to spowodować rozważana gałęzi pośrednich do obiektu docelowego niezamierzone gałęzi. Kontekst zaatakowanego można sterować wartości bajtu `CType1::field1` tablicy, mogą one do sterowania adres docelowy oddziału.

## <a name="mitigation-options"></a>Środki zaradcze opcje

Luki kanału po stronie rozważana wykonywania można zminimalizować przez wprowadzania zmian w kodzie źródłowym. Te zmiany może obejmować zmniejszenia określonych wystąpień luka w zabezpieczeniach, takie jak dodanie *bariery spekulacji*, lub wprowadzając zmiany w projekcie aplikacji, aby wprowadzić poufne informacje niedostępne do rozważana wykonanie.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Bariera spekulacji za pomocą ręcznej Instrumentacji

A *bariery spekulacji* mogą być ręcznie wstawiane przez dewelopera, aby zapobiec wykonaniu rozważana z przejściem na ścieżce architektury. Na przykład deweloper można wstawić barierę spekulacji przed niebezpiecznych wzorzec kodowania w treści bloku warunkowego, albo na początku bloku (po gałąź warunkowa) lub przed pierwszym obciążenia, które potencjalnie. Uniemożliwi to misprediction gałąź warunkowa, wykonywanie niebezpieczny kod na ścieżce architektury przez wykonywania serializacji. Sekwencja bariery spekulacji różni się architektury zgodnie z opisem w poniższej tabeli:

|Architektura|Bariera spekulacji|
|----------------|----------------|
|x86/x64|_mm_lfence()|
|ARM|Nie jest obecnie dostępna|
|ARM64|Nie jest obecnie dostępna|


Na przykład, można zminimalizować następującego wzorca kodu za pomocą `_mm_lfence` wewnętrznych, jak pokazano poniżej.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        _mm_lfence();
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Bariera spekulacji za pomocą Instrumentacji czasu kompilatora

Kompilator Visual C++ w programie Visual Studio 2017 r (począwszy od wersji 15.5.5) obejmuje obsługę `/Qspectre` przełącznika, który automatycznie wstawia barierę spekulacji dla ograniczony zestaw wzorców kodowania potencjalnie narażone związane z 5753-CVE-2017 r. W dokumentacji [/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) flagi zawiera więcej informacji na jego skutków i użycia. Należy zauważyć, że ta flaga nie obejmuje wszystkich wzorców potencjalnie narażone kodowania i sposób deweloperzy nie polegać na niej jako kompleksowe ograniczenie dla tej klasy luk w zabezpieczeniach.

### <a name="removing-sensitive-information-from-memory"></a>Usuwanie poufnych danych z pamięci

Innej metody, która może służyć do ograniczenia luk kanału po stronie rozważana wykonywania jest usunięcie poufnych informacji z pamięci. Deweloperzy oprogramowania można wyszukać możliwości Refaktoryzuj ich aplikacji w taki sposób, że podczas wykonywania rozważana informacje poufne jest niedostępny. Można to zrobić przez refaktoryzacji projekt aplikacji do izolowania poufne informacje w osobnych procesach. Na przykład aplikacja przeglądarki sieci web mogą próbować izolować dane skojarzone z każdego miejsca pochodzenia sieci web w osobnych procesach, co uniemożliwia jeden proces mogli uzyskiwać dostęp do wykonywania rozważana między źródłami danych.

## <a name="see-also"></a>Zobacz też

[Wskazówki w celu ograniczenia wykonywania rozważana kanału po stronie luk w zabezpieczeniach](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)

[Zmniejszenia rozważana wykonywania po stronie kanał sprzętu luk w zabezpieczeniach](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
