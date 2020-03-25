---
title: Ostrzeżenie LNK4075 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: e4a385b9559e2f54e81bda76e6dd13505e978a74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183491"
---
# <a name="linker-tools-warning-lnk4075"></a>Ostrzeżenie LNK4075 narzędzi konsolidatora

Ignorowanie "opcja1" ze względu na specyfikację "opcja2"

Druga opcja zastępuje pierwszy.

Są określone wzajemnie wykluczające się Opcje konsolidatora.  Sprawdź Opcje konsolidatora.  Gdzie określone Opcje konsolidatora zależą od sposobu kompilowania projektu.

- Jeśli tworzysz w środowisku programistycznym, poszukaj na stronie właściwości konsolidatora projektu i sprawdź, gdzie są określone obie opcje konsolidatora.  Aby uzyskać więcej informacji [, zobacz Ustawianie kompilatora i właściwości kompilacji](../../build/working-with-project-properties.md) .

- W przypadku kompilowania w wierszu polecenia należy zapoznać się z opcjami konsolidatora określonymi w tym miejscu.

- Jeśli kompilujesz ze skryptami kompilacji, zapoznaj się ze skryptami, aby zobaczyć, gdzie są określone te Opcje konsolidatora.

Po znalezieniu, gdzie są określone wzajemnie wykluczające się Opcje konsolidatora, Usuń jedną z opcji konsolidatora.

Przykłady określone poniżej:

- Jeśli połączysz moduł, który został skompilowany za pomocą **/Zi**, co oznacza wewnętrzną opcję konsolidatora o nazwie/EDITANDCONTINUE i moduł, który został skompilowany przy użyciu/OPT: REF,/OPT: ICF lub/Incremental: No, który nie ma/EDITANDCONTINUE, otrzymasz LNK4075 narzędzi konsolidatora.  Aby uzyskać więcej informacji [, zobacz/Z7,/Zi,/ZI (format informacji o debugowaniu)](../../build/reference/z7-zi-zi-debug-information-format.md) .
