---
title: Funkcje członkowskie CWinApp z możliwością zastąpienia
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 9f1098e305606df9463e308466b7864b019d5a00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459283"
---
# <a name="overridable-cwinapp-member-functions"></a>Funkcje członkowskie CWinApp z możliwością zastąpienia

[CWinApp](../mfc/reference/cwinapp-class.md) udostępnia kilka klucza możliwym do zastąpienia elementów członkowskich (`CWinApp` zastępuje te składowe z klasy [CWinThread](../mfc/reference/cwinthread-class.md), z którego `CWinApp` wywodzi się):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Uruchom](../mfc/run-member-function.md)

- [Exitinstance —](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

Tylko `CWinApp` jest funkcja elementu członkowskiego, konieczne jest przesłonięcie `InitInstance`.

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
