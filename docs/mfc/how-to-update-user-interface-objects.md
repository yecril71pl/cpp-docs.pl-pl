---
title: 'Porady: aktualizowanie obiektów interfejsu użytkownika | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 422be3d80614c526c7e634d22a0930458e4b4e26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346210"
---
# <a name="how-to-update-user-interface-objects"></a>Porady: aktualizowanie obiektów interfejsu użytkownika
Zazwyczaj elementy menu i przycisków paska narzędzi mają więcej niż jednego stanu. Na przykład element menu jest niedostępne (wygaszone), jeśli jest niedostępna w kontekście obecny. Elementy menu można także zaznaczać lub usuwać zaznaczenia. Również zostaną wyłączone przycisku paska narzędzi, jeśli jest niedostępny lub może być sprawdzone.  
  
 Kto aktualizuje stan tych elementów, jak program zmiany warunków logicznie, jeśli element menu generuje polecenia, który jest obsługiwany przez, powiedz, dokument, warto dokumentu aktualizacji elementu menu. Prawdopodobnie dokument zawiera informacje, na której oparto aktualizacji.  
  
 Jeśli polecenie ma wiele obiektów interfejsu użytkownika (możliwe, że element menu i przycisku paska narzędzi), zarówno są kierowane do tej samej funkcji obsługi. To jest hermetyzowany kod aktualizacji interfejsu użytkownika dla wszystkich obiektów równoważnych interfejsu użytkownika w jednym miejscu.  
  
 Platformę udostępnia wygodny interfejs na potrzeby automatyczne aktualizowanie obiektów interfejsu użytkownika. Można wykonać aktualizacji w inny sposób, ale jest interfejs dostarczony wydajne i łatwe w użyciu.  
  
 W poniższych tematach opisano użycie programy obsługi aktualizacji:  
  
-   [Kiedy są wywoływane programy obsługi aktualizacji](../mfc/when-update-handlers-are-called.md)  
  
-   [On_update_command_ui — makro](../mfc/on-update-command-ui-macro.md)  
  
-   [Ccmdui — klasa](../mfc/the-ccmdui-class.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Menu](../mfc/menus-mfc.md)

