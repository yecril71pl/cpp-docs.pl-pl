---
title: Przeciąganie i upuszczanie plików w oknie ramowym
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 34fb6ec6d57bcf8bc1cf51a3ac0c0db5203b3ffa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498861"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Przeciąganie i upuszczanie plików w oknie ramowym

Okno ramowe zarządza ustanowioną relację z Eksploratora plików lub Menedżer plików.

Przez dodanie kilku inicjowanie wywołań w zastąpienie metody `CWinApp` funkcja elementu członkowskiego `InitInstance`, zgodnie z opisem w [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md), może mieć okna ramki pośrednio Otwórz pliki przeciągnięte z pliku Eksplorator lub Menedżer plików i porzucić w oknie ramki. Zobacz [Menedżer plików — przeciąganie i upuszczanie](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](../mfc/using-frame-windows.md)

