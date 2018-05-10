---
title: 2.7.1 dyrektywa dotycząca prywatnego wątku | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c9912ccbfa6f5773ec1e523245f75e675bb82244
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="271-threadprivate-directive"></a>2.7.1 Dyrektywa dotycząca prywatnego wątku
`threadprivate` Dyrektywy sprawia, że nazwany zakres pliku, zakresie przestrzeni nazw lub zmienne statyczne zakresie bloku określone w *zmiennej listy* prywatnych do wątku. *Zmienna listy* rozdzielaną przecinkami listę zmiennych, które nie mają niekompletnego typu. Składnia `threadprivate` dyrektywy wygląda następująco:  
  
```  
#pragma omp threadprivate(variable-list) new-line  
```  
  
 Każda kopia `threadprivate` zmienna jest ustawiana na raz, w momencie nieokreślony w programie przed pierwszego odwołania do tej kopii i w zwykły sposób (tj., jak w serial wykonywanie tego programu będzie można zainicjować kopii głównej). Należy pamiętać, że jeśli obiekt odwołuje się do jawnej inicjatora elementu `threadprivate` zmienną i wartość obiektu jest modyfikowany przed pierwszego odwołania do kopiowania zmiennej, a następnie zachowanie jest nieokreślony.  
  
 Jak z dowolnej prywatnej zmiennej wątku nie może odwoływać się inny wątek kopię `threadprivate` obiektu. W regionach szeregowych i regiony głównym programu odwołania zostaną kopii obiektu głównego wątku.  
  
 Po wykonaniu pierwszej równoległego regionu, dane w `threadprivate` obiektów jest gwarantowana utrwalić, tylko jeśli dynamiczny wątki mechanizmu została wyłączona, a liczba wątków pozostaje niezmieniona dla wszystkich regionów równoległych.  
  
 Ograniczenia do `threadprivate` dyrektywy są następujące:  
  
-   A `threadprivate` dyrektywy w zakresie pliku lub zakresie przestrzeni nazw zmiennych musi występować poza deklaracji lub definicji i lexically musi poprzedzać wszystkie odwołania do ze zmiennych na liście.  
  
-   Każdej zmiennej w *zmiennej listy* z `threadprivate` dyrektywy w zakresie pliku lub przestrzeni nazw musi odwoływać się do deklaracji zmiennej w zakresie pliku lub przestrzeni nazw, lexically poprzedzający dyrektywy.  
  
-   A `threadprivate` dyrektywa zmiennych statycznych zakresie bloku musi występować w zakresie zmiennej, a nie w zagnieżdżonych zakresu. Dyrektywa lexically musi poprzedzać wszystkie odwołania do ze zmiennych na liście.  
  
-   Każdej zmiennej w *zmiennej listy* z `threadprivate` dyrektywy w zakresie bloku musi odwoływać się do deklaracji zmiennej w tym samym zakresie lexically poprzedzający dyrektywy. Deklaracja zmiennej należy użyć specyfikator statycznej klasy magazynowania.  
  
-   Jeśli zmienna jest określona w `threadprivate` dyrektywy w jednostce tłumaczenia jeden, musi być zdefiniowana w `threadprivate` dyrektywy w każdej jednostki tłumaczenia, w którym jest zadeklarowany.  
  
-   A `threadprivate` zmiennej nie musi występować w klauzuli z wyjątkiem `copyin`, `copyprivate`, `schedule`, `num_threads`, lub **Jeśli** klauzuli.  
  
-   Adres `threadprivate` zmienna nie jest stałą adres.  
  
-   A `threadprivate` zmiennej nie może mieć niekompletnego typu lub typ referencyjny.  
  
-   A `threadprivate` zmienna typu klasy innego niż POD musi mieć Konstruktor kopiujący dostępny, jednoznaczne, jeśli jest zadeklarowana przy użyciu jawnych inicjatora.  
  
 Poniższy przykład przedstawia sposób modyfikowania wyświetlany w inicjatorze zmiennej może spowodować nieokreślony zachowanie oraz sposób uniknąć tego problemu za pomocą konstruktora kopiującego i pomocnicze obiektu.  
  
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
  
-   Wątki dynamicznej, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.  
  
-   `OMP_DYNAMIC` środowisko zmiennych, zobacz [4.3 sekcji](../../parallel/openmp/4-3-omp-dynamic.md) na stronie 49.