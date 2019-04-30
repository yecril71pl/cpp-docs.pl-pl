---
title: Kiedy są wywoływane programy obsługi aktualizacji
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- command routing [MFC], update commands
- toolbar buttons [MFC], enabling
- disabling toolbar buttons
- menus [MFC], initializing
- update handlers [MFC]
- disabling menu items
- toolbars [MFC], updating
- menus [MFC], updating as context changes
- toolbar controls [MFC], updated during OnIdle method [MFC]
- menu items, enabling
- command routing [MFC], update handlers
- update handlers, calling
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
ms.openlocfilehash: 4a52c147d1abf02b7c5e89abf868f87a07ab32cc
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346064"
---
# <a name="when-update-handlers-are-called"></a>Kiedy są wywoływane programy obsługi aktualizacji

Załóżmy, że użytkownik kliknie przycisk myszy w menu Plik, która generuje komunikat WM_INITMENUPOPUP. Mechanizm struktury zbiorczo uaktualnienia wszystkie elementy w menu Plik, zanim menu zostanie rozwinięte, dzięki czemu użytkownik może wyświetlić go.

Aby to zrobić, trasy framework zaktualizować poleceń dla wszystkich elementów menu w menu podręcznym wzdłuż standardowego routingu poleceń. Obiekty docelowe poleceń na routing mógł zaktualizować wszystkie elementy menu, dopasowując polecenia update z wpisem odpowiednie mapy komunikatów (w postaci `ON_UPDATE_COMMAND_UI`) i wywoływania funkcji "procedury obsługi aktualizacji". W związku z tym do menu z elementami menu sześć sześć polecenia aktualizacji są wysyłane. Jeśli istnieje procedura obsługi aktualizacji dla Identyfikatora polecenia elementu menu, jest on nazywany wykonać aktualizację. Jeśli nie, w ramach sprawdza istnienie programu obsługi dla tego Identyfikatora polecenia i włącza lub wyłącza elementu menu, zgodnie z potrzebami.

Jeśli struktura nie może znaleźć `ON_UPDATE_COMMAND_UI` zapisu podczas routingu poleceń, automatycznie umożliwia obiektu interfejsu użytkownika w przypadku `ON_COMMAND` wpis gdzieś przy użyciu tego samego identyfikatora polecenia. W przeciwnym razie wyłącza obiektu interfejsu użytkownika. W związku z tym aby upewnić się, że obiekt interfejsu użytkownika jest włączona, należy dostarczyć obsługi dla polecenia, które generuje obiekt lub podać procedury obsługi aktualizacji. Zobacz ilustrację w temacie [obiekty interfejsu użytkownika i identyfikatory poleceń](../mfc/user-interface-objects-and-command-ids.md).

Istnieje możliwość wyłączyć domyślne wyłączenie obiektów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable) składowej klasy `CFrameWnd` w *odwołanie MFC*.

Inicjowanie menu odbywa się automatycznie w ramach, wykonywane, kiedy aplikacja otrzymuje komunikat WM_INITMENUPOPUP. Podczas wykonywania pętli bezczynności struktura wyszukuje polecenia routing programy obsługi aktualizacji przycisk w taki sam sposób jak w przypadku menu.

## <a name="see-also"></a>Zobacz także

[Instrukcje: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)
