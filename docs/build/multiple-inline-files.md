---
title: Wiele plików wbudowanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87d68034c4f0018d65020915d24d0b5c2ec5d61a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725598"
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