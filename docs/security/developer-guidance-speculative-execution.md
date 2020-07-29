---
title: Wskazówki dla deweloperów języka C++ dotyczące spekulacyjnych kanałów po stronie wykonywania
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: d0b9faf0bd11892c05e25e981e8cd729cb623dd4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219329"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Wskazówki dla deweloperów języka C++ dotyczące spekulacyjnych kanałów po stronie wykonywania

Ten artykuł zawiera wskazówki dla deweloperów, które ułatwiają identyfikację i łagodzenie luk w zabezpieczeniach kanału po stronie wykonywania spekulacyjnych w oprogramowaniu C++. Te luki w zabezpieczeniach mogą ujawniać poufne informacje między granicami zaufania i mogą mieć wpływ na oprogramowanie działające na procesorach, które obsługują spekulacyjne wykonywanie instrukcji z niezależną kolejnością. Ta klasa luk została najpierw opisana w styczniu, 2018 i dodatkowe tło i wskazówki można znaleźć w [poradniku zabezpieczeń firmy Microsoft](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002).

Wskazówki zawarte w tym artykule dotyczą klas luk w zabezpieczeniach reprezentowanej przez:

1. CVE-2017-5753, znany również jako Spectre Variant 1. Ta klasa luk w zabezpieczeniach sprzętowych jest związana z kanałami ubocznymi, które mogą powstać z powodu spekulacyjnego wykonania, które występuje w wyniku nieprawidłowych prognoz gałęzi warunkowej. Kompilator języka Microsoft C++ w programie Visual Studio 2017 (począwszy od wersji 15.5.5) zawiera obsługę `/Qspectre` przełącznika, który zapewnia ograniczenie czasu kompilacji dla ograniczonego zestawu potencjalnie narażonych wzorców kodowania związanych z CVE-2017-5753. `/Qspectre`Przełącznik jest również dostępny w programie Visual Studio 2015 Update 3 do [KB 4338871](https://support.microsoft.com/help/4338871). Dokumentacja flagi [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) zawiera więcej informacji na temat ich skutków i użycia.

2. CVE-2018-3639, znane także jako " [spekulacyjne" Obejście magazynu (SSB)](https://aka.ms/sescsrdssb). Ta klasa luk w zabezpieczeniach sprzętowych jest związana z kanałami ubocznymi, które mogą powstać z powodu spekulacyjnego wykonywania obciążenia przed magazynem zależnym w wyniku nieprawidłowych prognozowania dostępu do pamięci.

Dostępne Wprowadzenie do luk w zabezpieczeniach kanału po stronie wykonywania można znaleźć w prezentacji zatytułowanej [Spectre i Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) przez jeden z zespołów badawczych, który odnalazł te problemy.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>Co to są luki w zabezpieczeniach sprzętu kanału po stronie wykonywania spekulacyjnej?

Nowoczesne procesory CPU zapewniają wyższy poziom wydajności dzięki użyciu spekulacyjnych i nieaktualnych wykonań instrukcji. Na przykład jest to często osiągane przez przewidywanie docelowej gałęzi (warunkowej i pośredniej), która umożliwia PROCESORowi rozpoczęcie speculatively wykonywania instrukcji w przewidywanym miejscu docelowym gałęzi, co pozwala uniknąć braku miejsca do momentu rozwiązania rzeczywistego celu rozgałęzienia. W przypadku późniejszego wykrycia przez procesor CPU wystąpienia nieprawidłowych prognoz wszystkie Stany maszyn, które zostały obliczone speculatively, są odrzucane. Gwarantuje to, że nie ma żadnych widocznych pod kątem architektury efektów nieprzewidywalnej spekulacji.

Chociaż wykonywanie spekulacyjne nie wpływa na stan widoczny w architekturze, może pozostawić pozostałe ślady w stanie niezgodnym z architekturą, takie jak różne pamięci podręczne używane przez procesor CPU. Są to pozostałe ślady wykonania spekulacyjnego, które mogą powodować powstanie luk w zabezpieczeniach kanału. Aby lepiej zrozumieć to, weź pod uwagę Poniższy fragment kodu, który zawiera przykład CVE-2017-5753 (Pominięcie sprawdzania granic):

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

W tym przykładzie `ReadByte` podano bufor, rozmiar buforu i indeks w tym buforze. Parametr index określony przez `untrusted_index` , jest dostarczany przez kontekst o niższych uprawnieniach, taki jak proces nieadministracyjny. Jeśli `untrusted_index` jest mniejsza niż `buffer_size` , znak w tym indeksie jest odczytywany `buffer` i używany do indeksowania w udostępnionym regionie pamięci, do którego odwołuje się `shared_buffer` .

W perspektywie architektury ta sekwencja kodu jest doskonale bezpieczna, ponieważ jest gwarantowana, która `untrusted_index` zawsze będzie mniejsza niż `buffer_size` . Jednak w przypadku wykonywania spekulacyjnych jest możliwe, że procesor CPU przewidywalnuje gałąź warunkową i wykona treść instrukcji if, nawet gdy `untrusted_index` jest większy lub równy `buffer_size` . W związku z tym procesor CPU może speculatively odczytać bajt z przekroczenia granic `buffer` (które mogą być kluczem tajnym), a następnie użyć tej wartości bajtowej do obliczenia adresu kolejnego obciążenia przez `shared_buffer` .

Podczas gdy procesor CPU będzie ostatecznie wykrywał nieodpowiednie Przewidywania, skutki uboczne mogą pozostać w pamięci podręcznej procesora, która ujawnia informacje o wartości bajtowej, która została odczytana z `buffer` . Te efekty uboczne mogą być wykrywane przez niższy uprzywilejowany kontekst uruchomiony w systemie przez sondowanie, jak szybko każda linia pamięci podręcznej `shared_buffer` jest dostępna. Czynności, które można wykonać w celu osiągnięcia tego celu:

1. **Wywołaj `ReadByte` wiele razy przy `untrusted_index` `buffer_size` mniejszej **liczbie. Kontekst atakujący może spowodować wywołanie elementu ofiary `ReadByte` (np. za pośrednictwem wywołania RPC) w taki sposób, aby predykcyjny rozgałęzienia był szkolony do niewykonania, ponieważ `untrusted_index` jest mniejszy niż `buffer_size` .

2. **Opróżnianie wszystkich wierszy pamięci `shared_buffer` podręcznej w programie **. Kontekst atakujący musi opróżnić wszystkie wiersze pamięci podręcznej w udostępnionym regionie pamięci, do którego odwołuje się `shared_buffer` . Ponieważ region pamięci jest udostępniony, jest to bezpośrednie i można go wykonać przy użyciu wewnętrznych, takich jak `_mm_clflush` .

3. **Wywołaj `ReadByte` z `untrusted_index` `buffer_size` większą **liczbą. Kontekst atakujący powoduje, że kontekst ofiary wywołuje `ReadByte` takie, że nie zostanie on przewidywalna. Powoduje to, że procesor speculatively wykonywanie treści bloku if o `untrusted_index` wartości większej niż `buffer_size` , co prowadzi do przeczytania poza granice `buffer` . W związku z tym `shared_buffer` jest indeksowany przy użyciu potencjalnie tajnej wartości, która została odczytana z zakresu, co powoduje załadowanie odpowiedniej linii pamięci podręcznej przez procesor CPU.

4. **Zapoznaj się z każdą linią pamięci podręcznej w programie `shared_buffer` , aby zobaczyć, która jest najbardziej szybko dostępna** Kontekst atakujący może odczytać każdą linię pamięci podręcznej w programie `shared_buffer` i wykryć wiersz pamięci podręcznej, który ładuje znacznie szybciej niż inne. Jest to linia pamięci podręcznej, która prawdopodobnie została wprowadzona w kroku 3. Ponieważ w tym przykładzie istnieje relacja 1:1 między wartością bajtu i wierszem pamięci podręcznej, pozwala to osobie atakującej na wywnioskowanie rzeczywistej wartości bajtu, który był odczytywany poza granicami.

Powyższe kroki zapewniają przykład użycia techniki znanej jako OPRÓŻNIj i Załaduj ponownie w połączeniu z wykorzystaniem wystąpienia CVE-2017-5753.

## <a name="what-software-scenarios-can-be-impacted"></a>Jakie scenariusze może mieć wpływ na oprogramowanie?

Opracowywanie bezpiecznego oprogramowania przy użyciu procesu, takiego jak [cykl projektowania zabezpieczeń](https://www.microsoft.com/sdl/) (SDL), zwykle wymaga od deweloperów zidentyfikowania granic zaufania istniejących w aplikacji. Granica zaufania istnieje w miejscach, w których aplikacja może korzystać z danych udostępnianych przez niezaufany kontekst, takich jak inny proces w systemie lub proces trybu użytkownika niebędącego administratorami w przypadku sterownika urządzenia trybu jądra. Nowa klasa luk w zabezpieczeniach kanałów po stronie wykonywania jest istotna dla wielu granic zaufania w istniejących modelach zabezpieczeń oprogramowania, które izolują kod i dane na urządzeniu.

Poniższa tabela zawiera podsumowanie modeli zabezpieczeń oprogramowania, w przypadku których deweloperzy mogą być musieli zainteresowani tymi usterkami:

|Granica zaufania|Opis|
|----------------|----------------|
|Granica maszyny wirtualnej|Aplikacje, które izolują obciążenia w oddzielnych maszynach wirtualnych, które odbierają niezaufane dane z innej maszyny wirtualnej mogą być zagrożone.|
|Granica jądra|Może być narażony sterownik urządzenia trybu jądra, który odbiera niezaufane dane z procesu trybu użytkownika niebędącego administratorami.|
|Granica procesu|Aplikacja, która odbiera niezaufane dane z innego procesu działającego w systemie lokalnym, na przykład za pośrednictwem zdalnego wywołania procedury (RPC), pamięci współdzielonej lub innych mechanizmów komunikacji między procesami (IPC) może być zagrożona.|
|Granica enklawy|Aplikacja, która jest wykonywana w ramach bezpiecznego enklawy (na przykład Intel SGX), która odbiera niezaufane dane spoza enklawyu może być zagrożona.|
|Granica języka|Aplikacja, która interpretuje lub just-in-Time (JIT) kompiluje i wykonuje niezaufany kod zapisany w języku wyższego poziomu może być zagrożona.|

W przypadku aplikacji, które mają narażony obszar ataków na dowolne z powyższych granic zaufania, należy przejrzeć kod na stronie ataku, aby zidentyfikować i wyeliminować możliwe wystąpienia luk w zabezpieczeniach kanału po stronie wykonywania. Należy zauważyć, że granice zaufania uwidocznione na urządzeniach ataku zdalnego, takich jak zdalne protokoły sieciowe, nie zostały udowodnione, aby były zagrożone lukami w zabezpieczeniach kanału po stronie wykonywania.

## <a name="potentially-vulnerable-coding-patterns"></a>Potencjalnie narażone wzorce kodowania

Luki w zabezpieczeniach kanału po stronie wykonywania spekulacyjnego mogą wynikać z wielu wzorców kodowania. Ta sekcja zawiera opis potencjalnie narażonych wzorców kodowania i zawiera przykłady dla każdego z nich, ale powinien zostać rozpoznany, że zmiany w tych motywach mogą istnieć. W związku z tym deweloperzy są doradzani jako przykłady, a nie jako wyczerpująca lista wszystkich potencjalnie narażonych wzorców kodowania. Te same klasy luk w zabezpieczeniach pamięci, które mogą już znajdować się w oprogramowaniu, mogą również znajdować się w oparciu o spekulacyjne i nieaktualne ścieżki wykonywania, w tym między innymi przekroczenia buforu, dostęp do tablicy, niezainicjowane użycie pamięci, pomyłkę i tak dalej. Te same elementy pierwotne, których atakujący mogą używać do wykorzystania luk w zabezpieczeniach pamięci, w ramach ścieżek architektonicznych mogą również dotyczyć ścieżek spekulacyjnych.

Ogólnie rzecz biorąc, spekulacyjny kanał po stronie wykonywania związany z rozgałęzieniem warunkowym może wystąpić, gdy wyrażenie warunkowe działa na danych, które mogą być kontrolowane lub mieć wpływ na niezaufany kontekst. Na przykład może to obejmować wyrażenia warunkowe używane w **`if`** **`for`** instrukcjach,,, **`while`** **`switch`** lub. Dla każdej z tych instrukcji kompilator może wygenerować gałąź warunkową, która może następnie przewidzieć obiekt docelowy gałęzi w czasie wykonywania.

Dla każdego przykładu Komentarze z frazą "BARIERa SPEKULACYJNY" są wstawiane, gdy deweloper może wprowadzić barierę jako środek zaradczy. Zostało to omówione bardziej szczegółowo w sekcji dotyczącej środków zaradczych.

## <a name="speculative-out-of-bounds-load"></a>Ładowanie spekulacyjne z ograniczeniami

Ta kategoria wzorców kodowania obejmuje nieprawidłową prognozę gałęzi warunkowej, która prowadzi do spekulacyjnego dostępu do pamięci.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>Macierzowe ładowanie do sieci

Ten wzorzec kodowania jest oryginalnie opisanym wzorcem kodowania na potrzeby CVE-2017-5753 (obejście sprawdzania granic). W sekcji tła w tym artykule opisano szczegółowo ten wzorzec.

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

Podobnie obciążenie tablicy poza granicami może wystąpić w połączeniu z pętlą, która przekracza jego stan końcowy z powodu nieprawidłowego przewidywania. W tym przykładzie gałąź warunkowa skojarzona z `x < buffer_size` wyrażeniem może źle przewidzieć i speculatively wykonać treść **`for`** pętli, gdy jest ona `x` większa lub równa, co spowoduje `buffer_size` załadowanie spekulacyjnych niezwiązanych z ograniczeniami.

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

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Ładowanie z zewnątrz zakresu do macierzy podawanie pośredniego rozgałęzienia

Ten wzorzec kodowania obejmuje przypadek, w którym wystąpienie warunkowego nieprawidłowej przewidywania może prowadzić do nieograniczonego dostępu do tablicy wskaźników funkcji, które następnie prowadzi do pośredniego rozgałęzienia do adresu docelowego, który został odczytany poza granicami. Poniższy fragment kodu przedstawia przykład.

W tym przykładzie niezaufany Identyfikator komunikatu jest dostarczany do DispatchMessage za pomocą `untrusted_message_id` parametru. Jeśli `untrusted_message_id` jest mniejsza niż `MAX_MESSAGE_ID` , jest używana do indeksowania tablicy wskaźników funkcji i gałęzi do odpowiedniego obiektu docelowego rozgałęzienia. Ten kod jest bezpieczny w architekturze, ale jeśli procesor przewidywalnuje rozgałęzienie warunkowe, może wynikać z `DispatchTable` indeksowania, `untrusted_message_id` gdy jego wartość jest większa lub równa `MAX_MESSAGE_ID` , co prowadzi do nieograniczonego dostępu. Może to spowodować wykonanie spekulacyjne z adresu docelowego gałęzi, który jest wyprowadzany poza granice tablicy, co może prowadzić do ujawnienia informacji w zależności od kodu, który jest wykonywany speculatively.

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

Podobnie jak w przypadku macierzy niepowiązanej z załadowaniem innego obciążenia, ten stan może również wystąpić w połączeniu z pętlą, która przekracza jej stan końcowy z powodu nieprawidłowego przewidywania.

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>Tworzenie macierzy z magazynem poza granicami

W poprzednim przykładzie pokazano, jak obciążenie spekulacyjne z ograniczeniami może mieć wpływ na pośrednią metodę docelową gałęzi, ale jest również możliwe, aby Magazyn zewnętrzny mógł modyfikować pośredniego celu rozgałęzienia, na przykład wskaźnik funkcji lub adres zwrotny. Może to potencjalnie prowadzić do spekulacyjnego wykonania od adresu określonego osoby atakującej.

W tym przykładzie niezaufany indeks jest przenoszona przez `untrusted_index` parametr. Jeśli `untrusted_index` jest mniejsza niż liczba elementów `pointers` tablicy (elementy 256), podana wartość wskaźnika w `ptr` jest zapisywana w `pointers` tablicy. Ten kod jest bezpieczny w architekturze, ale jeśli procesor przewidywalnuje rozgałęzienie warunkowe, może to spowodować `ptr` speculatively zapisanie poza granicami tablicy z przydzieloną stosem `pointers` . Może to prowadzić do spekulacyjnego uszkodzenia adresu zwrotnego dla `WriteSlot` . Jeśli osoba atakująca może kontrolować wartość `ptr` , może być w stanie prowadzić spekulacyjne wykonywanie z dowolnego adresu, gdy `WriteSlot` powraca wzdłuż ścieżki spekulacyjnej.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

Podobnie, jeśli zmienna lokalna wskaźnika funkcji o nazwie `func` została przypisana na stosie, może być możliwe speculatively modyfikowanie adresu, `func` do którego odwołuje się w przypadku wystąpienia awarii gałęzi warunkowej. Może to spowodować wykonanie spekulacyjne z dowolnego adresu, gdy wskaźnik funkcji jest wywoływany przez.

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

Należy zauważyć, że oba te przykłady obejmują spekulacyjne modyfikacje wskaźników rozgałęzień pośrednich przypisywanych ze stosu. Możliwe jest również, aby można było modyfikować spekulacyjne w przypadku zmiennych globalnych, pamięci przydzieloną sterty, a nawet pamięci tylko do odczytu na niektórych procesorach. W przypadku pamięci przydzielonej przez stos kompilator języka Microsoft C++ wykonuje już kroki, aby utrudnić speculatively modyfikowanie rozgałęzień pośrednich przyznanych przez stosy, na przykład przez zmianę kolejności zmiennych lokalnych w taki sposób, że bufory znajdują się obok pliku cookie zabezpieczeń w ramach funkcji zabezpieczenia kompilatora [/GS](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check) .

## <a name="speculative-type-confusion"></a>Pomyłka typu spekulacyjnego

Ta kategoria dotyczy wzorców kodowania, które mogą spowodować pomyłkę w nieprawidłowym typie. Dzieje się tak, gdy dostęp do pamięci jest uzyskiwany przy użyciu nieprawidłowego typu w ścieżce niezgodnej ze standardem podczas wykonywania spekulacyjnego. Zarówno błędne rozgałęzienie, jak i spekulacyjne obejście magazynu mogą potencjalnie prowadzić do pomyłki w nieprawidłowym typie.

W przypadku obejścia ze sklepu spekulacyjnego może to wystąpić w scenariuszach, w których kompilator ponownie używa lokalizacji stosu dla zmiennych różnych typów. Wynika to z faktu, że magazyn architektoniczny zmiennej typu `A` może być pominięty, co pozwala na wykonanie ładowania typu `A` do speculatively przed przypisaniem zmiennej. Jeśli wcześniej przechowywana zmienna ma inny typ, może to spowodować pomyłkę dla typu spekulacyjnego.

W przypadku nieodpowiedniej przewidywania gałęzi warunkowej Poniższy fragment kodu zostanie użyty do opisania różnych warunków, które mogą spowodować pomyłkę w przypadku typu spekulacyjnego.

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

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Pomyłka typu spekulacyjnego prowadząca do obciążenia nieograniczonego

Ten wzorzec kodowania obejmuje przypadek, w którym pomyłka w przypadku typu spekulacyjnego może skutkować brakiem lub dostępem do pól z nieprawidłowym typem, gdzie załadowana wartość strumieniowo pobiera Następny adres ładowania. Jest to podobne do wzorca kodowania niepowiązanego z tablicą, ale jest on zakazany za pomocą alternatywnej sekwencji kodowania, jak pokazano powyżej. W tym przykładzie kontekst atakujący może spowodować wielokrotne wykonywanie kontekstu ofiary `ProcessType` przy użyciu obiektu typu `CType1` ( `type` pole jest równe `Type1` ). Będzie to miało wpływ na uczenie gałęzi warunkowej dla pierwszej **`if`** instrukcji w celu przewidywania, które nie zostały wykonane. Kontekst atakujący może spowodować, że kontekst ofiary będzie wykonywany `ProcessType` z obiektem typu `CType2` . Może to spowodować pomyłkę typu spekulacyjnego, jeśli gałąź warunkowa dla pierwszej instrukcji źle **`if`** przewidywalna i wykona treść **`if`** instrukcji, w ten sposób rzutowanie obiektu typu `CType2` do `CType1` . Ponieważ `CType2` jest mniejszy niż `CType1` , dostęp do pamięci `CType1::field2` będzie powodować spekulacyjne ładowanie niezwiązanych z danymi, które mogą być tajne. Ta wartość jest następnie używana w obciążeniu `shared_buffer` , z którego można tworzyć zauważalne efekty uboczne, podobnie jak w przypadku przykładu z podaną tablicą.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Pomyłka typu spekulacyjnego prowadząca do rozgałęzienia pośredniego

Ten wzorzec kodowania obejmuje przypadek, w którym pomyłka typu spekulacyjnego może spowodować powstanie niebezpiecznej gałęzi pośredniej podczas wykonywania spekulacyjnego. W tym przykładzie kontekst atakujący może spowodować wielokrotne wykonywanie kontekstu ofiary `ProcessType` przy użyciu obiektu typu `CType2` ( `type` pole jest równe `Type2` ). Będzie to miało wpływ na uczenie gałęzi warunkowej dla pierwszej **`if`** instrukcji i `else if` instrukcji, która nie zostanie podjęta. Kontekst atakujący może spowodować, że kontekst ofiary będzie wykonywany `ProcessType` z obiektem typu `CType1` . Może to spowodować pomyłkę typu, jeśli rozgałęzienie warunkowe dla pierwszej **`if`** instrukcji przewidywalna i `else if` przewidywalne instrukcji nie zostały wykonane, w związku z czym wykonywanie treści `else if` i rzutowanie obiektu typu `CType1` do `CType2` . Ponieważ `CType2::dispatch_routine` pole nakłada się na **`char`** tablicę `CType1::field1` , może to spowodować powstanie spekulacyjnej gałęzi pośredniej do niezamierzonego celu gałęzi. Jeśli kontekst atakujący może kontrolować wartości bajtowe w `CType1::field1` tablicy, może być w stanie kontrolować adres docelowy gałęzi.

## <a name="speculative-uninitialized-use"></a>Nieinicjowane użycie spekulacyjne

Ta kategoria wzorców kodowania obejmuje scenariusze, w których realizacja spekulacyjnego może uzyskać dostęp do niezainicjowanej pamięci i używać jej do tworzenia strumieniowego kolejnego obciążenia lub pośredniego rozgałęzienia. Aby te wzorce kodowania były możliwe do wykorzystania, osoba atakująca musi mieć możliwość kontrolowania lub znaczącego wpływu na zawartość pamięci, która jest używana bez inicjacji w kontekście, w którym jest używana.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>Nieinicjowane użycie spekulacyjne wiodące w obciążeniu niezwiązanym z ograniczeniami

Nieinicjowane użycie spekulacyjne może potencjalnie prowadzić do obciążenia poza granicami przy użyciu wartości kontrolowanej przez osobę atakującą. W poniższym przykładzie wartość `index` jest przypisywana `trusted_index` we wszystkich ścieżkach architektury i przyjmuje się, `trusted_index` że jest ona mniejsza lub równa `buffer_size` . Jednakże, w zależności od kodu utworzonego przez kompilator, możliwe jest obejście magazynu spekulacyjnego, który umożliwia ładowanie z `buffer[index]` i zależnych wyrażeń przed przypisaniem do `index` . W takim przypadku niezainicjowana wartość dla `index` zostanie użyta jako przesunięcie, w `buffer` którym osoba atakująca może odczytywać poufne informacje i przekazywać je za pośrednictwem kanału bocznego przez zależne obciążenie `shared_buffer` .

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

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>Nieinicjowane użycie spekulacyjne wiodące w oddziale pośrednim

Nieinicjowane użycie spekulacyjne może potencjalnie prowadzić do rozgałęzienia pośredniego, w którym obiekt docelowy gałęzi jest kontrolowany przez osobę atakującą. W poniższym przykładzie `routine` jest przypisany do albo w `DefaultMessageRoutine1` zależności od `DefaultMessageRoutine` wartości `mode` . W przypadku ścieżki architektonicznej spowoduje to, że `routine` zawsze zostanie zainicjowany przed gałęzią pośrednią. Jednakże, w zależności od kodu wygenerowanego przez kompilator, może wystąpić obejście ze sklepu spekulacyjnego, które umożliwia `routine` speculatively przed przypisaniem do `routine` . W takim przypadku osoba atakująca może mieć możliwość speculatively wykonywania z dowolnego adresu, przy założeniu, że osoba atakująca może mieć wpływ lub kontrolować niezainicjowaną wartość `routine` .

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

## <a name="mitigation-options"></a>Opcje łagodzenia

Luki w zabezpieczeniach kanału po stronie wykonywania spekulacyjnych można zmniejszyć, wprowadzając zmiany w kodzie źródłowym. Te zmiany mogą dotyczyć ograniczenia konkretnych wystąpień luki w zabezpieczeniach, takich jak dodanie *bariery spekulacji*lub wprowadzenie zmian w projekcie aplikacji, aby informacje poufne były niedostępne dla spekulacyjnego wykonywania.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Bariera spekulacyjny przy użyciu instrumentacji ręcznej

*Bariera spekulacyjnego* może zostać ręcznie wstawiona przez dewelopera, aby zapobiec postępowaniu spekulacyjnym na podstawie ścieżki bez architektury. Na przykład deweloper może wstawić barierę spekulacyjnyej przed niebezpiecznym wzorcem kodowania w treści bloku warunkowego, na początku bloku (po gałęzi warunkowej) lub przed pierwszym załadowaniem, którego dotyczy. Uniemożliwi to rozgałęzienie warunkowe nieprawidłową prognozowanie wykonywania niebezpiecznego kodu w ścieżce innej niż Architektura przez serializację wykonania. Sekwencja barier spekulacyjnych różni się od architektury sprzętu zgodnie z opisem w poniższej tabeli:

|Architektura|Wewnętrzna bariera spekulacji dla CVE-2017-5753|Wewnętrzna bariera spekulacji dla CVE-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence ()|_mm_lfence ()|
|ARM|obecnie niedostępne|__dsb (0)|
|ARM64|obecnie niedostępne|__dsb (0)|

Na przykład poniższy wzorzec kodu może zostać skorygowany przy użyciu `_mm_lfence` wewnętrznego, jak pokazano poniżej.

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Bariera spekulacyjny przez instrumentację czasu kompilatora

Kompilator języka Microsoft C++ w programie Visual Studio 2017 (począwszy od wersji 15.5.5) zawiera obsługę `/Qspectre` przełącznika, który automatycznie wstawia barierę spekulacyjnyą dla ograniczonego zestawu potencjalnie narażonych wzorców kodowania związanych z CVE-2017-5753. Dokumentacja flagi [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) zawiera więcej informacji na temat ich skutków i użycia. Należy pamiętać, że ta flaga nie obejmuje wszystkich potencjalnie narażonych wzorców kodowania i ponieważ tacy deweloperzy nie muszą polegać na tym, jak kompleksowe środki zaradcze dla tej klasy luk w zabezpieczeniach.

### <a name="masking-array-indices"></a>Maskowanie indeksów tablicy

W przypadkach, w których mogą występować spekulacyjne operacje ładowania, indeks tablicy można silnie powiązać zarówno ze ścieżką architektury, jak i bez architektury przez dodanie logiki, aby jawnie powiązać indeks tablicy. Na przykład, jeśli tablica może być przypisana do rozmiaru, który jest wyrównany do potęgi dwóch, można wprowadzić prostą maskę. Jest to zilustrowane w poniższym przykładzie, w którym zakłada się, że jest ono `buffer_size` wyrównane do potęgi dwóch. Gwarantuje to `untrusted_index` , że jest zawsze mniejsza niż `buffer_size` , nawet jeśli wystąpi błąd rozgałęzienia warunkowego i `untrusted_index` został on przekazano do wartości większej lub równej `buffer_size` .

Należy zauważyć, że maskowanie indeksów wykonywane w tym miejscu może podlegać obejść w sklepie spekulacyjnym w zależności od kodu wygenerowanego przez kompilator.

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

### <a name="removing-sensitive-information-from-memory"></a>Usuwanie poufnych informacji z pamięci

Inną techniką, która może służyć do łagodzenia luk w zabezpieczeniach kanału po stronie wykonywania, jest usunięcie poufnych informacji z pamięci. Deweloperzy oprogramowania mogą szukać możliwości refaktoryzacji aplikacji w taki sposób, że informacje poufne nie są dostępne podczas wykonywania spekulacyjnego. Można to osiągnąć przez refaktoryzację projektu aplikacji w celu odizolowania poufnych informacji w oddzielnych procesach. Na przykład aplikacja przeglądarki sieci Web może próbować izolować dane skojarzone z poszczególnymi źródłami sieci Web w osobnych procesach, co uniemożliwia jednemu procesowi dostęp do danych między źródłami za pośrednictwem wykonywania spekulacyjnego.

## <a name="see-also"></a>Zobacz także

[Wskazówki dotyczące eliminowania luk w zabezpieczeniach w kanale po stronie wykonywania](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[Łagodzenie luk w zabezpieczeniach sprzętu kanału po stronie wykonywania](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
