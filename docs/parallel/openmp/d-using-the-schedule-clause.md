---
title: D. Użycie klauzuli harmonogramu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d40b22a5e724f8d8b587e2928d3d1305a7fa807a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446147"
---
# <a name="d-using-the-schedule-clause"></a>D. Użycie klauzuli harmonogramu

Równoległego regionu ma co najmniej jeden barierę na jej końcu i mogą mieć dodatkowe barier w nim. Przy każdej barierze członkowie zespołu musi czekać na ostatni wątek dostarczenie. Aby zminimalizować czas oczekiwania, należy rozdzielić udostępnionego pracy tak, aby wszystkie wątki docierają do zapory, w tym samym czasie. Jeśli niektóre z udostępnionego pracy jest zawarta w **dla** konstrukcji, `schedule` klauzuli może służyć do tego celu.

W przypadku wielokrotnego odwołań do obiektów tego samego, wybór harmonogram **dla** konstrukcji można ustalić przede wszystkim przez właściwości układu pamięci, takie jak obecności i rozmiar pamięci podręcznej oraz czy dostęp do pamięci czasy są jednolite lub niejednorodnej. Względy takie mogą wprowadzać preferowane każdy wątek spójnie odnoszą się do tego samego zestawu elementów tablicy w serii pętli, nawet jeśli niektóre wątki są przypisywane stosunkowo mniej pracy, w niektórych pętli. Można to zrobić za pomocą **statyczne** harmonogramu o tej samej granice dla wszystkich pętli. W poniższym przykładzie należy zauważyć, że zero jest używany jako dolną granicę w drugim pętli, nawet jeśli **k** będzie stosować bardziej naturalne, jeśli harmonogram nie są istotne.

```
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

Pozostałe przykłady zakłada się, że pamięć nie ma dostępu do dominującą kwestią i, chyba że określono inaczej, że wszystkie wątki będą otrzymywać porównywalne zasoby obliczeniowe. W takich przypadkach wybór harmonogram **dla** konstrukcja jest zależna od całą pracę udostępnionego, który ma być przeprowadzane od najbliższej poprzedzającej barierę i barierę dorozumianych zamknięcia lub najbliższej kolejnych barierze, jeśli istnieje `nowait` klauzuli. Dla każdego rodzaju harmonogram krótki przykład pokazuje, jak może być najlepszym wyborem jest tego typu harmonogramu. Krótkie omówienie następuje po każdym przykładzie.

**Statyczne** harmonogramu jest również odpowiednie dla najprostszym przypadku równoległego regionu zawierający pojedynczy **dla** konstruowania każda iteracja wymaga tej samej ilości pracy.

```
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

**Statyczne** harmonogram charakteryzuje się właściwości pobierające każdy wątek w mniej więcej taką samą liczbę iteracji jak dowolnego innego wątku, a każdy wątek można niezależnie określić iteracje przypisane do niego. Dlatego synchronizacja nie jest wymagane do dystrybucji utworu i przy założeniu, że każda iteracja wymaga tej samej ilości pracy wszystkie wątki powinno zostać zakończone w tym samym czasie.

Dla zespołu `p` wątków, umożliwiają *ceiling(n/p)* być liczba całkowita *pytania*, który spełnia *n = p\*q - r* za pomocą *0 < = r < p* . Jedna implementacja **statyczne** zaplanować dla tego przykładu przypisywanej *q* iteracji do pierwszego *p-1* wątków, i *q-r* iteracje do ostatniego wątku.  Inną implementację dopuszczalne przypisywanej *q* iteracji do pierwszego *p-r* wątków, i *q-1* iteracji do pozostałych *r*wątków. Obrazuje to, dlaczego program nie należy polegać na szczegółów konkretnej implementacji.

**Dynamiczne** harmonogramu jest odpowiednia w przypadku **dla** skonstruować przy użyciu iteracji, wymagające różnych lub nawet nieprzewidywalne ilości pracy.

```
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

**Dynamiczne** harmonogramu jest określony przez właściwość, która żaden wątek nie oczekuje na barierę dłużej niż Trwa inny wątek, aby wykonać jego iterację końcowej. Wymaga to, że iteracji można przypisać pojedynczo do wątków po ich udostępnieniu, za pomocą synchronizacji dla każdego przypisania. Można zmniejszyć obciążenie synchronizacji, określając rozmiaru fragmentu minimalne *k* większy niż 1, tak aby wątki są przypisane *k* aż mniej niż *k* pozostają. Gwarantuje to, że żaden wątek nie oczekuje na dłużej niż Trwa inny wątek (maksymalnie) wykonaj jego ostatni fragment o barierę *k* iteracji.

**Dynamiczne** harmonogram może być przydatne, jeśli wątki zmieniającego się zasoby obliczeniowe, który ma znacznie taki sam skutek jak różnej ilości pracy dla każdej iteracji. Podobnie, dynamiczne harmonogram również może być przydatne w przypadku wątków przyjeździe do biura **dla** konstruowania w różnym czasie, chociaż w niektórych przypadkach **z przewodnikiem** harmonogram może być korzystniejsze.

**z przewodnikiem** harmonogram jest odpowiednie w przypadku, w którym wątków może pojawić się w różnych okresach czasu w **dla** skonstruować przy użyciu każda iteracja wymaga o tej samej ilości pracy. Może się to zdarzyć, jeśli, na przykład **dla** konstrukcja jest poprzedzony jedną lub więcej sekcji lub **dla** tworzy się za pomocą `nowait` klauzul.

```
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

Podobnie jak **dynamiczne**, **z przewodnikiem** zaplanować gwarantuje, że żaden wątek nie czeka na barierę dłużej niż Trwa inny wątek, aby wykonać jego iterację końcowego lub końcowego *k* Liczba iteracji, jeśli rozmiaru fragmentu wynoszącego *k* jest określony. Wśród takie harmonogramy **z przewodnikiem** harmonogramu jest określony przez właściwość wymaga najmniejszą liczbą synchronizacji. Dla rozmiaru fragmentu *k*, przypisze Typowa implementacja *q = ceiling(n/p)* iteracji, aby pierwszy dostępny wątek, ustaw *n* dla większej z *n-q* i *p\*k*i powtórz aż przypisany do wszystkich iteracji.

Gdy wybór optymalnego harmonogramu nie jest jako zwykły, podobnie jak w przypadku tych przykładach **środowiska uruchomieniowego** harmonogramu jest wygodne do eksperymentowania z różne harmonogramy i rozmiarach, bez konieczności modyfikowania i ponownie skompilować program. Go może również być przydatne podczas optymalne harmonogram zależy od (w jakiś sposób przewidywalny) danych wejściowych, do którego zastosowano program.

Aby zobaczyć przykład kompromis między różne harmonogramy, należy wziąć pod uwagę udostępnianie 1000 iteracji między 8 wątków. Załóżmy, że istnieje niezmiennej ilość pracy w każdej iteracji i używać go jako jednostka czasu.

Jeśli wszystkie wątki uruchamia się w tym samym czasie **statyczne** harmonogramu spowoduje, że konstrukcji, które można wykonać w jednostkach 125, nie synchronizacji. Jednak Załóżmy, że jeden wątek wynosi 100 jednostek w przychodzących. Następnie poczekaj pozostałych wątków siedem dla 100 jednostek w barierę i czas wykonywania dla całego konstrukcji wzrasta do 225.

Ponieważ zarówno **dynamiczne** i **z przewodnikiem** harmonogramy zapewnienia, że żaden wątek nie czeka na więcej niż jednej jednostki w barierę opóźnione wątku powoduje, że ich czasy wykonania dla konstrukcji zwiększyć tylko do 138 jednostki zwiększonej opóźnieniami z synchronizacji. Jeśli takie opóźnienia jest nieistotny, staje się ważne, czy liczba synchronizacji to 1000 **dynamiczne** , ale tylko 41 dla **z przewodnikiem**, zakładając, że domyślny rozmiar fragmentu w jednej. Przy użyciu rozmiaru fragmentu wynoszącego 25 **dynamiczne** i **z przewodnikiem** zarówno w Zakończ 150 jednostki, a także wszelkich opóźnień z wymaganych synchronizacje, który numer teraz tylko 40 i 20, odpowiednio.