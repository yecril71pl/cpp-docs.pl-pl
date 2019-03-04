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
ms.openlocfilehash: 35db009f86a0cb984f70a349a3ecdd93bfefb0f0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261248"
---
# <a name="overridable-cwinapp-member-functions"></a>Funkcje członkowskie CWinApp z możliwością zastąpienia

[CWinApp](../mfc/reference/cwinapp-class.md) udostępnia kilka klucza możliwym do zastąpienia elementów członkowskich (`CWinApp` zastępuje te składowe z klasy [CWinThread](../mfc/reference/cwinthread-class.md), z którego `CWinApp` wywodzi się):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Uruchom](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

Tylko `CWinApp` jest funkcja elementu członkowskiego, konieczne jest przesłonięcie `InitInstance`.

## <a name="see-also"></a>Zobacz także

[CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)
