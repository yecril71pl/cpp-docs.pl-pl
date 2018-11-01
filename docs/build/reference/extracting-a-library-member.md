---
title: Wyodrębnianie członka biblioteki
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 2975ef584b0244a16b556232b6939308d2e1bd14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447037"
---
# <a name="extracting-a-library-member"></a>Wyodrębnianie członka biblioteki

LIB można użyć, aby utworzyć plik obiektowy (.obj), który zawiera kopię elementu członkowskiego istniejącej biblioteki. Aby wyodrębnić kopiowania elementu członkowskiego, użyj następującej składni:

```
LIB library /EXTRACT:member /OUT:objectfile
```

To polecenie tworzy plik .obj, o nazwie *objectfile* zawierający kopię `member` z *biblioteki*. `member` Nazwa uwzględnia wielkość liter. Można wyodrębnić tylko jeden element członkowski w pojedynczym poleceniu. Opcja out jest wymagana; nie ma żadnych domyślna nazwa wyjściowego. Jeśli plik o nazwie *objectfile* już istnieje w określonym katalogu (lub bieżącego katalogu, jeśli nie określono katalogu przy użyciu *objectfile*), wyodrębnione *objectfile*zastępuje istniejący plik.

## <a name="see-also"></a>Zobacz też

[LIB — dokumentacja](../../build/reference/lib-reference.md)