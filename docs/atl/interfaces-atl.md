---
title: Interfejsy (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 2373351330982623ffa602fd81bec61d0bc257b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492137"
---
# <a name="interfaces-atl"></a>Interfejsy (ATL)

Interfejs to sposób, w jaki obiekt uwidacznia swoją funkcjonalność na świecie zewnętrznym. W modelu COM interfejs jest tabelą wskaźników (na C++ przykład tablicą metod wirtualnych) do funkcji implementowanych przez obiekt. Tabela reprezentuje interfejs, a funkcje, do których wskazuje, są metodami tego interfejsu. Obiekt może uwidaczniać dowolną liczbę interfejsów.

Każdy interfejs jest oparty na podstawowym interfejsie COM, [IUnknown](../atl/iunknown.md). Metody `IUnknown` zezwalania na nawigację do innych interfejsów uwidocznionych przez obiekt.

Ponadto każdy interfejs ma unikatowy identyfikator interfejsu (IID). Ta unikatowość ułatwia obsługę wersji interfejsu. Nowa wersja interfejsu jest po prostu nowym interfejsem z nowym identyfikatorem IID.

> [!NOTE]
>  IID dla standardowych interfejsów COM i OLE są wstępnie zdefiniowane.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Obiekty COM i interfejsy](/windows/win32/com/com-objects-and-interfaces)
