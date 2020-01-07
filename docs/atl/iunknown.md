---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 6adfbdc59b2a63aa2f2bb39e27139ca977ba9465
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298756"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jest interfejsem podstawowym każdego innego interfejsu com.  Ten interfejs definiuje trzy metody: [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)), [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)i [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). Funkcja [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) umożliwia użytkownikowi interfejsu poproszenie obiektu o wskaźnik do innego interfejsu. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [wydanie](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) Implementuj zliczanie odwołań w interfejsie.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Interfejs IUnknown i dziedziczenie interfejsu](/windows/win32/com/iunknown-and-interface-inheritance)
