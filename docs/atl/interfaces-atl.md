---
title: Interfejsy (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 5416fb8a99420f0f6c84318753ee3399ccf5db2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250317"
---
# <a name="interfaces-atl"></a>Interfejsy (ATL)

Interfejs jest sposób, w którym obiekt udostępnia funkcję na zewnątrz. W modelu COM interfejs jest tabela wskaźników (na przykład C++ vtable), funkcje implementowane przez obiekt. Tabela reprezentuje interfejs, a funkcje, które wskazuje są metody tego interfejsu. Obiekt można udostępnić dowolną liczbę interfejsów, jak go wybierze.

Każdy interfejs jest oparty na podstawowe interfejsu COM [IUnknown](../atl/iunknown.md). Metody `IUnknown` Zezwalaj nawigacji do innych interfejsów udostępnianych przez obiekt.

Ponadto każdy interfejs otrzymuje interfejsem Unikatowy identyfikator (IID). Unikatowość tej sprawia, że łatwo jest obsługiwać wersji interfejsu. Po prostu nowy interfejs, za pomocą nowego identyfikatora IID jest nowa wersja interfejsu.

> [!NOTE]
>  IID dla standardowych interfejsów COM i OLE są wstępnie zdefiniowane.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Obiekty COM i interfejsy](/windows/desktop/com/com-objects-and-interfaces)
