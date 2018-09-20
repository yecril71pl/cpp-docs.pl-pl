---
title: Identyfikatory poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5087c271151793169cbf7350f78750044ccead0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446975"
---
# <a name="command-ids"></a>Identyfikatory poleceń

Polecenie opisano szczegółowo za pomocą jego Identyfikatora polecenia samodzielnie (zakodowany w **WM_COMMAND** komunikat). Ten identyfikator jest przypisany do obiektu interfejsu użytkownika, który generuje polecenia. Zazwyczaj identyfikatory są nazywane funkcji obiektu interfejsu użytkownika, które są przypisane.

Na przykład, usuń zaznaczenie wszystkich elementów w menu Edycja może zostać przypisana Identyfikatora takich jak **id_edit_clear_all —**. Biblioteka klas powoduje wstępne definiowanie niektóre identyfikatory, szczególnie w przypadku poleceń w ramach obsługi przez siebie, takie jak **id_edit_clear_all —** lub **id_file_open —**. Utwórz inne identyfikatory poleceń będzie samodzielnie.

Podczas tworzenia własnych menu w programie Visual C++ Edytor menu, jest dobrym rozwiązaniem postępuj zgodnie z biblioteki klas w konwencji nazewnictwa zgodnie z przedstawionymi **id_file_open —**. [Polecenia standardowe](../mfc/standard-commands.md) opisano standardowe polecenia, które są definiowane przez bibliotekę klas.

## <a name="see-also"></a>Zobacz też

[Obiekty interfejsu użytkownika i identyfikatory poleceń](../mfc/user-interface-objects-and-command-ids.md)

