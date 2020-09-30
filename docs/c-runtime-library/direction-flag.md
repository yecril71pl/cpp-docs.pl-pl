---
title: Flaga kierunku
description: Opisuje efekt flagi kierunku procesora CPU w funkcjach środowiska uruchomieniowego Microsoft C.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: a8f06b3b8caf08e1d3db2159bfc730e25229733b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589994"
---
# <a name="direction-flag"></a>Flaga kierunku

Flaga kierunku jest flagą procesora CPU specyficzną dla wszystkich procesorów zgodnych z technologią Intel x86. Odnosi się do wszystkich instrukcji zestawu, które używają prefiksu przedstawiciela (Repeat), takiego jak MOVS, MOVSD, MOVSW i inne. Adresy podane do odpowiednich instrukcji są zwiększane, jeśli flaga kierunku jest wyczyszczona.

Procedury uruchomieniowe języka C zakładają, że flaga kierunku jest wyczyszczona. Jeśli używasz innych funkcji z funkcjami czasu wykonywania języka C, musisz się upewnić, że inne funkcje pozostawiają tylko flagę kierunku lub przywracają ją do oryginalnego stanu. Oczekiwano, że flaga kierunku ma być wyczyszczona przy wpisie sprawia, że kod czasu wykonywania jest szybszy i bardziej wydajny.

Funkcja biblioteki wykonawczej C, taka jak procedury manipulowania ciągiem i manipulowania buforem, oczekuje, że flaga kierunku ma być wyczyszczona.

## <a name="see-also"></a>Zobacz też

[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
