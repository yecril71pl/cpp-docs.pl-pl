---
title: 2.4.1 — dla konstrukcji
ms.date: 11/04/2016
ms.assetid: 27d2cbce-786b-4819-91d3-d55b2cc57a5e
ms.openlocfilehash: a6cd1733677a6211055a9b06231fb1686c8e2fde
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329502"
---
# <a name="241-for-construct"></a>2.4.1 — dla konstrukcji

**Dla** dyrektywy identyfikuje iteracyjne konstrukcji podziału pracy określający, że iteracje pętli skojarzone będą wykonywane równolegle. Iteracje **dla** pętli są rozmieszczone na wątki, które już istnieją w zespołach, wykonywanie równoległe konstrukcji, która wiąże. Składnia **dla** konstrukcja jest w następujący sposób:

```
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

Klauzula jest jedną z następujących czynności:

**prywatne (** *liście zmiennych* **)**

**firstprivate (** *liście zmiennych* **)**

**lastprivate (** *liście zmiennych* **)**

**redukcja (** *operator* **:** *liście zmiennych* **)**

**Uporządkowane**

**Harmonogram (** *rodzaj* [**,** *chunk_size*] **)**

**nowait**

**Dla** dyrektywy stosuje ograniczenia dla struktury odpowiadającego **dla** pętli. W szczególności odpowiednich **dla** pętli musi mieć kształtu kanoniczny:

**Aby uzyskać (** *init expr* **;** *b logiczne op var*; *incr expr* **)**

*wyrażenie inicjowania*<br/>
Jeden z poniższych:

*var* = *modułu równoważenia obciążenia*

*Typ liczby całkowitej var* = *modułu równoważenia obciążenia*

*incr — wyrażenie*<br/>
Jeden z poniższych:

++ *var*

*var* ++

-- *var*

*var* --

*var* += *incr*

*var* -= *incr*

*var* = *var* + *incr*

*var* = *incr* + *var*

*var* = *var* - *incr*

*var*<br/>
Zmienna liczba całkowita ze znakiem. Jeśli ta zmienna, w przeciwnym razie mogłyby być udostępniane, niejawnie staje się prywatnych na czas trwania **dla**.   Ta zmienna nie mogą zostać zmodyfikowane w treści **dla** instrukcji. Jeśli nie określono zmiennej **lastprivate**, jego wartość po pętli jest nieokreślony.

*op logiczne*<br/>
Jeden z poniższych:

\<

\<=

\>

\>=

*lb*, *b*, i *incr*<br>
Pętla wyrażeń niezmiennej liczby całkowitej. Brak synchronizacji podczas obliczania wartości tych wyrażeń nie istnieje. W związku z tym wszelkie ocenianą efekty uboczne generują nieokreślone wyniki.

Należy pamiętać, że forma kanoniczna umożliwia liczby iteracji pętli, które ma zostać obliczony przy uruchamianiu pętli. To obliczenie jest wykonywane przy użyciu wartości w typie *var*, po promocji typu całkowitego. W szczególności jeśli wartość *b* - *lb* + *incr* nie może być przedstawiony w tym typu, wynik jest nieokreślony. Dodatkowo Jeśli *logiczne op* jest < lub \<= then *incr expr* mogą powodować *var* zwiększyć w każdej iteracji pętli.   Jeśli *logiczne op* jest > lub > = then *incr expr* mogą powodować *var* zmniejszyć w każdej iteracji pętli.

**Harmonogram** klauzula określa sposób iteracje **dla** pętli są podzielone między wątki zespołu. Poprawność programu nie może zależeć od których wątek wykonuje konkretnej iteracji. Wartość *chunk_size*, jeśli określony, musi być wyrażeniem niezmiennej całkowitą pętli z wartością dodatnią. Brak synchronizacji podczas obliczania wyrażenia nie istnieje. W związku z tym wszelkie ocenianą efekty uboczne generują nieokreślone wyniki. Harmonogram *rodzaj* może być jedną z następujących czynności:

Tabela 2-1 **harmonogram** klauzuli *rodzaj* wartości

|||
|-|-|
|static|Gdy **harmonogram (statyczny,** *chunk_size* **)** określono iteracji są podzielone na fragmenty o rozmiarze określonym przez *chunk_size*. Fragmenty są statycznie przypisane do wątków w zespole w okrężne zgodnie z kolejnością liczba wątków. Gdy nie *chunk_size* określono miejsca iteracji jest podzielony na fragmenty, które są w przybliżeniu taki sam rozmiar, z jednym fragmencie przypisane do każdego wątku.|
|dynamic|Gdy **harmonogram (dynamiczny,** *chunk_size* **)** określono iteracje są podzielone na szereg fragmenty, każdy z nich zawiera *chunk_size* iteracji. Każdy fragment jest przypisany do wątku, który oczekuje na przydzielenie. Wątek wykonuje fragmentów iteracji, a następnie czeka na przypisania dalej, dopóki nie pozostaną bez fragmentów do przypisania. Należy pamiętać, że ostatni fragment do przypisania, może mieć mniejszej liczby iteracji. Gdy nie *chunk_size* jest określony, jego wartość domyślna to 1.|
|krok po kroku|Gdy **harmonogram (krok po kroku,** *chunk_size* **)** określono iteracje są przypisane do wątków we fragmentach, z malejącymi rozmiarów. Po zakończeniu jego przypisane fragmentów iteracji wątku go jest dynamicznie przypisywany innym fragmencie, dopóki nie pozostaną none. Aby uzyskać *chunk_size* 1, rozmiar każdego fragmentu jest około liczby iteracji nieprzypisane dzielona przez liczbę wątków. Te rozmiary obniżone około wykładniczo 1. Dla *chunk_size* wartością *k* większy niż 1, rozmiary obniżone około wykładniczo do *k*, z tą różnicą, że ostatni fragment może być mniejsza niż  *k* iteracji. Gdy nie *chunk_size* jest określony, jego wartość domyślna to 1.|
|środowisko uruchomieniowe|Gdy **schedule(runtime)** jest określony, decyzji dotyczących planowania jest odroczone do czasu środowiska uruchomieniowego. Harmonogram *rodzaj* i rozmiar fragmentów można wybrać w czasie wykonywania przez ustawienie zmiennej środowiskowej **OMP_SCHEDULE**. Jeśli nie ustawiono tej zmiennej środowiskowej, wynikowy harmonogram jest zdefiniowane w implementacji. Gdy **schedule(runtime)** jest określony, *chunk_size* nie może być określony.|

W przypadku braku jawnie zdefiniowanych **harmonogram** klauzuli, domyślnym **harmonogram** jest zdefiniowane w implementacji.

Program zgodny z OpenMP nie należy polegać na konkretny harmonogram wykonywania poprawne. Program nie należy polegać na podstawie harmonogramu *rodzaj* odpowiadających dokładnie opis podanej powyżej, ponieważ istnieje możliwość zmiany w implementacji tego samego harmonogramu *rodzaj* między różne kompilatory. Opisy może służyć do wybierz harmonogram, który jest odpowiedni dla danej sytuacji.

**Uporządkowane** klauzuli musi być obecny, kiedy **uporządkowane** dyrektywy powiązać **dla** konstruowania.

Na końcu ma niejawne barierę **dla** konstruowania, chyba że **nowait** jest określona klauzula.

Ograniczenia **dla** dyrektywy jest następująca:

- **Dla** pętli musi być strukturalnego bloku, a ponadto, jego wykonanie nie musi się kończyć znakiem **podziału** instrukcji.

- Wartości pętli kontrolować wyrażeń **dla** pętli skojarzone z **dla** dyrektywa musi być taka sama dla wszystkich wątków w zespole.

- **Dla** Zmienna iteracji pętli musi mieć typ liczby całkowitej ze znakiem.

- Tylko jeden **harmonogram** klauzula może występować na **dla** dyrektywy.

- Tylko jeden **uporządkowane** klauzula może występować na **dla** dyrektywy.

- Tylko jeden **nowait** klauzula może występować na **dla** dyrektywy.

- Jest nieokreślony, jeśli lub jak często wpływ dowolnej stronie w obrębie *chunk_size*, *lb*, *b*, lub *incr* wyrażenia wystąpić.

- Wartość *chunk_size* wyrażenie musi być taka sama dla wszystkich wątków w zespole.

## <a name="cross-references"></a>Odsyłacze:

- **prywatne**, **firstprivate**, **lastprivate**, i **redukcji** zdań, zobacz [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.

- **OMP_SCHEDULE** środowiska zmiennych, zobacz [sekcji 4.1](../../parallel/openmp/4-1-omp-schedule.md) na stronie 48.

- **uporządkowane** konstruowania, zobacz [sekcji 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stronie 22.

- [Załącznik D](../../parallel/openmp/d-using-the-schedule-clause.md), stronie 93, zawiera więcej informacji na temat użycie klauzuli harmonogramu.