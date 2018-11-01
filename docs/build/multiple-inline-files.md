---
title: Pliki wbudowane
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: ec531e5716098725782010927201ef57e2a8aa24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558161"
---
# <a name="multiple-inline-files"></a>Pliki wbudowane

Polecenia można utworzyć więcej niż jeden plik w tekście.

## <a name="syntax"></a>Składnia

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Uwagi

Dla każdego pliku należy określić jeden lub więcej wierszy tekstu wbudowany znak zawierający ogranicznik wiersza zamknięcia. Rozpocznij tekst drugiego pliku na wiersz po wierszu ograniczającego dla pierwszego pliku.

## <a name="see-also"></a>Zobacz też

[Pliki wbudowane w pliku reguł programu Make](../build/inline-files-in-a-makefile.md)