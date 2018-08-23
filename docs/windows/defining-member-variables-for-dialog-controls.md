---
title: Definiowanie zmiennych Członkowskich dla formantów okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog editor, defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dccf80feb4582610a4cfcc22ef0d658c2ce63fb2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599743"
---
# <a name="defining-member-variables-for-dialog-controls"></a>Definiowanie zmiennych członkowskich dla formantów okna dialogowego

Aby zdefiniować zmienną składową dla dowolnego formantu pola okna dialogowego z wyjątkiem przyciski, można użyć następującej metody.

> [!NOTE]
> Ten artykuł ma zastosowanie wyłącznie do formantów okna dialogowego, w ramach projektu MFC. Należy używać w projektach ATL **nowych komunikatów Windows do programów obsługi zdarzeń** okno dialogowe.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Aby zdefiniować zmienną składową formantu pola okna dialogowego (inne niż przycisk)

1. W [Edytor okien dialogowych](../windows/dialog-editor.md), wybierz formant.

2. Podczas naciśnięcie **Ctrl** klucza, kliknij dwukrotnie kontrolka okna dialogowego.

   [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md) pojawia się.

3. Wpisz odpowiednie informacje w **Dodaj zmienną elementu członkowskiego** kreatora. Aby uzyskać więcej informacji, zobacz [wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md).

4. Kliknij przycisk **OK** aby powrócić do **okna dialogowego** edytora.

   > [!TIP]
   > Aby przejść z dowolnego formantu pola okna dialogowego do jego istniejącej procedury obsługi, kliknij dwukrotnie formant.

Można również użyć **zmienne Członkowskie** karcie **Kreator klas MFC** Aby dodać nowe zmienne elementu członkowskiego dla określonej klasy i wyświetlić te, które zostały już zdefiniowane.

## <a name="requirements"></a>Wymagania

MFC

## <a name="see-also"></a>Zobacz też

[Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)  
[Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)  
[Kreator klas MFC](../mfc/reference/mfc-class-wizard.md)  
[Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)  
[Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)  
[Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)  
[Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)  
[Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)