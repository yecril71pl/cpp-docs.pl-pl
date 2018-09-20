---
title: Walidacja danych okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83c1208d3001739ca78186972c629ea8a094c8d8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430894"
---
# <a name="dialog-data-validation"></a>Walidacja danych okna dialogowego

Możesz określić sprawdzania poprawności, oprócz wymiany danych przez wywołanie funkcji DDV, jak pokazano w przykładzie w [wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md). `DDV_MaxChars` Wywołania w przykładzie weryfikuje, że wprowadzony w formancie pola tekstowego ciąg nie jest dłuższa niż 20 znaków. Funkcja DDV zazwyczaj alertów użytkownikowi okno komunikatu, gdy sprawdzanie poprawności nie powiedzie się i umieszcza fokus sterowanie powodujący problemy, dzięki czemu użytkownik może ponownie dane. Funkcja DDV określonej kontrolki należy wywołać natychmiast po funkcji DDX dla tej samej kontrolki.

Można również definiować własne niestandardowe procedury DDX i DDV. Aby uzyskać więcej informacji na ten temat i inne aspekty DDX i DDV, zobacz [MFC techniczne Uwaga 26](../mfc/tn026-ddx-and-ddv-routines.md).

[Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) będzie zapisywać wszystkie DDX i DDV wywołań na mapie danych dla Ciebie.

## <a name="see-also"></a>Zobacz też

[Wymiana i walidacja danych w oknie dialogowym](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Wymiana danych w oknie dialogowym](../mfc/dialog-data-exchange.md)

