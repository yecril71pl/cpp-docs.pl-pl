---
title: Dodawanie funkcji do kontrolek złożonych
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 9ad7ef3d80579804ac614fbefac1a042a9cf2fba
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299767"
---
# <a name="adding-functionality-to-the-composite-control"></a>Dodawanie funkcji do kontrolek złożonych

Po wstawieniu wszelkich niezbędnych opcji do kontrolek złożonych następny krok polega na dodawanie nowych funkcji. Ta nowa funkcja zwykle znajduje się na dwie kategorie:

- Obsługa dodatkowych interfejsów i dostosowywanie zachowania dotyczącego kontrolki złożonej za pomocą funkcje dodatkowe, przeznaczone specjalnie.

- Obsługa zdarzeń z zawartej kontrolki ActiveX (lub kontrolki).

Cel i zakres tego artykułu dalszej części tej sekcji skupiono się wyłącznie na Obsługa zdarzeń z kontrolki ActiveX.

> [!NOTE]
>  Jeśli trzeba obsługiwać komunikaty z kontrolek Windows, zobacz [Implementowanie okna](../atl/implementing-a-window.md) uzyskać więcej informacji dotyczących komunikatów w ATL.

Po wstawieniu kontrolki ActiveX w zasobie, okno dialogowe, kliknij prawym przyciskiem myszy formant, a następnie kliknij przycisk **dodać program obsługi zdarzeń**. Wybierz zdarzenie, aby obsłużyć, a następnie kliknij przycisk **dodawać i edytować**. Kod obsługi zdarzeń zostaną dodane do plik .h klasy formantu.

Punkty połączenia dla formantów ActiveX w złożonej kontrolki są automatycznie połączone i rozłączona za pośrednictwem wywołania [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

## <a name="see-also"></a>Zobacz także

[Podstawy złożonych kontrolek](../atl/atl-composite-control-fundamentals.md)
