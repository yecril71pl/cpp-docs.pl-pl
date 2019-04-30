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

**ANSI 4.9.6.2** interpretacji znak kreski (-), który jest ani pierwszym ani ostatnim znakiem w scanlist dla źródła danych % [konwersji w `fscanf` — funkcja

Następujący wiersz

```
fscanf( fileptr, "%[A-Z]", strptr);
```

odczytuje dowolną liczbę znaków z zakresu A-Z do ciągu do której `strptr` punktów.

## <a name="see-also"></a>Zobacz także

[Funkcje bibliotek](../c-language/library-functions.md)
