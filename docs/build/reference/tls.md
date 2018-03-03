---
title: -TLS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5adf246e343a16abebdc584589e9633b195444ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tls"></a>/TLS
Wyświetla strukturę IMAGE_TLS_DIRECTORY z pliku wykonywalnego.  
  
## <a name="remarks"></a>Uwagi  
 / TLS wyświetla pola struktury TLS, a także adresy TLS funkcje wywołania zwrotnego.  
  
 Jeśli program nie korzysta z magazynu lokalnego wątku, obraz nie będzie zawierać struktury TLS.  Zobacz [wątku](../../cpp/thread.md) Aby uzyskać więcej informacji.  
  
 IMAGE_TLS_DIRECTORY jest zdefiniowany w pliku winnt.h.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)