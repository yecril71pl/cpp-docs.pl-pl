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
ms.openlocfilehash: 8afe8f6f7594c2dff75125aa56a210505bf5301d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410590"
---
# <a name="how-to-update-user-interface-objects"></a>Porady: aktualizowanie obiektów interfejsu użytkownika

Zazwyczaj elementy menu i przycisków paska narzędzi mają więcej niż jednego stanu. Na przykład element menu jest niedostępna (wygaszone), jeśli jest niedostępna w kontekście obecne. Elementy menu mogą być także zaznaczony lub niezaznaczony. Przycisk paska narzędzi można również zostaną wyłączone, jeśli jest niedostępny lub może zostać sprawdzone.

Kto aktualizuje stan tych elementów, ponieważ program zmiana warunków logicznie, jeśli element menu generuje polecenia, który jest obsługiwany przez, np. dokument, dobrym pomysłem dokumentu aktualizacji elementu menu. Dokument jest prawdopodobnie zawiera informacje, na którym bazuje aktualizacji.

Jeśli polecenie ma wiele obiektów interfejsu użytkownika (być może element menu i przycisku paska narzędzi), oba są kierowane do tej samej funkcji programu obsługi. To jest hermetyzowany kod aktualizacji interfejsu użytkownika dla wszystkich obiektów równoważnych interfejsu użytkownika w jednym miejscu.

Struktura udostępnia wygodne interfejs umożliwiający automatyczne aktualizowanie obiektów interfejsu użytkownika. Można wybrać w celu aktualizowania w inny sposób, ale interfejs dostarczony jest wydajne i łatwy w użyciu.

W poniższych tematach opisano użycie programy obsługi aktualizacji:

- [Kiedy są wywoływane programy obsługi aktualizacji](../mfc/when-update-handlers-are-called.md)

- [ON_UPDATE_COMMAND_UI — makro](../mfc/on-update-command-ui-macro.md)

- [Klasa CCmdUI](../mfc/the-ccmdui-class.md)

## <a name="see-also"></a>Zobacz też

[Menu](../mfc/menus-mfc.md)

