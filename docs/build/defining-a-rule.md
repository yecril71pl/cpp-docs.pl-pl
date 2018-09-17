---
title: Definiowanie zasady | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8a5cb7a0285f7abf8bcf476141451eae1b10f85
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705578"
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

[Ścieżki wyszukiwania w zasadach](../build/search-paths-in-rules.md)

## <a name="see-also"></a>Zobacz też

[Zasady wnioskowania](../build/inference-rules.md)