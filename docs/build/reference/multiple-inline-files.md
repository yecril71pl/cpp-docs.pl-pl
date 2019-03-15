---
title: Pliki wbudowane
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: 71f17ff6717e717693facb21b4a4341a040b14c1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823823"
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

## <a name="see-also"></a>Zobacz także

[Pliki wbudowane w pliku reguł programu Make](inline-files-in-a-makefile.md)
