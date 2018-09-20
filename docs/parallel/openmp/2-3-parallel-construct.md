---
title: 2.3 konstrukcja równoległa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4be5bdc40f69cfa0a326ffa6a7f8465e401cfd33
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448236"
---
# <a name="23-parallel-construct"></a>2.3 Konstrukcja równoległa

Następująca dyrektywa definiuje równoległego regionu, czyli obszarem program, który ma być wykonane przez wiele wątków jednocześnie. Są to podstawowe konstrukcji, która rozpoczyna wykonywanie równoległe.

```
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*Klauzuli* jest jednym z następujących czynności:

**Jeśli (** *wyrażeń skalarnych* **)**

**prywatne (** *liście zmiennych* **)**

**firstprivate (** *liście zmiennych* **)**

**domyślne (udostępnionego &#124; none)**

**udostępnione (** *liście zmiennych* **)**

**copyin (** *liście zmiennych* **)**

**redukcja (** *operator* **:***liście zmiennych* **)** 

**num_threads(** *integer-expression* **)**

Gdy wątek napotka konstrukcja równoległa, zespół wątków jest tworzone, jeśli jest spełniony jeden z następujących przypadkach:

- Nie **Jeśli** klauzula jest obecny.

- **Jeśli** wyrażenie ma wartość różną od zera.

Ten wątek staje się główny wątek zespołu, wprowadzając szereg wątek 0, i regionu równolegle uruchomić wszystkie wątki w zespole, łącznie z wątku głównego. Jeśli wartość **Jeśli** wyrażenie jest równe zeru, region jest serializowana.

Aby określić liczbę wątków, które są wymagane, następujące reguły zostanie uwzględniony w kolejności. Pierwsza reguła, której warunek jest spełniony, zostaną zastosowane:

1. Jeśli **num_threads** klauzula jest obecna, a następnie wartość wyrażenia typu całkowitego jest liczba wątków zażądano.

1. Jeśli **omp_set_num_threads** została wywołana funkcja biblioteki, a następnie wartość argumentu w wywołaniu ostatnio wykonywanych jest liczba wątków żądanie.

1. Jeśli zmienna środowiskowa **OMP_NUM_THREADS** jest zdefiniowana, a następnie wartość tej zmiennej środowiskowej liczbę wątków, żądanie.

1. Jeśli żaden z powyższych metod zastosowano liczbę wątków, wymagane jest zdefiniowane w implementacji.

Jeśli **num_threads** klauzula jest obecna, a następnie zastępuje ona liczbę wątków, żądane przez **omp_set_num_threads** funkcja biblioteki lub **OMP_NUM_THREADS** Zmienna środowiskowa tylko w przypadku równoległego regionu jest stosowany do. Kolejnych regionów równoległych nie dotyczy on.

Liczba wątków, które są wykonywane równoległego regionu również zależy od czy dynamiczne Dostosowywanie liczby wątków jest włączona. Wyłączenie dynamiczne Dostosowywanie żądana liczba wątków będzie wykonywał równoległego regionu. Po włączeniu dynamicznego dostosowania żądana liczba wątków jest maksymalna liczba wątków, które może zostać wykonany równoległego regionu.

Jeśli równoległego regionu podczas dynamicznego dostosowania liczby wątków jest wyłączona, a liczba wątków żądany dla równoległego regionu przekracza liczbę, która może dostarczyć działającego systemu, jest zachowanie programu zdefiniowane w implementacji. Implementacja może na przykład przerywa wykonywanie programu, lub może serializować, równoległego regionu.

**Omp_set_dynamic** funkcja biblioteki i **OMP_DYNAMIC** zmiennej środowiskowej można włączać i wyłączać dynamiczne Dostosowywanie liczby wątków.

Liczba procesorów fizycznych, w rzeczywistości hostingu wątki w danym momencie jest zdefiniowane w implementacji. Po utworzeniu liczbę wątków w zespole pozostaje stały czas trwania tego równoległego regionu. Można zmienić, jawnie przez użytkownika lub automatycznie przez system środowiska wykonawczego z jednego regionu równoległego do innego.

Instrukcje zawarte w obrębie zakresu dynamicznego równoległego regionu są wykonywane przez poszczególne wątki, a każdy wątek może wykonać ścieżkę instrukcji, która różni się od innych wątków. Dyrektywy napotkano poza zakres leksykalne równoległego regionu są określane jako oddzielony dyrektywy.

Brak dorozumianych barierę na końcu równoległego regionu. Główny wątek zespół kontynuuje wykonywanie na końcu równoległego regionu.

Jeśli wątek w zespole wykonywania równoległego regionu napotka inna konstrukcja równoległa, powoduje to utworzenie nowego zespołu i staje się główną tego nowego zespołu. Zagnieżdżone regionów równoległych są serializowane domyślnie. Co w efekcie domyślnie zagnieżdżonych równoległego regionu jest wykonywana przez zespół składa się z jednego wątku. Domyślne zachowanie może zostać zmieniona przez przy użyciu albo funkcja biblioteki uruchomieniowej **omp_set_nested** lub zmiennej środowiskowej **OMP_NESTED**. Jednak liczbę wątków w zespołach, które są wykonywane zagnieżdżonych równoległego regionu jest zdefiniowane w implementacji.

Ograniczenia **równoległe** dyrektywy jest następująca:

- Co najwyżej jeden **Jeśli** klauzula może występować w dyrektywie.

- Jest nieokreślony, w czy dowolnej stronie efekty w Jeśli wyrażenie lub **num_threads** występować wyrażenie.

- A **throw** wykonywana wewnątrz równoległego regionu musi spowodować wykonanie można wznowić w ramach dynamicznej stopnia tego samego bloku ze strukturą, a musi być przechwycony przez tego samego wątku, który wygenerował wyjątek.

- Tylko jeden **num_threads** klauzula może występować w dyrektywie. **Num_threads** wyrażenie jest szacowana poza kontekstem równoległego regionu, a musi być dodatnią liczbą całkowitą.

- Kolejność obliczania **Jeśli** i **num_threads** klauzule jest nieokreślona.

## <a name="cross-references"></a>Odsyłacze:

- **prywatne**, **firstprivate**, **domyślne**, **udostępnionego**, **copyin**, i **redukcji**zdań, zobacz [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.

- **OMP_NUM_THREADS** zmiennej środowiskowej [4.2 sekcji](../../parallel/openmp/4-2-omp-num-threads.md) na stronie 48.

- **omp_set_dynamic** funkcja biblioteki, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.

- **OMP_DYNAMIC** środowiska zmiennych, zobacz [4.3 sekcji](../../parallel/openmp/4-3-omp-dynamic.md) na stronie 49.

- **omp_set_nested** funkcji, zobacz [sekcji 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stronie 40.

- **OMP_NESTED** środowiska zmiennych, zobacz [4.4 sekcji](../../parallel/openmp/4-4-omp-nested.md) na stronie 49.

- **omp_set_num_threads** funkcja biblioteki, zobacz [sekcji 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stronie 36.