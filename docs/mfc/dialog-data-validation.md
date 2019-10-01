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
ms.openlocfilehash: c89ed82b148062ddb64fa85eaabda12f44e59895
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685766"
---
# <a name="dialog-data-validation"></a>Walidacja danych okna dialogowego

Możesz określić sprawdzanie poprawności oprócz wymiany danych przez wywołanie funkcji DDV, jak pokazano w przykładzie w [oknie dialogowym wymiany danych](../mfc/dialog-data-exchange.md). Wywołanie `DDV_MaxChars` w przykładzie sprawdza, czy ciąg wprowadzony w kontrolce pola tekstowego nie jest dłuższy niż 20 znaków. Funkcja DDV zazwyczaj ostrzega użytkownika przy użyciu okna komunikatu, jeśli sprawdzanie poprawności zakończy się niepowodzeniem i umieści fokus na kontrolowanej kontroli, aby użytkownik mógł ponownie wprowadzić dane. Funkcja DDV dla danej kontrolki musi być wywoływana natychmiast po funkcji DDX dla tej samej kontrolki.

Można także definiować własne niestandardowe procedury DDX i DDV. Aby uzyskać szczegółowe informacje na temat tego i innych aspektów DDX i DDV, zobacz sekcję dotyczącą [MFC Technical uwagi 26](../mfc/tn026-ddx-and-ddv-routines.md).

[Kreator dodawania zmiennej członkowskiej](../ide/add-member-variable-wizard.md) będzie zapisywać wszystkie wywołania DDX i DDV na mapie danych.

## <a name="see-also"></a>Zobacz także

[Wymiana i walidacja danych w oknie dialogowym](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Wymiana danych w oknie dialogowym](../mfc/dialog-data-exchange.md)
