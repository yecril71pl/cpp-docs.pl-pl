---
title: Dodawanie funkcji do kontrolki złożonej
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 5de18f863831973af384d2456adb5b2214f0dd68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317425"
---
# <a name="adding-functionality-to-the-composite-control"></a>Dodawanie funkcji do kontrolki złożonej

Po wstawieniu wszelkich niezbędnych formantów do formantu złożonego następny krok obejmuje dodanie nowych funkcji. Ta nowa funkcja zazwyczaj dzieli się na dwie kategorie:

- Obsługa dodatkowych interfejsów i dostosowywanie zachowania sterowania złożonego za pomocą dodatkowych, określonych funkcji.

- Obsługa zdarzeń z zamkniętego formantu ActiveX (lub formantów).

Na potrzeby i zakres tego artykułu poniżej tej sekcji koncentruje się wyłącznie na obsłudze zdarzeń z formantów ActiveX.

> [!NOTE]
> Jeśli chcesz obsługiwać wiadomości z formantów systemu Windows, zobacz [Implementowanie okna,](../atl/implementing-a-window.md) aby uzyskać więcej informacji na temat obsługi wiadomości w pliku ATL.

Po wstawieniu formantu ActiveX do zasobu okna dialogowego kliknij prawym przyciskiem myszy formant i kliknij polecenie **Dodaj program obsługi zdarzeń**. Zaznacz zdarzenie, które chcesz obsłużyć, a następnie kliknij przycisk **Dodaj i edytuj**. Kod obsługi zdarzeń zostanie dodany do pliku .h formantu.

Punkty połączenia dla formantów ActiveX na formancie złożonym są automatycznie połączone i rozłączane za pośrednictwem wywołań [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

## <a name="see-also"></a>Zobacz też

[Podstawy kontroli złożonej](../atl/atl-composite-control-fundamentals.md)
