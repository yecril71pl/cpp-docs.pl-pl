---
title: Ostrzeżenie D9026 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 59dfcdc97fb9caf60a018cb20583ee6fca3dcb27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196706"
---
# <a name="command-line-warning-d9026"></a>Ostrzeżenie D9026 dla wiersza polecenia

Opcje stosują się do całego wiersza polecenia

Opcja została określona w poleceniu po określeniu nazwy pliku. Opcja została zastosowana do pliku, który poprzedzał go.

Na przykład w poleceniu

```
CL verdi.c /G5 puccini.c
```

plik VERDI. c zostanie skompilowany przy użyciu opcji/G5, a nie domyślnego/G4.

To zachowanie jest inne niż w przypadku niektórych poprzednich wersji, które dotyczyły tylko opcji określonych przed nazwą pliku, co spowodowało VERDI. c jest kompilowane przy użyciu/G4 i PUCCINI. c, które są kompilowane przy użyciu/G5.
