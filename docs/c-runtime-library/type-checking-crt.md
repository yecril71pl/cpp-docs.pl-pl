---
title: Sprawdzać typ (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.types
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
ms.openlocfilehash: bb5aecc2b47aa8e88666f42d8022395bf99fd85e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747686"
---
# <a name="type-checking-crt"></a>Sprawdzać typ (CRT)

Kompilator wykonuje ograniczoną kontrolę typów dla funkcji, które może potrwać zmienną liczbę argumentów, w następujący sposób:

|Wywołanie funkcji|Zaznaczone typów argumentów|
|-------------------|-----------------------------|
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|Pierwszy argument (format string)|
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|Pierwsze dwa argumenty (pliku lub buforu i format string)|
|`_snprintf_s`|Pierwsze trzy argumenty (pliku lub buforu, liczby wartości oraz ciąg formatu)|
|`_open`|Pierwsze dwa argumenty (ścieżki i `_open` flagi)|
|`_sopen_s`|Pierwszych trzech argumentów (ścieżka, `_open` flagę i tryb współdzielenia)|
|`_execl`, `_execle`, `_execlp`, `_execlpe`|Pierwsze dwa argumenty (ścieżki i pierwszy argument wskaźnik)|
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|Pierwsze trzy argumenty (flagę w trybie, ścieżki i pierwszy argument wskaźnik)|

Kompilator wykonuje ten sam typ ograniczony sprawdzania odpowiedniki o znakach szerokich tych funkcji.

## <a name="see-also"></a>Zobacz także

[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)
