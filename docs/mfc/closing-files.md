---
title: Zamykanie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c392ef728e1d796a02cfa32edc2c3e8c74d083b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426240"
---
# <a name="closing-files"></a>Zamykanie plików

Zwykły w operacjach we/wy, po zakończeniu z plikiem, należy go zamknąć.

#### <a name="to-close-a-file"></a>Aby zamknąć plik

1. Użyj **Zamknij** funkcja elementu członkowskiego. Ta funkcja zamyka plik systemu plików i opróżnia buforów, jeśli to konieczne.

Jeśli została przydzielona [CFile](../mfc/reference/cfile-class.md) obiekt w ramce (tak jak w przykładzie przedstawionym w [otwieranie plików](../mfc/opening-files.md)), obiekt zostanie automatycznie zamknięcia, a następnie niszczone, gdy jej wykracza poza zakres. Należy pamiętać, że usunięcie `CFile` obiektu nie powoduje usunięcia pliku fizycznego w systemie plików.

## <a name="see-also"></a>Zobacz też

[Pliki](../mfc/files-in-mfc.md)

