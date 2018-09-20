---
title: Funkcje Członkowskie CWinApp z możliwością | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ced9d7d5f7f49df50e028a299f83ddebdc9fc2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395137"
---
# <a name="overridable-cwinapp-member-functions"></a>Funkcje członkowskie CWinApp z możliwością zastąpienia

[CWinApp](../mfc/reference/cwinapp-class.md) udostępnia kilka klucza możliwym do zastąpienia elementów członkowskich (`CWinApp` zastępuje te składowe z klasy [CWinThread](../mfc/reference/cwinthread-class.md), z którego `CWinApp` wywodzi się):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Run](../mfc/run-member-function.md)

- [Exitinstance —](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

Tylko `CWinApp` jest funkcja elementu członkowskiego, konieczne jest przesłonięcie `InitInstance`.

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
