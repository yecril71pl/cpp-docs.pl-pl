---
title: Używanie list obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: cb95de134939e1b06e2a8b827424c986f8c48ef3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293878"
---
# <a name="using-an-image-list"></a>Używanie list obrazów

Typowy listy obrazów jest zgodny ze wzorcem poniżej:

- Konstruowania [CImageList](../mfc/reference/cimagelist-class.md) obiektu, a następnie wywołać jedno z przeciążeń z jego [Utwórz](../mfc/reference/cimagelist-class.md#create) funkcję, aby utworzyć listy obrazów i dołączyć go do `CImageList` obiektu.

- Jeśli obrazy nie zostały dodane po utworzeniu listy obrazów, dodawanie obrazów do listy obrazów, wywołując [Dodaj](../mfc/reference/cimagelist-class.md#add) lub [odczytu](../mfc/reference/cimagelist-class.md#read) funkcja elementu członkowskiego.

- Skojarz listy obrazów z formantem przez wywołanie funkcji właściwego członka tej kontrolki lub rysowanie obrazów z listy obrazów, samodzielnie za pomocą listy obrazów [Rysowanie](../mfc/reference/cimagelist-class.md#draw) funkcja elementu członkowskiego.

- Być może umożliwić użytkownikowi przeciągnij obraz, przeciągając go przy użyciu wbudowanej obsługi listy obrazów.

> [!NOTE]
>  Jeśli na liście obraz został utworzony za pomocą **nowe** operatora, użytkownik musi zniszczyć `CImageList` obiektu, kiedy są z nią zrobić.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
