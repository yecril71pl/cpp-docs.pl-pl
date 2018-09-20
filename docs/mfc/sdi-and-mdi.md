---
title: SDI i MDI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8189af7939bfca0fd206fa72892098e373444879
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401449"
---
# <a name="sdi-and-mdi"></a>SDI i MDI

MFC sprawia, że proste w użyciu interfejs dokumentu pojedynczego (SDI) i aplikacje interfejsu wielu dokumentów (MDI).

Aplikacje SDI umożliwiają tylko jedno okno ramki w otwartym dokumencie naraz. Aplikacje MDI umożliwiają wielu dokumentów, okien ramowych były otwarte w tym samym wystąpieniu aplikacji. Aplikacja MDI oknem w ramach której MDI wiele okien podrzędnych, które same okna ramki, można otworzyć, każdy z nich zawiera oddzielny dokument. W niektórych aplikacjach okien podrzędnych może być różnych typów, takich jak wykres systemu windows i windows arkusza kalkulacyjnego. W takim przypadku na pasku menu można zmieniać oknami podrzędnymi MDI o różnych typach zostaną aktywowane.

> [!NOTE]
>  W obszarze Windows 95 i nowszych aplikacje są często SDI ponieważ system operacyjny przyjęła widok "tematyka dokumentu".

Aby uzyskać więcej informacji, zobacz [dokumenty, widoki i struktura](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Zobacz też

[Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
