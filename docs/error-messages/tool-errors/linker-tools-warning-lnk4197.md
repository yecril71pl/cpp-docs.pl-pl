---
title: Ostrzeżenie LNK4197 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4197
dev_langs:
- C++
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55044ce511e2584e2859b7e8a8d723cbe0976105
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894489"
---
# <a name="linker-tools-warning-lnk4197"></a>Ostrzeżenie LNK4197 narzędzi konsolidatora

> Eksportowanie "*exportname*" określono wiele razy; zostanie użyta pierwsza Specyfikacja

Eksport jest określona w wielu i różne sposoby. Konsolidator używa pierwszej specyfikacji i pomija pozostałe.

Do odbudowywania biblioteki wykonawczej języka C, możesz zignorować ten komunikat.

Jeśli eksport został określony wiele razy ten sam sposób, konsolidator nie będzie wystawiać ostrzeżenie.

Na przykład poniższą zawartość pliku .def spowodowałoby to ostrzeżenie:

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Ten sam eksportu jest określony zarówno w wierszu polecenia (przy użyciu eksportu:) i w pliku .def.

2. Ten sam eksportu znajduje się dwa razy w pliku .def, z różnymi atrybutami.