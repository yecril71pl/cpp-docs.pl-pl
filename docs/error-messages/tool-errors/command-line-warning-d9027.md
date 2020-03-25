---
title: Ostrzeżenie D9027 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: 46ed5750bd1f315f20658ace9b83fac532fbbabb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196681"
---
# <a name="command-line-warning-d9027"></a>Ostrzeżenie D9027 dla wiersza polecenia

Zignorowano plik źródłowy "\<filename >"

CL. exe zignorował wejściowy plik źródłowy.

To ostrzeżenie może być spowodowane spacją między opcją/fo a wyjściową nazwą pliku w wierszu polecenia z/c opcją. Na przykład:

```
cl /c /Fo output.obj input.c
```

Ponieważ istnieje spacja między/FO i `output.obj`, CL. exe pobiera `output.obj` jako nazwę pliku wejściowego. Aby rozwiązać ten problem, Usuń miejsce:

```
cl /c /Fooutput.obj input.c
```
