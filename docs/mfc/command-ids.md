---
title: Identyfikatory poleceń
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: f7d675891904301b16aafe3acb2c294eede6d8d8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619040"
---
# <a name="command-ids"></a>Identyfikatory poleceń

Polecenie jest w pełni opisane za pomocą samego identyfikatora polecenia (zakodowane w wiadomości **WM_COMMAND** ). Ten identyfikator jest przypisany do obiektu interfejsu użytkownika, który generuje polecenie. Zwykle identyfikatory są nazywane dla funkcji obiektu interfejsu użytkownika, do którego są przypisane.

Na przykład Wyczyść wszystkie elementy w menu Edycja mogą mieć przypisany identyfikator, taki jak **ID_EDIT_CLEAR_ALL**. Biblioteka klas wstępnie definiuje niektóre identyfikatory, szczególnie dla poleceń obsługiwanych przez platformę, takich jak **ID_EDIT_CLEAR_ALL** lub **ID_FILE_OPEN**. Inne identyfikatory poleceń utworzysz samodzielnie.

Gdy tworzysz własne menu w edytorze menu Visual C++, dobrym pomysłem jest przestrzeganie konwencji nazewnictwa biblioteki klas, jak pokazano na **ID_FILE_OPEN**. [Standardowe polecenia](standard-commands.md) objaśniają standardowe polecenia zdefiniowane przez bibliotekę klas.

## <a name="see-also"></a>Zobacz też

[Obiekty interfejsu użytkownika i identyfikatory poleceń](user-interface-objects-and-command-ids.md)
