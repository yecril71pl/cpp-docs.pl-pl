---
title: Zgodność ze starszymi wersjami
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: d418a3450f22e53c8cb320f0a1a27c9f2e434c54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460557"
---
# <a name="backward-compatibility"></a>Zgodność ze starszymi wersjami

Zgodność między wersjami produktów, biblioteka OLDNAMES. LIB mapuje starych nazw na nowe nazwy. Na przykład `open` mapuje `_open`. Musisz jawnie połączyć za pomocą OLDNAMES. Lib — tylko wtedy, gdy kompilujesz przy użyciu następujących kombinacji opcji wiersza polecenia:

- `/Zl` (Pomiń domyślną nazwę biblioteki z pliku obiektu) i `/Ze` (wartość domyślna — korzystanie z rozszerzeń firmy Microsoft)

- `/link` (formant konsolidatora), `/NOD` (bez wyszukiwania bibliotekę domyślną), i `/Ze`

Aby uzyskać więcej informacji na temat opcji wiersza polecenia kompilatora, zobacz [odwołanie do kompilatora](../build/reference/compiler-options.md).

## <a name="see-also"></a>Zobacz też

[Zgodność](../c-runtime-library/compatibility.md)