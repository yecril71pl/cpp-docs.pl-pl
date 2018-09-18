---
title: Interfejsy (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef93476e669b923d642f79f480c602229d6a4322
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071162"
---
# <a name="interfaces-atl"></a>Interfejsy (ATL)

Interfejs jest sposób, w którym obiekt udostępnia funkcję na zewnątrz. W modelu COM interfejs jest tabela wskaźników (na przykład C++ vtable), funkcje implementowane przez obiekt. Tabela reprezentuje interfejs, a funkcje, które wskazuje są metody tego interfejsu. Obiekt można udostępnić dowolną liczbę interfejsów, jak go wybierze.

Każdy interfejs jest oparty na podstawowe interfejsu COM [IUnknown](../atl/iunknown.md). Metody `IUnknown` Zezwalaj nawigacji do innych interfejsów udostępnianych przez obiekt.

Ponadto każdy interfejs otrzymuje interfejsem Unikatowy identyfikator (IID). Unikatowość tej sprawia, że łatwo jest obsługiwać wersji interfejsu. Po prostu nowy interfejs, za pomocą nowego identyfikatora IID jest nowa wersja interfejsu.

> [!NOTE]
>  IID dla standardowych interfejsów COM i OLE są wstępnie zdefiniowane.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Obiekty COM i interfejsy](/windows/desktop/com/com-objects-and-interfaces)

