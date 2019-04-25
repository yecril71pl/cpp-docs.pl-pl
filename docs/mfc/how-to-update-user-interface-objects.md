---
title: 'Instrukcje: Aktualizowanie obiektów interfejsu użytkownika'
ms.date: 11/04/2016
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
ms.openlocfilehash: 0dee9bb48c11cf061af60ebaf9a80c0123d339be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160279"
---
# <a name="how-to-update-user-interface-objects"></a>Instrukcje: Aktualizowanie obiektów interfejsu użytkownika

Zazwyczaj elementy menu i przycisków paska narzędzi mają więcej niż jednego stanu. Na przykład element menu jest niedostępna (wygaszone), jeśli jest niedostępna w kontekście obecne. Elementy menu mogą być także zaznaczony lub niezaznaczony. Przycisk paska narzędzi można również zostaną wyłączone, jeśli jest niedostępny lub może zostać sprawdzone.

Kto aktualizuje stan tych elementów, ponieważ program zmiana warunków logicznie, jeśli element menu generuje polecenia, który jest obsługiwany przez, np. dokument, dobrym pomysłem dokumentu aktualizacji elementu menu. Dokument jest prawdopodobnie zawiera informacje, na którym bazuje aktualizacji.

Jeśli polecenie ma wiele obiektów interfejsu użytkownika (być może element menu i przycisku paska narzędzi), oba są kierowane do tej samej funkcji programu obsługi. To jest hermetyzowany kod aktualizacji interfejsu użytkownika dla wszystkich obiektów równoważnych interfejsu użytkownika w jednym miejscu.

Struktura udostępnia wygodne interfejs umożliwiający automatyczne aktualizowanie obiektów interfejsu użytkownika. Można wybrać w celu aktualizowania w inny sposób, ale interfejs dostarczony jest wydajne i łatwy w użyciu.

W poniższych tematach opisano użycie programy obsługi aktualizacji:

- [Kiedy są wywoływane programy obsługi aktualizacji](../mfc/when-update-handlers-are-called.md)

- [ON_UPDATE_COMMAND_UI — makro](../mfc/on-update-command-ui-macro.md)

- [Klasa CCmdUI](../mfc/the-ccmdui-class.md)

## <a name="see-also"></a>Zobacz także

[Menu](../mfc/menus-mfc.md)
