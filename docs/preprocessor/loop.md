---
title: pętla
ms.date: 10/18/2018
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: a1640881d98073381a941478f4b78177a95698d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411334"
---
# <a name="loop"></a>pętla

Określa, jak kod pętli jest uznawana za automatycznego zrównoleglacza i/lub wyłącza pętlę pod uwagę przy automatycznego wektoryzera.

## <a name="syntax"></a>Składnia

```
#pragma loop( hint_parallel(n) )
#pragma loop( no_vector )
#pragma loop( ivdep )
```

### <a name="parameters"></a>Parametry

*hint_parallel(n)*<br/>
Wskazówki, aby kompilator, że ta pętla powinna być przeprowadzana równolegle w *n* wątków, gdzie *n* jest literałem dodatnią liczbą całkowitą lub zerem. Jeśli *n* wynosi zero, maksymalna liczba wątków jest używany w czasie wykonywania. Jest to wskazówka dla kompilatora nie polecenia i nie ma żadnej gwarancji, że pętla będzie odbywać się równolegle. Jeśli pętla zawiera zależności danych lub problemów strukturalnych — na przykład pętla przechowuje do skalaru, który jest używany poza ciało pętli —, a następnie pętli nie będzie zrównoleglona.

Kompilator ignoruje tej opcji, chyba że [/Qpar](../build/reference/qpar-auto-parallelizer.md) określono przełącznika kompilatora.

*no_vector*<br/>
Domyślnie auto-vectorizer jest włączone i podejmie próbę vectorize wszystkich pętli, które ocenia jako korzystających z niej. Określ tej pragmie, aby wyłączyć automatycznego wektoryzera dla pętli, który po nim następuje.

*ivdep*<br/>
Wskazówki dotyczące kompilatorowi ignorowanie wektor zależności dla tej pętli. Użyj tego w połączeniu z *hint_parallel*.

## <a name="remarks"></a>Uwagi

Do użycia **pętli** pragma, umieść go bezpośrednio przed — nie — definicja pętli. Pragmy w życie dla zakresu pętli, który po nim następuje. Wiele dyrektyw pragma można zastosować do pętli, w dowolnej kolejności, ale musi zawierać każdego z nich w instrukcji oddzielne pragmy.

## <a name="see-also"></a>Zobacz także

[Automatyczna paralelizacja i wektoryzacja](../parallel/auto-parallelization-and-auto-vectorization.md)<br/>
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)