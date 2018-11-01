---
title: Walidacja danych okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
ms.openlocfilehash: 2283806d3fe7c4ff6bd3abc2ae6a86f5dd176d10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483358"
---
# <a name="dialog-data-validation"></a>Walidacja danych okna dialogowego

Możesz określić sprawdzania poprawności, oprócz wymiany danych przez wywołanie funkcji DDV, jak pokazano w przykładzie w [wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md). `DDV_MaxChars` Wywołania w przykładzie weryfikuje, że wprowadzony w formancie pola tekstowego ciąg nie jest dłuższa niż 20 znaków. Funkcja DDV zazwyczaj alertów użytkownikowi okno komunikatu, gdy sprawdzanie poprawności nie powiedzie się i umieszcza fokus sterowanie powodujący problemy, dzięki czemu użytkownik może ponownie dane. Funkcja DDV określonej kontrolki należy wywołać natychmiast po funkcji DDX dla tej samej kontrolki.

Można również definiować własne niestandardowe procedury DDX i DDV. Aby uzyskać więcej informacji na ten temat i inne aspekty DDX i DDV, zobacz [MFC techniczne Uwaga 26](../mfc/tn026-ddx-and-ddv-routines.md).

[Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) będzie zapisywać wszystkie DDX i DDV wywołań na mapie danych dla Ciebie.

## <a name="see-also"></a>Zobacz też

[Wymiana i walidacja danych w oknie dialogowym](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Wymiana danych w oknie dialogowym](../mfc/dialog-data-exchange.md)

