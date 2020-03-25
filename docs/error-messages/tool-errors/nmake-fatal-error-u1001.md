---
title: Błąd krytyczny NMAKE U1001
ms.date: 11/04/2016
f1_keywords:
- U1001
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
ms.openlocfilehash: bb39d9080fdceb1ab26c32e9aedc654323581eb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173455"
---
# <a name="nmake-fatal-error-u1001"></a>Błąd krytyczny NMAKE U1001

Błąd składniowy: niedozwolony znak "Character" w makrze

Dany znak pojawia się w makrze, ale nie jest literą, cyfrą lub podkreśleniem.

Ten błąd może być spowodowany brakiem dwukropka w rozwinięciu makra:

```
syntax error : illegal character '=' in macro
```
