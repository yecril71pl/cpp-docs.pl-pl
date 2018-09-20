---
title: 'Schowek: Kiedy korzystać z mechanizmu Schowka | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard, guidelines
- Clipboard [MFC], mechanisms
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
- Clipboard [MFC], formats
ms.assetid: fd071996-ef8c-488b-81bd-89057095a201
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18b8a772dd58cf9623d4076665e7859d191bb27e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379817"
---
# <a name="clipboard-when-to-use-each-clipboard-mechanism"></a>Schowek: kiedy korzystać z mechanizmu schowka

Przestrzegać następujących wytycznych w korzystanie ze Schowka:

- Użyj z mechanizmu Schowka OLE, aby włączyć nowe możliwości w przyszłości. Podczas standardowych interfejsów API schowka zostaną zachowane, mechanizmu OLE przyszłościowe transferu danych.

- Jeśli piszesz aplikację OLE lub ma żadnych funkcji OLE, takich jak przeciągnij i upuść, należy użyć z mechanizmu Schowka OLE.

- Jeśli udostępniasz formaty OLE, należy korzystać z mechanizmu Schowka OLE.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Korzystanie z mechanizmu Schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [Korzystać z mechanizmu Schowka Windows](../mfc/clipboard-using-the-windows-clipboard.md)

## <a name="see-also"></a>Zobacz też

[Schowek](../mfc/clipboard.md)

