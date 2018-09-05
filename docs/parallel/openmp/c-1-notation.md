---
title: C.1 Notacja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d3ada700955c3acd2e96aa3e8a98c25c51393c1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766155"
---
# <a name="c1-notation"></a>C.1 Notacja
Reguły gramatyki składają się z nazwy dla inny niż końcowy, następuje dwukropek, następuje zastąpienie alternatywy w osobnych wierszach.

Termin składni wyrażenia<sub>zoptymalizowany pod kątem</sub> wskazuje, że termin jest opcjonalna w ramach wymiany.

Składni wyrażenia *termin*<sub>optseq</sub> jest odpowiednikiem *termin seq*<sub>zoptymalizowany pod kątem</sub> z następujące reguły dodatkowe:

*termin seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Termin*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termin seq* *termin*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termin seq* **,** *termin*