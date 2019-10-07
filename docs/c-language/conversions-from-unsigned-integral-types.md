---
title: Konwersje z niepodpisanych typów całkowitych
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 3099f0113103223e392dc20560899b4a6e3ebf20
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998791"
---
# <a name="conversions-from-unsigned-integral-types"></a>Konwersje z niepodpisanych typów całkowitych

Gdy liczba całkowita bez znaku jest konwertowana na typ liczba całkowita lub zmiennoprzecinkowa, jeśli oryginalna wartość jest reprezentacja w typie wyniku, wartość nie jest zmieniana.

Podczas konwertowania liczby całkowitej bez znaku na liczbę całkowitą o większym rozmiarze wartość jest zerowa-rozszerzona. Podczas konwertowania na liczbę całkowitą o mniejszym rozmiarze bity o wysokim stopniu są obcinane. Wynik jest interpretowany przy użyciu typu wyniku, jak pokazano w tym przykładzie.

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

W przypadku konwertowania nieoznaczonej liczby całkowitej na typ zmiennoprzecinkowy, jeśli oryginalna wartość nie może być reprezentowana dokładnie w typie wyniku, wynik jest następną wyższą lub mniejszą reprezentacją wartości.

Zobacz [Magazyn typów podstawowych](../c-language/storage-of-basic-types.md) , aby uzyskać informacje o rozmiarach typów całkowitych i zmiennoprzecinkowych.

**Specyficzne dla firmy Microsoft**

W kompilatorze Microsoft: **unsigned** (lub **unsigned int**) i **unsigned long** są DISTINCT, ale równoważnymi typami. Konwersja **niepodpisanej wartości int** jest wykonywana w taki sam sposób jak w przypadku konwersji typu **unsigned long**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Poniższa tabela zawiera podsumowanie konwersji z niepodpisanych typów całkowitych.

## <a name="table-of-conversions-from-unsigned-integral-types"></a>Tabela konwersji z niepodpisanych typów całkowitych

|Z|Do|Metoda|
|----------|--------|------------|
|**znak bez znaku**|**char**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**znak bez znaku**|**short**|Zero — zwiększenie|
|**znak bez znaku**|**long**|Zero — zwiększenie|
|**znak bez znaku**|**Long Long**|Zero — zwiększenie|
|**znak bez znaku**|**bez znaku Short**|Zero — zwiększenie|
|**znak bez znaku**|**bez znaku**|Zero — zwiększenie|
|**znak bez znaku**|**bez znaku Long Long**|Zero — zwiększenie|
|**znak bez znaku**|**float**|Konwertuj na **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**znak bez znaku**|**double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**znak bez znaku**|**Long Double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**bez znaku Short**|**char**|Zachowaj bajt o niskiej kolejności|
|**bez znaku Short**|**short**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**bez znaku Short**|**long**|Zero — zwiększenie|
|**bez znaku Short**|**Long Long**|Zero — zwiększenie|
|**bez znaku Short**|**znak bez znaku**|Zachowaj bajt o niskiej kolejności|
|**bez znaku Short**|**bez znaku**|Zero — zwiększenie|
|**bez znaku Short**|**bez znaku Long Long**|Zero — zwiększenie|
|**bez znaku Short**|**float**|Konwertuj na **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**bez znaku Short**|**double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**bez znaku Short**|**Long Double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**bez znaku**|**char**|Zachowaj bajt o niskiej kolejności|
|**bez znaku**|**short**|Zachowaj wyraz o niskiej kolejności|
|**bez znaku**|**long**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**bez znaku**|**Long Long**|Zero — zwiększenie|
|**bez znaku**|**znak bez znaku**|Zachowaj bajt o niskiej kolejności|
|**bez znaku**|**bez znaku Short**|Zachowaj wyraz o niskiej kolejności|
|**bez znaku**|**bez znaku Long Long**|Zero — zwiększenie|
|**bez znaku**|**float**|Konwertuj na **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**bez znaku**|**double**|Konwertuj bezpośrednio do **podwójnego**|
|**bez znaku**|**Long Double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**bez znaku Long Long**|**char**|Zachowaj bajt o niskiej kolejności|
|**bez znaku Long Long**|**short**|Zachowaj wyraz o niskiej kolejności|
|**bez znaku Long Long**|**long**|Zachowywanie wartości DWORD z niską kolejnością|
|**bez znaku Long Long**|**Long Long**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**bez znaku Long Long**|**znak bez znaku**|Zachowaj bajt o niskiej kolejności|
|**bez znaku Long Long**|**bez znaku Short**|Zachowaj wyraz o niskiej kolejności|
|**bez znaku Long Long**|**bez znaku**|Zachowywanie wartości DWORD z niską kolejnością|
|**bez znaku Long Long**|**float**|Konwertuj na **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**bez znaku Long Long**|**double**|Konwertuj bezpośrednio do **podwójnego**|
|**bez znaku Long Long**|**Long Double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
