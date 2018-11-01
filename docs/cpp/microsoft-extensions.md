---
title: Rozszerzenia Microsoft
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: d8104c2df2335e11dcb711108d566e0fdd069762
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592208"
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