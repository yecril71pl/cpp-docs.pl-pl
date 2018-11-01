---
title: C.1 Notacja
ms.date: 11/04/2016
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
ms.openlocfilehash: 593450b6dd7dcb30adbf8546ad96ff716c6fbc1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473986"
---
# <a name="c1-notation"></a>C.1 Notacja

Reguły gramatyki składają się z nazwy dla inny niż końcowy, następuje dwukropek, następuje zastąpienie alternatywy w osobnych wierszach.

Termin składni wyrażenia<sub>zoptymalizowany pod kątem</sub> wskazuje, że termin jest opcjonalna w ramach wymiany.

Składni wyrażenia *termin*<sub>optseq</sub> jest odpowiednikiem *termin seq*<sub>zoptymalizowany pod kątem</sub> z następujące reguły dodatkowe:

*termin seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Termin*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termin seq* *termin*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termin seq* **,** *termin*