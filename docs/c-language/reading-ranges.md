---
title: Odczytywanie zakresów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76530dfdac917dfbde50bc3fb1b17a3c31178729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030247"
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