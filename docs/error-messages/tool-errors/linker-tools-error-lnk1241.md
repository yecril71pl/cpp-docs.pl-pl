---
title: Błąd narzędzi konsolidatora LNK1241 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1241
dev_langs:
- C++
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4c11a97dd99515ff7623b77ff31de5fb8577b5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040625"
---
# <a name="linker-tools-error-lnk1241"></a>Błąd narzędzi konsolidatora LNK1241

Plik zasobów 'plik zasobu' już określony

Ten błąd jest generowany, gdy uruchamiasz **cvtres** ręcznie z poziomu wiersza polecenia i jeśli następnie przekazać .obj wynikowy plik konsolidatora dodatkowo do innych plików .res.

Do określenia wielu plików .res, przekazać je wszystkie do konsolidatora jako pliki .res, nie z poziomu plików .obj utworzony przez **cvtres**.