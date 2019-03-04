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
ms.openlocfilehash: 0129b939e0fe2afd5dd29623bb44418bfd16c20d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260417"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Przeciąganie i upuszczanie plików w oknie ramowym

Okno ramowe zarządza ustanowioną relację z Eksploratora plików lub Menedżer plików.

Przez dodanie kilku inicjowanie wywołań w zastąpienie metody `CWinApp` funkcja elementu członkowskiego `InitInstance`, zgodnie z opisem w [CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md), może mieć pośrednio otwieranie plików przeciągnięty z Eksploratora plików lub Menedżer plików i porzucić w oknie ramki okna ramki. Zobacz [Menedżer plików — przeciąganie i upuszczanie](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Zobacz także

[Używanie okien ramowych](../mfc/using-frame-windows.md)
