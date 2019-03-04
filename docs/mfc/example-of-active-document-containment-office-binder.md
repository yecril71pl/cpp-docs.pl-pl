---
title: 'Przykład zawierania dokumentów aktywnych: Office Binder'
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
ms.openlocfilehash: b06bc0f22ee71c8afbbc8feadca68895fc24a50b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279188"
---
# <a name="example-of-active-document-containment-office-binder"></a>Przykład zawierania dokumentów aktywnych: Office Binder

Microsoft Office Binder jest przykładem kontener aktywnego dokumentu. Office Binder zawiera dwa okienka podstawowego, jak kontenery zwykle. W okienku po lewej stronie zawiera ikony, które odpowiadają dokumenty aktywne w obiekt wiążący. Każdy dokument jest nazywany *sekcji* w ramach obiektu wiążącego. Na przykład obiekt wiążący może zawierać dokumentów programu Word, pliki programu PowerPoint, arkusze kalkulacyjne programu Excel i tak dalej.

Klikając ikonę w okienku po lewej stronie aktywuje odpowiedniego aktywnego dokumentu. Prawe okienko integratora następnie wyświetla zawartość aktualnie zaznaczonego aktywnego dokumentu.

Jeśli otworzysz i Aktywuj dokument programu Word w integratora Word pasek menu i paski narzędzi są wyświetlane w górnej ramce widoku, a następnie edytować zawartość dokumentu przy użyciu dowolnego polecenia programu Word lub narzędzia. Jednak na pasku menu jest kombinacją paski menu zarówno obiekt wiążący firmy, jak i programu Word. Ponieważ integratorów modeli i program Word ma **pomocy** scalania menu i zawartość odpowiednich menu. Kontenery dokumentów aktywnych, takich jak Office Binder automatycznie udostępniają **pomocy** menu scalanie; Aby uzyskać więcej informacji, zobacz [scalanie Menu Pomoc](../mfc/help-menu-merging.md).

Po wybraniu aktywnego dokumentu innego typu aplikacji, zmiany w interfejsie integratorów modeli do obsługi z typem aplikacji aktywnego dokumentu. Na przykład jeśli obiekt wiążący zawiera arkusz kalkulacyjny programu Excel, można zauważyć że menu w obiekt wiążący zmienić po wybraniu sekcji arkusz kalkulacyjny programu Excel.

Istnieją oczywiście innych możliwych typów kontenery obok wiążących. Eksplorator plików używa typowej interfejsu podwójne okienka, w którym okienka po lewej stronie używa formantu drzewa do wyświetlania hierarchiczną listę katalogów w dysku lub w sieci, a w okienku po prawej stronie wyświetla pliki znajdujące się w aktualnie wybranego katalogu. Internet — typ przeglądarki kontenera (na przykład program Microsoft Internet Explorer), a nie przy użyciu interfejsu podwójne okienka zwykle ma jedną klatkę i zapewnia nawigacji za pomocą hiperlinków.

## <a name="see-also"></a>Zobacz także

[Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)
