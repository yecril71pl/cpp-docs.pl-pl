---
title: Ostrzeżenie LNK4197 narzędzi konsolidatora
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 0abad1b98ff4782f077312752603ec17fd611c12
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390363"
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