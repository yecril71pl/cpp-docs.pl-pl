---
title: Zgodność z poprzednimi wersjami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3056b90f3c6f0f62158a9b6dcfe145cda9740c6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092196"
---
# <a name="backward-compatibility"></a>Zgodność ze starszymi wersjami

Zgodność między wersjami produktów, biblioteka OLDNAMES. LIB mapuje starych nazw na nowe nazwy. Na przykład `open` mapuje `_open`. Musisz jawnie połączyć za pomocą OLDNAMES. Lib — tylko wtedy, gdy kompilujesz przy użyciu następujących kombinacji opcji wiersza polecenia:

- `/Zl` (Pomiń domyślną nazwę biblioteki z pliku obiektu) i `/Ze` (wartość domyślna — korzystanie z rozszerzeń firmy Microsoft)

- `/link` (formant konsolidatora), `/NOD` (bez wyszukiwania bibliotekę domyślną), i `/Ze`

Aby uzyskać więcej informacji na temat opcji wiersza polecenia kompilatora, zobacz [odwołanie do kompilatora](../build/reference/compiler-options.md).

## <a name="see-also"></a>Zobacz też

[Zgodność](../c-runtime-library/compatibility.md)