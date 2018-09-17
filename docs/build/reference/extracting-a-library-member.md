---
title: Wyodrębnianie członka biblioteki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9207a77868b3257d09f0d9efe38e4765cb8f4906
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726521"
---
# <a name="extracting-a-library-member"></a>Wyodrębnianie członka biblioteki

LIB można użyć, aby utworzyć plik obiektowy (.obj), który zawiera kopię elementu członkowskiego istniejącej biblioteki. Aby wyodrębnić kopiowania elementu członkowskiego, użyj następującej składni:

```
LIB library /EXTRACT:member /OUT:objectfile
```

To polecenie tworzy plik .obj, o nazwie *objectfile* zawierający kopię `member` z *biblioteki*. `member` Nazwa uwzględnia wielkość liter. Można wyodrębnić tylko jeden element członkowski w pojedynczym poleceniu. Opcja out jest wymagana; nie ma żadnych domyślna nazwa wyjściowego. Jeśli plik o nazwie *objectfile* już istnieje w określonym katalogu (lub bieżącego katalogu, jeśli nie określono katalogu przy użyciu *objectfile*), wyodrębnione *objectfile*zastępuje istniejący plik.

## <a name="see-also"></a>Zobacz też

[LIB — dokumentacja](../../build/reference/lib-reference.md)