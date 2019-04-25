---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: 751c212398f3d309b1d31d204291fe3a0503cf06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317266"
---
# <a name="tls"></a>/TLS

Wyświetla strukturę IMAGE_TLS_DIRECTORY z pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

/ TLS wyświetla pola struktury TLS, a także adresy protokołu TLS funkcji wywołania zwrotnego.

Jeśli program nie używa lokalnego magazynu wątków, obraz nie będzie zawierać struktura TLS.  Zobacz [wątku](../../cpp/thread.md) Aby uzyskać więcej informacji.

IMAGE_TLS_DIRECTORY jest zdefiniowana w pliku winnt.h.

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)
