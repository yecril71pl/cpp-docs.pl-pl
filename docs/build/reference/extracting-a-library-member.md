---
title: Wyodrębnianie członka biblioteki
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 874866627099eb5aeb318273db26a976e99bac7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439880"
---
# <a name="extracting-a-library-member"></a>Wyodrębnianie członka biblioteki

Do utworzenia pliku obiektu (. obj), który zawiera kopię elementu członkowskiego istniejącej biblioteki, można użyć LIB. Aby wyodrębnić kopię elementu członkowskiego, należy użyć następującej składni:

```
LIB library /EXTRACT:member /OUT:objectfile
```

To polecenie tworzy plik. obj o nazwie *objectfile* , który zawiera kopię `member` *biblioteki*. W nazwie `member` rozróżniana jest wielkość liter. Można wyodrębnić tylko jeden element członkowski w pojedynczym poleceniu. Opcja/OUT jest wymagana; nie istnieje domyślna nazwa wyjściowa. Jeśli plik o nazwie *objectfile* już istnieje w określonym katalogu (lub bieżącym katalogu, jeśli nie określono katalogu z *objectfile*), wyodrębnione *objectfile* zastępuje istniejący plik.

## <a name="see-also"></a>Zobacz też

[LIB — dokumentacja](lib-reference.md)
