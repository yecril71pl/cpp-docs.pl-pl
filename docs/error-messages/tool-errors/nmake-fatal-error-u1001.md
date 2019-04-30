---
title: Błąd krytyczny NMAKE U1001
ms.date: 11/04/2016
f1_keywords:
- U1001
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
ms.openlocfilehash: bfe2edf9c57eda073826a8c161ae0c358f3a6232
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378456"
---
# <a name="nmake-fatal-error-u1001"></a>Błąd krytyczny NMAKE U1001

Błąd składni: niedozwolony znak "character" w makrze

Dany znak pojawia się w makrze, ale nie jest literą, cyfrą lub znakiem podkreślenia.

Ten błąd może być spowodowany przez brak dwukropka w rozwinięciu makra:

```
syntax error : illegal character '=' in macro
```