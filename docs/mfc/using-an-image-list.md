---
title: Używanie list obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 0d9566739a15e5d216eb052a7265313850515648
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366574"
---
# <a name="using-an-image-list"></a>Używanie list obrazów

Typowe użycie listy obrazów następuje poniżej wzorze:

- Konstruuj [CImageList](../mfc/reference/cimagelist-class.md) obiektu i wywołać jeden z przeciążeń jego [Tworzenie](../mfc/reference/cimagelist-class.md#create) `CImageList` funkcji, aby utworzyć listę obrazów i dołączyć go do obiektu.

- Jeśli podczas tworzenia listy obrazów nie dodano obrazów, dodaj obrazy do listy obrazów, wywołując funkcję [Dodaj](../mfc/reference/cimagelist-class.md#add) lub [Odczytuj.](../mfc/reference/cimagelist-class.md#read)

- Skojarz listę obrazów z formantem, wywołując odpowiednią funkcję elementu członkowskiego tego formantu lub samodzielnie rysuj obrazy z listy obrazów za pomocą funkcji elementu członkowskiego [Rysowanie](../mfc/reference/cimagelist-class.md#draw) listy obrazów.

- Być może zezwolić użytkownikowi na przeciąganie obrazu przy użyciu wbudowanej obsługi listy obrazów do przeciągania.

> [!NOTE]
> Jeśli lista obrazów została utworzona z **nowym** operatorem, należy zniszczyć `CImageList` obiekt po zakończeniu z nim.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Formanty](../mfc/controls-mfc.md)
