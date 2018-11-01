---
title: Odczytywanie zakresów
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: b5c6a6baf43b8786fbd0301e4b89ea856d839606
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604119"
---
# <a name="reading-ranges"></a>Odczytywanie zakresów

**ANSI 4.9.6.2** interpretacji znak kreski (-), który jest ani pierwszym ani ostatnim znakiem w scanlist dla źródła danych % [konwersji w `fscanf` — funkcja

Następujący wiersz

```
fscanf( fileptr, "%[A-Z]", strptr);
```

odczytuje dowolną liczbę znaków z zakresu A-Z do ciągu do której `strptr` punktów.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)