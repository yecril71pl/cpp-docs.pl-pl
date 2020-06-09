---
title: Dostosowywanie na potrzeby MFC
ms.date: 11/04/2016
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
ms.openlocfilehash: 3b7597c3709ed700e82af94c78450ee5aff2d99b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622963"
---
# <a name="customization-for-mfc"></a>Dostosowywanie na potrzeby MFC

Ten temat zawiera wskazówki dotyczące dostosowywania aplikacji MFC.

## <a name="general-customizations"></a>Ogólne dostosowania

Stan aplikacji można zapisać i załadować do rejestru. Po włączeniu tej opcji aplikacja będzie ładować stan początkowy z rejestru. Jeśli zmienisz początkowy układ dokowania dla aplikacji, musisz wyczyścić dane rejestru dla swojej aplikacji. W przeciwnym razie dane w rejestrze zastąpią wszelkie zmiany wprowadzone w układzie początkowym.

## <a name="class-specific-customizations"></a>Dostosowania specyficzne dla klasy

Dodatkowe wskazówki dotyczące dostosowywania można znaleźć w następujących tematach:

- [Klasa CBasePane](reference/cbasepane-class.md)

- [Klasa CDockablePane](reference/cdockablepane-class.md)

- [Klasa CDockingManager](reference/cdockingmanager-class.md)

- [Klasa CMFCBaseTabCtrl](reference/cmfcbasetabctrl-class.md)

## <a name="additional-customization-tips"></a>Dodatkowe porady dotyczące dostosowywania

[Dostosowywanie klawiatury i myszy](keyboard-and-mouse-customization.md)

[Narzędzia zdefiniowane przez użytkownika](user-defined-tools.md)

## <a name="see-also"></a>Zobacz też

[Aplikacje klasyczne MFC](mfc-desktop-applications.md)<br/>
[Konsekwencje dostosowania związane z zabezpieczeniami](security-implications-of-customization.md)
