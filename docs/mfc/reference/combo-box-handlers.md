---
title: Programy obsługi pól kombi
ms.date: 11/04/2016
f1_keywords:
- ON_CBN_KILLFOCUS
- ON_CBN_ERRSPACE
- ON_CBN_EDITCHANGE
- ON_CBN_CLOSEUP
- ON_CBN_DBLCLK
- ON_CBN_EDITUPDATE
- ON_CBN_DROPDOWN
- ON_CBN_SELENDOK
- ON_CBN_SELCHANGE
- ON_CBN_SETFOCUS
- ON_CBN_SELENDCANCEL
helpviewer_keywords:
- ON_CBN_CLOSEUP
- ON_CBN_SETFOCUS
- ON_CBN_DBLCLK
- ON_CBN_SELENDCANCEL
- ON_CBN_DROPDOWN
- ON_CBN_EDITUPDATE
- ON_CBN_KILLFOCUS
- combo boxes [MFC], handlers
- ON_CBN_EDITCHANGE
- ON_CBN_ERRSPACE
- ON_CBN_SELENDOK
- ON_CBN_SELCHANGE
ms.assetid: 7f092412-01b7-4242-95ec-41ba506b9d71
ms.openlocfilehash: 44fbf74174df833badd18ee29416ed936ea69293
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438132"
---
# <a name="combo-box-handlers"></a>Programy obsługi pól kombi

Następujące wpisy mapy odpowiadają prototypy funkcji.

|Wpis mapy|Prototyp funkcji|
|---------------|------------------------|
|ON_CBN_CLOSEUP ( \<id >, \<memberFxn >)|(afx_msg void memberFxn)|
|ON_CBN_DBLCLK ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_CBN_DROPDOWN ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_CBN_EDITCHANGE ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_CBN_EDITUPDATE ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_CBN_ERRSPACE ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_CBN_KILLFOCUS ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_CBN_SELCHANGE ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_CBN_SELENDCANCEL ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_CBN_SELENDOK ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|
|ON_CBN_SETFOCUS ( \<id >, \<memberFxn >)|() void memberFxn afx_msg;|

## <a name="see-also"></a>Zobacz też

[Mapy komunikatów](../../mfc/reference/message-maps-mfc.md)

