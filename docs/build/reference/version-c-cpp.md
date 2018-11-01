---
title: WERSJA (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VERSION
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
ms.openlocfilehash: 98758da627390ba4c7e852905457527a343baccc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667379"
---
# <a name="version-cc"></a>WERSJA (C/C++)

Informuje LINK, aby umieścić numer w nagłówku pliku .exe lub DLL.

```
VERSION major[.minor]
```

## <a name="remarks"></a>Uwagi

*Głównych* i *pomocnicza* argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535. Wartość domyślna to wersja 0,0.

Równoważne sposobem Określ numer wersji jest użycie [informacje o wersji](../../build/reference/version-version-information.md) (/ wersji) opcji.

## <a name="see-also"></a>Zobacz też

[Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)