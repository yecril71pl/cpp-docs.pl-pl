---
title: -RAWDATA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rawdata
dev_langs:
- C++
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38677b0e67ddaec5b6ef0e3fcffed1bed27826b6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707177"
---
# <a name="rawdata"></a>/RAWDATA

```
/RAWDATA[:{1|2|4|8|NONE[,number]]
```

## <a name="remarks"></a>Uwagi

Ta opcja wyświetla nieprzetworzonej zawartości każdej sekcji w pliku. Argumenty kontrolować format wyświetlania, jak pokazano poniżej:

|Argument|Wynik|
|--------------|------------|
|1|Domyślnie. Zawartość jest wyświetlana bajty szesnastkowe, a także jako znaki ASCII, jeśli mają one reprezentację drukowanych.|
|2|Zawartości są wyświetlane jako wartości szesnastkowych 2-bajtowych.|
|4|Zawartości są wyświetlane jako wartości szesnastkowych 4-bajtowe.|
|8|Zawartość jest wyświetlana jako wartości 8-bajtowych szesnastkowe.|
|BRAK|Nieprzetworzone dane są pomijane. Ten argument jest przydatne do kontroli danych wyjściowych/ALL.|
|*Numer*|Wyświetlane wiersze są ustawione na szerokość, który przechowuje `number` wartości w każdym wierszu.|

Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)