---
title: Błąd narzędzi konsolidatora LNK1158 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1158
dev_langs:
- C++
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ce319aa4529c74cad00342b09aa0ed98bb49ce7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094172"
---
# <a name="linker-tools-error-lnk1158"></a>Błąd narzędzi konsolidatora LNK1158

Nie można uruchomić "filename"

Podanego pliku wykonywalnego o nazwie [łącze](../../build/reference/linker-command-line-syntax.md) jest nie w katalogu, który zawiera łącze, ani w katalogu określonego w zmiennej środowiskowej PATH.

Na przykład, otrzymasz ten błąd przy próbie użyć parametru PGOPTIMIZE do [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) — opcja konsolidatora na komputerze z 32-bitowym systemie operacyjnym.