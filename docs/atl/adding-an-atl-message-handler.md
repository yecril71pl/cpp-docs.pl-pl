---
title: Dodawanie programu obsługi komunikatów ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 712f1b725afd52057deca8f05047c91bfc4affce
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753413"
---
# <a name="adding-an-atl-message-handler"></a>Dodawanie programu obsługi komunikatów ATL

Aby dodać program obsługi komunikatów (funkcja członkowska, która obsługuje komunikaty Windows) do formantu, należy najpierw wybrać formant w widoku klas. Następnie otwórz **właściwości** wybierz **wiadomości** ikonę, a następnie kliknij przycisk listy rozwijanej kontrolować w polu obok komunikatu wymagane. Spowoduje to dodanie deklarację dla obsługi wiadomości w pliku nagłówka kontrolki i szkielet implementację programu obsługi w plik CPP kontrolki. Zostanie również dodać mapy wiadomości i Dodaj wpis dla programu obsługi.

Dodawanie obsługi wiadomości w ATL jest podobne do dodawania programu obsługi komunikatów do klasy MFC. Zobacz [Dodawanie Handlera komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md) Aby uzyskać więcej informacji.

Tylko do dodawania programu obsługi komunikatów ATL mają zastosowanie następujące warunki:

- Programy obsługi komunikatów postępuj zgodnie z tej samej konwencji nazewnictwa jak MFC.

- Nowe wpisy mapy komunikatów są dodawane do mapy wiadomości głównego. Kreator nie może rozpoznać mapy komunikatów alternatywnej i tworzenie łańcuchów.

## <a name="see-also"></a>Zobacz też

[Implementowanie okna](../atl/implementing-a-window.md)

