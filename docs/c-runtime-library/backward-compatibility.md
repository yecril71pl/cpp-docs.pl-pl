---
title: "Zgodność z poprzednimi wersjami | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8ffcc5ab1f50c474ed0ecf4d014419111682b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="backward-compatibility"></a>Zgodność ze starszymi wersjami
Zgodność między wersjami, biblioteki OLDNAMES. LIB mapuje nazwy stare na nowe nazwy. Na przykład `open` mapuje `_open`. Należy jawnie połączyć z OLDNAMES. LIB tylko w przypadku kompilacji z następujących kombinacji opcji wiersza polecenia:  
  
-   `/Zl`(Pomiń domyślną nazwę biblioteki z pliku obiektu) i `/Ze` (wartość domyślna — za pomocą rozszerzeń firmy Microsoft)  
  
-   `/link`(konsolidator control), `/NOD` (nie wyszukiwania biblioteka domyślna), a`/Ze`  
  
 Aby uzyskać więcej informacji na temat opcji wiersza polecenia kompilatora, zobacz [kompilatora](../build/reference/compiler-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zgodność](../c-runtime-library/compatibility.md)