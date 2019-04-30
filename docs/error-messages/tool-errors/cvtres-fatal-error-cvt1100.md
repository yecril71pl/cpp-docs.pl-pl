---
title: Błąd krytyczny CVTRES CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: c7e65ccc79852ec99dd2406398fe1b3cdecacde7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406278"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Błąd krytyczny CVTRES CVT1100

Zduplikowany zasób — typu: Nazwa: nazwa, język: języka, flagi: flagi, rozmiar: rozmiar

Danego zasobu został określony więcej niż jeden raz.

Ten błąd może wystąpić, jeśli konsolidator tworzy bibliotekę typów, a nie określiła [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) i 1 już korzysta z zasobów w projekcie. W takim przypadku Określ /TLBID i określ inną liczbę do 65535.