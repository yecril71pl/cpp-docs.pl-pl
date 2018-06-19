---
title: -TLS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5e510f406ceae7508f9b84f99e7ab397d22f114
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373527"
---
# <a name="tls"></a>/TLS
Wyświetla strukturę IMAGE_TLS_DIRECTORY z pliku wykonywalnego.  
  
## <a name="remarks"></a>Uwagi  
 / TLS wyświetla pola struktury TLS, a także adresy TLS funkcje wywołania zwrotnego.  
  
 Jeśli program nie korzysta z magazynu lokalnego wątku, obraz nie będzie zawierać struktury TLS.  Zobacz [wątku](../../cpp/thread.md) Aby uzyskać więcej informacji.  
  
 IMAGE_TLS_DIRECTORY jest zdefiniowany w pliku winnt.h.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)