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
ms.openlocfilehash: e9a04dec046435478ca621ad8f5e2e3c4323f3e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="backward-compatibility"></a>Zgodność ze starszymi wersjami
Zgodność między wersjami, biblioteki OLDNAMES. LIB mapuje nazwy stare na nowe nazwy. Na przykład `open` mapuje `_open`. Należy jawnie połączyć z OLDNAMES. LIB tylko w przypadku kompilacji z następujących kombinacji opcji wiersza polecenia:  
  
-   `/Zl` (Pomiń domyślną nazwę biblioteki z pliku obiektu) i `/Ze` (wartość domyślna — za pomocą rozszerzeń firmy Microsoft)  
  
-   `/link` (konsolidator control), `/NOD` (nie wyszukiwania biblioteka domyślna), a `/Ze`  
  
 Aby uzyskać więcej informacji na temat opcji wiersza polecenia kompilatora, zobacz [kompilatora](../build/reference/compiler-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zgodność](../c-runtime-library/compatibility.md)