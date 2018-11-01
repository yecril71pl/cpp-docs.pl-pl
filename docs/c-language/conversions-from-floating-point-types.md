---
title: Konwersje z typów zmiennoprzecinkowych
ms.date: 01/29/2018
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: 87e1554897326039649829539443795cbc0fabab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570559"
---
# <a name="conversions-from-floating-point-types"></a>Konwersje z typów zmiennoprzecinkowych

A **float** wartość konwertowana na **double** lub **typu long double**, lub **double** przekonwertowane na **double**, ulega nie zmieni się wartość. A **double** wartość konwertowana na **float** wartość jest reprezentowana w dokładnie tak, jeśli jest to możliwe. Precyzja mogą zostać utracone, jeśli wartość nie może być reprezentowany dokładnie. Jeśli wynik jest poza zakresem, zachowanie jest niezdefiniowane. Zobacz [limity dla stałych zmiennopozycyjna](../c-language/limits-on-floating-point-constants.md) zakresu typów zmiennoprzecinkowych.

Wartość zmiennoprzecinkową jest konwertowana na wartość całkowitą, konwertując pierwszy **długie**, następnie z **długie** wartość do określonej wartości całkowitej. Część dziesiętną wartość zmiennoprzecinkową zostanie usunięty podczas konwersji do **długie**. Jeśli wynik nadal jest zbyt duży, aby mieściły się w **długie**, wynik konwersji jest niezdefiniowana.

**Microsoft Specific**

Podczas konwertowania **double** lub **typu long double** liczba zmiennoprzecinkowa na mniejsze liczbę zmiennoprzecinkową, wartość zmiennej zmiennoprzecinkowych został obcięty kierunku zera, gdy występuje niedopełnienie. Przepełnienie powoduje błąd czasu wykonywania. Należy zauważyć, że kompilator Microsoft C: mapuje **typu long double** na typ **double**.

**END specyficzny dla Microsoft**

W poniższej tabeli przedstawiono konwersje z typów zmiennoprzecinkowych.

## <a name="conversions-from-floating-point-types"></a>Konwersje z typów zmiennoprzecinkowych

|Z|Zadanie|Metoda|
|----------|--------|------------|
|**float**|**char**|Konwertuj na **długie**; Konwertuj **długie** do **char**|
|**float**|**short**|Konwertuj na **długie**; Konwertuj **długie** do **krótki**|
|**float**|**long**|Obetnij po punkcie dziesiętnym. Jeśli wynik jest za duży, może być reprezentowana jako **długie**, wynik jest niezdefiniowany.|
|**float**|**short bez znaku**|Konwertuj na **długie**; Konwertuj **długie** do **typ unsigned short**|
|**float**|**unsigned long**|Konwertuj na **długie**; Konwertuj **długie** do **unsigned long**|
|**float**|**double**|Zmień wewnętrznej reprezentacji|
|**float**|**Liczba typu double**|Zmień wewnętrznej reprezentacji|
|**double**|**char**|Konwertuj na **float**; Konwertuj **float** do **char**|
|**double**|**short**|Konwertuj na **float**; Konwertuj **float** do **krótki**|
|**double**|**long**|Obetnij po punkcie dziesiętnym. Jeśli wynik jest za duży, może być reprezentowana jako **długie**, wynik jest niezdefiniowany.|
|**double**|**short bez znaku**|Konwertuj na **długie**; Konwertuj **długie** do **typ unsigned short**|
|**double**|**unsigned long**|Konwertuj na **długie**; Konwertuj **długie** do **unsigned long**|
|**double**|**float**|Reprezentacja jako **float**. Jeśli **double** wartość nie może być reprezentowany dokładnie jako **float**, dojdzie do utraty precyzji. Jeśli wartość jest zbyt duży, może być reprezentowana jako **float**, wynik jest niezdefiniowany.|
|**Liczba typu double**|**char**|Konwertuj na **float**; Konwertuj **float** do **char**|
|**Liczba typu double**|**short**|Konwertuj na **float**; Konwertuj **float** do **krótki**|
|**Liczba typu double**|**long**|Obetnij po punkcie dziesiętnym. Jeśli wynik jest za duży, może być reprezentowana jako **długie**, wynik jest niezdefiniowany.|
|**Liczba typu double**|**short bez znaku**|Konwertuj na **długie**; Konwertuj **długie** do **typ unsigned short**|
|**Liczba typu double**|**unsigned long**|Konwertuj na **długie**; Konwertuj **długie** do **unsigned long**|
|**Liczba typu double**|**float**|Reprezentacja jako **float**. Jeśli **double** wartość nie może być reprezentowany dokładnie jako **float**, dojdzie do utraty precyzji. Jeśli wartość jest zbyt duży, może być reprezentowana jako **float**, wynik jest niezdefiniowany.|
|**Liczba typu double**|**double**|**Typu long double** wartość jest traktowana jako **double**.|

Konwersje z **float**, **double**, lub **typu long double** wartości **unsigned long** nie są prawidłowe, jeśli jest konwertowana wartość większy niż maksymalny dodatni **długie** wartość.

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
