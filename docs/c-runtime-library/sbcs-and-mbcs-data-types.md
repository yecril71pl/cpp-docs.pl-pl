---
title: SBCS i MBCS — Typy danych
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 2d73155e36909efb1a7261f9fe45c2431525437a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742906"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS i MBCS — Typy danych

Oczekuje, że do procedury biblioteki czasu wykonywania MBCS firmy Microsoft, który obsługuje tylko jeden znak wielobajtowy lub jednobajtowego znaku wielobajtowego `unsigned int` argumentu (gdzie 0x00 < = wartość znaku < = 0xFFFF i 0x00 < = wartość bajtu < = 0xFF). Procedura MBCS, który obsługuje wielobajtowych bajtów lub znaków w kontekście ciągu oczekuje, że może być reprezentowana jako ciąg znaków wielobajtowych `unsigned char` wskaźnika.

> [!CAUTION]
> Każdego bajtu wiodącego znaku wielobajtowego mogą być przedstawione na 8-bitową **char**. Jednak znak Jednobajtowy SBCS lub MBCS typu **char** o wartości większej niż 0x7F jest ujemny. Gdy taki znak jest konwertowany bezpośrednio do **int** lub **długie**, wynik jest rozszerzona o znak przez kompilator i w związku z tym może przynieść nieoczekiwane wyniki.

W związku z tym najlepiej reprezentują bajtu wiodącego znaku wielobajtowego jak 8-bitową `unsigned char`. Lub, aby uniknąć wynik ujemny, po prostu konwersji znaków jednobajtowych typu **char** do `unsigned char` przed przekonwertowaniem go do **int** lub **długie**.

Ponieważ niektóre parametry SBCS — Obsługa funkcji take (z podpisem) **char** <strong>\*</strong> parametrów ostrzeżenia kompilatora niezgodność typu spowoduje, że gdy **_MBCS** jest zdefiniowane. Istnieją trzy sposoby, aby uniknąć to ostrzeżenie, wymienione w kolejności wydajność:

1. W TCHAR, należy używać funkcji śródwierszowych bezpiecznegop typu. H. Jest to zachowanie domyślne.

1. Użyj makra bezpośrednie w TCHAR. H, definiując **_MB_MAP_DIRECT** w wierszu polecenia. Jeśli to zrobisz, musisz ręcznie dopasować typów. To najszybszy sposób, ale nie jest bezpieczny.

1. W TCHAR, należy użyć funkcji bezpiecznego typu statycznie połączoną bibliotekę. H. Aby to zrobić, należy zdefiniować stałą **_NO_INLINING** w wierszu polecenia. Jest to metoda najwolniejsze, ale najbardziej bezpieczny.

## <a name="see-also"></a>Zobacz także

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
