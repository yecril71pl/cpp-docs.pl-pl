---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: c125a6439e6cda2159a8bde2317528e667eaf310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532642"
---
# <a name="tls"></a>/TLS

Wyświetla strukturę IMAGE_TLS_DIRECTORY z pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

/ TLS wyświetla pola struktury TLS, a także adresy protokołu TLS funkcji wywołania zwrotnego.

Jeśli program nie używa lokalnego magazynu wątków, obraz nie będzie zawierać struktura TLS.  Zobacz [wątku](../../cpp/thread.md) Aby uzyskać więcej informacji.

IMAGE_TLS_DIRECTORY jest zdefiniowana w pliku winnt.h.

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)