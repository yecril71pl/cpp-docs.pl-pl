---
title: Ostrzeżenie LNK4075 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: bf22e7c78dce6949c357d7ad4a0c76209c88eef3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186908"
---
# <a name="linker-tools-warning-lnk4075"></a>Ostrzeżenie LNK4075 narzędzi konsolidatora

Opcja "1" z powodu specyfikacji "opcja2" zignorowano

Druga opcja przesłania pierwszego.

Określania opcji konsolidatora wzajemnie się wykluczają.  Sprawdź opcje konsolidatora.  Gdzie są określone opcje konsolidatora, zależy od tego, jak tworzysz projekt.

- Jeśli tworzysz w środowisku programistycznym, Szukaj w strony właściwości konsolidatora projektu i zobacz, gdzie określone obie opcje konsolidatora.  Zobacz [Ustaw kompilatora i właściwości kompilacji](../../build/working-with-project-properties.md) Aby uzyskać więcej informacji.

- Jeśli kompilujesz w wierszu polecenia, sprawdź opcje konsolidatora określone.

- Jeśli tworzysz ze skryptami kompilacji, przejrzyj skryptach, aby zobaczyć, gdzie określone opcje konsolidatora.

Jeśli okaże się, gdy są określone opcje konsolidatora wzajemnie się wykluczają, usuń jedną z opcji konsolidatora.

Kilka przykładów:

- Jeśli łączysz się moduł, który został skompilowany przy użyciu **/zi**, co oznacza wewnętrzne konsolidatora opcję o nazwie/editandcontinue i moduł, który został skompilowany przy użyciu/OPT: REF, / OPT: ICF lub/incremental: No, co oznacza nie/editandcontinue, będzie Uzyskaj LNK4075.  Zobacz [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md) Aby uzyskać więcej informacji.