---
title: Ostrzeżenie wiersza polecenia D9026 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07be633e56dad6c8f0b304a3c88c1b9919221d4a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079157"
---
# <a name="command-line-warning-d9026"></a>Ostrzeżenie D9026 dla wiersza polecenia

opcje są stosowane do całego wiersza polecenia

Określono opcję dotyczącą polecenia po określono nazwę pliku. Opcja została zastosowana do pliku, który go poprzedzał.

Na przykład w poleceniu

```
CL verdi.c /G5 puccini.c
```

Plik VERDI.c zostanie skompilowany przy użyciu opcji /G5, a nie domyślnym /G4.

To zachowanie różni się od niektórych poprzednich wersji, które były stosowane tylko opcje określone przed nazwy pliku, co spowoduje VERDI.c kompilowany przy użyciu/4. generacji i PUCCINI.c kompilowany przy użyciu /G5.