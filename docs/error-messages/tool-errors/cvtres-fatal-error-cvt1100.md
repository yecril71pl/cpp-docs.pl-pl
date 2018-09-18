---
title: Błąd krytyczny CVTRES CVT1100 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CVT1100
dev_langs:
- C++
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18a5508301c54637fb34a751c8f1c4e307e47d50
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068965"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Błąd krytyczny CVTRES CVT1100

Zduplikowany zasób — typu: Nazwa: nazwa, język: języka, flagi: flagi, rozmiar: rozmiar

Danego zasobu został określony więcej niż jeden raz.

Ten błąd może wystąpić, jeśli konsolidator tworzy bibliotekę typów, a nie określiła [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) i 1 już korzysta z zasobów w projekcie. W takim przypadku Określ /TLBID i określ inną liczbę do 65535.