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
ms.openlocfilehash: 79608b5ca4335ee3c30bdab27e7efade5b7e2f54
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998721"
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

Poniższa tabela zawiera podsumowanie konwersji z podpisanych typów całkowitych. Przyjęto założenie, że typ **char** jest podpisany domyślnie. Jeśli użyjesz opcji czasu kompilowania, aby zmienić wartość domyślną dla typu **char** na unsigned, zamiast konwersji w tej tabeli należy zastosować konwersje [z tabeli niepodpisanych typów całkowitych](../c-language/conversions-from-unsigned-integral-types.md) dla typu **znak bez znaku** .

**Specyficzne dla firmy Microsoft**

W kompilatorze firmy Microsoft **int** i **Long** są odrębnymi, ale równoważnymi typami. Konwersja wartości **int** jest wykonywana w taki sam sposób jak w przypadku konwersji **Long**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="table-of-conversions-from-signed-integral-types"></a>Tabela konwersji z podpisanych typów całkowitych

|Z|Do|Metoda|
|----------|--------|------------|
|**znak**<sup>1</sup>|**short**|Podjęcie i rozciągnięcie|
|**char**|**long**|Podjęcie i rozciągnięcie|
|**char**|**Long Long**|Podjęcie i rozciągnięcie|
|**char**|**znak bez znaku**|Zachowaj wzorzec; bit o wysokiej kolejności utraci funkcję jako bit znaku|
|**char**|**bez znaku Short**|Podpisz do **Short**; Konwertuj **krótko** - **unsigned Short**|
|**char**|**bez znaku**|Podpisz do **Long**; Konwertuj **Long** na **Long bez znaku**|
|**char**|**bez znaku Long Long**|Podpisz do **Long Long**; Konwertuj **Long** Long na **unsigned** Long Long|
|**char**|**float**|Podpisz do **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**char**|**double**|Podpisz do **Long**; Konwertuj **Long** na **Double**|
|**char**|**Long Double**|Podpisz do **Long**; Konwertuj **Long** na **Double**|
|**short**|**char**|Zachowaj bajt o niskiej kolejności|
|**short**|**long**|Podjęcie i rozciągnięcie|
|**short**|**Long Long**|Podjęcie i rozciągnięcie|
|**short**|**znak bez znaku**|Zachowaj bajt o niskiej kolejności|
|**short**|**bez znaku Short**|Zachowaj wzorzec bitowy; bit o wysokiej kolejności utraci funkcję jako bit znaku|
|**short**|**bez znaku**|Podpisz do **Long**; Konwertuj **Long** na **Long bez znaku**|
|**short**|**bez znaku Long Long**|Podpisz do **Long Long**; Konwertuj **Long** Long na **unsigned** Long Long|
|**short**|**float**|Podpisz do **Long**; Konwertuj **Long** na **zmiennoprzecinkową**|
|**short**|**double**|Podpisz do **Long**; Konwertuj **Long** na **Double**|
|**short**|**Long Double**|Podpisz do **Long**; Konwertuj **Long** na **Double**|
|**long**|**char**|Zachowaj bajt o niskiej kolejności|
|**long**|**short**|Zachowaj wyraz o niskiej kolejności|
|**long**|**Long Long**|Podjęcie i rozciągnięcie|
|**long**|**znak bez znaku**|Zachowaj bajt o niskiej kolejności|
|**long**|**bez znaku Short**|Zachowaj wyraz o niskiej kolejności|
|**long**|**bez znaku**|Zachowaj wzorzec bitowy; bit o wysokiej kolejności utraci funkcję jako bit znaku|
|**long**|**bez znaku Long Long**|Podpisz do **Long Long**; Konwertuj **Long** Long na **unsigned** Long Long|
|**long**|**float**|Reprezentuje jako **zmiennoprzecinkowe**. Jeśli **Long** nie można przedstawić dokładnie, pewna precyzja zostanie utracona.|
|**long**|**double**|Reprezentuje jako **Double**. Jeśli **Long** nie można reprezentować dokładnie jako **podwójnej**precyzji, pewne są tracone.|
|**long**|**Long Double**|Reprezentuje jako **Double**. Jeśli **Long** nie można reprezentować dokładnie jako **podwójnej**precyzji, pewne są tracone.|
|**Long Long**|**char**|Zachowaj bajt o niskiej kolejności|
|**Long Long**|**short**|Zachowaj wyraz o niskiej kolejności|
|**Long Long**|**long**|Zachowywanie wartości DWORD z niską kolejnością|
|**Long Long**|**znak bez znaku**|Zachowaj bajt o niskiej kolejności|
|**Long Long**|**bez znaku Short**|Zachowaj wyraz o niskiej kolejności|
|**Long Long**|**bez znaku**|Zachowywanie wartości DWORD z niską kolejnością|
|**Long Long**|**bez znaku Long Long**|Zachowaj wzorzec bitowy; bit o wysokiej kolejności utraci funkcję jako bit znaku|
|**Long Long**|**float**|Reprezentuje jako **zmiennoprzecinkowe**. Jeśli **Long Long** nie można dokładnie przedstawić, pewna dokładność zostanie utracona.|
|**Long Long**|**double**|Reprezentuje jako **Double**. Jeśli **Long Long** nie można reprezentować dokładnie jako **Double**, pewna dokładność zostanie utracona.|
|**Long Long**|**Long Double**|Reprezentuje jako **Double**. Jeśli **Long Long** nie można reprezentować dokładnie jako **Double**, pewna dokładność zostanie utracona.|

<sup>1</sup> wszystkie wpisy **znaków** zakładają, że typ **char** jest podpisany domyślnie.

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
