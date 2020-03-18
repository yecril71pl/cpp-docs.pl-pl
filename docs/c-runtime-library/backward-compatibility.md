---
title: Zgodność ze starszymi wersjami
ms.date: 11/04/2016
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: 2c2b4570e5e3131911e7f424280f16e9977f047e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438562"
---
# <a name="backward-compatibility"></a>Zgodność ze starszymi wersjami

W celu zapewnienia zgodności między wersjami produktów Biblioteka OLDNAMES. LIB mapuje stare nazwy na nowe nazwy. Na przykład `open` Maps `_open`. Musisz jawnie powiązać z OLDNAMES. LIB tylko w przypadku kompilowania z następującymi kombinacjami opcji wiersza polecenia:

- `/Zl` (Pomiń domyślną nazwę biblioteki z pliku obiektu) i `/Ze` (domyślnie — Użyj rozszerzeń Microsoft)

- `/link` (formant konsolidatora), `/NOD` (brak wyszukiwania biblioteki domyślnej) i `/Ze`

Aby uzyskać więcej informacji na temat opcji wiersza polecenia kompilatora, zobacz [Dokumentacja kompilatora](../build/reference/compiler-options.md).

## <a name="see-also"></a>Zobacz też

[Zgodność](../c-runtime-library/compatibility.md)
