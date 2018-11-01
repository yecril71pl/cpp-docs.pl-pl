---
title: Zamykanie plików
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 04e5084615b1f1cf85d9f41e2c4dcc84910b9d05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636270"
---
# <a name="closing-files"></a>Zamykanie plików

Zwykły w operacjach we/wy, po zakończeniu z plikiem, należy go zamknąć.

#### <a name="to-close-a-file"></a>Aby zamknąć plik

1. Użyj **Zamknij** funkcja elementu członkowskiego. Ta funkcja zamyka plik systemu plików i opróżnia buforów, jeśli to konieczne.

Jeśli została przydzielona [CFile](../mfc/reference/cfile-class.md) obiekt w ramce (tak jak w przykładzie przedstawionym w [otwieranie plików](../mfc/opening-files.md)), obiekt zostanie automatycznie zamknięcia, a następnie niszczone, gdy jej wykracza poza zakres. Należy pamiętać, że usunięcie `CFile` obiektu nie powoduje usunięcia pliku fizycznego w systemie plików.

## <a name="see-also"></a>Zobacz też

[Pliki](../mfc/files-in-mfc.md)

