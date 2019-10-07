---
title: Konwersje z typów zmiennoprzecinkowych
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998717"
---
# <a name="conversions-from-floating-point-types"></a>Konwersje z typów zmiennoprzecinkowych

Wartość zmiennoprzecinkowa, która jest konwertowana na inny typ zmiennoprzecinkowy, nie zmienia wartości, jeśli oryginalna wartość zostanie zaprezentowana dokładnie w typie wynikowym. Jeśli oryginalna wartość jest wartością liczbową, ale nie będzie można jej przedstawić dokładnie, wynikiem jest kolejna lub Następna Dolna wartość. Zobacz [limity dla stałych zmiennoprzecinkowych](../c-language/limits-on-floating-point-constants.md) dla zakresu typów zmiennoprzecinkowych.

Wartość zmiennoprzecinkowa konwertowana na typ całkowity jest najpierw obcinana przez odrzucenie dowolnej wartości ułamkowej. Jeśli ta obcięta wartość będzie reprezentować w typie wyniku, wynik musi być tą wartością. Gdy nie można jej reprezentować, wartość wyniku jest niezdefiniowana.

**Specyficzne dla firmy Microsoft**

Kompilatory firmy Microsoft wykorzystują reprezentację binary32 IEEE-754 dla wartości **zmiennoprzecinkowych** i reprezentację binary64 dla **Long Double** i **Double**. Ponieważ **Long Double** i **Double** używają tej samej reprezentacji, mają one ten sam zakres i precyzję.

Gdy kompilator konwertuje liczbę zmiennoprzecinkową **podwójną** lub **długą** na **zmiennoprzecinkową**, zaokrągla wynik zgodnie z kontrolkami środowisk zmiennoprzecinkowych, które domyślnie są "okrągłe do najbliższe, powiązania z parzystością". Jeśli wartość liczbowa jest zbyt duża lub zbyt niska, aby mogła być reprezentowana jako liczbowa wartość **zmiennoprzecinkowa** , wynik konwersji jest dodatnią lub ujemną nieskończoność zgodnie ze znakiem oryginalnej wartości i zostanie zgłoszony wyjątek przepełnienia, jeśli jest włączony.

Podczas konwertowania na typy całkowite wynik konwersji do typu mniejszego niż **Long** jest wynikiem konwersji wartości na wartość **Long**, a następnie konwertowania na typ wyniku.

Dla konwersji na typy całkowite o rozmiarze co najmniej tak **długo**, konwersja wartości, która jest zbyt duża lub zbyt niska do reprezentowania w typie wynikowym, może zwracać jedną z następujących wartości:

- Wynik może być *wartością wskaźnikową*, która jest reprezentacją z wartości od zera. W przypadku podpisanych typów jest to najniższa wartość reprezentacja (0x800... 0). W przypadku typów bez znaku jest to najwyższa reprezentacja wartości (0xFF... F).

- Wyniki mogą być *nasycone*, gdzie wartości zbyt wysokie do reprezentowania są konwertowane na największą reprezentację wartości, a wartości zbyt niskie do reprezentowania są konwertowane na najniższą reprezentację wartości. Jedna z tych dwóch wartości jest również używana jako wartość wskaźnikowa.

- W przypadku konwersji do **niepodpisanej** długiej lub **niepodpisanej długi**czas, wynikiem konwersji wartości poza zakresem może być wartość inna niż najwyższa lub najniższa wartość, którą można reprezentować. Określa, czy wynik jest wartością wskaźnikową, czy niezależną od opcji kompilatora i architektury docelowej. Przyszłe wydania kompilatora mogą zwrócić wartość nasyconej lub wskaźnikowej.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

W poniższej tabeli zestawiono konwersje z typów zmiennoprzecinkowych.

## <a name="table-of-conversions-from-floating-point-types"></a>Tabela konwersji z typów zmiennoprzecinkowych

|Z|Do|Metoda|
|----------|--------|------------|
|**float**|**char**|Konwertuj na **Long**; Konwertuj wartość **Long** na **char**|
|**float**|**short**|Konwertuj na **Long**; Konwertuj z **Long** na **Short**|
|**float**|**int**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży do reprezentowania jako **int**, wynik jest niezdefiniowany.|
|**float**|**long**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży do reprezentowania jako **Long**, wynik jest niezdefiniowany.|
|**float**|**Long Long**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży do reprezentowania jako **Long Long**, wynik jest niezdefiniowany.|
|**float**|**znak bez znaku**|Konwertuj na **Long**; Konwertuj **Long** na **znak bez znaku**|
|**float**|**bez znaku Short**|Konwertuj na **Long**; Konwertuj **Long** na **Short bez znaku**|
|**float**|**bajt**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży do reprezentowania jako **unsigned**, wynik jest niezdefiniowany.|
|**float**|**bez znaku**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży, aby można go było przedstawić jako **Long unsigned**, wynik jest niezdefiniowany.|
|**float**|**bez znaku Long Long**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży do reprezentowania jako **unsigned long long**, wynik jest niezdefiniowany.|
|**float**|**double**|Reprezentuje jako **Double**.|
|**float**|**Long Double**|Reprezentuje jako **Long Double**.|
|**double**|**char**|Konwertuj na **zmiennoprzecinkowe**; Konwertuj wartość **zmiennoprzecinkową** na wartość typu **char**|
|**double**|**short**|Konwertuj na **zmiennoprzecinkowe**; Konwertuj **zmiennoprzecinkowe** na **krótkie**|
|**double**|**int**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży do reprezentowania jako **int**, wynik jest niezdefiniowany.|
|**double**|**long**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży do reprezentowania jako **Long**, wynik jest niezdefiniowany.|
|**double**|**znak bez znaku**|Konwertuj na **Long**; Konwertuj **Long** na **znak bez znaku**|
|**double**|**bez znaku Short**|Konwertuj na **Long**; Konwertuj **Long** na **Short bez znaku**|
|**double**|**bajt**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży do reprezentowania jako **unsigned**, wynik jest niezdefiniowany.|
|**double**|**bez znaku**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży, aby można go było przedstawić jako **Long unsigned**, wynik jest niezdefiniowany.|
|**double**|**bez znaku Long Long**|Obetnij w punkcie dziesiętnym. Jeśli wynik jest zbyt duży do reprezentowania jako **unsigned long long**, wynik jest niezdefiniowany.|
|**double**|**float**|Reprezentuje jako wartość **zmiennoprzecinkową**. Jeśli wartość **podwójnej precyzji** nie może być reprezentowana dokładnie jako **zmiennoprzecinkowa**, nastąpi utrata dokładności. Jeśli wartość jest zbyt duża, aby była reprezentowana jako **zmiennoprzecinkowa**, wynik jest niezdefiniowany.|
|**double**|**Long Double**|Wartość **Long Double** jest traktowana jako **Double**.|

Konwersje z **Long Double** są takie same jak konwersje z **Double**.

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
