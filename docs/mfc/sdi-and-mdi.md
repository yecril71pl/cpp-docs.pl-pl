---
title: SDI i MDI
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
ms.openlocfilehash: 9730e7baf9589c4b05a60703c619aae2e941bdec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372757"
---
# <a name="sdi-and-mdi"></a>SDI i MDI

MFC ułatwia pracę z aplikacjami interfejsu pojedynczego dokumentu (SDI), jak i z interfejsem wielu dokumentów (MDI).

Aplikacje SDI zezwalają tylko na jedno otwarte okno ramki dokumentu naraz. Aplikacje MDI umożliwiają otwieranie wielu okien ramek dokumentu w tym samym wystąpieniu aplikacji. Aplikacja MDI ma okno, w którym można otworzyć wiele okien podrzędnych MDI, które są oknami ramki, z których każdy zawiera oddzielny dokument. W niektórych aplikacjach okna podrzędne mogą być różnych typów, takich jak okna wykresu i arkusza kalkulacyjnego. W takim przypadku pasek menu może ulec zmianie, ponieważ aktywowane są okna podrzędne MDI różnych typów.

> [!NOTE]
> W systemie Windows 95 lub nowszych aplikacje są powszechnie SDI, ponieważ system operacyjny przyjął widok "wyśrodkowany do dokumentu".

Aby uzyskać więcej informacji, zobacz [Dokumenty, Widoki i Ramy](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Zobacz też

[Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
