---
title: Przeciąganie i upuszczanie plików w oknie ramowym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fc68923de531240a2d59336c79e54f6562b369c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380532"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Przeciąganie i upuszczanie plików w oknie ramowym

Okno ramowe zarządza ustanowioną relację z Eksploratora plików lub Menedżer plików.

Przez dodanie kilku inicjowanie wywołań w zastąpienie metody `CWinApp` funkcja elementu członkowskiego `InitInstance`, zgodnie z opisem w [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md), może mieć okna ramki pośrednio Otwórz pliki przeciągnięte z pliku Eksplorator lub Menedżer plików i porzucić w oknie ramki. Zobacz [Menedżer plików — przeciąganie i upuszczanie](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](../mfc/using-frame-windows.md)

