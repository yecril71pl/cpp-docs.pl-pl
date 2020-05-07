---
title: Odczytywanie zakresów
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: 86bb24647084d8bdc452960bab631587c2413276
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343146"
---
# <a name="reading-ranges"></a>Odczytywanie zakresów

**4.9.6.2 ANSI** Interpretacja znaku kreski (-), który nie jest pierwszym ani ostatnim znakiem w scanlist dla% [konwersja w `fscanf` funkcji

Poniższy wiersz

```
fscanf( fileptr, "%[A-Z]", strptr);
```

odczytuje dowolną liczbę znaków z zakresu od A do Z do ciągu, do którego `strptr` punkty.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)
