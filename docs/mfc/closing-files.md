---
title: Zamykanie plików
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 51e51c88260a51ec44f11ecb5c2a88e645194f4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617234"
---
# <a name="closing-files"></a>Zamykanie plików

Jak zwykle w operacjach we/wy, po zakończeniu pracy z plikiem należy go zamknąć.

#### <a name="to-close-a-file"></a>Aby zamknąć plik

1. Użyj **zamykającej** funkcji członkowskiej. Ta funkcja zamyka plik systemu plików i opróżnia bufory w razie potrzeby.

Jeśli przydzielono obiekt [CFile](reference/cfile-class.md) w ramce (jak w przykładzie pokazanym w [otwieraniu plików](opening-files.md)), obiekt zostanie automatycznie zamknięty, a następnie zniszczony, gdy wykracza poza zakres. Należy pamiętać, że usunięcie `CFile` obiektu nie powoduje usunięcia pliku fizycznego w systemie plików.

## <a name="see-also"></a>Zobacz też

[Files](files-in-mfc.md)
