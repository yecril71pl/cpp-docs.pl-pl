---
title: Exitinstance — funkcja członkowska | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords: []
dev_langs:
- C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da411fbecdea0a1e7b8976ca119057204693a9bd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387864"
---
# <a name="exitinstance-member-function"></a>ExitInstance — Funkcja członkowska

[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) funkcji składowej klasy typu [CWinApp](../mfc/reference/cwinapp-class.md) jest wywoływana za każdym razem kopii aplikacji, kończy działanie, zwykle po wysłaniu przez użytkownika, zamykanie aplikacji.

Zastąp `ExitInstance` Jeżeli potrzebujesz specjalnej operacji czyszczenia przetwarzania, takich jak zwalnianie zasobów interface (GDI) urządzenia grafiki lub cofnięcie przydziału pamięci używanej podczas wykonywania programu. Wyczyść elementy standardowe, takich jak dokumenty i widoki, jednak znajduje się przez platformę, z innymi funkcjami możliwym do zastąpienia do wykonywania specjalnej operacji czyszczenia specyficzne dla tych obiektów.

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
