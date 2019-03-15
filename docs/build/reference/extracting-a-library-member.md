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
ms.openlocfilehash: 6c577300f747d6f546b7caa3c66bddd6a516e16b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818066"
---
# <a name="extracting-a-library-member"></a>Wyodrębnianie członka biblioteki

LIB można użyć, aby utworzyć plik obiektowy (.obj), który zawiera kopię elementu członkowskiego istniejącej biblioteki. Aby wyodrębnić kopiowania elementu członkowskiego, użyj następującej składni:

```
LIB library /EXTRACT:member /OUT:objectfile
```

To polecenie tworzy plik .obj, o nazwie *objectfile* zawierający kopię `member` z *biblioteki*. `member` Nazwa uwzględnia wielkość liter. Można wyodrębnić tylko jeden element członkowski w pojedynczym poleceniu. Opcja out jest wymagana; nie ma żadnych domyślna nazwa wyjściowego. Jeśli plik o nazwie *objectfile* już istnieje w określonym katalogu (lub bieżącego katalogu, jeśli nie określono katalogu przy użyciu *objectfile*), wyodrębnione *objectfile*zastępuje istniejący plik.

## <a name="see-also"></a>Zobacz także

[LIB — dokumentacja](lib-reference.md)
