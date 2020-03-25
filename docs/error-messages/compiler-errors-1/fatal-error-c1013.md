---
title: Błąd krytyczny C1013
ms.date: 11/04/2016
f1_keywords:
- C1013
helpviewer_keywords:
- C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
ms.openlocfilehash: 88b748aa81580191088e0c1f3f9d09664af67013
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204779"
---
# <a name="fatal-error-c1013"></a>Błąd krytyczny C1013

ograniczenie kompilatora: zbyt wiele otwartych nawiasów

Wyrażenie zawiera zbyt wiele poziomów nawiasów w jednym wyrażeniu. Uprość wyrażenie lub Podziel je na wiele instrukcji.

W systemach starszych C++ niż Visual 6,0 Service Pack 3 limit zagnieżdżonych nawiasów w jednym wyrażeniu wynosił 59. Obecnie limit zagnieżdżonych nawiasów wynosi 256.
