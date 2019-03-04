---
title: ExitInstance — Funkcja członkowska
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: c76f588b22ad8ffd1d3dae954c5113feffb62a3f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279435"
---
# <a name="exitinstance-member-function"></a>ExitInstance — Funkcja członkowska

[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) funkcji składowej klasy typu [CWinApp](../mfc/reference/cwinapp-class.md) jest wywoływana za każdym razem kopii aplikacji, kończy działanie, zwykle po wysłaniu przez użytkownika, zamykanie aplikacji.

Zastąp `ExitInstance` Jeżeli potrzebujesz specjalnej operacji czyszczenia przetwarzania, takich jak zwalnianie zasobów interface (GDI) urządzenia grafiki lub cofnięcie przydziału pamięci używanej podczas wykonywania programu. Wyczyść elementy standardowe, takich jak dokumenty i widoki, jednak znajduje się przez platformę, z innymi funkcjami możliwym do zastąpienia do wykonywania specjalnej operacji czyszczenia specyficzne dla tych obiektów.

## <a name="see-also"></a>Zobacz także

[CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)
