---
title: Flaga kierunku
ms.date: 11/04/2016
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: 04e096c6a62f806f4c214745a8401b1730eda3a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443382"
---
# <a name="direction-flag"></a>Flaga kierunku

Flaga kierunku jest flagą procesora CPU specyficzną dla wszystkich procesorów zgodnych z technologią Intel x86. Odnosi się do wszystkich instrukcji zestawu, które używają prefiksu przedstawiciela (Repeat), takiego jak MOVS, MOVSD, MOVSW i inne. Adresy podane do odpowiednich instrukcji są zwiększane, jeśli flaga kierunku jest wyczyszczona.

Procedury uruchomieniowe języka C zakładają, że flaga kierunku jest wyczyszczona. Jeśli używasz innych funkcji z funkcjami czasu wykonywania języka C, musisz się upewnić, że inne funkcje pozostawiają tylko flagę kierunku lub przywracają ją do oryginalnego stanu. Oczekiwano, że flaga kierunku ma być wyczyszczona przy wpisie sprawia, że kod czasu wykonywania jest szybszy i bardziej wydajny.

Funkcja biblioteki wykonawczej C, taka jak procedury manipulowania ciągiem i manipulowania buforem, oczekuje, że flaga kierunku ma być wyczyszczona.

## <a name="see-also"></a>Zobacz też

[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)
