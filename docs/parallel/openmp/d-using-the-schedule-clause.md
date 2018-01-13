---
title: D. Zgodnie z harmonogramem klauzuli | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b51eeb36a4cffafde0e90586fec08d28b9672e5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="d-using-the-schedule-clause"></a>D. Zgodnie z harmonogramem — klauzula
Równoległego regionu ma co najmniej jeden bariery na jej końcu i mogą mieć dodatkowe bariery w niej. W każdej bariery ostatni wątek odebranie należy poczekać innych członków zespołu. Aby zminimalizować czas oczekiwania, pracy udostępniony powinien zostać przekazany tak, aby wszystkie wątki przyjeździe zapory w o tym samym czasie. Jeśli niektóre z udostępnionego pracy jest zawarta w **dla** konstrukcje, `schedule` klauzuli może służyć do tego celu.  
  
 W przypadku wielokrotnego odwołania do tego samego obiektów, wybór harmonogram **dla** konstrukcji mogą być określone głównie przez właściwości układu pamięci, takich jak obecność i rozmiar pamięci podręcznej oraz określa, czy dostęp do pamięci czas jest wyrównana lub niejednorodnej. Takie zagadnienia może być najlepszym podejściem każdy wątek spójnie odwoływać się do tego samego zestawu elementów tablicy w szeregu pętle, nawet jeśli niektóre wątki są przypisane stosunkowo mniej pracy w niektórych pętli. Można to zrobić za pomocą **statycznych** harmonogramu o tym samym zakresem dla wszystkich pętle. W poniższym przykładzie, należy pamiętać, że zero jest używany jako dolnej granicy w drugiej pętli, nawet jeśli **k** będzie bardziej naturalne harmonogramu nie są istotne.  
  
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
  
 W pozostałych przykładach, zakłada się, że pamięć dostępu nie jest dominującą brany pod uwagę i, chyba że określono inaczej, że wszystkie wątki będą otrzymywać można porównywać pod względem zasobów obliczeniowych. W takich przypadkach wybór harmonogram **dla** konstrukcja zależy od wszystkich udostępnionych pracy, którą ma zostać wykonane między najbliższy poprzedzający bariery i bariery domniemanych zamknięcia lub najbliższej kolejnych bariery, jeśli istnieje `nowait` klauzuli. Dla każdego rodzaju harmonogram krótkich przykładzie pokazano, jak mogą być najlepszym rozwiązaniem jest tego typu harmonogramu. Krótkie omówienie następuje każdy przykład.  
  
 **Statycznych** harmonogramu jest również w przypadku najprostszym równoległego regionu zawierający pojedynczy **dla** utworzenia, a każda iteracja wymaga takiego poziomu w pracy.  
  
```  
#pragma omp parallel for schedule(static)  
for(i=0; i<n; i++) {  
  invariant_amount_of_work(i);  
}  
```  
  
 **Statycznych** harmonogram charakteryzuje się właściwości którym każdy wątek pobiera mniej więcej taką samą liczbę iteracji jako innego wątku, przy czym każdy wątek można niezależnie iteracji przypisane do niej. W związku z tym synchronizacja nie jest wymagana do dystrybucji pracy i przy założeniu, że każda iteracja wymaga tego samego ilość pracy wszystkie wątki powinno zostać zakończone na o tym samym czasie.  
  
 Dla zespołu `p` let wątków, *ceiling(n/p)* być liczbą całkowitą *q*, który spełnia *n = p\*q - r* z *0 < = r < p* . Jedna implementacja **statycznych** planowanie dla tego przykładu przypisywanej *q* iteracji, aby pierwszy *p-1* wątków, i *q-r* iteracji, aby ostatni wątek.  Przypisać inną implementację dopuszczalne *q* iteracji, aby pierwszy *p-r* wątków, i *q-1* iteracji, aby pozostały *r*wątków. Przedstawiono to, dlaczego programu nie należy polegać na szczegóły konkretnej implementacji.  
  
 **Dynamiczne** harmonogramu jest odpowiednia w przypadku **dla** skonstruować z iteracji wymagają różnych lub nawet nieprzewidywalne ilości pracy.  
  
```  
#pragma omp parallel for schedule(dynamic)  
  for(i=0; i<n; i++) {  
    unpredictable_amount_of_work(i);  
}  
```  
  
 **Dynamiczne** harmonogramu jest określony przez właściwość żadnego wątku czeka na bariera dla trwa dłużej niż inny wątek można wykonać jego iterację końcowego. Wymaga to, czy iteracji można przypisać pojedynczo wątków staną się one dostępne z synchronizacji dla każdego przydziału. Można zmniejszyć koszty synchronizacji przez określenie rozmiaru fragmentu minimalne *k* większa niż 1, dzięki czemu wątki są przypisane *k* aż mniej niż *k* pozostają. Gwarantuje to, że wątek nie oczekuje na dłużej niż Trwa inny wątek (maksymalnie) wykonać jego końcowego fragmentu bariery *k* iteracji.  
  
 **Dynamiczne** harmonogram może być przydatne, jeśli wątki odbierać zróżnicowanymi zasoby obliczeniowe, który ma wiele ten sam efekt co zmiennych ilości pracy dla każdej iteracji. Podobnie, dynamiczne harmonogram również może być przydatna, jeśli przyjeździe wątki **dla** skonstruować w różnym czasie, chociaż w niektórych przypadkach **z przewodnikiem** harmonogram może być wskazane.  
  
 **z przewodnikiem** harmonogram jest odpowiednie do sytuacji, w którym wątki może pojawić się w różnych okresach czasu w **dla** skonstruować przy każdej iteracji wymagające o tej samej ilość pracy. Może się to zdarzyć, jeśli na przykład **dla** konstrukcja jest poprzedzony co najmniej jednej sekcji lub **dla** tworzy z `nowait` klauzul.  
  
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
  
 Podobnie jak **dynamiczne**, **z przewodnikiem** zaplanować gwarancji, które nie wątek oczekuje na bariery dłużej niż Trwa inny wątek można wykonać jego iterację końcowego lub końcowego *k* Liczba iteracji, jeśli rozmiar fragmentu *k* jest określona. Wśród takie harmonogramy **z przewodnikiem** harmonogramu jest określony przez właściwość wymaga najmniejszej synchronizacji. Rozmiar fragmentu *k*, przypisze Typowa implementacja *q = ceiling(n/p)* iteracji, aby pierwszy dostępny wątku, ustaw  *n*  do większy z *n-q* i *p\*k*i powtórz przypisano wszystkich iteracji.  
  
 Gdy wybór optymalnego harmonogramu nie jest jako zwykły, podobnie jak w przypadku tych przykładach **środowiska uruchomieniowego** harmonogramu jest wygodną metodą eksperymentowanie z różne harmonogramy i rozmiarach, bez konieczności modyfikowania i skompiluj ponownie ten program. Można również go przydatne podczas optymalnego harmonogram zależy (w jakiś sposób wartości prognozowanych) danych wejściowych, do którego zastosowano program.  
  
 Aby zapoznać się z przykładem kompromis między różne harmonogramy, należy wziąć pod uwagę udostępnianie 1000 iteracji między 8 wątków. Załóżmy, że istnieje niezmiennej ilość pracy w każdej iteracji i używać go jako jednostka czasu.  
  
 Jeśli w tym samym czasie, można uruchomić wszystkie wątki **statycznych** harmonogramu spowoduje, że konstrukcja do wykonania w jednostkach 125, nie synchronizacji. Ale Załóżmy, że jeden wątek wynosi 100 jednostek w przychodzących. Pozostałe wątki siedmiu poczekaj 100 jednostek w bariery, a czas wykonania dla całego konstrukcji zwiększa 225.  
  
 Ponieważ zarówno **dynamiczne** i **z przewodnikiem** harmonogramy zapewnienia, że wątek nie oczekuje na więcej niż jednej jednostki w bariera czas wykonywania dla konstrukcji zwiększyć tylko do 138 powoduje opóźnione wątku jednostki zwiększonej opóźnieniami z synchronizacji. Opóźnienia nie są bez znaczenia, staje się ważne, czy liczba synchronizacje jest 1000 **dynamiczne** , ale tylko 41 dla **z przewodnikiem**, przy założeniu domyślny rozmiar fragmentu jednego. Z rozmiaru fragmentu wynoszącego 25 **dynamiczne** i **z przewodnikiem** oba zakończenia w 150 jednostki, a także wszelkich opóźnień z wymagane synchronizacje numer teraz tylko 40 i 20, odpowiednio.