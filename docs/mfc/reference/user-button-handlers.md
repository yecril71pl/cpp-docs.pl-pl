---
title: Programy obsługi przycisków użytkownika
ms.date: 11/04/2016
f1_keywords:
- ON_BN_HILITE
- ON_BN_DOUBLECLICKED
- ON_BN_CLICKED
- ON_BN_PAINT
- ON_BN_DISABLE
- ON_BN_UNHILITE
helpviewer_keywords:
- ON_BN_PAINT
- user buttons [MFC]
- ON_BN_DOUBLECLICKED [MFC]
- ON_BN_DISABLE [MFC]
- ON_BN_UNHILITE [MFC]
- ON_BN_HILITE [MFC]
- ON_BN_CLICKED [MFC]
ms.assetid: 410ea968-478f-4806-b7b8-5d7c8dc2bf42
ms.openlocfilehash: 55bf42d88cca805a8a75165e6fa868b9925d4d4f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542379"
---
# <a name="user-button-handlers"></a>Programy obsługi przycisków użytkownika

Następujące wpisy mapy odpowiadają prototypy funkcji.

|Wpis mapy|Prototyp funkcji|
|---------------|------------------------|
|ON_BN_CLICKED ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_BN_DISABLE ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_BN_DOUBLECLICKED ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_BN_HILITE ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_BN_PAINT ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_BN_UNHILITE ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|

## <a name="see-also"></a>Zobacz też

[Mapy komunikatów](../../mfc/reference/message-maps-mfc.md)

