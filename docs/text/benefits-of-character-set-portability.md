---
title: Zalety zestawu znaków przenośność | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 115a4524f3b11d847291015f3bee5ca10f628310
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423445"
---
# <a name="benefits-of-character-set-portability"></a>Zalety przenośności zestawu znaków

Możesz korzystać z przy użyciu funkcji przenoszenia środowiska wykonawczego MFC i C, nawet wtedy, gdy nie można obecnie podjąć zamierzasz internationalize aplikacji:

- Kodowanie portably sprawia, że Twój kod podstawowy elastyczne. Można później przenieść je łatwo do standardu Unicode i MBCS.

- Przy użyciu standardu Unicode sprawia, że aplikacje dla Windows bardziej wydajne. Ponieważ Windows używa Unicode, innego niż Unicode ciągi przekazywane do i z systemu operacyjnego musi podlegać translacji, która wiąże się obciążenie.


## <a name="see-also"></a>Zobacz też

[Unicode i MBCS](../text/unicode-and-mbcs.md)<br/>
[Obsługa formatu Unicode](../text/support-for-unicode.md)