---
title: Przegląd C++ AMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca91e614438695a14c6c16c05c5d778b143657eb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219386"
---
# <a name="c-amp-overview"></a>Przegląd C++ AMP
C++ Accelerated Massive Parallelism (C++ AMP) przyspiesza wykonywanie kodu C++ wykorzystując sprzęt zrównoleglający dane, takie jak jednostka przetwarzania grafiki (GPU) na dyskretną kartę graficzną. Używając C++ AMP, możesz programować algorytmy wielowymiarowych danych, dzięki czemu można przyspieszyć wykonywanie za pomocą równoległości na heterogenicznym sprzęcie. Model programowania C++ AMP zawiera tablice wielowymiarowe, indeksowanie, transfer pamięci, fragmentacji i bibliotekę funkcji matematycznych. Można użyć rozszerzeń języka C++ AMP do kontrolowania sposobu przenoszenia danych z procesora CPU do procesora GPU i z powrotem, dzięki czemu można zwiększyć wydajność.  
  
## <a name="system-requirements"></a>Wymagania systemowe  
  
- Windows 7, Windows 8, Windows Server 2008 R2 lub Windows Server 2012  
  
- DirectX 11 poziom funkcji 11.0 lub nowszy sprzęt  
  
- Do debugowania na emulatorze oprogramowania, Windows 8 lub Windows Server 2012 jest wymagany. Do debugowania na sprzęcie, należy zainstalować sterowniki dla karty graficznej. Aby uzyskać więcej informacji, zobacz [debugowania kodu GPU](/visualstudio/debugger/debugging-gpu-code).  
  
## <a name="introduction"></a>Wprowadzenie  
 
Dwa poniższe przykłady ilustrują podstawowe składniki C++ AMP. Załóżmy, że chcesz dodać odpowiadające elementy dwóch tablic jednowymiarowych. Na przykład możesz chcieć dodać `{1, 2, 3, 4, 5}` i `{6, 7, 8, 9, 10}` uzyskać `{7, 9, 11, 13, 15}`. Bez korzystania z C++ AMP można napisać następujący kod do dodawania liczb i wyświetlania wyników.  
  
```cpp  
#include <iostream>  
  
void StandardMethod() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        sumCPP[idx] = aCPP[idx] + bCPP[idx];  
    }  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        std::cout << sumCPP[idx] << "\n";  
    }  
}  
```  
  
Ważne elementy kodu są następujące:  
  
- Dane: Dane składają się z trzech tablic. Wszystkie mają te same rangi (jeden) i długości (pięć).  
  
- Iteracja: Pierwsza `for` pętli udostępnia mechanizm do iteracji na elementach w tablicach. Kod, który ma zostać wykonane w celu obliczenia sum, jest zawarty w pierwszym `for` bloku.  
  
- Indeks: `idx` zmiennej uzyskuje dostęp do poszczególnych elementów tablic.  
  
 Korzystanie z C++ AMP można napisać poniższy kod zamiast tego.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
const int size = 5;  
  
void CppAmpMethod() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[size];  
  
    // Create C++ AMP objects.  
    array_view<const int, 1> a(size, aCPP);  
    array_view<const int, 1> b(size, bCPP);  
    array_view<int, 1> sum(size, sumCPP);  
    sum.discard_data();  
  
    parallel_for_each(   
        // Define the compute domain, which is the set of threads that are created.  
        sum.extent,   
        // Define the code to run on each thread on the accelerator.  
        [=](index<1> idx) restrict(amp) {  
            sum[idx] = a[idx] + b[idx];  
        }  
    );  
  
    // Print the results. The expected output is "7, 9, 11, 13, 15".  
    for (int i = 0; i < size; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
```  
  
Te same elementy podstawowe są obecne, ale użyte są konstrukcje C++ AMP:  
  
- Dane: Używasz tablic C++ do konstruowania trzech C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) obiektów. Należy dostarczyć czterech wartości do konstruowania `array_view` obiektu: wartości danych, Ranking, typ elementu i długość `array_view` w każdym wymiarze. Ranga i typ są przekazywane jako parametry typu. Dane i długość są przekazywane jako parametry konstruktora. W tym przykładzie tablica C++, która jest przekazywana do konstruktora jest jednowymiarowa. Ranga i długość są używane do konstruowania prostokątnego kształtu danych w `array_view` obiektów i danych, wartości są używane do wypełnienia tablicy. Biblioteka wykonawcza obejmuje również [array, klasa](../../parallel/amp/reference/array-class.md), która posiada interfejs podobny `array_view` klasy i jest omówiona w dalszej części tego artykułu.  
  
- Iteracja: [parallel_for_each — funkcja (C++ AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) udostępnia mechanizm do iteracji na elementach danych lub *domenę obliczeniową*. W tym przykładzie domena obliczeniowa jest określona przez `sum.extent`. Kod, który chcesz wykonać, znajduje się w wyrażeniu lambda lub *funkcja jądra*. `restrict(amp)` Wskazuje, że używany jest tylko podzbiór języka C++, który C++ AMP może przyspieszyć.  
  
- Indeks: [index, klasa](../../parallel/amp/reference/index-class.md) zmiennej `idx`, jest zadeklarowana z rangą równą jeden, aby odpowiadać randze obiektu `array_view` obiektu. Korzystając z indeksu, można uzyskać dostęp do poszczególnych elementów `array_view` obiektów.  
  
## <a name="shaping-and-indexing-data-index-and-extent"></a>Formowanie i indeksowanie danych: indeks i zakres  
 
Należy zdefiniować wartości danych i zadeklarować kształt danych przed uruchomieniem kodu jądra. Wszystkie dane są zdefiniowane jako tablica (prostokątna) i można zdefiniować tablicę o każdej randze (liczba wymiarów). Dane mogą być dowolnego rozmiaru, w dowolnym z wymiarów.  
  
### <a name="index-class"></a>index — Klasa  
[Index, klasa](../../parallel/amp/reference/index-class.md) Określa lokalizację w `array` lub `array_view` obiekt poprzez hermetyzację przesunięcia z miejsca pochodzenia w każdym wymiarze w jeden obiekt. Gdy uzyskujesz dostęp do lokalizacji w tablicy, Przekaż `index` obiektu do operatora indeksowania `[]`, zamiast listy indeksów liczb całkowitych. Dostęp do elementów w każdym wymiarze przy użyciu [array:: operator() — Operator](reference/array-class.md#operator_call) lub [array_view::operator() Operator](reference/array-view-class.md#operator_call).  
  
Poniższy przykład tworzy jednowymiarowy indeks, który określa trzeci element w jednowymiarowym `array_view` obiektu. Indeks służy do drukowania trzeciego elementu w `array_view` obiektu. Wynik to 3.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5};  
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";    
// Output: 3  
```  
  
Poniższy przykład tworzy dwuwymiarowy indeks, który określa element gdzie wiersz = 1 i kolumna = 2, w dwuwymiarowym `array_view` obiektu. Pierwszy parametr w `index` Konstruktor jest składnikiem wiersza, a drugi parametr jest składnikiem kolumny. Dane wyjściowe to 6.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6};  
array_view<int, 2> a(2, 3, aCPP);  
  
index<2> idx(1, 2);  
  
std::cout <<a[idx] << "\n";    
// Output: 6  
```  
  
Poniższy przykład tworzy trójwymiarowy indeks, który określa element gdzie głębokość = 0, wiersz = 1 i kolumna = 3, w trójwymiarowym `array_view` obiektu. Należy zauważyć, że pierwszy parametr jest składnikiem głębokości, drugi parametr jest składnikiem wiersza i trzeci parametr jest składnikiem kolumny. Wynikiem jest 8.  
  
```cpp  
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
 
array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.  
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";  
// Output: 8  
```  
  
### <a name="extent-class"></a>extent — Klasa  
[Extent, klasa](../../parallel/amp/reference/extent-class.md) określa długość danych każdego wymiaru `array` lub `array_view` obiektu. Możesz utworzyć zakres i użyć go do utworzenia `array` lub `array_view` obiektu. Można także pobrać zakres istniejącego `array` lub `array_view` obiektu. Poniższy przykład drukuje długość zakresu w każdym wymiarze `array_view` obiektu.  
  
```cpp  
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
// There are 3 rows and 4 columns, and the depth is two.  
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";  
std::cout << "The number of rows is " << a.extent[1] << "\n";  
std::cout << "The depth is " << a.extent[0] << "\n";  
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";  
```  
  
Poniższy przykład tworzy `array_view` obiekt, który ma takie same wymiary jak obiekt w poprzednim przykładzie, ale w tym przykładzie używa `extent` obiektu zamiast używania jawnych parametrów w `array_view` konstruktora.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};  
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";  
std::cout << "The number of rows is " << a.extent[1] << "\n";  
std::cout << "The depth is " << a.extent[0] << "\n";  
```  
  
## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>Przenoszenie danych do akceleratora: array i array_view  
 
Dwa kontenery danych, używane do przenoszenia danych do akceleratora są zdefiniowane w bibliotece środowiska uruchomieniowego. Są one [array, klasa](../../parallel/amp/reference/array-class.md) i [array_view, klasa](../../parallel/amp/reference/array-view-class.md). `array` Klasa jest klasą kontenera, która tworzy głęboką kopię danych, gdy obiekt jest konstruowany. `array_view` Klasa jest klasą otoki, która kopiuje dane, gdy funkcja jądra uzyskuje dostęp do danych. Gdy dane są potrzebne na urządzeniu źródłowym dane są kopiowane z powrotem.  
  
### <a name="array-class"></a>array — Klasa  
Gdy `array` obiekt jest konstruowany, głęboka kopia danych jest tworzony na akceleratorze, jeśli został użyty Konstruktor, który zawiera wskaźnik do zestawu danych. Funkcja jądra modyfikuje kopię na akceleratorze. Po zakończeniu wykonywania funkcji jądra należy skopiować dane do struktury źródła danych. Poniższy przykład mnoży każdy element wektora przez 10. Po zakończeniu funkcji jądra `vector conversion operator` służy do kopiowania danych z powrotem do obiektu wektora.  
  
```cpp  
std::vector<int> data(5);

for (int count = 0; count <5; count++)   
{  
    data[count] = count;  
}  
 
array<int, 1> a(5, data.begin(), data.end());
 
parallel_for_each(
    a.extent, 
    [=, &a](index<1> idx) restrict(amp) {  
        a[idx] = a[idx]* 10;  
    });
  
data = a;  
for (int i = 0; i < 5; i++)   
{  
    std::cout << data[i] << "\n";  
}  
```  
  
### <a name="arrayview-class"></a>array_view — Klasa  
`array_view` Ma prawie te same elementy członkowskie jako `array` klasy, ale jej zachowanie podstawowe nie jest taka sama. Dane przekazywane do `array_view` Konstruktor nie są replikowane na GPU, tak jak w `array` konstruktora. Zamiast tego dane są kopiowane do akceleratora po wykonaniu funkcji jądra. W związku z tym jeśli utworzysz dwa `array_view` obiektów, które używają tych samych danych, zarówno `array_view` obiekty odnoszą się do tego samego obszaru pamięci. Po wykonaniu tej czynności należy zsynchronizować każdy dostęp wielowątkowy. Główną zaletą używania `array_view` klasa jest, że dane są przenoszone tylko wtedy, gdy jest to konieczne.  
  
### <a name="comparison-of-array-and-arrayview"></a>Porównanie klas array i array_view  
W poniższej tabeli zestawiono podobieństwa i różnice między `array` i `array_view` klasy.  
  
|Opis|array — Klasa|array_view — klasa|  
|-----------------|-----------------|-----------------------|  
|Kiedy ustalana jest ranga|W czasie kompilacji.|W czasie kompilacji.|  
|Kiedy określany jest zakres|W czasie wykonywania.|W czasie wykonywania.|  
|Kształt|Prostokątny.|Prostokątny.|  
|Magazyn danych|Jest kontenerem danych.|Jest otoką danych.|  
|Kopiuj|Jawnego i głębokiego kopiowania w definicji.|Niejawne kopiowanie, gdy dostęp uzyskuje funkcja jądra.|  
|Pobieranie danych|Przez skopiowanie danych z powrotem do obiektu w wątku Procesora.|Przez bezpośredni dostęp do obiektu `array_view` obiektu lub przez wywołanie metody [array_view::synchronize — metoda](reference/array-view-class.md#synchronize) stałego dostępu do danych w oryginalnym kontenerze.|  
  
### <a name="shared-memory-with-array-and-arrayview"></a>Pamięć współużytkowana z tablicą i array_view  
Pamięć współużytkowana jest pamięcią, która może zostać oceniony przez Procesor ani akcelerator. Wykorzystanie pamięci współdzielonej eliminuje lub znacznie zmniejsza obciążenie kopiowania danych między procesorem a akceleratorem. Mimo że pamięć jest udostępniona, nie są dostępne w współbieżnie przez Procesor ani akcelerator, a czynność ta powoduje niezdefiniowane zachowanie.  
  
`array` obiekty mogą służyć do określenie dokładnej kontroli wykorzystania pamięci współdzielonej, jeśli skojarzony akcelerator obsługuje tę funkcję. Czy akcelerator obsługuje pamięć współużytkowaną jest określane przez akcelerator [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) właściwość, która zwraca **true** Jeśli pamięci współużytkowana jest obsługiwana. Jeśli pamięci współużytkowana jest obsługiwana, domyślny [access_type — wyliczenie](reference/concurrency-namespace-enums-amp.md#access_type) pamięci alokacji na akceleratorze jest określana przez `default_cpu_access_type` właściwości. Domyślnie `array` i `array_view` obiekty działają tak samo `access_type` jako podstawowe związane `accelerator`.  
  
Ustawiając [Array::cpu_access_type — członek danych](reference/array-class.md#cpu_access_type) właściwość `array` jawnie, możesz szczegółowe zasady wykonywania kontrolowania nad współużytkowaną pamięcią jest używany, dzięki czemu można zoptymalizować aplikację dla wydajności sprzętu właściwości, w oparciu o wzorce dostępu do pamięci jej jąder obliczeniowych odniosą. `array_view` Odzwierciedla tę samą `cpu_access_type` jako `array` skojarzonego z; lub, jeśli array_view jest skonstruowany bez źródła danych, jej `access_type` odzwierciedla środowisko, w którym po raz pierwszy powoduje przydzielanie pamięci masowej. Oznacza to, jeśli najpierw odbywa się przez hosta (CPU), następnie działa tak, jakby zostały utworzone przez źródło danych CPU i udziałów `access_type` z `accelerator_view` skojarzony przez Przechwytywanie; jednak jeśli po raz pierwszy dostępu `accelerator_view`, a następnie działa tak, jakby był to utworzone przez `array` tworzone na tym `accelerator_view` i udziałów `array`firmy `access_type`.  
  
Poniższy przykład kodu pokazuje, jak ustalić, czy akcelerator domyślny obsługuje pamięć współużytkowaną, a następnie tworzy kilka tablic, które mają różne konfiguracje cpu_access_type.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
  
using namespace Concurrency;  
  
int main()  
{  
    accelerator acc = accelerator(accelerator::default_accelerator);  
  
    // Early out if the default accelerator doesn’t support shared memory.  
    if (!acc.supports_cpu_shared_memory)  
    {  
        std::cout << "The default accelerator does not support shared memory" << std::endl;  
        return 1;  
    }  
  
    // Override the default CPU access type.  
    acc.default_cpu_access_type = access_type_read_write  
  
    // Create an accelerator_view from the default accelerator. The  
    // accelerator_view inherits its default_cpu_access_type from acc.  
    accelerator_view acc_v = acc.default_view;  
  
    // Create an extent object to size the arrays.  
    extent<1> ex(10);  
  
    // Input array that can be written on the CPU.  
    array<int, 1> arr_w(ex, acc_v, access_type_write);  
  
    // Output array that can be read on the CPU.  
    array<int, 1> arr_r(ex, acc_v, access_type_read);  
  
    // Read-write array that can be both written to and read from on the CPU.  
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);  
}  
```  
  
## <a name="executing-code-over-data-parallelforeach"></a>Wykonywanie kodu na danych: parallel_for_each  
 
[Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) funkcja definiuje kod, który chcesz uruchomić na akceleratorze przeciwko danym w `array` lub `array_view` obiektu. Należy wziąć pod uwagę następujący kod po wprowadzeniu tego tematu.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
void AddArrays() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5] = {0, 0, 0, 0, 0};  
  
    array_view<int, 1> a(5, aCPP);  
    array_view<int, 1> b(5, bCPP);  
    array_view<int, 1> sum(5, sumCPP);  
  
    parallel_for_each(  
        sum.extent,   
        [=](index<1> idx) restrict(amp)  
        {  
            sum[idx] = a[idx] + b[idx];  
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
```  
  
`parallel_for_each` Metoda przyjmuje dwa argumenty, domenę obliczeniową i Wyrażenie lambda.  
  
*Domenę obliczeniową* jest `extent` obiektu lub `tiled_extent` obiektu, który definiuje zestaw wątków do utworzenia dla przetwarzania równoległego. Jeden wątek jest generowany dla każdego elementu w domenie obliczeniowej. W tym przypadku `extent` obiektu jest jednowymiarowy i zawiera pięć elementów. Dlatego jest pięć wątków.  
  
*Wyrażenia lambda* definiuje kod, aby uruchomić w każdym wątku. Klauzula przechwytywania `[=]`, określa, że treść wyrażenia lambda uzyskuje dostęp do wszystkich przechwyconych zmiennych według wartości, które są w tym przypadku `a`, `b`, i `sum`. W tym przykładzie lista parametrów tworzy jednowymiarową `index` zmiennej o nazwie `idx`. Wartość `idx[0]` wynosi 0, w pierwszym wątku i zwiększa o jeden w każdym kolejnym wątku. `restrict(amp)` Wskazuje, że używany jest tylko podzbiór języka C++, który C++ AMP może przyspieszyć.  Ograniczenia dotyczące funkcji, które mają modyfikator są opisane w [ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md). Aby uzyskać więcej informacji znajduje się pozycja [Lambda Expression Syntax](../../cpp/lambda-expression-syntax.md).  
  
Wyrażenie lambda może zawierać kod do wykonania lub może wywołać oddzielną funkcję jądra. Funkcja jądra musi zawierać `restrict(amp)` modyfikator. Poniższy przykład jest równoważny do poprzedniego przykładu, ale wywołuje oddzielną funkcję jądra.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
void AddElements(
    index<1> idx,  
    array_view<int, 1> sum,  
    array_view<int, 1> a,  
    array_view<int, 1> b) restrict(amp) {  
    sum[idx] = a[idx] + b[idx];  
}  
  
void AddArraysWithFunction() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5] = {0, 0, 0, 0, 0};  
  
    array_view<int, 1> a(5, aCPP);  
    array_view<int, 1> b(5, bCPP);  
    array_view<int, 1> sum(5, sumCPP);  
  
    parallel_for_each(  
        sum.extent,   
        [=](index<1> idx) restrict(amp) {  
            AddElements(idx, sum, a, b);  
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
```  
  
## <a name="accelerating-code-tiles-and-barriers"></a>Kod przyspieszenia: Fragmenty i bariery  

Dodatkowe przyspieszenie można uzyskać za pomocą fragmentowania. Fragmentacja dzieli wątki na równe podzestawy prostokątne lub *Kafelki*. Należy określić odpowiedni rozmiar fragmentu na podstawie zestawu danych i algorytmu, który jest kodowany. Dla każdego wątku, masz dostęp do *globalnego* lokalizacji elementu danych w stosunku do całości `array` lub `array_view` oraz dostęp do *lokalnego* lokalizacji dla fragmentu. Przy użyciu lokalnej wartości indeksu upraszcza kod, ponieważ nie trzeba pisać kodu do przekształcania wartości indeksu z globalnej na lokalną. W celu użycia fragmentowania należy wywołać [Extent::Tile — metoda](reference/extent-class.md#tile) w domenie obliczeniowej w `parallel_for_each` metoda i użyj [tiled_index](../../parallel/amp/reference/tiled-index-class.md) obiektu w wyrażeniu lambda.  
  
W typowych aplikacjach elementy we fragmencie są powiązane w jakiś sposób, a kod musi uzyskać dostęp i śledzić wartości całym fragmencie. Użyj [tile_static — słowo kluczowe](../../cpp/tile-static-keyword.md) — słowo kluczowe i [tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait) w tym celu. Zmienna, która ma **tile_static** — słowo kluczowe ma zakres na całym fragmencie, a wystąpienie zmiennej jest tworzone dla każdego fragmentu. Należy obsłużyć synchronizację dostępu wątków fragmentu do zmiennej. [Tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait) zatrzymuje wykonywanie bieżącego wątku, dopóki wszystkie wątki we fragmencie osiągną wywołanie `tile_barrier::wait`. Więc można zbierać wartości całego fragmentu, za pomocą **tile_static** zmiennych. Następnie można zakończyć wszelkie obliczenia, które wymagają dostępu do wszystkich wartości.  
  
Poniższy diagram przedstawia dwuwymiarową tablicę danych próbkowania, które są ułożone WE fragmenty.  
  
![Indeks wartości w stopniu fragmentacji](../../parallel/amp/media/camptiledgridexample.png "camptiledgridexample")  
  
Poniższy przykład kodu używa danych próbkowania, z poprzedniego diagramu. Kod zastępuje każdą wartość we fragmencie średnią wartości we fragmencie.  
  
```cpp  
// Sample data:  
int sampledata[] = {  
    2, 2, 9, 7, 1, 4,  
    4, 4, 8, 8, 3, 4,  
    1, 5, 1, 2, 5, 2,  
    6, 8, 3, 2, 7, 2};  
 
// The tiles:  
// 2 2    9 7    1 4  
// 4 4    8 8    3 4  
//  
// 1 5    1 2    5 2  
// 6 8    3 2    7 2  
 
// Averages:  
int averagedata[] = {   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
};  
 
array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);  
  
parallel_for_each(  
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.  
    sample.extent.tile<2,2>(), 
        [=](tiled_index<2,2> idx) restrict(amp) { 
        // Create a 2 x 2 array to hold the values in this tile.  
        tile_static int nums[2][2];  

        // Copy the values for the tile into the 2 x 2 array.  
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];  

        // When all the threads have executed and the 2 x 2 array is complete, find the average.  
        idx.barrier.wait();  
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.  
        average[idx.global] = sum / 4;  
    });
  
for (int i = 0; i <4; i++) {  
    for (int j = 0; j <6; j++) {  
        std::cout << average(i,j) << " ";  
    }  
    std::cout << "\n";  
}  
 
// Output:  
// 3 3 8 8 3 3  
// 3 3 8 8 3 3  
// 5 5 2 2 4 4  
// 5 5 2 2 4 4  
```  
  
## <a name="math-libraries"></a>Biblioteki matematyczne  
 
C++ AMP zawiera dwie biblioteki funkcji matematycznych. Biblioteka podwójnej precyzji w [Namespace Concurrency::precise_math](../../parallel/amp/reference/concurrency-precise-math-namespace.md) zapewnia obsługę funkcji podwójnej precyzji. Umożliwia także pomocy technicznej dla funkcji pojedynczej precyzji, chociaż wsparcia podwójnej precyzji na sprzęcie jest nadal wymagana. Jest on zgodny z [specyfikacją C99 (ISO/IEC 9899)](http://go.microsoft.com/fwlink/p/?linkid=225887). Akcelerator musi pełni obsługiwać podwójną precyzję. Można określić, czy jest ona spełniona, sprawdzając wartość [Accelerator::supports_double_precision — członek danych](reference/accelerator-class.md#supports_double_precision). Szybka biblioteka funkcji matematycznych w [Namespace Concurrency::fast_math](../../parallel/amp/reference/concurrency-fast-math-namespace.md), zawiera inny zestaw funkcji matematycznych. Te funkcje, które obsługują tylko `float` , wykonują się dużo szybciej, ale nie są tak dokładne jak te w bibliotece funkcji matematycznych podwójnej precyzji. Funkcje są zawarte w \<amp_math.h > plik nagłówkowy i wszystkie są zadeklarowane za pomocą `restrict(amp)`. Funkcje w \<cmath > plik nagłówkowy są importowane do obu `fast_math` i `precise_math` przestrzeni nazw. **Ograniczyć** — słowo kluczowe jest używane do odróżniania \<cmath > i wersja języka C++ AMP. Poniższy kod oblicza logarytm base 10, przy użyciu metody szybkiej, dla każdej wartości, która znajduje się w domenie obliczeniowej.  

```cpp  
#include <amp.h>  
#include <amp_math.h>  
#include <iostream>  
using namespace concurrency;  
  
void MathExample() {  
  
    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };  
    array_view<double, 1> logs(6, numbers);  
  
    parallel_for_each(  
        logs.extent,  
 [=] (index<1> idx) restrict(amp) {  
            logs[idx] = concurrency::fast_math::log10(logs[idx]);  
        }  
    );  
  
    for (int i = 0; i < 6; i++) {  
        std::cout << logs[i] << "\n";  
    }  
}  
```  
  
## <a name="graphics-library"></a>Biblioteka graficzna  
 
C++ AMP zawiera bibliotekę graficzną, która jest przeznaczona do przyspieszonego programowania grafiki. Ta biblioteka jest używana tylko na urządzeniach, które obsługują macierzystą funkcjonalność graficzną. Metody znajdują się w [Namespace Concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) i są zawarte w \<amp_graphics.h > pliku nagłówka. Kluczowe składniki biblioteki graficznej to:  
  
- [Texture, klasa](../../parallel/amp/reference/texture-class.md): można użyć klasy texture do utworzenia tekstur z pamięci lub z pliku. Tekstury przypominają tablice, ponieważ zawierają one dane i przypominają kontenery w standardowej biblioteki języka C++ w odniesieniu do konstrukcji przydziału i kopiowania. Aby uzyskać więcej informacji, zobacz [standardowych kontenerów biblioteki języka C++](../../standard-library/stl-containers.md). Parametry szablonu dla `texture` klasy są typami elementu i rangi. Ranga może być 1, 2 lub 3. Typ elementu może być jednym z typów krótkich wektorów, które są opisane w dalszej części tego artykułu.  
  
- [writeonly_texture_view, klasa](../../parallel/amp/reference/writeonly-texture-view-class.md): umożliwia dostęp tylko do zapisu do wszelkich tekstur.  
  
- [Krótki wektor biblioteki](https://msdn.microsoft.com/4c4f5bed-c396-493b-a238-c347563f645f): definiuje zestaw typów krótkich wektorów, o długości 2, 3 i 4, które są oparte na **int**, `uint`, **float**, **double**, [norm](../../parallel/amp/reference/norm-class.md), lub [unorm](../../parallel/amp/reference/unorm-class.md).  
  
## <a name="universal-windows-platform-uwp-apps"></a>Universal Windows Platform (systemu Windows UWP) aplikacji  
 
Podobnie jak inne biblioteki C++ można użyć C++ AMP w aplikacjach platformy uniwersalnej systemu Windows. Artykuły te opisują sposób dołączyć kod C++ AMP w aplikacjach, który jest tworzony przy użyciu języka C++, C#, Visual Basic lub JavaScript:  
  
- [Korzystanie z C++ AMP w aplikacjach platformy uniwersalnej systemu Windows](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)  
  
- [Wskazówki: Tworzenie podstawowego składnika środowiska wykonawczego Windows w języku C++ i wywoływanie z kodu JavaScript](http://go.microsoft.com/fwlink/p/?linkid=249077)  
  
- [Zestaw Bing Maps optymalizatora podróży, app Store okna, w języku JavaScript i C++](http://go.microsoft.com/fwlink/p/?linkid=249078)  
  
- [Jak używać biblioteki C++ AMP z kodu C# za pomocą środowiska uruchomieniowego Windows](http://go.microsoft.com/fwlink/p/?linkid=249080)  
  
- [Jak używać biblioteki C++ AMP z kodu C#](http://go.microsoft.com/fwlink/p/?linkid=249081)  
  
- [Wywoływanie funkcji natywnych z kodu zarządzanego](../../dotnet/calling-native-functions-from-managed-code.md)  
  
## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP i Concurrency Visualizer  
 
Narzędzie Concurrency Visualizer zawiera obsługę dla analizowania wydajności kodu C++ AMP. Artykuły te opisują następujące funkcje:  
  
- [Wykres aktywności procesora GPU](/visualstudio/profiling/gpu-activity-graph)  
  
- [Aktywność procesora GPU (Stronicowanie)](/visualstudio/profiling/gpu-activity-paging)  
  
- [Aktywności procesora GPU (ten proces)](/visualstudio/profiling/gpu-activity-this-process)  
  
- [Aktywność procesora GPU (inne procesy)](/visualstudio/profiling/gpu-activity-other-processes)  
  
- [Kanały (Widok wątków)](/visualstudio/profiling/channels-threads-view)  
  
- [Analizowanie kodu C++ AMP w narzędziu Concurrency Visualizer](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)  
  
## <a name="performance-recommendations"></a>Zalecenia dotyczące wydajności  
 
Wyznaczanie modułu i dzielenie liczb całkowitych bez znaku ma znacznie lepszą wydajność niż wyznaczanie modułu i dzielenie liczb całkowitych ze znakiem. Zaleca się, że używasz możliwych liczb całkowitych bez znaku.  
  
## <a name="see-also"></a>Zobacz też  
 
[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
[Składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md)   
[Odwołanie (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)   
[Programowanie równoległe w kodzie macierzystym bloga](http://go.microsoft.com/fwlink/p/?linkid=238472)