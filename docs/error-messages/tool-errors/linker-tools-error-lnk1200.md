---
title: Błąd narzędzi konsolidatora LNK1200 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03ecd51142bf30230b6b177a36e007345e93bf2c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059319"
---
# <a name="linker-tools-error-lnk1200"></a>Błąd narzędzi konsolidatora LNK1200

Błąd odczytu bazy danych programu "filename"

Nie można odczytać bazy danych programu (PDB).

Ten błąd może być spowodowany przez uszkodzenie pliku.

Jeśli `filename` jest pliku PDB dla pliku obiektu, należy ponownie skompilować przy użyciu pliku obiektu [/zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Jeśli `filename` jest plik PDB dla pliku wyjściowego głównym, a ten błąd wystąpił podczas konsolidowania przyrostowego, usuń plik PDB i połącz ponownie.