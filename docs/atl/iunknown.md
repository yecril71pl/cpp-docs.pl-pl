---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 17561092c6cccbad264bb82d68dbef9c0e078f76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250298"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) jest interfejsem podstawowy każdego interfejsu COM.  Ten interfejs definiuje trzy metody: [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)), [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), i [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release). [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) pozwala użytkownikowi interfejsu poprosić obiekt o wskaźnik do innego z jego interfejsów. [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) i [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) zaimplementować na interfejsie zliczanie odwołań.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[IUnknown i dziedziczenia interfejsu](/windows/desktop/com/iunknown-and-interface-inheritance)
