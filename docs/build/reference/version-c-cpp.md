---
title: WERSJA (C/C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VERSION
dev_langs:
- C++
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7330d979e841d952f7e800e52ae762256ede6808
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718305"
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