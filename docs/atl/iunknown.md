---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 9c9faa4cffcdc8e6840dfbbe141cb63f51155ded
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492074"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jest interfejsem podstawowym każdego innego interfejsu com.  Ten interfejs definiuje trzy metody: [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)), [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)i [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). Funkcja [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) umożliwia użytkownikowi interfejsu poproszenie obiektu o wskaźnik do innego interfejsu. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [wydanie](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) Implementuj zliczanie odwołań w interfejsie.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Interfejs IUnknown i dziedziczenie interfejsu](/windows/win32/com/iunknown-and-interface-inheritance)
