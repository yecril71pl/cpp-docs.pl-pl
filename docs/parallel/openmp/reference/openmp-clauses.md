---
title: Klauzule OpenMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afd0a8f66f9b0d027671629998597955b3aa69e9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378337"
---
# <a name="openmp-clauses"></a>Klauzule OpenMP

Zawiera łącza do klauzul używany w interfejsie API OpenMP.

Visual C++ obsługuje następujące klauzule OpenMP:

|Klauzula|Opis|
|------------|-----------------|
|[copyin](../../../parallel/openmp/reference/copyin.md)|Umożliwia wątków, aby uzyskiwać dostęp do wartości głównego wątku dla [threadprivate](../../../parallel/openmp/reference/threadprivate.md) zmiennej.|
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|Określa, czy co najmniej jednej zmiennej powinien być współużytkowane przez wszystkie wątki.|
|[default](../../../parallel/openmp/reference/default-openmp.md)|Określa zachowanie zmiennych niewystępującego w zakresie równoległego regionu.|
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|Określa, że każdy wątek ma własne wystąpienie zmiennej i że zmiennej powinna zostać zainicjowana z wartością zmiennej, ponieważ istnieje przed konstrukcja równoległa.|
|[if](../../../parallel/openmp/reference/if-openmp.md)|Określa, czy pętla powinny być wykonywane równolegle lub w seryjny.|
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|Określa, że wersja w otaczającym kontekście zmiennej jest równa wersji prywatnej niezależnie od wątku wykonuje końcowe iteracji (konstrukcji pętli for) lub ostatnia sekcja (#pragma sekcji).|
|[nowait](../../../parallel/openmp/reference/nowait.md)|Zastępuje barierę niejawne w dyrektywie.|
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|Ustawia liczbę wątków w zespole wątku.|
|[Uporządkowane](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|Wymagane na równoległego [dla](../../../parallel/openmp/reference/for-openmp.md) instrukcji Jeśli [uporządkowane](../../../parallel/openmp/reference/ordered-openmp-directives.md) dyrektywy ma być używana w pętli.|
|[private](../../../parallel/openmp/reference/private-openmp.md)|Określa, że każdy wątek ma własne wystąpienie zmiennej.|
|[reduction](../../../parallel/openmp/reference/reduction.md)|Określa, że jeden lub więcej zmiennych, które są prywatne każdy wątek jest przedmiotem operację redukcji, na końcu równoległego regionu.|
|[schedule](../../../parallel/openmp/reference/schedule.md)|Dotyczy [dla](../../../parallel/openmp/reference/for-openmp.md) dyrektywy.|
|[Udostępnione](../../../parallel/openmp/reference/shared-openmp.md)|Określa, czy co najmniej jednej zmiennej powinien być współużytkowane przez wszystkie wątki.|

## <a name="see-also"></a>Zobacz też

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)