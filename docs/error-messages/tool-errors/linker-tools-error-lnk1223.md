---
title: Błąd narzędzi konsolidatora LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 9c9d4c7224a7e65775354a86bd34fa9ea1b074af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195035"
---
# <a name="linker-tools-error-lnk1223"></a>Błąd narzędzi konsolidatora LNK1223

nieprawidłowy lub uszkodzony plik: plik zawiera nieprawidłowe udziały pData

W przypadku platform RISC wykorzystujących pData ten błąd wystąpi, jeśli kompilator emituje sekcję. pdata z nieposortowanymi wpisami.

Aby rozwiązać ten problem, należy wykonać kompilację bez włączonej [/GL (Optymalizacja całego programu)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) . Puste treści funkcji mogą również spowodować wystąpienie tego błędu w niektórych przypadkach.
