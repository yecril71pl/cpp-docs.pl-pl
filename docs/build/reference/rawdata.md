---
title: /RAWDATA
ms.date: 11/04/2016
f1_keywords:
- /rawdata
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
ms.openlocfilehash: 02af8df04d80c20c5d7629b51abab6295a21f5e5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816467"
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
|*Liczba*|Wyświetlane wiersze są ustawione na szerokość, który przechowuje `number` wartości w każdym wierszu.|

Tylko [/HEADERS](headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)
