---
title: Ostrzeżenie LNK4075 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a021a9345975dcb197ab578901baf22f76db846
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059657"
---
# <a name="linker-tools-warning-lnk4075"></a>Ostrzeżenie LNK4075 narzędzi konsolidatora

Opcja "1" z powodu specyfikacji "opcja2" zignorowano

Druga opcja przesłania pierwszego.

Określania opcji konsolidatora wzajemnie się wykluczają.  Sprawdź opcje konsolidatora.  Gdzie są określone opcje konsolidatora, zależy od tego, jak tworzysz projekt.

- Jeśli tworzysz w środowisku programistycznym, Szukaj w strony właściwości konsolidatora projektu i zobacz, gdzie określone obie opcje konsolidatora.  Zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md) Aby uzyskać więcej informacji.

- Jeśli kompilujesz w wierszu polecenia, sprawdź opcje konsolidatora określone.

- Jeśli tworzysz ze skryptami kompilacji, przejrzyj skryptach, aby zobaczyć, gdzie określone opcje konsolidatora.

Jeśli okaże się, gdy są określone opcje konsolidatora wzajemnie się wykluczają, usuń jedną z opcji konsolidatora.

Kilka przykładów:

- Jeśli łączysz się moduł, który został skompilowany przy użyciu **/zi**, co oznacza wewnętrzne konsolidatora opcję o nazwie/editandcontinue i moduł, który został skompilowany przy użyciu/OPT: REF, / OPT: ICF lub/incremental: No, co oznacza nie/editandcontinue, będzie Uzyskaj LNK4075.  Zobacz [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md) Aby uzyskać więcej informacji.