---
title: "Przegląd C++ AMP | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0ee5b9c04794c531e2fa16cee72d6eee607dfbd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="c-amp-overview"></a>Przegląd C++ AMP
C++ Accelerated Massive Parallelism (C++ AMP) przyspiesza wykonywanie kodu C++ dzięki wykorzystaniu danych równoległe sprzętu, takie jak procesor graficzny (GPU) na karcie odrębne grafika. Przy użyciu C++ AMP, można kodu algorytmy danych wielowymiarowych, dzięki czemu wykonanie może przyspieszyć przy użyciu równoległości w heterogenicznych sprzętu. Model programowania C++ AMP zawiera tablice wielowymiarowe, indeksowania, transfer pamięci, kafelków i bibliotekę matematyczna funkcji. Aby kontrolować sposób przenoszenia danych z Procesora GPU i na odwrót, dzięki czemu można zwiększyć wydajność, można użyć rozszerzenia języka C++ AMP.  
  
## <a name="system-requirements"></a>Wymagania systemowe  
  
- [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)], lub [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]  
  
-   DirectX 11 funkcji poziom 11.0 lub nowszy sprzętu  
  
-   Do debugowania w emulatorze oprogramowania [!INCLUDE[win8](../../build/reference/includes/win8_md.md)] lub [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] jest wymagana. Do debugowania na sprzęcie, musisz zainstalować sterowników dla karty graficznej. Aby uzyskać więcej informacji, zobacz [debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code).  
  
## <a name="introduction"></a>Wprowadzenie  
 Dwa poniższe przykłady przedstawiają podstawowych składników C++ AMP. Załóżmy, że chcesz dodać odpowiednie elementy dwie tablice jednowymiarowe. Na przykład można dodać `{1, 2, 3, 4, 5}` i `{6, 7, 8, 9, 10}` uzyskanie `{7, 9, 11, 13, 15}`. Bez korzystania z C++ AMP może zapisać następujący kod, aby dodać liczby i wyświetlić wyniki.  
  
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
  
 Ważne fragmenty kodu są następujące:  
  
-   Dane: Danych składa się z trzech tablic. Wszystkie mają taką samą rangę (jeden) i długości (5).  
  
-   Iteracja: Pierwszy `for` pętli udostępnia mechanizm iteracja elementów w tablicach. Kod, który będzie wykonywany do obliczenia sumy znajduje się w pierwszym `for` bloku.  
  
-   Indeks: `idx` zmiennej uzyskuje dostęp do poszczególnych elementów tablic.  
  
 Korzystanie z C++ AMP, można napisać kod następujących zamiast tego.  
  
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
  
 Te same elementy podstawowe są obecne, ale konstrukcje C++ AMP:  
  
-   Dane: Umożliwia C++ — tablice utworzyć trzy C++ AMP [array_view —](../../parallel/amp/reference/array-view-class.md) obiektów. Należy podać cztery wartości do utworzenia `array_view` obiektu: wartości danych, rangę typ elementu i długość `array_view` obiektu w każdego wymiaru. Ranga i typ są przekazywane jako parametry typu. Dane i długość są przekazywane jako parametry konstruktora. W tym przykładzie tablica C++, która jest przekazany do konstruktora jest jednowymiarowa. Ranga i długość są używane do skonstruowania prostokątnego kształtu danych w `array_view` obiektu, a dane wartości są używane do wypełnienia tablicy. Obejmuje także biblioteki środowiska uruchomieniowego [array — klasa](../../parallel/amp/reference/array-class.md), który ma interfejs, który jest podobny `array_view` klasy i omówione w dalszej części tego artykułu.  
  
-   Iteracja: [parallel_for_each — funkcja (C++ AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) zapewnia mechanizm iteracja elementy danych lub *obliczeniowe domeny*. W tym przykładzie domenie obliczeniowej jest określony przez `sum.extent`. Kod, który będzie wykonywany jest zawarty w wyrażeniu lambda lub *funkcji jądra*. `restrict(amp)` Wskazuje, że jest używana tylko podzbiór języka C++, która umożliwia przyspieszanie C++ AMP.  
  
-   Indeks: [indeksu klasy](../../parallel/amp/reference/index-class.md) zmiennej `idx`, jest zadeklarowany za pomocą Rząd równy jeden, aby dopasować rangę `array_view` obiektu. Korzystając z indeksu, można uzyskać dostęp do poszczególnych elementów `array_view` obiektów.  
  
## <a name="shaping-and-indexing-data-index-and-extent"></a>Formowanie i indeksowania danych: indeks i zakresu  
 Należy określić wartości danych i zadeklarować kształtu danych przed uruchomieniem kodu jądra. Wszystkie dane są zdefiniowane jako tablica (prostokątny), a można zdefiniować tablicy, tak aby mieć żadnych rangę (liczba wymiarów). Dane mogą być dowolnej wielkości, w żadnym z wymiarów.  
  
### <a name="index-class"></a>index — Klasa  
 [Indeksu klasy](../../parallel/amp/reference/index-class.md) Określa lokalizację w `array` lub `array_view` obiektu hermetyzując przesunięcie od źródła w każdego wymiaru do jednego obiektu. Gdy uzyskujesz dostęp do lokalizacji w tablicy, Przekaż `index` obiektu do indeksowania operatora `[]`, zamiast listy liczb całkowitych. Dostęp do elementów w każdego wymiaru przy użyciu [array:: operator() — Operator](reference/array-class.md#operator_call) lub [array_view::operator() Operator](reference/array-view-class.md#operator_call).  
  
 Poniższy przykład tworzy jednowymiarowa indeks, który określa trzeciego elementu w jednowymiarowa `array_view` obiektu. Indeks służy do drukowania trzeciego elementu w `array_view` obiektu. Dane wyjściowe to 3.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5};  
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";    
// Output: 3  
```  
  
 Poniższy przykład tworzy dwuwymiarowa indeks, który określa element gdzie wiersz = 1 i kolumna = 2 w dwuwymiarowa `array_view` obiektu. Pierwszy parametr w `index` Konstruktor jest składnikiem wiersza, a drugi parametr jest składnikiem kolumny. Dane wyjściowe to 6.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6};  
array_view<int, 2> a(2, 3, aCPP);  
  
index<2> idx(1, 2);  
  
std::cout <<a[idx] << "\n";    
// Output: 6  
```  
  
 Poniższy przykład tworzy trójwymiarowy indeks, który określa element gdzie głębokość = 0, wiersz = 1, a kolumna = 3, trójwymiarowy `array_view` obiektu. Zauważyć, że pierwszym parametrem jest składnik głębokość, drugi parametr jest składnikiem wiersza, a trzeci parametr jest składnikiem kolumny. Dane wyjściowe to 8.  
  
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
 [Extent — klasa](../../parallel/amp/reference/extent-class.md) określa długość danych w każdego wymiaru `array` lub `array_view` obiektu. Można utworzyć zakres i umożliwia tworzenie `array` lub `array_view` obiektu. Można również pobierać zakres istniejące `array` lub `array_view` obiektu. Poniższy przykład drukuje długość zakresu w każdego wymiaru `array_view` obiektu.  
  
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
  
 Poniższy przykład tworzy `array_view` obiektu, który ma takie same wymiary jako obiekt w poprzednim przykładzie, ale w tym przykładzie używa `extent` obiektu zamiast jawne parametry w `array_view` konstruktora.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};  
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";  
std::cout << "The number of rows is " << a.extent[1] << "\n";  
std::cout << "The depth is " << a.extent[0] << "\n";  
```  
  
## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>Przenoszenie danych do akceleratora: tablica i array_view —  
 Dwa kontenery danych używane do przenoszenia danych do akceleratora są definiowane w Biblioteka środowiska uruchomieniowego. Są one [array — klasa](../../parallel/amp/reference/array-class.md) i [array_view — klasa](../../parallel/amp/reference/array-view-class.md). `array` Klasy to klasa kontenera, która tworzy głęboką kopię danych podczas konstruowania obiektu. `array_view` Klasy to klasa otoki, które kopiuje dane, gdy funkcja jądra uzyskuje dostęp do danych. Gdy dane są potrzebne na urządzeniu źródła danych jest kopiowana ponownie.  
  
### <a name="array-class"></a>array — Klasa  
 Gdy `array` obiekt jest tworzony, głęboką kopię danych jest tworzona na akceleratora, jeśli używasz konstruktora, który zawiera wskaźnik do zestawu danych. Funkcja jądra modyfikuje kopii na akceleratora. Po zakończeniu wykonywania funkcji jądra, należy skopiować dane do struktury źródła danych. Poniższy przykład mnoży każdego elementu w wektorze przez 10. Po zakończeniu działania funkcji jądra `vector conversion operator` służy do kopiowania danych do obiektu wektora.  
  
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
 `array_view` Ma niemal tych samych elementów członkowskich jako `array` klasy, ale podstawowe zachowanie nie jest taka sama. Dane przekazywane do `array_view` Konstruktor nie jest replikowana na procesorze GPU, jak w przypadku `array` konstruktora. Zamiast tego dane są kopiowane do akceleratora podczas wykonywania funkcji jądra. Dlatego w przypadku utworzenia dwóch `array_view` obiektów, które używają tych samych danych, zarówno `array_view` obiektów odwoływać się do tego samego obszaru pamięci. Po wykonaniu tej czynności należy zsynchronizować wielowątkowych dostęp. Główną zaletą `array_view` klasy jest przenoszenia danych tylko wtedy, gdy jest to konieczne.  
  
### <a name="comparison-of-array-and-arrayview"></a>Porównanie tablicy i array_view —  
 Poniższa tabela zawiera podsumowanie podobieństwa i różnice między `array` i `array_view` klasy.  
  
|Opis|array — Klasa|array_view — klasa|  
|-----------------|-----------------|-----------------------|  
|Gdy pozycja jest określana|W czasie kompilacji.|W czasie kompilacji.|  
|Gdy zakres jest określany|W czasie wykonywania.|W czasie wykonywania.|  
|Kształt|Prostokątny.|Prostokątny.|  
|Magazyn danych|To kontener danych.|Jest otoką elementu danych.|  
|Kopiuj|Jawne i głębokie kopiowanie w definicji.|Niejawne kopiowania na dostępie przy użyciu funkcji jądra.|  
|Pobieranie danych|Przez skopiowanie danych tablicy obiektu w wątku procesora CPU.|Przez bezpośredni dostęp do `array_view` obiektu lub poprzez wywołanie [array_view::synchronize — metoda](reference/array-view-class.md#synchronize) aby kontynuować, uzyskiwanie dostępu do danych w oryginalnej kontenera.|  
  
### <a name="shared-memory-with-array-and-arrayview"></a>Pamięci współużytkowanej tablicy i array_view —  
 Pamięci współużytkowanej jest pamięci dostępnej dla procesora CPU i akceleratora. Użycie pamięci współużytkowanej eliminuje lub znacznie zmniejsza obciążenie związane z kopiowanie danych między procesora CPU i akceleratora. Choć jest udostępniana pamięć, jest niedostępny jednocześnie przez procesor CPU i akceleratora i powoduje to niezdefiniowane zachowanie.  
  
 `array` obiekty może służyć do określenia precyzyjną kontrolę nad użycie pamięci współużytkowanej, jeśli skojarzone akceleratora obsługuje. Czy akceleratora obsługuje pamięci współużytkowanej jest określany przez akceleratora [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) właściwość, która zwraca `true` po pamięci współużytkowanej jest obsługiwana. Jeśli jest obsługiwany pamięci współużytkowanej, domyślnie [access_type — wyliczenie](reference/concurrency-namespace-enums-amp.md#access_type) pamięci alokacje na akceleratora jest określany przez `default_cpu_access_type` właściwości. Domyślnie `array` i `array_view` zająć obiekty na tym samym `access_type` jako podstawowy skojarzony `accelerator`.  
  
 Przez ustawienie [Array::cpu_access_type — członek danych](reference/array-class.md#cpu_access_type) właściwość `array` jawnie, możesz wykonywania szczegółowych sterować za pośrednictwem udostępnionych pamięć jest używana, tak, aby zoptymalizować aplikacji wydajności sprzętu właściwości, na podstawie wzorców dostępu do pamięci jądra jego obliczeń. `array_view` Odzwierciedla takie same `cpu_access_type` jako `array` skojarzonego z; lub, jeśli array_view — został skonstruowany bez źródła danych, jej `access_type` odzwierciedla środowiska, która najpierw go przydzielić magazyn. Oznacza to, jeśli jest on dostępny najpierw przez hosta (CPU), następnie działa tak, jakby zostały utworzone przez procesor CPU źródła danych i udziałów `access_type` z `accelerator_view` skojarzona przez przechwytywania; jednak jeśli jest to pierwszy dostępu `accelerator_view`, a następnie zachowuje się tak, jakby była utworzone przez `array` utworzone na tej `accelerator_view` i udostępnia `array`w `access_type`.  
  
 Poniższy przykład kodu pokazuje sposób określania, czy obsługuje pamięci współużytkowanej akceleratora domyślne, a następnie tworzy wiele tablic, które mają cpu_access_type różne konfiguracje.  
  
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
  
## <a name="executing-code-over-data-parallelforeach"></a>Wykonywanie kodu nad danymi: parallel_for_each  
 [Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) funkcja definiuje kod, który ma zostać uruchomione na akceleratora z danymi w `array` lub `array_view` obiektu. Rozważmy poniższy kod po wprowadzeniu tego tematu.  
  
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
  
 `parallel_for_each` Metoda przyjmuje dwa argumenty, domenie obliczeniowej i wyrażenia lambda.  
  
 *Obliczeniowe domeny* jest `extent` obiektu lub `tiled_extent` obiektu, który definiuje zestaw wątków, aby utworzyć dla przetwarzania równoległego. Jeden wątek jest generowany dla każdego elementu w domenie obliczeniowej. W takim przypadku `extent` obiektu jednowymiarowa i ma pięć elementów. W związku z tym pięciu wątki są uruchamiane.  
  
 *Wyrażenia lambda* definiuje kodu do uruchomienia na każdy wątek. W klauzuli przechwytywania `[=]`, określa, że treść wyrażenia lambda uzyskuje dostęp do wszystkich przechwyconych zmiennych wg wartości, które są w tym przypadku `a`, `b`, i `sum`. W tym przykładzie lista parametrów tworzy jednowymiarowa `index` zmiennej o nazwie `idx`. Wartość `idx[0]` jest równa 0 w pierwszym wątkiem i zwiększa o jeden w każdym kolejnych wątku. `restrict(amp)` Wskazuje, że jest używana tylko podzbiór języka C++, która umożliwia przyspieszanie C++ AMP.  Ograniczenia dotyczące funkcji, które mają modyfikator Ogranicz opisanym w [Ogranicz (C++ AMP)](../../cpp/restrict-cpp-amp.md). Aby uzyskać więcej informacji zobacz, [składnia wyrażenia Lambda](../../cpp/lambda-expression-syntax.md).  
  
 Wyrażenia lambda mogą zawierać kod do wykonania lub może wywołać funkcję oddzielne jądra. Funkcja jądra musi zawierać `restrict(amp)` modyfikator. Poniższy przykład jest odpowiednikiem poprzedniego przykładu, ale wywołuje funkcję oddzielne jądra.  
  
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
  
## <a name="accelerating-code-tiles-and-barriers"></a>Zwiększającej tempo kodu: Kafelki i bariery  

 Aby uzyskać dodatkowe przyspieszenie przy użyciu kafelków. Kafelków dzieli wątki równy podzestawy prostokątne lub *Kafelki*. Należy określić rozmiar kafelka odpowiednie na podstawie zestawu danych i algorytm są kodowania. Dla każdego wątku, musisz mieć dostęp do *globalne* lokalizacji elementu danych względem całego `array` lub `array_view` i uzyskiwanie dostępu do *lokalnego* lokalizacji względnej wobec kafelka. Używając wartości indeksu lokalnej upraszcza kodu, ponieważ nie trzeba napisać kod do przekształcania wartości indeksu globalnego lokalnymi. Aby użyć kafelków, należy wywołać [extent::tile — metoda](reference/extent-class.md#tile) w domenie obliczeniowej w `parallel_for_each` — metoda i użyj [tiled_index —](../../parallel/amp/reference/tiled-index-class.md) obiektu w wyrażeniu lambda.  
  
 W typowych aplikacjach elementów na kafelku są powiązane w inny sposób, a kod ma dostęp i śledzenie wartości na kafelku. Użyj [tile_static — słowo kluczowe](../../cpp/tile-static-keyword.md) — słowo kluczowe i [tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait) w tym celu. Zmienna, która ma `tile_static` — słowo kluczowe ma zakres przez cały kafelka i wystąpienia zmiennej jest tworzony dla każdego kafelka. Synchronizacja wątku kafelka dostępu do zmiennej musi obsługiwać. [Tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait) zatrzymuje wykonanie bieżącego wątku, dopóki wszystkie wątki na kafelku osiągnięto wywołanie `tile_barrier::wait`. Dlatego użytkownik może spowodować zgromadzenie wartości na kafelku przy użyciu `tile_static` zmiennych. Następnie można zakończyć wszystkie obliczenia, które wymagają dostępu do wszystkich wartości.  

  
 Poniższy diagram przedstawia jest tablicą dwuwymiarową pobierania próbek danych, które są rozmieszczone na kafelkach.  
  
 ![Indeks wartości w układzie sąsiadującym zakresie](../../parallel/amp/media/camptiledgridexample.png "camptiledgridexample")  
  
 Poniższy przykład kodu wykorzystuje próbkowania danych z poprzedniego diagramu. Ten kod zastępuje każdej wartości na kafelku przez średnią z wartości na kafelku.  
  
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
 C++ AMP zawiera dwa biblioteki matematyczne. Biblioteka podwójnej precyzji w [Namespace CONCURRENCY::precise_math —](../../parallel/amp/reference/concurrency-precise-math-namespace.md) zapewnia obsługę funkcji podwójnej precyzji. Zapewnia także obsługę funkcji pojedynczej precyzji, mimo że nadal wymagana jest obsługa podwójnej precyzji na sprzęcie. Jest on zgodny z [C99 specyfikacji (ISO/IEC 9899)](http://go.microsoft.com/fwlink/p/?linkid=225887). Akceleratora musi obsługiwać pełnej podwójnej precyzji. Można określić, czy operacje wartości [Accelerator::supports_double_precision — członek danych](reference/accelerator-class.md#supports_double_precision). Biblioteki matematyczne szybkiego, w [Namespace CONCURRENCY::fast_math —](../../parallel/amp/reference/concurrency-fast-math-namespace.md), zawiera inny zestaw funkcji matematycznych. Te funkcje, które obsługują tylko `float` argumentów operacji, wykonać szybciej, ale nie jako dokładne, jak te w bibliotece matematyczne podwójnej precyzji. Funkcje są zawarte w \<amp_math.h > plik nagłówka i wszystkie są deklarowane jako z `restrict(amp)`. Funkcje w \<cmath > plik nagłówka są importowane do obu `fast_math` i `precise_math` przestrzeni nazw. `restrict` Słowo kluczowe jest używane w celu rozróżnienia \<cmath > i wersja C++ AMP. Poniższy kod oblicza logarytm base-10, przy użyciu metody szybkiego, w każdej wartości, który znajduje się w domenie obliczeniowej.  

  
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
  
## <a name="graphics-library"></a>Biblioteka grafiki  
 C++ AMP zawiera bibliotekę grafiki, które jest przeznaczone do programowania grafiki przyspieszonego. Ta biblioteka jest używana tylko na urządzeniach, które obsługuje funkcje graficzne macierzystego. Te metody są w [Namespace Concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) i są zawarte w \<amp_graphics.h > pliku nagłówka. Najważniejsze składniki bibliotekę grafiki są:  
  
- [Texture — klasa](../../parallel/amp/reference/texture-class.md): klasa tekstury umożliwia utworzenie tekstury z pamięci lub z pliku. Tekstury przypominać tablic, ponieważ zawierają one dane, a są podobne do kontenerów w standardowa biblioteka C++ względem przydziałów i tworzenia kopii. Aby uzyskać więcej informacji, zobacz [standardowe kontenery biblioteki C++](../../standard-library/stl-containers.md). Parametry szablonu `texture` klasy to typ elementu i rangę. Pozycja może być 1, 2 lub 3. Typ elementu może być jedną z typami wektorów krótki, które zostały opisane w dalszej części tego artykułu.  
  
- [writeonly_texture_view — klasa](../../parallel/amp/reference/writeonly-texture-view-class.md): umożliwia dostęp tylko do zapisu do dowolnego tekstury.  
  
- [Krótka biblioteki wektor](http://msdn.microsoft.com/en-us/4c4f5bed-c396-493b-a238-c347563f645f): definiuje zestaw typów krótkich wektor o długości 2, 3 i 4, które są oparte na `int`, `uint`, `float`, `double`, [normy](../../parallel/amp/reference/norm-class.md), lub [unorm —](../../parallel/amp/reference/unorm-class.md).  
  
## <a name="universal-windows-platform-uwp-apps"></a>Aplikacji platformy Uniwersalnej uniwersalnych systemu Windows  
 Podobnie jak inne biblioteki języka C++ można użyć C++ AMP w aplikacjach platformy uniwersalnej systemu Windows. Te artykuły zawierają opis uwzględnienie kodu C++ AMP w aplikacjach, która jest tworzona przy użyciu języka C++, C#, Visual Basic lub JavaScript:  
  
- [Korzystanie z C++ AMP w aplikacjach platformy uniwersalnej systemu Windows](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)  
  
- [Wskazówki: Tworzenie podstawowego składnika środowiska wykonawczego systemu Windows w języku C++ i wywoływania go z poziomu języka JavaScript](http://go.microsoft.com/fwlink/p/?linkid=249077)  
  
- [Optymalizator podróży, aplikację ze Sklepu Windows, JavaScript i C++ mapy Bing](http://go.microsoft.com/fwlink/p/?linkid=249078)  
  
- [Jak używać C++ AMP w języku C# za pomocą środowiska wykonawczego systemu Windows](http://go.microsoft.com/fwlink/p/?linkid=249080)  
  
- [Jak używać C++ AMP w języku C#](http://go.microsoft.com/fwlink/p/?linkid=249081)  
  
- [Wywoływanie funkcji natywnych z kodu zarządzanego](../../dotnet/calling-native-functions-from-managed-code.md)  
  
## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP i Concurrency Visualizer  
 Narzędzia Concurrency Visualizer obsługuje analizowania wydajności kodu C++ AMP. Te artykuły zawierają następujące funkcje:  
  
- [Wykres aktywności procesora GPU](/visualstudio/profiling/gpu-activity-graph)  
  
- [Aktywność procesora GPU (Stronicowanie)](/visualstudio/profiling/gpu-activity-paging)  
  
- [Aktywności procesora GPU (ten proces)](/visualstudio/profiling/gpu-activity-this-process)  
  
- [Aktywność procesora GPU (inne procesy)](/visualstudio/profiling/gpu-activity-other-processes)  
  
- [Kanały (Widok wątków)](/visualstudio/profiling/channels-threads-view)  
  
- [Analizowanie kodu C++ AMP z narzędzia Concurrency Visualizer](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)  
  
## <a name="performance-recommendations"></a>Zalecenia dotyczące wydajności  
 Modulo i dzielenia liczb całkowitych bez znaku mają znacznie lepszą wydajność niż modulo i dzielenia liczb całkowitych ze znakiem. Zaleca się, że używasz możliwe liczb całkowitych bez znaku.  
  
## <a name="see-also"></a>Zobacz też  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md)   
 [Odwołanie (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)   
 [Programowanie równoległe w blogu kodu natywnego](http://go.microsoft.com/fwlink/p/?linkid=238472)
