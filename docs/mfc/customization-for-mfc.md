---
title: Dostosowywanie na potrzeby MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 640d6726623e8fb6d563153823f449f7caefcf30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385004"
---
# <a name="customization-for-mfc"></a>Dostosowywanie na potrzeby MFC

Ten temat zawiera wskazówki dotyczące dostosowywania aplikacji MFC.

## <a name="general-customizations"></a>Dostosowania ogólne

Można zapisać i załadować stanu aplikacji do rejestru. Po włączeniu tej opcji, aplikacja będzie ładować stanu początkowego z rejestru. Jeśli zmienisz wstępny układ dokowania dla aplikacji, należy wyczyścić dane rejestru dla aplikacji. W przeciwnym razie dane w rejestrze zastąpią wszelkie zmiany wprowadzone do początkowego układu.

## <a name="class-specific-customizations"></a>Dostosowania swoiste dla klas

Wskazówki dotyczące dodatkowych dostosowań można znaleźć w następujących tematach:

- [Klasa CBasePane](../mfc/reference/cbasepane-class.md)

- [Klasa CDockablePane](../mfc/reference/cdockablepane-class.md)

- [Klasa CDockingManager](../mfc/reference/cdockingmanager-class.md)

- [Klasa CMFCBaseTabCtrl](../mfc/reference/cmfcbasetabctrl-class.md)

## <a name="additional-customization-tips"></a>Porady dotyczące dostosowywania dodatkowe

[Dostosowywanie klawiatury i myszy](../mfc/keyboard-and-mouse-customization.md)

[Narzędzia zdefiniowane przez użytkownika](../mfc/user-defined-tools.md)

## <a name="see-also"></a>Zobacz też

[Aplikacje klasyczne MFC](../mfc/mfc-desktop-applications.md)<br/>
[Konsekwencje dostosowania związane z zabezpieczeniami](../mfc/security-implications-of-customization.md)

