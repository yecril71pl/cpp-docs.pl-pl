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
|**unsigned char**|**char**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**unsigned char**|**short**|Zero — zwiększenie|
|**unsigned char**|**długi**|Zero — zwiększenie|
|**unsigned char**|**long long**|Zero — zwiększenie|
|**unsigned char**|**unsigned short**|Zero — zwiększenie|
|**unsigned char**|**unsigned long**|Zero — zwiększenie|
|**unsigned char**|**bez znaku Long Long**|Zero — zwiększenie|
|**unsigned char**|**float**|Konwertuj na **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**unsigned char**|**double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**unsigned char**|**Long Double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**unsigned short**|**char**|Zachowaj bajt o niskiej kolejności|
|**unsigned short**|**short**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**unsigned short**|**długi**|Zero — zwiększenie|
|**unsigned short**|**long long**|Zero — zwiększenie|
|**unsigned short**|**unsigned char**|Zachowaj bajt o niskiej kolejności|
|**unsigned short**|**unsigned long**|Zero — zwiększenie|
|**unsigned short**|**bez znaku Long Long**|Zero — zwiększenie|
|**unsigned short**|**float**|Konwertuj na **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**unsigned short**|**double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**unsigned short**|**Long Double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**unsigned long**|**char**|Zachowaj bajt o niskiej kolejności|
|**unsigned long**|**short**|Zachowaj wyraz o niskiej kolejności|
|**unsigned long**|**długi**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**unsigned long**|**long long**|Zero — zwiększenie|
|**unsigned long**|**unsigned char**|Zachowaj bajt o niskiej kolejności|
|**unsigned long**|**unsigned short**|Zachowaj wyraz o niskiej kolejności|
|**unsigned long**|**bez znaku Long Long**|Zero — zwiększenie|
|**unsigned long**|**float**|Konwertuj na **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**unsigned long**|**double**|Konwertuj bezpośrednio do **podwójnego**|
|**unsigned long**|**Long Double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|
|**bez znaku Long Long**|**char**|Zachowaj bajt o niskiej kolejności|
|**bez znaku Long Long**|**short**|Zachowaj wyraz o niskiej kolejności|
|**bez znaku Long Long**|**długi**|Zachowywanie wartości DWORD z niską kolejnością|
|**bez znaku Long Long**|**long long**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**bez znaku Long Long**|**unsigned char**|Zachowaj bajt o niskiej kolejności|
|**bez znaku Long Long**|**unsigned short**|Zachowaj wyraz o niskiej kolejności|
|**bez znaku Long Long**|**unsigned long**|Zachowywanie wartości DWORD z niską kolejnością|
|**bez znaku Long Long**|**float**|Konwertuj na **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**bez znaku Long Long**|**double**|Konwertuj bezpośrednio do **podwójnego**|
|**bez znaku Long Long**|**Long Double**|Konwertuj na **Long**; Konwertuj **Long** na **Double**|

## <a name="see-also"></a>Zobacz też

[Konwersje przypisań](../c-language/assignment-conversions.md)
