---
title: Błąd narzędzi konsolidatora LNK1223 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8639919c74559829367108b36d62594e2a83a91a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067995"
---
# <a name="linker-tools-error-lnk1223"></a>Błąd narzędzi konsolidatora LNK1223

nieprawidłowy lub uszkodzony plik: plik zawiera nieprawidłowy .pdata wkładów

W przypadku platform RISC, które używają pdata ten błąd wystąpi, jeśli kompilator emitowane sekcji .pdata z wpisy nieposortowana.

Aby rozwiązać ten problem, spróbuj użyć skompilowanie bez [/GL (Optymalizacja Całoprogramowa)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) włączone. Ciało funkcji jest puste może również spowodować, że ten błąd w niektórych przypadkach.