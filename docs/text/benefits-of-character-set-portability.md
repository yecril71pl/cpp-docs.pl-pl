---
title: Zalety przenośności zestawu znaków
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
ms.openlocfilehash: 0ca7e46cabb2d98a64a244863f8574a3e9e2a456
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750009"
---
# <a name="benefits-of-character-set-portability"></a>Zalety przenośności zestawu znaków

Możesz korzystać z przy użyciu funkcji przenoszenia środowiska wykonawczego MFC i C, nawet wtedy, gdy nie można obecnie podjąć zamierzasz internationalize aplikacji:

- Kodowanie portably sprawia, że Twój kod podstawowy elastyczne. Można później przenieść je łatwo do standardu Unicode i MBCS.

- Przy użyciu standardu Unicode sprawia, że aplikacje dla Windows bardziej wydajne. Ponieważ Windows używa Unicode, innego niż Unicode ciągi przekazywane do i z systemu operacyjnego musi podlegać translacji, która wiąże się obciążenie.

## <a name="see-also"></a>Zobacz także

[Unicode i MBCS](../text/unicode-and-mbcs.md)<br/>
[Obsługa formatu Unicode](../text/support-for-unicode.md)
