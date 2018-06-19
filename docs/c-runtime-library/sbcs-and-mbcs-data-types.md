---
title: SBCS i MBCS — typy danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- MBCS
- SBCS
dev_langs:
- C++
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccdec81251589ba36209f878f1fa8b727d7d2b98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409280"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS i MBCS — Typy danych

Do procedury biblioteki czasu wykonywania MBCS firmy Microsoft, które obsługuje tylko znaków wielobajtowych jednego lub jeden bajt znaków wielobajtowych oczekuje `unsigned int` argumentu (gdzie 0x00 < = wartość znaku < = 0xFFFF i 0x00 < = wartość bajtu < = 0xFF). Procedura MBCS obsługująca wielobajtowe bajtów lub znaków w kontekście ciąg spodziewa się ciągu znaków wielobajtowych może być reprezentowana jako `unsigned char` wskaźnika.

> [!CAUTION]
> Każdy bajt znaków wielobajtowych może być reprezentowany w 8-bitową **char**. Jednak SBCS i MBCS znaków jednobajtowych typu **char** o wartości większej niż 0x7F jest ujemna. Gdy taki znak jest konwertowany bezpośrednio do **int** lub **długi**, wynik jest znakiem przez kompilator i w związku z tym może dać nieoczekiwane wyniki.

W związku z tym najlepiej do reprezentowania bajt znaków wielobajtowych jako 8-bitową `unsigned char`. Lub, w celu uniknięcia negatywnego wyniku, po prostu wykonać konwersji znaków typu **char** do `unsigned char` przed przekonwertowaniem go do **int** lub **długi**.

Ponieważ niektóre SBCS ciąg służącego do obsługi funkcji podjęcia (ze znakiem) **char\***  parametrów, ostrzeżenie kompilatora niezgodność typu spowoduje, że podczas **_MBCS** jest zdefiniowany. Istnieją trzy sposoby, aby uniknąć tego ostrzeżenia, wymienionych według wydajności:

1. Użyj funkcji śródwierszowych bezpieczne w tchar —. H. Jest to zachowanie domyślne.

1. Użyj bezpośredniego makra w tchar —. H, definiując **_MB_MAP_DIRECT** w wierszu polecenia. Jeśli to zrobisz, musisz ręcznie dopasować typów. To jest najszybszy sposób, ale nie jest bezpieczne.

1. Użyj funkcji bezpieczny statycznie połączone biblioteki w tchar —. H. Aby to zrobić, należy zdefiniować stała **_NO_INLINING** w wierszu polecenia. Jest to metoda najwolniejsze, ale najbardziej bezpieczne.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
