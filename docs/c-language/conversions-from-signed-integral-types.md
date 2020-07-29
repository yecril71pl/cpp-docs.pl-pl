---
title: Konwersje z podpisanych typów całkowitych
ms.date: 10/02/2019
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: d41d2fd205a87f9f2be2179ffd8e38256a96e4f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226480"
---
# <a name="conversions-from-signed-integral-types"></a>Konwersje z podpisanych typów całkowitych

Gdy liczba całkowita ze znakiem jest konwertowana na liczbę całkowitą lub typ zmiennoprzecinkowy, jeśli oryginalna wartość jest reprezentacja w typie wynikowym, wartość nie jest zmieniana.

Gdy liczba całkowita ze znakiem jest konwertowana na liczbę całkowitą o większym rozmiarze, wartość jest podwyższana. W przypadku przekonwertowania na liczbę całkowitą o mniejszym rozmiarze bity o dużej kolejności są obcinane. Wynik jest interpretowany przy użyciu typu wyniku, jak pokazano w poniższym przykładzie:

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

W przypadku konwertowania podpisanej liczby całkowitej na typ zmiennoprzecinkowy, jeśli oryginalna wartość nie jest zaprezentowana dokładnie w typie wynikowym, wynik jest następną wyższą lub mniejszą reprezentacją wartości.

Informacje o rozmiarach typów całkowitych i zmiennoprzecinkowych znajdują się w temacie [Storage of Basic Types](../c-language/storage-of-basic-types.md).

Poniższa tabela zawiera podsumowanie konwersji z podpisanych typów całkowitych. Zakłada, że **`char`** Typ jest podpisany domyślnie. Jeśli używasz opcji czasu kompilowania, aby zmienić wartość domyślną dla **`char`** typu unsigned, konwersje podanych w tabeli [typów całkowitych bez znaku](../c-language/conversions-from-unsigned-integral-types.md) dla **`unsigned char`** typu Apply zamiast konwersji w tej tabeli.

**Specyficzne dla firmy Microsoft**

W kompilatorze firmy Microsoft **`int`** i **`long`** są to różne, ale równoważne typy. Konwersja wartości jest wykonywana **`int`** w taki sam sposób jak w przypadku konwersji **`long`** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="table-of-conversions-from-signed-integral-types"></a>Tabela konwersji z podpisanych typów całkowitych

|Źródło|Działanie|Metoda|
|----------|--------|------------|
|**`char`**<sup>jedno</sup>|**`short`**|Podjęcie i rozciągnięcie|
|**`char`**|**`long`**|Podjęcie i rozciągnięcie|
|**`char`**|**`long long`**|Podjęcie i rozciągnięcie|
|**`char`**|**`unsigned char`**|Zachowaj wzorzec; bit o wysokiej kolejności utraci funkcję jako bit znaku|
|**`char`**|**`unsigned short`**|Podpisz do **`short`** ; Konwertuj **`short`** na**`unsigned short`**|
|**`char`**|**`unsigned long`**|Podpisz do **`long`** ; Konwertuj **`long`** na**`unsigned long`**|
|**`char`**|**`unsigned long long`**|Podpisz do **`long long`** ; Konwertuj **`long long`** na**`unsigned long long`**|
|**`char`**|**`float`**|Podpisz do **`long`** ; Konwertuj **`long`** na**`float`**|
|**`char`**|**`double`**|Podpisz do **`long`** ; Konwertuj **`long`** na**`double`**|
|**`char`**|**`long double`**|Podpisz do **`long`** ; Konwertuj **`long`** na**`double`**|
|**`short`**|**`char`**|Zachowaj bajt o niskiej kolejności|
|**`short`**|**`long`**|Podjęcie i rozciągnięcie|
|**`short`**|**`long long`**|Podjęcie i rozciągnięcie|
|**`short`**|**`unsigned char`**|Zachowaj bajt o niskiej kolejności|
|**`short`**|**`unsigned short`**|Zachowaj wzorzec bitowy; bit o wysokiej kolejności utraci funkcję jako bit znaku|
|**`short`**|**`unsigned long`**|Podpisz do **`long`** ; Konwertuj **`long`** na**`unsigned long`**|
|**`short`**|**`unsigned long long`**|Podpisz do **`long long`** ; Konwertuj **`long long`** na**`unsigned long long`**|
|**`short`**|**`float`**|Podpisz do **`long`** ; Konwertuj **`long`** na**`float`**|
|**`short`**|**`double`**|Podpisz do **`long`** ; Konwertuj **`long`** na**`double`**|
|**`short`**|**`long double`**|Podpisz do **`long`** ; Konwertuj **`long`** na**`double`**|
|**`long`**|**`char`**|Zachowaj bajt o niskiej kolejności|
|**`long`**|**`short`**|Zachowaj wyraz o niskiej kolejności|
|**`long`**|**`long long`**|Podjęcie i rozciągnięcie|
|**`long`**|**`unsigned char`**|Zachowaj bajt o niskiej kolejności|
|**`long`**|**`unsigned short`**|Zachowaj wyraz o niskiej kolejności|
|**`long`**|**`unsigned long`**|Zachowaj wzorzec bitowy; bit o wysokiej kolejności utraci funkcję jako bit znaku|
|**`long`**|**`unsigned long long`**|Podpisz do **`long long`** ; Konwertuj **`long long`** na**`unsigned long long`**|
|**`long`**|**`float`**|Reprezentuje jako **`float`** . Jeśli **`long`** nie może być reprezentowany dokładnie, pewna dokładność zostanie utracona.|
|**`long`**|**`double`**|Reprezentuje jako **`double`** . Jeśli **`long`** element nie może być reprezentowany dokładnie jako **`double`** , pewna dokładność zostanie utracona.|
|**`long`**|**`long double`**|Reprezentuje jako **`double`** . Jeśli **`long`** element nie może być reprezentowany dokładnie jako **`double`** , pewna dokładność zostanie utracona.|
|**`long long`**|**`char`**|Zachowaj bajt o niskiej kolejności|
|**`long long`**|**`short`**|Zachowaj wyraz o niskiej kolejności|
|**`long long`**|**`long`**|Zachowywanie wartości DWORD z niską kolejnością|
|**`long long`**|**`unsigned char`**|Zachowaj bajt o niskiej kolejności|
|**`long long`**|**`unsigned short`**|Zachowaj wyraz o niskiej kolejności|
|**`long long`**|**`unsigned long`**|Zachowywanie wartości DWORD z niską kolejnością|
|**`long long`**|**`unsigned long long`**|Zachowaj wzorzec bitowy; bit o wysokiej kolejności utraci funkcję jako bit znaku|
|**`long long`**|**`float`**|Reprezentuje jako **`float`** . Jeśli **`long long`** nie może być reprezentowany dokładnie, pewna dokładność zostanie utracona.|
|**`long long`**|**`double`**|Reprezentuje jako **`double`** . Jeśli **`long long`** element nie może być reprezentowany dokładnie jako **`double`** , pewna dokładność zostanie utracona.|
|**`long long`**|**`long double`**|Reprezentuje jako **`double`** . Jeśli **`long long`** element nie może być reprezentowany dokładnie jako **`double`** , pewna dokładność zostanie utracona.|

<sup>1</sup> wszystkie **`char`** wpisy zakładają, że **`char`** Typ jest podpisany domyślnie.

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
