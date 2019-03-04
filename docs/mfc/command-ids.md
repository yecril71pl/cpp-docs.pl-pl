---
title: Identyfikatory poleceń
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: 76071105e72f1ca4a851b9cdb76d5f1a96f44edb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274582"
---
# <a name="command-ids"></a>Identyfikatory poleceń

Polecenie opisano szczegółowo za pomocą jego Identyfikatora polecenia samodzielnie (zakodowany w **WM_COMMAND** komunikat). Ten identyfikator jest przypisany do obiektu interfejsu użytkownika, który generuje polecenia. Zazwyczaj identyfikatory są nazywane funkcji obiektu interfejsu użytkownika, które są przypisane.

Na przykład, usuń zaznaczenie wszystkich elementów w menu Edycja może zostać przypisana Identyfikatora takich jak **id_edit_clear_all —**. Biblioteka klas powoduje wstępne definiowanie niektóre identyfikatory, szczególnie w przypadku poleceń w ramach obsługi przez siebie, takie jak **id_edit_clear_all —** lub **id_file_open —**. Utwórz inne identyfikatory poleceń będzie samodzielnie.

Podczas tworzenia własnych menu w programie Visual C++ Edytor menu, jest dobrym rozwiązaniem postępuj zgodnie z biblioteki klas w konwencji nazewnictwa zgodnie z przedstawionymi **id_file_open —**. [Polecenia standardowe](../mfc/standard-commands.md) opisano standardowe polecenia, które są definiowane przez bibliotekę klas.

## <a name="see-also"></a>Zobacz także

[Obiekty interfejsu użytkownika i identyfikatory poleceń](../mfc/user-interface-objects-and-command-ids.md)
