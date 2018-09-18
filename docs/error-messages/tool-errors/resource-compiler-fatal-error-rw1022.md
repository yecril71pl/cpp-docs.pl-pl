---
title: Błąd krytyczny kompilatora zasobów RW1022 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1022
dev_langs:
- C++
helpviewer_keywords:
- RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caaefc045a31ca64aa9843927d550ef66285cb2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099853"
---
# <a name="resource-compiler-fatal-error-rw1022"></a>Błąd krytyczny kompilatora zasobów RW1022

**Operacje We/Wy wystąpił błąd podczas zapisywania pliku**

Kompilator zasobów nie można zapisać do pliku.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Brak miejsca na dysku. Ilość wolnego miejsca musi wynosić co najmniej dwa razy rozmiaru pliku wykonywalnego, który tworzysz.

1. Wolumin jest tylko do odczytu.

1. Uszkodzonych sektorów.

1. Naruszenie zasad współużytkowania.