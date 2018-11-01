---
title: Ostrzeżenie LNK4075 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: bba0fa85a3f2590c84cbb6f78fac7e49386d35a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548255"
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