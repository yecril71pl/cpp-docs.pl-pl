---
title: Ocena tokenów
ms.date: 11/04/2016
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
ms.openlocfilehash: 15775ca9a7ada46aaf4e53ae952cd67e95bbf8d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234026"
---
# <a name="evaluation-of-tokens"></a>Ocena tokenów

Gdy kompilator interpretuje tokeny, zawiera dowolną liczbę znaków w ramach jednego tokenu przed przejściem do następnego tokenu. Ze względu na to zachowanie kompilator może nie interpretować tokenów zgodnie z oczekiwaniami, jeśli nie są prawidłowo oddzielone znakami odstępu. Rozważ następujące wyrażenie:

```
i+++j
```

W tym przykładzie kompilator najpierw tworzy najdłuższy możliwy operator (`++`) od trzech znaków plus, a następnie przetwarza pozostałe znak plus jako operator dodawania (`+`). W tym celu wyrażenie jest interpretowane `(i++) + (j)`jako, `(i) + (++j)`nie. W tym i podobnym przypadku użyj białych znaków i nawiasów, aby uniknąć niejednoznaczności i zapewnić poprawne obliczanie wyrażeń.

**Specyficzne dla firmy Microsoft**

Kompilator języka C traktuje znak CTRL + Z jako wskaźnik końca pliku. Ignoruje dowolny tekst po kombinacji klawiszy CTRL + Z.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Tokeny języka C](../c-language/c-tokens.md)
