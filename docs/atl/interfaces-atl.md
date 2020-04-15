---
title: Interfejsy (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 56d5a010bc28257dce181ee33e0ddf74655ccd3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319384"
---
# <a name="interfaces-atl"></a>Interfejsy (ATL)

Interfejs jest sposób, w jaki obiekt udostępnia swoje funkcje do świata zewnętrznego. W COM interfejs jest tabelą wskaźników (takich jak C++ vtable) do funkcji zaimplementowanych przez obiekt. Tabela reprezentuje interfejs, a funkcje, do których wskazuje są metody tego interfejsu. Obiekt może udostępnić dowolną liczbę interfejsów.

Każdy interfejs jest oparty na podstawowym interfejsie COM, [IUnknown](../atl/iunknown.md). Metody zezwalają `IUnknown` na nawigację do innych interfejsów udostępniane przez obiekt.

Ponadto każdy interfejs otrzymuje unikatowy identyfikator interfejsu (IID). Ta unikatowość ułatwia obsługę wersji interfejsu. Nowa wersja interfejsu jest po prostu nowy interfejs, z nowym IID.

> [!NOTE]
> Identyfikatory IID dla standardowych interfejsów COM i OLE są wstępnie zdefiniowane.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Obiekty i interfejsy COM](/windows/win32/com/com-objects-and-interfaces)
