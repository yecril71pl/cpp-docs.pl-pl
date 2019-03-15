---
title: Długie nazwy plików w pliku reguł programu Make
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, long filenames
- long filenames
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
ms.openlocfilehash: 758f81e2e1b822c00b54cdaedfe996c9c7db2ef2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823933"
---
# <a name="long-filenames-in-a-makefile"></a>Długie nazwy plików w pliku reguł programu Make

Należy ująć długie nazwy plików w znaki cudzysłowu, w następujący sposób:

```
all : "VeryLongFileName.exe"
```

## <a name="see-also"></a>Zobacz także

[Zawartość pliku reguł programu Make](contents-of-a-makefile.md)
