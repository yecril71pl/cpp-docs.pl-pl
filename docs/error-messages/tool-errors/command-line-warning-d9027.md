---
title: Ostrzeżenie D9027 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: f89e7416efe7a0069ee2dae8df921933bbe76bcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214131"
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