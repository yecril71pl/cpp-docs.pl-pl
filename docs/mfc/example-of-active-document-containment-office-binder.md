---
title: 'Przykład zawierania dokumentów aktywnych: Office Binder | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7e4f82840a4c5620762ad57b5b9fa8dd7e62d0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="example-of-active-document-containment-office-binder"></a>Przykład zawierania dokumentów aktywnych: Office Binder
Microsoft Office Binder jest przykładem kontenera dokumentów aktywnych. Office Binder zawiera dwa okienka podstawowego, jak kontenery zwykle. W okienku po lewej stronie zawiera ikony, które odpowiadają dokumenty aktywne w obiekt wiążący. Każdy dokument jest nazywany *sekcji* w ramach obiektu wiążącego. Na przykład integratora może zawierać dokumentów programu Word, PowerPoint pliki, arkusze programu Excel i tak dalej.  
  
 Kliknięcie ikony w okienku po lewej stronie aktywuje odpowiedniego aktywny dokument. Prawe okienko integratora następnie wyświetla zawartość aktualnie zaznaczonego aktywny dokument.  
  
 Jeśli zostanie otwarty i aktywować dokumentu programu Word w integratora, Word paska menu i pasków zadań są wyświetlane w górnej ramce widoku i można edytować zawartość dokumentu przy użyciu dowolnego polecenia Word lub narzędzia. Jednak na pasku menu jest kombinacją paski menu zarówno dla obiekt wiążący, jak i Word. Ponieważ zarówno integratora i Word **pomocy** scalania menu, zawartość odpowiednich menu. Kontenery dokumentów aktywnych, takich jak Office Binder automatycznie udostępnić **pomocy** menu scalanie; Aby uzyskać więcej informacji, zobacz [scalanie Menu Pomoc](../mfc/help-menu-merging.md).  
  
 Po wybraniu aktywnego dokumentu innego typu aplikacji, powoduje interfejsu obiektu wiążącego dostosowanie tego typu aplikacji w aktywnym dokumencie. Na przykład jeśli obiekt wiążący zawiera arkusz kalkulacyjny programu Excel, widoczny będzie, że menu w obiekt wiążący zmienić po wybraniu sekcji arkusz kalkulacyjny programu Excel.  
  
 Istnieją oczywiście innych możliwych typów kontenery obok obiektów wiążących. Eksploratora plików korzysta z typowych interfejsu podwójnego okienko, w którym okienka po lewej stronie używa formantu drzewa do wyświetlenia hierarchiczną listę katalogów w dysku lub w sieci, gdy okienku po prawej stronie wyświetla plików znajdujących się w aktualnie wybranym katalogu. Internet — typ przeglądarki kontenera (na przykład program Microsoft Internet Explorer), a nie przy użyciu interfejsu okienku procesory, zwykle ma jedną ramkę i zapewnia nawigacji przy użyciu hiperłącza.  
  
## <a name="see-also"></a>Zobacz też  
 [Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

