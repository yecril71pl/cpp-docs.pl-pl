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
ms.openlocfilehash: 08b88b1343f56f8d79fc39c53505b26caecfe3c4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226467"
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

W kompilatorze firmy Microsoft **`unsigned`** (lub **`unsigned int`** ) i **`unsigned long`** są to różne, ale równoważne typy. Konwersja **`unsigned int`** wartości jest wykonywana w taki sam sposób jak w przypadku konwersji **`unsigned long`** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Poniższa tabela zawiera podsumowanie konwersji z niepodpisanych typów całkowitych.

## <a name="table-of-conversions-from-unsigned-integral-types"></a>Tabela konwersji z niepodpisanych typów całkowitych

|Źródło|Działanie|Metoda|
|----------|--------|------------|
|**`unsigned char`**|**`char`**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**`unsigned char`**|**`short`**|Zero — zwiększenie|
|**`unsigned char`**|**`long`**|Zero — zwiększenie|
|**`unsigned char`**|**`long long`**|Zero — zwiększenie|
|**`unsigned char`**|**`unsigned short`**|Zero — zwiększenie|
|**`unsigned char`**|**`unsigned long`**|Zero — zwiększenie|
|**`unsigned char`**|**`unsigned long long`**|Zero — zwiększenie|
|**`unsigned char`**|**`float`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`float`**|
|**`unsigned char`**|**`double`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`double`**|
|**`unsigned char`**|**`long double`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`double`**|
|**`unsigned short`**|**`char`**|Zachowaj bajt o niskiej kolejności|
|**`unsigned short`**|**`short`**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**`unsigned short`**|**`long`**|Zero — zwiększenie|
|**`unsigned short`**|**`long long`**|Zero — zwiększenie|
|**`unsigned short`**|**`unsigned char`**|Zachowaj bajt o niskiej kolejności|
|**`unsigned short`**|**`unsigned long`**|Zero — zwiększenie|
|**`unsigned short`**|**`unsigned long long`**|Zero — zwiększenie|
|**`unsigned short`**|**`float`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`float`**|
|**`unsigned short`**|**`double`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`double`**|
|**`unsigned short`**|**`long double`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`double`**|
|**`unsigned long`**|**`char`**|Zachowaj bajt o niskiej kolejności|
|**`unsigned long`**|**`short`**|Zachowaj wyraz o niskiej kolejności|
|**`unsigned long`**|**`long`**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**`unsigned long`**|**`long long`**|Zero — zwiększenie|
|**`unsigned long`**|**`unsigned char`**|Zachowaj bajt o niskiej kolejności|
|**`unsigned long`**|**`unsigned short`**|Zachowaj wyraz o niskiej kolejności|
|**`unsigned long`**|**`unsigned long long`**|Zero — zwiększenie|
|**`unsigned long`**|**`float`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`float`**|
|**`unsigned long`**|**`double`**|Konwertuj bezpośrednio na**`double`**|
|**`unsigned long`**|**`long double`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`double`**|
|**`unsigned long long`**|**`char`**|Zachowaj bajt o niskiej kolejności|
|**`unsigned long long`**|**`short`**|Zachowaj wyraz o niskiej kolejności|
|**`unsigned long long`**|**`long`**|Zachowywanie wartości DWORD z niską kolejnością|
|**`unsigned long long`**|**`long long`**|Zachowaj wzorzec bitowy; bit z wysokim priorytetem jest bit znaku|
|**`unsigned long long`**|**`unsigned char`**|Zachowaj bajt o niskiej kolejności|
|**`unsigned long long`**|**`unsigned short`**|Zachowaj wyraz o niskiej kolejności|
|**`unsigned long long`**|**`unsigned long`**|Zachowywanie wartości DWORD z niską kolejnością|
|**`unsigned long long`**|**`float`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`float`**|
|**`unsigned long long`**|**`double`**|Konwertuj bezpośrednio na**`double`**|
|**`unsigned long long`**|**`long double`**|Konwertuj na **`long`** ; Konwertuj **`long`** na**`double`**|

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
