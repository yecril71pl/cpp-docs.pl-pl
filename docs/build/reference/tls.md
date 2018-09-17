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
ms.openlocfilehash: 78f485a783dbe8b5fe9a49ed3100754115bf50b8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714678"
---
# <a name="tls"></a>/TLS

Wyświetla strukturę IMAGE_TLS_DIRECTORY z pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

/ TLS wyświetla pola struktury TLS, a także adresy protokołu TLS funkcji wywołania zwrotnego.

Jeśli program nie używa lokalnego magazynu wątków, obraz nie będzie zawierać struktura TLS.  Zobacz [wątku](../../cpp/thread.md) Aby uzyskać więcej informacji.

IMAGE_TLS_DIRECTORY jest zdefiniowana w pliku winnt.h.

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)