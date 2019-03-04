---
title: Zamykanie plików
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 69a0960c1edabab00cb71702acda526ee9ebd798
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267059"
---
# <a name="closing-files"></a>Zamykanie plików

Zwykły w operacjach we/wy, po zakończeniu z plikiem, należy go zamknąć.

#### <a name="to-close-a-file"></a>Aby zamknąć plik

1. Użyj **Zamknij** funkcja elementu członkowskiego. Ta funkcja zamyka plik systemu plików i opróżnia buforów, jeśli to konieczne.

Jeśli została przydzielona [CFile](../mfc/reference/cfile-class.md) obiekt w ramce (tak jak w przykładzie przedstawionym w [otwieranie plików](../mfc/opening-files.md)), obiekt zostanie automatycznie zamknięcia, a następnie niszczone, gdy jej wykracza poza zakres. Należy pamiętać, że usunięcie `CFile` obiektu nie powoduje usunięcia pliku fizycznego w systemie plików.

## <a name="see-also"></a>Zobacz także

[Pliki](../mfc/files-in-mfc.md)
