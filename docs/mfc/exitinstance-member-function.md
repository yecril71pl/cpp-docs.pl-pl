---
title: ExitInstance — Funkcja członkowska
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: b1c5b3a20f25f909188023ab1650bc41316d7a9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637739"
---
# <a name="exitinstance-member-function"></a>ExitInstance — Funkcja członkowska

[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) funkcji składowej klasy typu [CWinApp](../mfc/reference/cwinapp-class.md) jest wywoływana za każdym razem kopii aplikacji, kończy działanie, zwykle po wysłaniu przez użytkownika, zamykanie aplikacji.

Zastąp `ExitInstance` Jeżeli potrzebujesz specjalnej operacji czyszczenia przetwarzania, takich jak zwalnianie zasobów interface (GDI) urządzenia grafiki lub cofnięcie przydziału pamięci używanej podczas wykonywania programu. Wyczyść elementy standardowe, takich jak dokumenty i widoki, jednak znajduje się przez platformę, z innymi funkcjami możliwym do zastąpienia do wykonywania specjalnej operacji czyszczenia specyficzne dla tych obiektów.

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
