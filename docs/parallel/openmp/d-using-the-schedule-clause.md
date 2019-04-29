---
title: D. W klauzuli harmonogramu
ms.date: 01/22/2019
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
ms.openlocfilehash: 89e011784c5cccedc4a75f38d553458ea2e5d7e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362884"
---
# <a name="d-the-schedule-clause"></a>D. W klauzuli harmonogramu

Równoległego regionu ma co najmniej jeden barierę na jej końcu i mogą mieć dodatkowe barier w nim. Przy każdej barierze członkowie zespołu musi czekać na ostatni wątek dostarczenie. Aby zminimalizować czas oczekiwania, należy rozdzielić udostępnionego pracy tak, aby wszystkie wątki docierają do zapory, w tym samym czasie. Jeśli niektóre z udostępnionego pracy jest zawarta w `for` konstrukcji, `schedule` klauzuli może służyć do tego celu.

W przypadku wielokrotnego odwołań do obiektów tego samego, wybór harmonogram `for` konstrukcji można ustalić przede wszystkim przez właściwości układu pamięci, takie jak obecności i rozmiar pamięci podręcznej oraz tego, czy czas dostępu do pamięci są jednolite, lub nonuniform. Względy takie mogą wprowadzać preferowane każdy wątek spójnie odnoszą się do tego samego zestawu elementów tablicy w serii pętli, nawet jeśli niektóre wątki są przypisywane stosunkowo mniej pracy, w niektórych pętli. Ta konfiguracja może odbywać się przy użyciu `static` harmonogramu o tej samej granice dla wszystkich pętli. W poniższym przykładzie zero jest używany jako dolną granicę w drugim pętli, nawet jeśli `k` będzie stosować bardziej naturalne, jeśli harmonogram nie są istotne.

```cpp
#pragma omp parallel
{
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    a[i] = work1(i);
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    if(i>=k) a[i] += work2(i);
}
```

Pozostałe przykłady przejęła pamięci dostępu nie jest dominującym brany pod uwagę. Jeżeli nie określono inaczej, że wszystkie wątki będą otrzymywać porównywalne zasoby obliczeniowe. W takich przypadkach wybór harmonogram `for` konstrukcja jest zależna od całą pracę udostępnionego, który ma być przeprowadzane od najbliższej poprzedzającej barierę i barierę dorozumianych zamknięcia lub najbliższej nadchodzących barierze, jeśli istnieje `nowait` Klauzula. Dla każdego rodzaju harmonogram krótki przykład pokazuje, jak może być najlepszym wyborem jest tego typu harmonogramu. Krótkie omówienie następuje po każdym przykładzie.

`static` Harmonogramu jest również odpowiednie dla najprostszym przypadku równoległego regionu zawierający pojedynczy `for` konstruowania każda iteracja wymaga tej samej ilości pracy.

```cpp
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

`static` Harmonogram charakteryzuje się właściwości pobierające każdy wątek w mniej więcej taką samą liczbę iteracji jak dowolnego innego wątku, a każdy wątek można niezależnie określić iteracje przypisane do niego. Dlatego synchronizacja nie jest wymagane do dystrybucji utworu i przy założeniu, że każda iteracja wymaga tej samej ilości pracy wszystkie wątki powinno zostać zakończone w tym samym czasie.

Dla zespołu *p* wątków, umożliwiają *ceiling(n/p)* być liczba całkowita *q*, który spełnia *n = p\*q - r* z *0 < = r < p*. Jedna implementacja `static` zaplanować dla tego przykładu przypisywanej *q* iteracji do pierwszego *p-1* wątków, i *q-r* iteracji do ostatniego wątku.  Inną implementację dopuszczalne przypisywanej *q* iteracji do pierwszego *p-r* wątków, i *q-1* iteracji do pozostałych *r*wątków. Ten przykład ilustruje, dlatego program nie powinien zależą od szczegółów konkretnej implementacji.

`dynamic` Harmonogramu jest odpowiednia w przypadku `for` skonstruować przy użyciu iteracji, wymagające różnych lub nawet nieprzewidywalne ilości pracy.

```cpp
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

`dynamic` Harmonogramu jest określony przez właściwość, która żaden wątek nie oczekuje na barierę dłużej niż Trwa inny wątek, aby wykonać jego iterację końcowej. Wymaganie to oznacza, że iteracji należy przypisać pojedynczo do wątków w miarę ich udostępniania przy synchronizacji dla każdego przypisania. Można zmniejszyć obciążenie synchronizacji, określając rozmiaru fragmentu minimalne *k* większy niż 1, tak aby wątki są przypisane *k* aż mniej niż *k* pozostają. Gwarantuje to, że żaden wątek nie oczekuje na dłużej niż Trwa inny wątek (maksymalnie) wykonaj jego ostatni fragment o barierę *k* iteracji.

`dynamic` Harmonogram może być przydatne, jeśli wątki zmieniającego się zasoby obliczeniowe, który ma znacznie taki sam skutek jak różnej ilości pracy dla każdej iteracji. Podobnie, dynamiczne harmonogram również może być przydatne w przypadku wątków przyjeździe do biura `for` konstruowania w różnym czasie, chociaż w niektórych przypadkach `guided` harmonogram może być korzystniejsze.

`guided` Harmonogram jest odpowiednie w przypadku, w którym wątków może pojawić się w różnych okresach czasu w `for` skonstruować przy użyciu każda iteracja wymaga o tej samej ilości pracy. Ta sytuacja może wystąpić, jeśli, na przykład `for` konstrukcja jest poprzedzony jedną lub więcej sekcji lub `for` tworzy się za pomocą `nowait` klauzul.

```cpp
#pragma omp parallel
{
  #pragma omp sections nowait
  {
    // ...
  }
  #pragma omp for schedule(guided)
  for(i=0; i<n; i++) {
    invariant_amount_of_work(i);
  }
}
```

Podobnie jak `dynamic`, `guided` zaplanować gwarantuje, że żaden wątek nie czeka na barierę dłużej niż Trwa inny wątek, aby wykonać jego iterację końcowego lub końcowego *k* iteracji, jeśli rozmiaru fragmentu wynoszącego *k* jest określony. Wśród takie harmonogramy `guided` harmonogramu jest określony przez właściwość wymaga najmniejszą liczbą synchronizacji. Dla rozmiaru fragmentu *k*, przypisze Typowa implementacja *q = ceiling(n/p)* iteracji, aby pierwszy dostępny wątek, ustaw *n* dla większej z *n-q* i *p\*k*i powtórz aż przypisany do wszystkich iteracji.

Podczas wyboru optymalnego harmonogramu nie jako zwykły, podobnie jak w przypadku tych przykładach `runtime` harmonogramu jest wygodne do eksperymentowania z różne harmonogramy i rozmiarach, bez konieczności modyfikowania i ponownie skompilować program. Go może również być przydatne podczas optymalne harmonogram zależy od (w jakiś sposób przewidywalny) danych wejściowych, do którego zastosowano program.

Aby zobaczyć przykład kompromis między różne harmonogramy, należy wziąć pod uwagę udostępnianie 1000 iteracji między ośmioma wątków. Załóżmy, że istnieje niezmiennej ilość pracy w każdej iteracji i używać go jako jednostka czasu.

Jeśli wszystkie wątki uruchamia się w tym samym czasie `static` harmonogramu spowoduje, że konstrukcji, które można wykonać w jednostkach 125, nie synchronizacji. Jednak Załóżmy, że jeden wątek wynosi 100 jednostek w przychodzących. Następnie poczekaj pozostałych wątków siedem dla 100 jednostek w barierę i czas wykonywania dla całego konstrukcji wzrasta do 225.

Ponieważ zarówno `dynamic` i `guided` harmonogramy upewnij się, że żaden wątek nie czeka na więcej niż jednej jednostki w barierę opóźnione wątku powoduje, że ich czasy wykonania dla konstrukcji zwiększyć jedynie do jednostek 138 zwiększonej opóźnieniami z Synchronizacja. Jeśli takie opóźnienia nie są niewielkie, staje się ważne, czy liczba synchronizacji to 1000 `dynamic` , ale tylko 41 dla `guided`, zakładając, że domyślny rozmiar fragmentu jednego. Przy użyciu rozmiaru fragmentu wynoszącego 25 `dynamic` i `guided` zarówno w Zakończ 150 jednostki, a także wszelkich opóźnień z wymaganych synchronizacje, który numer teraz tylko 40 i 20, odpowiednio.
