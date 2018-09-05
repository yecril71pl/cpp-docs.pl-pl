---
title: Rozszerzenia Microsoft | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5699ce82a6e8537f12da50fdcb8288da167ecca3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752242"
---
# <a name="microsoft-extensions"></a>Rozszerzenia Microsoft

*Instrukcja Asm*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm***instrukcji montażu* **;** <sub>zoptymalizowany pod kątem  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {***instrukcji montażu***};** <sub>zoptymalizowany pod kątem    </sub>

*instrukcji montażu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji montażu* **;** <sub>zoptymalizowany pod kątem</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji montażu* **;** *instrukcji montażu* **;** <sub>zoptymalizowany pod kątem</sub>

*MS modyfikator list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Modyfikator MS* *ms modyfikator listy*<sub>zoptymalizowany pod kątem</sub>

*Modyfikator MS*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** (zarezerwowane dla przyszłych wdrożeń)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** (zarezerwowane dla przyszłych wdrożeń)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** (zarezerwowane dla przyszłych wdrożeń)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*na podstawie modyfikator*

*na podstawie modyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *na podstawie typu* **)**

*na podstawie typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Nazwa*