---
title: Funkcje członkowskie CWinApp z możliwością zastąpienia
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 7ae72a52c37582f8398ebc03f404ff105fe14650
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624012"
---
# <a name="overridable-cwinapp-member-functions"></a>Funkcje członkowskie CWinApp z możliwością zastąpienia

[CWinApp](reference/cwinapp-class.md) udostępnia kilka kluczowych funkcji Członkowskich ( `CWinApp` zastępuje te elementy z klasy [CWinThread](reference/cwinthread-class.md), z których `CWinApp` wynika):

- [InitInstance](initinstance-member-function.md)

- [Uruchom](run-member-function.md)

- [ExitInstance](exitinstance-member-function.md)

- [OnIdle](onidle-member-function.md)

Jedyną `CWinApp` funkcją członkowską, którą należy przesłonić, jest `InitInstance` .

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](cwinapp-the-application-class.md)
