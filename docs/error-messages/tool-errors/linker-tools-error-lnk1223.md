---
title: Błąd narzędzi konsolidatora LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 331521c357389c2f7c1aa786969154a2b747ffe5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537972"
---
# <a name="linker-tools-error-lnk1223"></a>Błąd narzędzi konsolidatora LNK1223

nieprawidłowy lub uszkodzony plik: plik zawiera nieprawidłowy .pdata wkładów

W przypadku platform RISC, które używają pdata ten błąd wystąpi, jeśli kompilator emitowane sekcji .pdata z wpisy nieposortowana.

Aby rozwiązać ten problem, spróbuj użyć skompilowanie bez [/GL (Optymalizacja Całoprogramowa)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) włączone. Ciało funkcji jest puste może również spowodować, że ten błąd w niektórych przypadkach.