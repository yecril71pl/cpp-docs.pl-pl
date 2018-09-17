---
title: Makra zmiennych środowiskowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cebb544b1d8fc8489de298bf7512cc612a6dfef2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701171"
---
# <a name="environment-variable-macros"></a>Makra zmiennych środowiskowych

NMAKE dziedziczy definicji makra zmiennych środowiskowych, występujących przed rozpoczęciem sesji. Jeśli zmienna została ustawiona w środowisku systemu operacyjnego, jest ona dostępna jako makro NMAKE. Odziedziczone nazwy są konwertowane na wielkie litery. Dziedziczenie wcześniejsza przetwarzania wstępnego. Opcja /E umożliwia powodują, że makra odziedziczone zmiennych środowiskowych w celu zastąpienia makra o tej samej nazwie w pliku reguł programu make.

Makra zmiennych środowiskowych można ponownie zdefiniować w sesji, a spowoduje to zmianę odpowiednich zmiennej środowiskowej. Można również zmienić zmienne środowiskowe w poleceniu SET. Aby zmienić zmienną środowiskową w sesji przy użyciu polecenia SET nie zmienia się odpowiednie makro, jednak.

Na przykład:

```
PATH=$(PATH);\nonesuch

all:
    echo %PATH%
```

W tym przykładzie, zmieniając `PATH` zmienia odpowiednią zmienną środowiska `PATH`; dołącza `\nonesuch` do ścieżki.

Jeśli zmienna środowiskowa jest zdefiniowana jako ciąg, który jest nieprawidłowy w pliku reguł programu make, makro nie zostanie utworzony i jest generowany bez ostrzeżenia. Jeśli wartość zmiennej zawiera znak dolara ($), NMAKE zinterpretuje ją jako początek wywołanie makra. Za pomocą makra może spowodować nieoczekiwane zachowanie.

## <a name="see-also"></a>Zobacz też

[Specjalne makra NMAKE](../build/special-nmake-macros.md)