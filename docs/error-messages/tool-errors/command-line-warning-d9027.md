---
title: Ostrzeżenie D9027 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: f89e7416efe7a0069ee2dae8df921933bbe76bcf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482605"
---
# <a name="command-line-warning-d9027"></a>Ostrzeżenie D9027 dla wiersza polecenia

plik źródłowy "\<nazwa pliku >" zignorowany

CL.exe zignorowany plik źródła danych wejściowych.

To ostrzeżenie może być spowodowany odstęp między opcją /Fo i nazwa pliku wyjściowego, w wierszu polecenia z opcją/c. Na przykład:

```
cl /c /Fo output.obj input.c
```

Ponieważ odstęp między /Fo i `output.obj`, przyjmuje CL.exe `output.obj` jako nazwę pliku wejściowego. Aby rozwiązać ten problem, Usuń miejsce:

```
cl /c /Fooutput.obj input.c
```