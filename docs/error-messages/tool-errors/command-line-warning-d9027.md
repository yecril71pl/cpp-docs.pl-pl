---
title: Ostrzeżenie wiersza polecenia D9027 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 105ebbf62027ac3d9377c513c4f7c59e261b983d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112528"
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