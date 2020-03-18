---
title: Funkcje członkowskie CWinApp z możliwością zastąpienia
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 28ba243bd755e25db5f2cb03d08013f082fbc918
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447265"
---
# <a name="overridable-cwinapp-member-functions"></a>Funkcje członkowskie CWinApp z możliwością zastąpienia

[CWinApp](../mfc/reference/cwinapp-class.md) udostępnia kilka kluczowych funkcji członkowskich (`CWinApp` zastępuje te elementy członkowskie z klasy [CWinThread](../mfc/reference/cwinthread-class.md), z których `CWinApp` wynika):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Run](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

Jedyną `CWinApp` funkcją członkowską, którą należy przesłonić, jest `InitInstance`.

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
