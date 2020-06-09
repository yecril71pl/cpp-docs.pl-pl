---
title: ExitInstance — Funkcja członkowska
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: 58546d26293ad48a39a36b98ba4bfdabb68385ee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622695"
---
# <a name="exitinstance-member-function"></a>ExitInstance — Funkcja członkowska

Funkcja członkowska [ExitInstance](reference/cwinapp-class.md#exitinstance) klasy [CWinApp](reference/cwinapp-class.md) jest wywoływana za każdym razem, gdy kopia aplikacji zostanie zakończona, zazwyczaj w wyniku zamknięcia aplikacji.

Zastąp `ExitInstance` , jeśli wymagane jest specjalne oczyszczanie, np. zwalnianie zasobów interfejsu urządzenia graficznego (GDI) lub cofanie alokacji pamięci używanej podczas wykonywania programu. Oczyszczanie elementów standardowych, takich jak dokumenty i widoki, jest jednak dostarczane przez platformę z innymi funkcjami zaszeregowania służącymi do wykonywania specjalnych czynności czyszczących specyficznych dla tych obiektów.

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](cwinapp-the-application-class.md)
