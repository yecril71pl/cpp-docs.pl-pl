---
title: 2.7.1, dyrektywa threadprivate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31c9c70940b558d0b4cc3f77677665235417694d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398147"
---
# <a name="271-threadprivate-directive"></a>2.7.1 Dyrektywa dotycząca prywatnego wątku

`threadprivate` Dyrektywy sprawia, że nazwany zakres pliku, zakresie przestrzeni nazw lub zmiennych statycznych zasięgiem bloku określone w *liście zmiennych* prywatnego wątku. *Lista zmiennej* znajduje się lista rozdzielonych przecinkami zmiennych, które nie mają niekompletnego typu. Składnia `threadprivate` dyrektywy jest następująca:

```
#pragma omp threadprivate(variable-list) new-line
```

Każda kopia `threadprivate` zmienna jest inicjowana raz, w momencie nieokreślony w programie przed pierwszym odwołaniu do tej kopii, jak i w zwykły sposób (czyli jako kopia główna może być inicjowane w wykonanie szeregowe programu). Należy pamiętać, że jeśli obiekt jest wywoływane w inicjatorze jawne z `threadprivate` zmienną i wartość obiektu zostanie zmodyfikowany przed pierwszym odwołaniu kopię zmiennej, a następnie zachowanie jest nieokreślone.

Jak za pomocą dowolnej zmiennej prywatnej wątek nie może odwoływać się inny wątek kopię `threadprivate` obiektu. W regionach szeregowych i regiony głównego programu odwołania zostaną kopii obiektu głównego wątku.

Po wykonaniu pierwszej równoległego regionu, dane w `threadprivate` obiektów jest gwarantowane do utrwalenia, tylko jeśli dynamicznej wątki mechanizm został wyłączony, a jeśli liczba wątków pozostaje niezmieniona dla wszystkich regionów równoległych.

Ograniczenia do `threadprivate` dyrektywy jest następująca:

- A `threadprivate` dyrektywy dla zmiennych w zakresie pliku lub zakresie przestrzeni nazw musi znajdować się poza deklaracji lub definicji i leksykalnie musi poprzedzać wszystkie odwołania do tych zmiennych na liście.

- Każdej zmiennej w *liście zmiennych* z `threadprivate` dyrektywy w zakresie pliku lub przestrzeni nazw musi odwoływać się do deklaracji zmiennej w zakresie pliku lub przestrzeni nazw, leksykalnie poprzedzającym dyrektywy.

- A `threadprivate` dyrektywy zmiennych statycznych zakresie bloku musi znajdować się w zakresie zmiennej i nie znajduje się w zakresie zagnieżdżonych. Dyrektywa leksykalnie musi poprzedzać wszystkie odwołania do tych zmiennych na liście.

- Każdej zmiennej w *liście zmiennych* z `threadprivate` dyrektywy w zakresie bloku musi odwoływać się do deklaracji zmiennej w tym samym zakresie, leksykalnie poprzedzającym dyrektywy. Deklaracja zmiennej, należy użyć specyfikator statycznej klasy magazynowania.

- Jeśli zmienna jest określona w `threadprivate` dyrektywy w jednostce translacji jeden, musi być określona w `threadprivate` dyrektywy w każdej jednostce translacji, w którym jest zdeklarowana.

- A `threadprivate` zmiennej nie musi znajdować się w żadnej klauzuli, z wyjątkiem `copyin`, `copyprivate`, `schedule`, `num_threads`, lub **Jeśli** klauzuli.

- Adres `threadprivate` zmienna nie jest stałą adresu.

- A `threadprivate` zmiennej nie może mieć typu niekompletnego lub typu odwołania.

- A `threadprivate` zmienna typu non-POD klasy musi mieć konstruktora kopiującego dostępny, jednoznaczną, jeśli jest zadeklarowana za pomocą jawnego inicjatora.

Poniższy przykład ilustruje sposób modyfikowania zmienną, która pojawia się w inicjatorze może spowodować nieokreślone zachowanie oraz sposób uniknąć tego problemu za pomocą konstruktora kopiującego i pomocnicze w ramach obiektu.

```
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

## <a name="cross-references"></a>Odsyłacze:

- Dynamiczne wątków, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.

- `OMP_DYNAMIC` Zobacz zmiennej środowiska [4.3 sekcji](../../parallel/openmp/4-3-omp-dynamic.md) na stronie 49.