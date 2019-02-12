---
title: Konwersje z podpisanych typów całkowitych
ms.date: 11/04/2016
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: 4d2f0ab43adf3cbad3d1ffa244551c67883c6606
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152784"
---
# <a name="conversions-from-signed-integral-types"></a>Konwersje z podpisanych typów całkowitych

Jeśli wartość liczby całkowitej ze znakiem nie jest ujemna liczba całkowita ze znakiem jest konwertowany na liczbę całkowitą bez znaku z równym lub większym rozmiarze, wartość jest bez zmian. Konwersja dokonuje logowania zwiększanie liczby całkowitej ze znakiem. Liczba całkowita ze znakiem jest konwertowany krótszy liczby całkowitej ze znakiem tworzy bardziej znaczących bitów. Wynik jest interpretowany jako wartość nieoznaczona, jak pokazano w poniższym przykładzie.

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

Dane nie zostaną utracone podczas liczba całkowita ze znakiem jest konwertowana na wartość zmiennoprzecinkową, z wyjątkiem tego, aby precyzyjnie mogą zostać utracone podczas **long int** lub **unsigned long int** wartość jest konwertowana na **float** wartość.

W poniższej tabeli przedstawiono konwersje z podpisanych typów całkowitych. Ta tabela zakłada się, że **char** typ ma znak domyślnie. Jeśli używasz opcji kompilacji, aby zmienić domyślną **char** konwersje w typów na typy bez znaku, [konwersje z niepodpisanych typów całkowitych](../c-language/conversions-from-unsigned-integral-types.md) tabeli dla **unsigned char**  typu Zastosuj zamiast konwersje w poniższej tabeli, konwersje z typów całkowitych oznaczonych.

### <a name="conversions-from-signed-integral-types"></a>Konwersje z podpisanych typów całkowitych

|Z|Zadanie|Metoda|
|----------|--------|------------|
|**CHAR**1|**short**|Rozszerzanie logowania|
|**char**|**long**|Rozszerzanie logowania|
|**char**|**unsigned char**|Zachowaj wzorca; bit wyższego rzędu traci funkcję jako bitu znaku|
|**char**|**short bez znaku**|Rozszerzenie o znak na **krótki**; Konwertuj **krótki** do **typ unsigned short**|
|**char**|**unsigned long**|Rozszerzanie logowania na **długie**; Konwertuj **długie** do **unsigned long**|
|**char**|**float**|Rozszerzanie logowania na **długie**; Konwertuj **długie** do **float**|
|**char**|**double**|Rozszerzanie logowania na **długie**; Konwertuj **długie** do **double**|
|**char**|**Liczba typu double**|Rozszerzanie logowania na **długie**; Konwertuj **długie** do **double**|
|**short**|**char**|Zachowaj mniej znaczący bajt|
|**short**|**long**|Rozszerzanie logowania|
|**short**|**unsigned char**|Zachowaj mniej znaczący bajt|
|**short**|**short bez znaku**|Zachowaj wzorzec bitowy; bit wyższego rzędu traci funkcję jako bitu znaku|
|**short**|**unsigned long**|Rozszerzanie logowania na **długie**; Konwertuj **długie** do **unsigned long**|
|**short**|**float**|Rozszerzanie logowania na **długie**; Konwertuj **długie** do **float**|
|**short**|**double**|Rozszerzanie logowania na **długie**; Konwertuj **długie** do **double**|
|**short**|**Liczba typu double**|Rozszerzanie logowania na **długie**; Konwertuj **długie** do **double**|
|**long**|**char**|Zachowaj mniej znaczący bajt|
|**long**|**short**|Zachowaj niskiego rzędu programu word|
|**long**|**unsigned char**|Zachowaj mniej znaczący bajt|
|**long**|**short bez znaku**|Zachowaj niskiego rzędu programu word|
|**long**|**unsigned long**|Zachowaj wzorzec bitowy; bit wyższego rzędu traci funkcję jako bitu znaku|
|**long**|**float**|Reprezentacja jako **float**. Jeśli **długie** nie może być reprezentowany dokładnie tak, niektóre dokładności zostaną utracone.|
|**long**|**double**|Reprezentacja jako **double**. Jeśli **długie** nie może być reprezentowany dokładnie jako **double**, niektóre dokładności zostaną utracone.|
|**long**|**Liczba typu double**|Reprezentacja jako **double**. Jeśli **długie** nie może być reprezentowany dokładnie jako **double**, niektóre dokładności zostaną utracone.|

1. Wszystkie **char** wpisy przyjęto założenie, że **char** typ ma znak domyślnie.

**Microsoft Specific**

Kompilator Microsoft 32-bitowe języka C, liczba całkowita jest odpowiednikiem **długie**. Konwersja **int** wartość rozpoczynające się takie same jak w przypadku **długie**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
