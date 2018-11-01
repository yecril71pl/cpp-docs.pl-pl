---
title: Wskazówki dla deweloperów C++ spekulacyjnego kanałów po stronie wykonywania
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: 94e55f08e4ff427aef0c93bf74c711a6fd935d0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631043"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Wskazówki dla deweloperów C++ spekulacyjnego kanałów po stronie wykonywania

Ten artykuł zawiera wskazówki dla deweloperów, która pomaga w identyfikacji i ograniczanie ryzyka związanego z wykonywaniem spekulatywnym po stronie kanału sprzętowych luk w zabezpieczeniach oprogramowania C++. Te luki w zabezpieczeniach może ujawnić poufne informacje w granicach zaufania i może mieć wpływ na oprogramowanie, które jest uruchamiane na procesorach obsługujących spekulacyjnego, poza kolejnością wykonywania instrukcji. Ta klasa luk w zabezpieczeniach był pierwszy opisanego w stycznia 2018 r. i dodatkowych informacji uzupełniających i wskazówki można znaleźć w [biuletyn zabezpieczeń firmy Microsoft](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002).

Ze wskazówkami zawartymi w tym artykule dotyczy klasy reprezentowane przez luki w zabezpieczeniach:

1. CVE-2017-5753, znany także jako luki Spectre w wariancie 1. Ta klasa luk w zabezpieczeniach sprzętu jest powiązana z kanałów po stronie, które mogą wystąpić z powodu wykonywaniem spekulatywnym, który występuje w wyniku misprediction gałąź warunkowa. Kompilator języka Visual C++ w programie Visual Studio 2017 (począwszy od wersji 15.5.5) obejmuje obsługę `/Qspectre` przełącznika, który umożliwia ograniczenie kompilacji, dla ograniczonego zestawu schematów kodowania potencjalnie zagrożone związane z CVE-2017-5753. `/Qspectre` Przełącznik jest również dostępna w programie Visual Studio 2015 Update 3 za pomocą [KB 4338871](https://support.microsoft.com/help/4338871). W dokumentacji dotyczącej [/qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) flagi zawiera więcej informacji na jego skutków i użycia.

2. CVE-2018-3639, nazywana również [spekulacyjnego obejścia Store (SSB)](https://aka.ms/sescsrdssb). Ta klasa luk w zabezpieczeniach sprzętu jest powiązana z kanałów po stronie, które mogą wystąpić z powodu związanego z wykonywaniem spekulatywnym obciążenia wcześniej zależne magazynu wyniku misprediction dostępu do pamięci.

Dostępne wprowadzenie lukami kanału, wykonywaniem spekulatywnym po stronie znajdują się w prezentacji, pod tytułem [przypadek z krokami zaradczymi dla luki i Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) przez jeden z zespołów badawczych, odnalezionych tych problemów.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>Co to jest kanał po stronie wykonywania spekulacyjne sprzętowych luk w zabezpieczeniach?

Nowoczesnych procesorów zapewniają wyższy stopień wydajności, wprowadzając użytkowania spekulacyjnego i poza kolejnością wykonywania instrukcji. Na przykład często to osiągnąć przez prognozowania danych docelowych gałęzi (warunkowe i pośredniego), co umożliwia Procesora rozpocznie speculatively wykonywanie zgodnie z instrukcjami na cel rozgałęzienia przewidywane, unikając w ten sposób wstrzymania, aż do cel rozgałęzienia rzeczywiste rozwiązany. W przypadku, gdy procesor CPU później wykryje, że misprediction wystąpił, cały stan maszyny, która została obliczona speculatively jest odrzucany. Dzięki temu, że nie istnieją żadne pod względem architektury widoczne efekty mispredicted wstawiał.

Gdy związanego z wykonywaniem spekulatywnym nie ma wpływu na pod względem architektury widoczności, jej pozostaw śladów w stanie architektury, takie jak różne pamięci podręczne, które są używane przez procesor CPU. Jest tych śladów pozostałości z wykonywaniem spekulatywnym, który może powodować powstanie luk w zabezpieczeniach po stronie kanału. Aby lepiej zrozumieć to, należy wziąć pod uwagę następujący fragment kodu, który zawiera przykładowy CVE-2017-5753 (Obejdź sprawdzanie granic):

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

W tym przykładzie `ReadByte` jest dostarczony bufor, rozmiar buforu i indeksu do tego buforu. Jako określony przez parametr indeksu `untrusted_index`, jest dostarczana przez mniej uprzywilejowanego kontekstu, takich jak proces innych niż administracyjne. Jeśli `untrusted_index` jest mniejsza niż `buffer_size`, a następnie znak na pozycji indeksu są odczytywane z `buffer` i używany do indeksu w udostępnionym region pamięci określonych przez `shared_buffer`.

Z punktu widzenia architektury, ta sekwencja kodu jest idealnie bezpieczne, ponieważ ma żadnej gwarancji, że `untrusted_index` zawsze będzie mniejsza niż `buffer_size`. Jednak obecności związanego z wykonywaniem spekulatywnym, jest możliwe, że Procesor będzie złych przewidywań gałąź warunkowa i wykonania treści, jeśli instrukcja nawet wtedy, gdy `untrusted_index` jest większa niż lub równa `buffer_size`. W wyniku tego Procesora może speculatively Odczytaj bajt from beyond granice `buffer` (może być wpisu tajnego), a następnie użyj tej wartości bajtów do obliczania adresu kolejnych obciążenia za pomocą `shared_buffer`.

Gdy Procesora po pewnym czasie wykryje to misprediction, pozostałe efekty uboczne może pozostać w pamięci podręcznej Procesora, które ujawniają informacje o wartości bajtów odczytanych poza zakresem od `buffer`. Efekty uboczne, te mogą być wykryte przez mniej uprzywilejowanego kontekstu uruchomionych w systemie, jak szybko sondowanie linię każda usługa pamięć podręczna `shared_buffer` jest dostępny. Dostępne są następujące kroki, które mogą być wykonywane w tym celu:

1. **Wywoływanie `ReadByte` wiele razy z `untrusted_index` jest mniejsza niż `buffer_size`** . Zaatakowanego kontekst może spowodować, że kontekst ofiarą do wywołania `ReadByte` (np. przez RPC), w której jest predykcyjne gałęzi przeszkolony i nie traktowana jako `untrusted_index` jest mniejsza niż `buffer_size`.

2. **Opróżnij wszystkie wiersze w pamięci podręcznej w `shared_buffer`** . Kontekst zaatakowanego musi opróżnienia wszystkich wierszy pamięci podręcznej w udostępniony region pamięci określonych przez `shared_buffer`. Ponieważ regionu pamięci jest udostępniony, to jest proste i można osiągnąć przy użyciu funkcji wewnętrznych, takich jak `_mm_clflush`.

3. **Wywoływanie `ReadByte` z `untrusted_index` są większe niż `buffer_size`** . Kontekst zaatakowanego powoduje, że kontekst ofiarą do wywołania `ReadByte` taki sposób, że nieprawidłowo przewiduje, gałąź nie zostaną wykonane. Ta powoduje, że procesor speculatively wykonania treści czy zablokować za pomocą `untrusted_index` są większe niż `buffer_size`, dlatego wiodące na liczbach odczytu z `buffer`. W związku z tym `shared_buffer` jest indeksowane, za pomocą potencjalnie poufne wartość, która została odczytana w liczbach, powodując w ten sposób można załadować CPU linii odpowiedniej pamięci podręcznej.

4. **Przeczytaj każdy wiersz pamięci podręcznej w `shared_buffer` aby zobaczyć, który jest dostępny w najbardziej szybko**. Kontekst zaatakowanego może odczytywać każdy wiersz pamięci podręcznej w `shared_buffer` i wykryć wiersza pamięci podręcznej, który ładuje się znacznie szybciej niż pozostałe. Jest to wiersz pamięci podręcznej, który może być wprowadzone kroku 3. Ponieważ istnieje relacja 1:1 między wierszem wartość i pamięć podręczna bajtów w tym przykładzie, umożliwia osobie atakującej na wnioskowanie rzeczywistej wartości bajtów, które zostały odczytane w liczbach.

Powyższe kroki zawierają z przykładem użycia techniką OPRÓŻNIANIA + Załaduj ponownie w połączeniu z eksploatacji wystąpienie CVE-2017-5753.

## <a name="what-software-scenarios-can-be-impacted"></a>Może to mieć wpływ jaki scenariusz oprogramowania?

Tworzenie bezpiecznego oprogramowania za pomocą procesu, takich jak [cyklu projektowania zabezpieczeń](https://www.microsoft.com/sdl/) (SDL) zwykle wymaga deweloperom identyfikowanie granic zaufania, które istnieją w aplikacjach. Istnieje granicy zaufania w miejscach, w których aplikacja może współpracować z danych pochodzących z kontekstu niższym poziomie zaufania, takich jak innego procesu w systemie lub proces trybu użytkownika niebędącego administratorem w przypadku sterownik urządzenia trybu jądra. Nowa klasa luk w zabezpieczeniach dotyczące kanałów po stronie wykonywania spekulacyjnego ma zastosowanie do wielu granic zaufania w istniejących modeli zabezpieczeń oprogramowania, które izolowania kodu i danych na urządzeniu.

Poniższa tabela zawiera podsumowanie modele zabezpieczeń oprogramowania, których deweloperzy może być konieczne zwracać uwagę na te luki w zabezpieczeniach, występuje:

|Granica zaufania|Opis|
|----------------|----------------|
|Granica maszyny wirtualnej|Aplikacje, które izolowania obciążeń w osobne maszyny wirtualne, które odbierają niezaufanych danych z innej maszyny wirtualnej mogą być narażone na ryzyko.|
|Granica jądra|Sterownik urządzenia trybu jądra, który odbiera od proces trybu użytkownika niebędącego administratorem niezaufane dane mogą być narażone na ryzyko.|
|Granica procesu|Aplikacja, która odbiera niezaufane dane z innego procesu, uruchomiony w systemie lokalnym za pośrednictwem zdalnego wywoływania (procedur RPC), pamięci współużytkowanej lub innych komunikacji między procesu (IPC) mechanizmów mogą być narażone na ryzyko.|
|Granica enklawy|Aplikacja, która jest wykonywana w ramach enklawy bezpieczne (na przykład Intel SGX) odbierająca niezaufanych danych poza enklawy mogą być narażone na ryzyko.|
|Język granic|Aplikacja, który interpretuje lub just in Time (JIT) kompiluje i wykonuje z niezaufanego kodu napisanego w języku wyższego poziomu mogą być narażone na ryzyko.|

Aplikacje, które mają obszar narażony na ataki udostępniane do żadnej z powyższych ufać granice, należy przejrzeć kod na ataki, aby identyfikować i minimalizować możliwe wystąpienia związanego z wykonywaniem spekulatywnym po stronie kanału luk w zabezpieczeniach. Należy zauważyć, że granice zaufania połączenie zdalne attack surfaces takich jak protokoły sieciowe zdalnego nie został wykazały, zagrożenie lukami kanału, wykonywaniem spekulatywnym po stronie.

## <a name="potentially-vulnerable-coding-patterns"></a>Potencjalnie zagrożone schematów kodowania

Związanego z wykonywaniem spekulatywnym po stronie kanału luk w zabezpieczeniach może wystąpić w wyniku wiele schematów kodowania. W tej sekcji opisano potencjalnie zagrożone schematów kodowania i zawiera przykłady dla każdego, ale powinien był zostać rozpoznany, że zmiany na te tematy mogą istnieć. W efekcie deweloperom doradza się do wykonania tych wzorców jako przykłady, a nie stanowi wyczerpującej listy wszystkich schematów kodowania potencjalnie zagrożone. Tych samych klas pamięci bezpieczeństwa luk w zabezpieczeniach, które mogą istnieć w oprogramowaniu już dziś również mogą istnieć wzdłuż spekulacyjnego, a poza kolejnością ścieżki wykonywania, w tym między innymi na przepełnienia buforu liczbach tablicy uzyskuje dostęp do, użycie niezainicjowanej pamięci typu pomyłek i tak dalej. Tego samego podstawowych, które osoby atakujące mogą użyć wykorzystać luki bezpieczeństwa pamięci wzdłuż ścieżek architektury mogą dotyczyć także spekulacyjnego ścieżki.

Ogólnie rzecz biorąc związanego z wykonywaniem spekulatywnym po stronie Kanały związanych z warunkowych gałęzi misprediction mogą zostać zgłoszone podczas wyrażenia warunkowego operuje na danych, które mogą być kontrolowane lub zależeć od kontekstu z niższym poziomie zaufania. Na przykład, mogą to być używane w wyrażenia warunkowe `if`, `for`, `while`, `switch`, lub trójargumentowy instrukcji. Dla każdej z tych instrukcji kompilator może wygenerować gałąź warunkowa, który Procesor może następnie przewidzieć cel rozgałęzienia dla w czasie wykonywania.

W każdym przykładzie komentarz z frazę "WSTAWIAŁ BARIERĘ przewidywania" jest wstawiany gdy deweloper może wprowadzić barierę jako środki zaradcze. Zostało to omówione bardziej szczegółowo w sekcji środki zaradcze.

## <a name="speculative-out-of-bounds-load"></a>Ładowanie liczbach spekulacyjne

Ta kategoria wzorców obejmuje misprediction gałąź warunkowa, który prowadzi do spekulacyjnego liczbach dostęp do pamięci.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>Tablica liczbach obciążenia, wprowadzając obciążenia

Ten wzorzec kodowania jest narażony pierwotnie opisano wzorzec kodowania dla CVE-2017-5753 (Obejdź sprawdzanie granic). Tło części w tym artykule opisano tego wzorca szczegółowo.

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

Podobnie tablica liczbach obciążenia mogą wystąpić w połączeniu z pętlę, która przekracza jego zakończenie warunek z powodu misprediction. W tym przykładzie gałąź warunkowa skojarzone z `x < buffer_size` wyrażenie może złe przewidywania i speculatively wykonania treści `for` pętli, kiedy `x` jest większa niż lub równa `buffer_size`co w efekcie spekulacyjne liczbach obciążenia.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[x];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Tablica liczbach obciążenia, wprowadzając pośrednich gałęzi

Ten wzorzec pisania kodu obejmuje przypadek, w którym misprediction gałąź warunkowa może prowadzić do liczbach dostęp do tablicy wskaźników funkcji, które następnie prowadzi do pośredniego gałęzi do obiektu docelowego adresów, które zostały odczytane liczbach. Poniższy fragment kodu stanowi przykład demonstrujący ten.

W tym przykładzie został podany identyfikator niezaufanych wiadomości do DispatchMessage za pośrednictwem `untrusted_message_id` parametru. Jeśli `untrusted_message_id` jest mniejsza niż `MAX_MESSAGE_ID`, zostanie użyty do indeksowania do tablicy wskaźników funkcji i gałęzi do odpowiedniego cel rozgałęzienia. Ten kod jest bezpiecznym pod względem architektury, ale jeśli Procesora źle przewidzianych gałęzi warunkowej, może to spowodować `DispatchTable` indeksowane przez `untrusted_message_id` , gdy jej wartość jest większa niż lub równa `MAX_MESSAGE_ID`, dlatego prowadzących do liczbach dostępu. Może to spowodować związanego z wykonywaniem spekulatywnym z adresu docelowego gałęzi, który jest tworzony poza granice tablicy, która może prowadzić do ujawnienia informacji w zależności od kodu, który jest wykonywany speculatively.

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

Zgodnie z przypadkiem tablicy w liczbach załadować, wprowadzając inny obciążenia, warunek ten również mogą wystąpić w połączeniu z pętlę, która przekracza jego warunek kończący z powodu misprediction.

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>Tablica liczbach przechowywania, wprowadzając pośrednich gałęzi

Gdy w poprzednim przykładzie pokazano sposób spekulacyjnego liczbach obciążenia mogą mieć wpływ na obiekt docelowy gałęzi pośrednich, możliwe jest również dla liczbach przechowywania, aby zmodyfikować cel rozgałęzienia pośrednich, takich jak wskaźnika funkcji lub adres zwrotny. To może prowadzić do związanego z wykonywaniem spekulatywnym z adresu określona osoba atakująca.

W tym przykładzie jest przekazywana niezaufanych indeksu `untrusted_index` parametru. Jeśli `untrusted_index` jest mniejsza niż liczba elementów: `pointers` tablicy (256 elementy), a następnie wartość podany wskaźnik w `ptr` są zapisywane do `pointers` tablicy. Ten kod jest bezpiecznym pod względem architektury, ale jeśli Procesora źle przewidzianych gałęzi warunkowej, może to spowodować `ptr` speculatively zapisywana poza granice przydzielanych ze stosów `pointers` tablicy. Może to prowadzić do uszkodzenia spekulacyjnego adres zwrotny `WriteSlot`. Jeśli osoba atakująca może kontrolować wartość `ptr`, może być możliwości wywarcia związanego z wykonywaniem spekulatywnym z dowolnego adresu, gdy `WriteSlot` zwraca spekulacyjnego ścieżce.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

Podobnie jeśli funkcja wskaźnik zmiennej lokalnej o nazwie `func` została przydzielona na stosie, a następnie może być możliwe speculatively modyfikowanie adresu, `func` odnosi się do sytuacji misprediction gałąź warunkowa. Może to spowodować związanego z wykonywaniem spekulatywnym z dowolnego adresu po wywołaniu za pomocą wskaźnika funkcji.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    void (*func)() = &callback;
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
    func();
}
```

Należy zauważyć, że obu tych przykładach obejmują spekulacyjnego modyfikacji wskaźników przydzielanych ze stosów pośrednich gałęzi. Istnieje możliwość modyfikacji spekulacyjnego mógł także wystąpić dla zmiennych globalnych, pamięci przydzielony w stercie i nawet pamięci tylko do odczytu na niektórych procesorach. Dla pamięci przydzielonej przez stos kompilator języka Visual C++ ma już kroki, aby utrudnić speculatively zmodyfikować przydzielanych ze stosów pośrednich gałęzi docelowych, takich jak zmiana kolejności zmiennych lokalnych w taki sposób, że bufory są umieszczane obok plik cookie zabezpieczeń jako część [/GS](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check) kompilatora funkcji zabezpieczeń.

## <a name="speculative-type-confusion"></a>Błąd typu spekulacyjne

Ta kategoria zajmuje się wzorców, które powodują powstanie pomyłek spekulacyjnego typu kodowania. Dzieje się tak, jeśli pamięć uzyskuje się dostęp przy użyciu nieprawidłowy typ w ścieżce architektury podczas wykonywania spekulacyjnego. Gałąź warunkowa misprediction i obejścia spekulacyjnego magazynu potencjalnie może prowadzić do pomyłek spekulacyjnego typu.

Dla magazynu spekulacyjnego jednokrotnego obejścia to może wystąpić w scenariuszach, gdzie kompilator używa lokalizacji stosu dla zmiennych wielu typów. Jest to spowodowane architektury magazynu zmienną typu `A` mogą ominąć, dzięki czemu obciążenia typu `A` speculatively wykonać przed przypisaniem zmiennej. Jeśli poprzednio zapisanego zmienna jest innego typu, to można utworzyć warunków pomyłek spekulacyjnego typu.

W misprediction gałąź warunkowa poniższy fragment kodu będzie używany do opisania różnych warunków, które umożliwia niejasności spekulacyjnego typu, powoduje.

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

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Pomyłek spekulacyjnego typu, co prowadzi do liczbach obciążenia

Ten wzorzec pisania kodu obejmuje przypadek, gdzie może spowodować pomyłek spekulacyjnego typu liczbach lub dostęp do mylić typu pola, gdzie wartość załadować źródła danych adres kolejnych obciążenia. Jest to podobne do wzorca liczbach kodowania tablicy, ale jest on dyskowe widoczne za pośrednictwem zamiast kodowania sekwencji, jak pokazano powyżej. W tym przykładzie zaatakowanego kontekst może spowodować ofiarą Kontekst wykonywania `ProcessType` wiele razy z obiektem typu `CType1` (`type` pole jest równa `Type1`). Będzie to miało wpływ szkolenia gałąź warunkowa w pierwszym `if` instrukcję, aby przewidzieć nie podjęto. Kontekst zaatakowanego następnie może spowodować ofiarą Kontekst wykonywania `ProcessType` z obiektem typu `CType2`. Może to spowodować pomyłek spekulacyjnego typu Jeśli warunkowych gałęzi w pierwszym `if` instrukcji źle przewidzianych i wykonuje treść `if` instrukcji, w związku z tym rzutowanie obiektu typu `CType2` do `CType1`. Ponieważ `CType2` jest mniejszy niż `CType1`, dostęp do pamięci, aby `CType1::field2` wynik na liście spekulacyjnego liczbach załaduje danych, które mogą być wpisu tajnego. Ta wartość jest następnie używany w obciążenia z `shared_buffer` której można utworzyć dostrzegalnych efekty uboczne, podobnie jak w przypadku tablicy liczbach przykład opisanych powyżej.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Typ spekulacyjnego pomyłek prowadzące do pośredniego gałęzi

Ten wzorzec pisania kodu obejmuje przypadek, w którym pomyłek spekulacyjnego typu mogą powodować niebezpieczne gałęzi pośrednie podczas związanego z wykonywaniem spekulatywnym. W tym przykładzie zaatakowanego kontekst może spowodować ofiarą Kontekst wykonywania `ProcessType` wiele razy z obiektem typu `CType2` (`type` pole jest równa `Type2`). Będzie to miało wpływ szkolenia gałąź warunkowa w pierwszym `if` instrukcji do wykonania i `else if` instrukcję, aby nie należy podjąć. Kontekst zaatakowanego następnie może spowodować ofiarą Kontekst wykonywania `ProcessType` z obiektem typu `CType1`. Może to spowodować pomyłek spekulacyjnego typu Jeśli warunkowych gałęzi w pierwszym `if` przewiduje instrukcji wykonane i `else if` związku z tym instrukcja przewiduje nie podjęto wykonywanie treści `else if` i rzutowanie obiektu typu `CType1` do `CType2`. Ponieważ `CType2::dispatch_routine` nakłada się na pola `char` tablicy `CType1::field1`, może to spowodować spekulacyjnego gałęzi pośrednich do obiektu docelowego gałęzi niezamierzone. Jeśli kontekst zaatakowanego kontrolować wartości bajtów w `CType1::field1` tablicy, mogą być w stanie kontrolować adres docelowy gałęzi.

## <a name="speculative-uninitialized-use"></a>Użycie niezainicjowanej spekulacyjne

Ta kategoria wzorców polega na scenariuszach, gdzie związanego z wykonywaniem spekulatywnym może mają dostęp do pamięci niezainicjowanej i użyć go do kanału informacyjnego kolejnych obciążenia lub pośredniego gałęzi. Do tych schematów kodowania stanowiące osoba atakująca musi mieć możliwość kontrolowania lub znacząco wpłynąć na zawartość pamięci, który jest używany bez inicjowany przez kontekst, który jest używany w.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>Spekulacyjnego użycia niezainicjowanej prowadzące do liczbach obciążenia

Spekulacyjnego użycia niezainicjowanej może potencjalnie doprowadzić do liczbach obciążenia przy użyciu wartości osoba atakująca kontrolowany. W przykładzie poniżej wartości `index` przypisano `trusted_index` we wszystkich ścieżkach architektury i `trusted_index` zakłada, że mniejsze niż lub równe `buffer_size`. W zależności od kodu wytworzone przez kompilator, jest jednak możliwe obejścia spekulacyjnego magazynu może wystąpić umożliwiająca obciążenia z `buffer[index]` i wyrażenia zależne do wykonania w przód od przypisania do `index`. W takim przypadku niezainicjalizowanej wartości dla `index` będzie służyć jako przesunięcie do `buffer` umożliwiające osobie atakującej odczytu informacji poufnych w liczbach i przekazuje to za pośrednictwem kanału po stronie za pomocą zależnych obciążenia `shared_buffer` .

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

void InitializeIndex(unsigned int trusted_index, unsigned int *index) {
    *index = trusted_index;
}

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int trusted_index) {
    unsigned int index;

    InitializeIndex(trusted_index, &index); // not inlined

    // SPECULATION BARRIER
    unsigned char value = buffer[index];
    return shared_buffer[value * 4096];
}
```

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>Spekulacyjnego użycia niezainicjowanej prowadzące do pośredniego gałęzi

Spekulacyjnego użycia niezainicjowanej potencjalnie może prowadzić do pośredniego gałęzi, której cel rozgałęzienia jest kontrolowany przez osobę atakującą. W poniższym przykładzie `routine` jest przypisany do jednej `DefaultMessageRoutine1` lub `DefaultMessageRoutine` zależności od wartości `mode`. W ścieżce architektury, spowoduje to `routine` zawsze zainicjowany wcześniejsze gałąź pośrednich. Jednak w zależności od kodu wytworzone przez kompilator, obejście spekulacyjnego magazynu może wystąpić, umożliwiająca pośrednich gałęzi za pomocą `routine` speculatively wykonywanej w przód od przypisania do `routine`. W takim przypadku osoba atakująca może speculatively wykonać z dowolnego adresu, zakładając, że osoba atakująca może mieć wpływ lub kontroli niezainicjowany wartości `routine`.

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];
extern unsigned int mode;

void InitializeRoutine(MESSAGE_ROUTINE *routine) {
    if (mode == 1) {
        *routine = &DefaultMessageRoutine1;
    }
    else {
        *routine = &DefaultMessageRoutine;
    }
}

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    MESSAGE_ROUTINE routine;

    InitializeRoutine(&routine); // not inlined

    // SPECULATION BARRIER
    routine(buffer, buffer_size);
}
```

## <a name="mitigation-options"></a>Opcje ograniczania ryzyka

Związanego z wykonywaniem spekulatywnym po stronie kanału luk w zabezpieczeniach, może być ograniczona przez wprowadzanie zmian do kodu źródłowego. Te zmiany może obejmować łagodzenia konkretne wystąpienia luki w zabezpieczeniach, takie jak dodanie *wstawiał barierę przewidywania*, lub wprowadzając zmiany w projekcie aplikacji umożliwiają poufne informacje niedostępne do spekulacyjne wykonanie.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Wstawiał barierę przewidywania za pomocą ręcznej Instrumentacji

A *wstawiał barierę przewidywania* mogą być wstawiane ręcznie przez dewelopera, aby zapobiec związanego z wykonywaniem spekulatywnym z przejściem na ścieżce architektury. Na przykład deweloper można wstawić wstawiał barierę przewidywania przed niebezpiecznych wzorzec pisania kodu w treści bloku warunkowego, albo na początku bloku (po gałąź warunkowa) lub przed pierwszym obciążenia, który stanowi zagrożenie. Uniemożliwi to misprediction gałąź warunkowa, wykonanie niebezpieczny kod dla innej architektury ścieżka przez wykonywanie serializacji. Sekwencja wstawiał barierę różni się architekturą sprzętową zgodnie z opisem w poniższej tabeli:

|Architektura|Wstawiał barierę przewidywania wewnętrzne dla CVE-2017-5753|Wstawiał barierę przewidywania wewnętrzne dla CVE-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence()|_mm_lfence()|
|ARM|nie jest obecnie dostępna|__dsb(0)|
|ARM64|nie jest obecnie dostępna|__dsb(0)|

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Wstawiał barierę przewidywania za pomocą kompilatora czasu Instrumentacji

Kompilator języka Visual C++ w programie Visual Studio 2017 (począwszy od wersji 15.5.5) obejmuje obsługę `/Qspectre` przełącznika, który wstawia automatycznie wstawiał barierę dla ograniczonego zestawu schematów kodowania potencjalnie zagrożone związane z CVE-2017-5753. W dokumentacji dotyczącej [/qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) flagi zawiera więcej informacji na jego skutków i użycia. Należy pamiętać, że ta flaga nie obejmuje wszystkich potencjalnie zagrożone schematów kodowania i jako takie deweloperzy nie należy polegać na go jako kompleksowe środki zaradcze dla tej klasy luk w zabezpieczeniach.

### <a name="masking-array-indices"></a>Indeksy tablicy maskowania

W przypadkach, w którym spekulacyjnego liczbach obciążenia może wystąpić, indeks tablicy można zdecydowanie ograniczone na ścieżkę architektury i architektury przez dodanie logiki można jawnie powiązać indeksu tablicy. Na przykład jeśli tablica może być przydzielona do rozmiaru, który jest wyrównany do potęgi liczby dwa, następnie maska proste mogą zostać wprowadzone. Jest to zilustrowane w poniższym przykładzie gdzie zakłada się, że `buffer_size` pokrywa się z potęgą liczby dwa. Gwarantuje to, że `untrusted_index` jest zawsze mniejsza niż `buffer_size`nawet wtedy, gdy występuje misprediction gałąź warunkowa i `untrusted_index` został przekazany przy użyciu wartości większe niż lub równa `buffer_size`.

Należy zauważyć, że maskowanie indeksu, wykonywane na w tym miejscu może być obejścia spekulacyjnego magazynu, w zależności od kodu, który jest generowany przez kompilator.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        untrusted_index &= (buffer_size - 1);
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="removing-sensitive-information-from-memory"></a>Usuwanie poufne informacje z pamięci

Inna technika, który może służyć do złagodzenia związanego z wykonywaniem spekulatywnym po stronie kanału luk w zabezpieczeniach jest usunąć poufne informacje z pamięci. Deweloperzy oprogramowania można wyszukać możliwości refaktoryzacji swoich aplikacji w taki sposób, że informacje poufne nie jest dostępny podczas wykonywania spekulacyjnego. Można to osiągnąć przez refaktoryzacji projektu aplikacji do izolowania poufnych informacji w osobnych procesach. Na przykład aplikacja przeglądarki sieci web mogą próbować izolowania danych skojarzonych z każdego miejsca pochodzenia w sieci web w osobnych procesach i w ten sposób zapobiegając jeden proces będzie mogła uzyskiwać dostęp do związanego z wykonywaniem spekulatywnym między źródłami danych.

## <a name="see-also"></a>Zobacz też

[Wskazówki, aby uniknąć kanału po stronie wykonywania spekulacyjnego luk w zabezpieczeniach](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[Ograniczanie ryzyka związanego z wykonywaniem spekulatywnym po stronie kanału sprzętowych luk w zabezpieczeniach](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
