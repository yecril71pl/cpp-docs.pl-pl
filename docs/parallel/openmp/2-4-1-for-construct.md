---
title: 2.4.1 dla konstrukcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 27d2cbce-786b-4819-91d3-d55b2cc57a5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5165c21f0bf6f2b9757550208d5e8e26a2bd3b1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="241-for-construct"></a>2.4.1 — dla konstrukcji
**Dla** dyrektywy identyfikuje iteracyjne konstrukcji podziału pracy określający, że iteracji pętli skojarzone będą wykonywane równolegle. Iteracje **dla** pętli są rozproszone na wątków, które już istnieją w zespole wykonywanie równoległe konstrukcji, do którego jest on powiązany. Składnia **dla** konstrukcja wygląda następująco:  
  
```  
#pragma omp for [clause[[,] clause] ... ] new-linefor-loop  
```  
  
 Klauzuli jest jednym z następujących czynności:  
  
 **prywatne (** *zmiennej listy* **)**  
  
 **firstprivate (** *zmiennej listy* **)**  
  
 **lastprivate (** *zmiennej listy* **)**  
  
 **redukcja (** *operator* **:** *zmiennej — lista ***)**  
  
 **uporządkowane**  
  
 **Harmonogram (** *rodzaj*[, *chunk_size*]**)**  
  
 **nowait**  
  
 **Dla** dyrektywy wprowadza ograniczenia w strukturze odpowiadającego **dla** pętli. W szczególności odpowiadającego **dla** pętli musi być kanoniczny kształtu:  
  
 **Aby uzyskać (** *wyrażenie init* **;** *b logicznej op var*; *incr — wyrażenie ***)**  
  
 *init — wyrażenie*  
 Jeden z poniższych:  
  
 *var* = *równoważeniem obciążenia*  
  
 *Liczba całkowita typu, var* = *równoważeniem obciążenia*  
  
 *incr — wyrażenie*  
 Jeden z poniższych:  
  
 ++*var*  
  
 *var* ++  
  
 -- *var*  
  
 *var* --  
  
 *var* += *incr*  
  
 *var* -= *incr*  
  
 *var* = *var* + *incr*  
  
 *var* = *incr* + *var*  
  
 *var* = *var* - *incr*  
  
 *var*  
 Zmienna liczbę całkowitą ze znakiem. Jeśli ta zmienna w przeciwnym razie może być udostępniany, jest niejawnie on prywatnych w czasie trwania **dla**.   Ta zmienna nie muszą zostać zmodyfikowane w treści **dla** instrukcji. Jeśli nie określono zmiennej **lastprivate**, jego wartość po pętli jest nieokreślony.  
  
 *logiczne op*  
 Jeden z poniższych:  
  
 <  
  
 \<=  
  
 >  
  
 \>=  
  
 *lb*, *b*, i *incr*  
 Pętla wyrażenia niezmiennej liczby całkowitej. Synchronizacja nie podczas obliczania wyrażenia te nie istnieje. W związku z tym wszystkie ocenianego efekty uboczne dostarczyło wyników nieokreślony.  
  
 Należy zauważyć, że forma kanoniczna pozwala liczby iteracji pętli ma zostać obliczony przy wejściu do pętli. Te obliczenia jest wykonywane z wartości w typie *var*, po promocje typów całkowitych. W szczególności, jeśli wartość *b* - *lb* + *incr* nie może być przedstawiony w tym typie, wynikiem jest nieokreślony. Dalsze, jeśli *logicznej op* jest < lub \<= następnie *wyrażenie incr* mogą powodować *var* zwiększające w każdej iteracji pętli.   Jeśli *logicznej op* jest > lub > = następnie *wyrażenie incr* mogą powodować *var* zmniejszyć w każdej iteracji pętli.  
  
 **Harmonogram** klauzuli określa sposób iteracje **dla** pętli są podzielone między wątki zespołu. Poprawność program nie mogą zależeć od wątku, który wykonuje określonego iteracji. Wartość *chunk_size*, jeśli zostanie określona, musi być wyrażeniem pętli niezmiennej całkowitą wartością dodatnią. Synchronizacja nie podczas oceny tego wyrażenia nie istnieje. W związku z tym wszystkie ocenianego efekty uboczne dostarczyło wyników nieokreślony. Harmonogram *rodzaj* może być jedną z następujących czynności:  
  
 Tabela 2-1 **harmonogram** klauzuli *rodzaj* wartości  
  
|||  
|-|-|  
|static|Gdy **harmonogram (statyczne,** *chunk_size ***)** określono iteracji są podzielone na fragmenty o rozmiarze określonym przez *chunk_size*. Fragmenty są statycznie przypisane do wątki zespołu w sposób okrężnego według liczby wątków. Gdy nie *chunk_size* określono miejsca iteracji jest podzielona na fragmenty przybliżeniu równe w rozmiarze z jednym fragmencie przypisane do każdego wątku.|  
|dynamic|Gdy **harmonogram (dynamiczny,** *chunk_size ***)** określono iteracji dzielą się na szeregu fragmentów, każdy z nich zawiera *chunk_size* iteracji. Każdy fragment jest przypisany do wątku, który oczekuje na przydzielenie. Wątek wykonuje fragmentów iteracji i następnie czeka na jego dalej przypisania, dopóki nie pozostaną bez fragmentów do przypisania. Należy pamiętać, że ostatni fragment do przypisania może mieć mniejszej liczby iteracji. Gdy nie *chunk_size* jest określony, domyślnie przyjmuje wartość 1.|  
|Przewodnik|Gdy **harmonogram (z przewodnikiem,** *chunk_size ***)** określono iteracji są przypisane do wątków w fragmentów z zmniejszenie wielkości. Po zakończeniu jego przypisanej fragmentu iteracji wątku dynamicznie przypisano innego fragmentu, dopóki nie pozostaną none. Aby uzyskać *chunk_size* 1, rozmiar każdego fragmentu wynosi około liczby iteracji nieprzypisane podzielona przez liczbę wątków. Rozmiary około zmniejszyć wykładniczo do 1. Dla *chunk_size* z wartością *k* większa niż 1, rozmiar około zmniejszyć wykładniczo do *k*, z wyjątkiem tego, że ostatni fragment może mieć mniej niż  *k* iteracji. Gdy nie *chunk_size* jest określony, domyślnie przyjmuje wartość 1.|  
|środowisko uruchomieniowe|Gdy **schedule(runtime)** jest określony, decyzji dotyczących planowania została odroczona do środowiska wykonawczego. Harmonogram *rodzaj* i rozmiaru fragmenty można wybrać w czasie wykonywania przez ustawienie zmiennej środowiskowej **OMP_SCHEDULE**. Jeśli nie ustawiono tej zmiennej środowiskowej, wynikowy harmonogram jest zdefiniowane w implementacji. Gdy **schedule(runtime)** jest określony, *chunk_size* nie może być określony.|  
  
 W przypadku braku jawnie zdefiniowanych **harmonogram** klauzuli, domyślne **harmonogram** jest zdefiniowane w implementacji.  
  
 Program zgodny z OpenMP nie należy polegać na konkretny harmonogram wykonywania poprawne. Program nie należy polegać na harmonogram *rodzaj* odpowiadających dokładnie opisu podanego powyżej, ponieważ jest możliwe zmiany w implementacji ten sam harmonogram *rodzaj* między kompilatory inny. Opisy może służyć do wybierz harmonogram, który jest odpowiedni dla danej sytuacji.  
  
 **Uporządkowane** klauzuli musi być obecny, kiedy **uporządkowane** dyrektywy powiązać **dla** utworzenia.  
  
 Na koniec istnieje niejawna bariery **dla** skonstruować, chyba że **nowait** jest określona klauzula.  
  
 Ograniczenia **dla** dyrektywy są następujące:  
  
-   **Dla** pętli musi być strukturalnego bloku, a ponadto, jego wykonanie nie musi się kończyć znakiem **podziału** instrukcji.  
  
-   Wartości pętli kontrolować wyrażeń **dla** pętli skojarzone z **dla** dyrektywa musi być taka sama dla wszystkich wątków w zespole.  
  
-   **Dla** zmiennej iteracji pętli muszą mieć typ, liczbę całkowitą ze znakiem.  
  
-   Tylko jeden **harmonogram** klauzula może występować w **dla** dyrektywy.  
  
-   Tylko jeden **uporządkowane** klauzula może występować w **dla** dyrektywy.  
  
-   Tylko jeden **nowait** klauzula może występować w **dla** dyrektywy.  
  
-   Jest nieokreślony if lub częstotliwość dowolnej stronie efekty w *chunk_size*, *lb*, *b*, lub *incr* wystąpić wyrażenia.  
  
-   Wartość *chunk_size* wyrażenie musi być taka sama dla wszystkich wątków w zespole.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **prywatne**, **firstprivate**, **lastprivate**, i **redukcji** klauzule, zobacz [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.  
  
-   **OMP_SCHEDULE** środowiska zmiennych, zobacz [4.1 sekcji](../../parallel/openmp/4-1-omp-schedule.md) na stronie 48.  
  
-   **uporządkowane** utworzyć, zobacz [sekcji 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stronie 22.  
  
-   [Dodatek D](../../parallel/openmp/d-using-the-schedule-clause.md), strony 93, zawiera więcej informacji na temat przy użyciu klauzuli harmonogramu.