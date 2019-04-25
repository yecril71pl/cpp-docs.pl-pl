---
title: Ostrzeżenie D9026 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 3fd8d442dfabaf2f03d8b564c9fdfb1537f6ff28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214210"
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