---
title: Makra zmiennych środowiskowych
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
ms.openlocfilehash: 4691f89f1886b40637a0800ee8a6a94e4b4e06c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594301"
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