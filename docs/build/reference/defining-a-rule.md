---
title: Definiowanie zasady
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: cd82dc5b0693e563fd3d75a0215265089ff57913
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342893"
---
# <a name="defining-a-rule"></a>Definiowanie zasady

*Fromext* reprezentuje rozszerzenie nazwy pliku zależnego i *toext* reprezentuje rozszerzenie nazwy pliku docelowego.

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>Uwagi

Rozszerzenia nie jest uwzględniana wielkość liter. Makra może być użyta do reprezentowania *fromext* i *toext*; makra są rozwijane podczas wstępnego przetwarzania. Kropka (.) poprzedniego *fromext* musi znajdować się na początku wiersza. Dwukropek (:) jest poprzedzone zero lub więcej tabulacji lub spacji. Może występować tylko z miejsc do magazynowania lub kart, średnika (;), aby określić polecenie, znak numeru (#) do określenia komentarz lub znak nowego wiersza. Nie inne spacje są dozwolone. Polecenia są określane jak bloki opisów.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Ścieżki wyszukiwania w zasadach](search-paths-in-rules.md)

## <a name="see-also"></a>Zobacz także

[Zasady wnioskowania](inference-rules.md)
